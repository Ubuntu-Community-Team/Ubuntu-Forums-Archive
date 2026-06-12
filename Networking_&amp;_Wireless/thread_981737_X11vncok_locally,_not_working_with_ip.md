---
title: "X11vnc:ok locally, not working with ip"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by linuxgr on 2008-11-14
Hi everybody.

I am using X11VNC to remotely access my pc. When in the local network, I can access the pc using

vncviewer pcdomain:0

but when using the internet ip address(i.e. when I am not home)

vncviewer xxx.xxx.xxx.xxx:0

it says "connection refused". I have already changed the firewall settings on my 2-wire 2701-HG-B router and allowed port 5900. I have also used many tools to verify that 5900 is open.

Is there something else I should do? By the way, i am also experimenting with the external ip when I am still on the local network(when i am home, using the laptop i try vncviewer xxx.xxx.xxx.xxx:0 trying different things). Is this ok? Can I do that when the laptop has the same external ip with the pc(when it is connected to the same modem)?

Thanks

---

### Post by linuxgr on 2008-11-14
anyone???

---

### Post by jonobr on 2008-11-14
if your sure the port is open and forwarding to the right machine, and the logs on the router seem to concur
I recommend getting some network sniffing tracing.
Download wireshark or tcpdump.
Run a pcap trace on interface from your machine which is trying to access remotely.

Wireshark gui wise is pretty easy to capture
if you prefer to install and use tcpdump, thats even better,
after installing tcpdump (it actually may be installed already)
execute
tcpdump -w test.pcap -s 1550 port 5900

where 
tcpdump is the binary
-w captures in a format that can be read by a sniffer program
test.pcap is the file it produces and dumps the info in
-s 1550 adjust the packet capture size to 1550 bytes
port 5900 only captures packets using port 5900
if you dont get any info 
insert -i any this traces on all interfaces

when running, execute vnc connection and capture results
post the test.pcap here.

Before executing these commands, be sure you happy with the info i gave you an look at the help pages of tcpdump.


man tcpdump

---

### Post by krunge on 2008-11-15
> **linuxgr said:**
> 
vncviewer xxx.xxx.xxx.xxx:0

it says "connection refused". I have already changed the firewall settings on my 2-wire 2701-HG-B router and allowed port 5900.

x11vnc will print out logging info when the viewer connects to it.  Do you see any?

"Connection refused" is normally a message sent by the kernel (or perhaps an intermediate router's kernel), so I don't think the connection is even getting to x11vnc.

There might be some useful info at this link: [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

---

