---
title: "How to find an IP address when you only know the MAC address"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by theacoustician on 2008-02-05
Ok, here's the situation.  I've got a Qvidium DR-2112 video encoder that has decided to go retarded on me.  I tried resetting the device which should knock the default IP to 192.168.1.100.  For whatever reason, this isn't working as there's no response from the device at all from that address.  So the only things I know about it are its MAC address, that its running a Linux kernel, and its not using DHCP.  Arping'ing the MAC doesn't work.  So now I'm completely lost.  Is there any way to figure out what IP address a machine is using when you only know the MAC?  Thanks.

---

### Post by pytheas22 on 2008-02-05
If there's any traffic coming from it you should be able to use a packet sniffer like Ethereal and look through the packet dump to figure it out.  I don't have much experience with Ethereal though so I can't tell you specifically what to look for.  But it's a very well documented program.

Someone else maybe has a simpler solution, too...

---

### Post by theacoustician on 2008-02-06
> **pytheas22 said:**
> If there's any traffic coming from it you should be able to use a packet sniffer like Ethereal and look through the packet dump to figure it out.  I don't have much experience with Ethereal though so I can't tell you specifically what to look for.  But it's a very well documented program.

Someone else maybe has a simpler solution, too...Ethereal is now called Wireshark (that's just and FYI).  I tried it, but I'm not entirely sure I have it set up correctly.  I know the device isn't trying to use DHCP, so I can't look for a broadcast request there.  Other than that, I don't know enough about the program to set up anything useful.  If anyone could offer suggestions of filters to set up or tests to conduct, that would be most appriciated.

---

### Post by pytheas22 on 2008-02-06
another idea is to run a port scanner.  Maybe it will find the machine and tell you its address.  If not it might at least reveal open ports that you could use to ssh or something into the machine...although I guess you would probably need the IP address first to do that, but maybe there are ways around that.  I think that Nmap would do what you need; it can tell you what OS each system is running, among other things, so since the machine you're looking for is presumably running a weird version of Linux (e.g. not Ubuntu or Fedora or something standard), it would probably stand out from other computers.  You would need to specify a range of IP addresses for Nmap to ping, however.

Also if you have any idea what range of IP addresses the machine could have, you could write a BASH script to ping each address one by one until it gets a response (provided that the machine would respond, which may not be assured, but it's better than nothing).

---

