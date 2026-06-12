---
title: "Tracking packets within the network stack"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by colin36 on 2015-02-02
Hi,

I have a case where we run several servers with an application behind it. I don't have the ability to modify the application.

We are investigating connections from a remote party that are going unanswered so I set up iptables logging for SYN packets on the relevant port.

The remote admins provided timestamped logs for the unanswered connections and I checked the iptables log. Sure enough it saw the SYN packets and logged them. The application (which logs a huge amount of information) didn't record even seeing the connection.

The system concerned is a mail system and the remote party is a large mail delivery company that one of our clients uses thus they are probably the largest single traffic generator for this application. Noone else has reported these issues but they may have not noticed.

I've seen mention of dropwatch but that seems to be a redhat utility. I'm used to using packet sniffered but don't know how to address this issue.

I need to find out if something in the system or kernel is dropping the packets or if it is the application not responding. None of our monitoring indicates a high load on any part of the system so there is in theory no reason why either would drop packets without logging them. These are virtual machines so as a test I doubled the resources allocated and the issue didn't change.

Any suggestions on how to proceed would be very much appreciated as at the moment all I can think of is putting a load balancer in front and firing up more instances to ensure that every connection gets answered.

---

### Post by The Cog on 2015-02-02
It may be informative to run tcpdump to get a print-out of the packets, just to check that the SYN, SYN-ACK, ACK 3-way handshake completes properly. It should do, because it's the OS and not the application that performs that handshake. But it might give you a clue. Something like:
sudo tcpdump -np host 1.2.3.4 and tcp port 25
Actually, with -w, -W -C, -G you can write sniffer compatible capture files for later analysis if you prefer.

---

### Post by colin36 on 2015-02-02
Unfortunately the remote party in question has a distributed architecture and emails can come from any random address out of 20 or so subnets. We don't have the spare storage to capture everything that comes from them though I wonder if I can make iptables log SYN-ACK outbound as well as SYN in without much hassle. 

If the SYN-ACK are missing, I'd at least be able to identify affected connections myself without having to rely on a third party inform me of unanswered connections..

I've done some reading on the sysctl.conf options hoping to find something that would cause anything dropped to be logged but didn't see anything. I have done a bit of tuning with:

# NIC/TCP Tuning
net.ipv4.tcp_max_syn_backlog = 4096
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.core.netdev_max_backlog = 30000
net.ipv4.tcp_congestion_control=cubic

---

### Post by The Cog on 2015-02-02
This seems to catch just SYN, SYN-ACK and RST packets:
tcpdump -np 'tcp[tcpflags] & (tcp-syn|tcp-fin|tcp-rst) != 0 and net 212.58.0.0/16 and tcp port 80'
Might help.

P.S.
With iptables, you can do rate limiting. I'm sure that with some fiddling you could rate limit the logging to just the first n packets of a connection, but not actually drop the packets (-j LOG instead of -j DROP) Google for "iptables rate limit".

---

