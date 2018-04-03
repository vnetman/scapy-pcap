
scapy_pcap.py: Generate a pcap with multiple TCP sessions at specified bitrates
===============================================================================

The purpose of this script is to generate a single .pcap file.

./scapy_pcap.py --out <file.pcap>

The .pcap file contains packets for one or more complete TCP sessions (starting
from the SYN handshake to the FIN/ACK sequence).

The parameters of the TCP sessions (i.e. addresses, packet lengths, bitrates
etc.) are coded in the script itself, because it is too cumbersome to specify
these on the command line.

It is possible to start a TCP session whilst others are in progress (i.e. it is
not necessary to start a session only after the previous one has finished).

Packet lengths as well as bitrates can also be specified on a per-session basis.

E.g. you can ask for a pcap file containing three TCP streams, the first
starting at time 0s and lasting 300 seconds, the second starting at time 10s and
lasting 110 seconds, and the third starting at time 100s and lasting 45 seconds,
i.e. like this:

           0                                300
 Stream A: |---------------------------------| 30kbps
                                               Packet len = 1400 bytes 

             10          120
 Stream B:    |-----------|                    1Mbps
                                               Packet len = 580 bytes

                       100   145     
 Stream D:              |-----|                4Mbps
                                               Packet len = 100 bytes

scapy_pcap can be used to generate .pcap files for consumption by other programs
such as traffic analytics tools.
