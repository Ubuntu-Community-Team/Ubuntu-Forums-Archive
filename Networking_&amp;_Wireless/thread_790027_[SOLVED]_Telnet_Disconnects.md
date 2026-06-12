---
title: "[SOLVED] Telnet Disconnects"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by haraldmilz on 2008-05-11
I work in networking and use telnet frequently. Most switches I telnet have very long configurations (+500 lines) which, in the case of Alcatel, are not divided by pages (like when you get "--MORE--" at the end of each page and hit the spacebar for the next page, just like when you issue the command "<command> | more"). It will only disconnect when I do not have the ability to view the results by pages, like with cisco.
What happens is that when it reaches the line 300-400 aprox. I get disconnected. This happens always, no matter what telnet client I use.
I tried the following telnet clients:

- "telnet" from the console
- "putty" for linux (GUI)
- run "telnet" from cmd within a VM. Tried both VMWare and VirtualBox.

Why this happens?

I can observe (comparing to Windows native) that the configuration is arriving very slow to my system when running ubuntu, as if I was limiting my bandwidth to 4800bps. A configuration of about 500 lines will take about 8-12 seconds to show on my screen, just before it disconnects, when on Windows it will take less than a second.

My ubuntu release:
Description: Ubuntu 7.10
Release: 7.10

Version of telnet I am using:
telnet:
  Installed: 0.17-35ubuntu1
  Candidate: 0.17-35ubuntu1
  Version table:
 *** 0.17-35ubuntu1 0
        500 [http://ftp.hosteurope.de](http://ftp.hosteurope.de) gutsy/main Packages
        100 /var/lib/dpkg/status

PLEASE, I need some help to get this diagnosed and fixed. Thank you!!

Harald

---

### Post by haraldmilz on 2008-05-13
After performing a packet capture, I realized that I am sending "Zero Window" and "Zero Window Probe" packets, meaning (probably) that my Lenovo T61 (Dual-Core with 3GB of RAM) is "slower" in processing the packets than a simple Telnet session with a Network Switch.
Being the above hard to believe, I ask for guidance on properly diagnosing this issue.
If further info is required, please let me know.
P.S.: My notebook has dual-boot with Windows XP. When booting with Windows XP, this behaviour is not encountered.
KR, Harald.-

---

### Post by superprash2003 on 2008-05-13
you could try this tool called EXPECT for linux

---

### Post by haraldmilz on 2008-05-13
I don't see how EXPECT would help with this issue. I read (part of) the manual and everything points that EXPECT is just an "intelligent" scripting utility.
Could you please be more specific as to what should I do with this utility?

KR, Harald.-

---

### Post by haraldmilz on 2008-05-27
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

(Special thanks to the ubuntu mailing list members for their help)

KR, Harald

---

