---
title: "Odd networking issue"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by socaltenor42 on 2008-09-22
I have built a server with Ubuntu Gutsy, and I am having an issue with connectivity. Using ethtool, I have found there is a link detected, and I have ensured there is no IP conflict on the segment. One thing I noticed (and what has prompted me to post here) is the output of ifconfig. I see that inbound packets (RX) packets to the NIC are incrementing, while outbound packets (TX) are not- the count remains at 0. Also, the txqueuelen is 1000. What does that mean (I know it's queue length, but does that mean that the card knows there are packets actually queued to be sent out the interface, and for some reason they are not due to a misconfiguration or other reason?). I just think I should see tx packets incrementing, since I am pinging everything in the segment to test.

---

### Post by Iowan on 2008-09-22
Firewall?

[Edit] Guess not if pings are working... are they?

---

### Post by socaltenor42 on 2008-09-22
no firewall...just a switch with a vlan configured where every system in that vlan can talk to each other.

---

### Post by socaltenor42 on 2008-09-24
I just wonder if there is an IRQ conflict. Is there a way I could verify that?

---

### Post by Iowan on 2008-09-24
Can you ping this machine from another box?

---

### Post by cariboo on 2008-09-24
It could be a couple of things, are the ip addresses in the same netblock, and are the computers in the same workgroup?

Jim

---

### Post by socaltenor42 on 2008-09-25
I cannot ping the Ubuntu server from another server. Secondly, the servers are in the same IP segment (I always triple check the configs), but I have not gone so far to assign this server to a workgroup. Still...as long as the servers are on the same segment, I should see ICMP replies.I looked at the configs in ifconfig and /etc/network/interfaces to verify settings are correct. Plus, I have ensured the interface is up.

---

### Post by willca on 2008-09-25
Are you able to try to look in the interface whats happening by running tcpdump against it?

sudo tcpdump -nv -i eth0

---

### Post by socaltenor42 on 2008-09-25
I did that...great tip by the way. But below is the output. Looks like the NIC is receiving broadcasted ARP requests. Now I am very confounded on why I wouldn't receive ICMP replies from any of the servers on the 10.2.1.x segment.

---

### Post by socaltenor42 on 2008-09-25
What's odd is that I see all these packets being processed (ARP requests mainly), but ICMP packets inbound or outbound are not being processed. Has anyone seen anything similar to this before?

---

### Post by socaltenor42 on 2008-09-25
Here's another thing. I got this info from the switch to which this server is connected:

[COLOR="Red"]  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     **176 packets input**, 14702 bytes, 0 no buffer
     Received 30 broadcasts (0 multicasts)
     0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored
     0 watchdog, 18 multicast, 0 pause input
     0 input packets with dribble condition detected
     **3643858 packets output**, 337566924 bytes, 0 underruns
     0 output errors, 0 collisions, 0 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier, 0 PAUSE output
     0 output buffer failures, 0 output buffers swapped out[/COLOR]

In other words...the server is just not sending any packets OUT from the interface...but it is processing inbound packets in bunches. Very weird to me.

---

### Post by gpredrag on 2008-09-25
very weird.
I would realy double check cables and connectors. Also what happens when you change the port of the switch? For example, swap ports on the switch between some regular working host and this problematic.

---

### Post by socaltenor42 on 2008-09-26
Ok...I switched the port to a known good port and swapped cables-still the same result. Is there anything else I can look at in configs anywhere?

---

