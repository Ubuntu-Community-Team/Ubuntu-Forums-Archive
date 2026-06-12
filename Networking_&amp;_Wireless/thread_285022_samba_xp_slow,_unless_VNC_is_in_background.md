---
title: "samba xp slow, unless VNC is in background"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by scottpreston on 2006-10-26
this is a tierd thread that there is no solution to (that works for me) but I have found a strange work-around that always works and I am not sure why.

i have a standard xp sp2 box that I am doing an XCOPY to a samba share via a gigabit connection.

it's very slow to samba, about 1/5th the speed as going to another XP box with a 100MB connection.

now i bring up VNC because I am modifiying the smb.conf file and restartig samba, etc. and guess what? VERY VERY FAST, as fast as FTP.

I minimize VNC, VERY SLOW. I bring it back and VERY FAST.

So my guess is there is something happening with the network connection that is causing it go be fast in one case and very slow in another, but I have NO CLUE what it could be.

Thanks,
Scott

p.s. I have tried everything in this forum for a fix but none of them work.

---

### Post by tjerkh on 2007-05-28
Hello,

i use Feisty fawn 7.04 and i am having the exact same problem. Without VNC in the foreground on Windows XP SP2, it slows down to lower than 1% usage of my Gbit Lan (extremely slow) . With VNC in the foregroundit immediately jumps to  some 30 % ( almost 30 megabytes a second ).

Also copying via samba on two ubuntu machines is very slow. The Lan connection is fine ( checked with netio and FTP ) . FTP cranks out a 35 megabytes a second.

Can it be a samba setting like  DNS proxy or Netbios setting ? I have set samba to be a wins server. It is also the DNS server (through dnsmasq) which runs smoothly as far as i can observe ( all dns queries resolve perfectly).

Thanks for all your help

Tjerk

---

### Post by zogbench on 2007-07-30
I am experiencing the same issue.

**Problem: **
When connected at 1000baseT (gigabit) I get 35MB/s (fast) transfer from Ubuntu to Windows (originating transfer from Ubuntu PC) and only around 8KB/s (slow) transfer from Windows XP to Ubuntu (again originating transfer from Ubuntu PC as the controlling PC).  When I switch back to 100baseT I get 7MB/s transfer each direction.

Using 1000baseT and connecting from Windows to Ubuntu, running FTPd, I get a transfer rate of 35MB/s.  Retrying the transfer using the shared folder still shows around 8KB/s.

I am not sure if this is a problem with the Ubuntu PC or the Windows PC.  I do not have any other PC's with GB ethernet to test.  I supposed I could go buy another for my NetBSD box...

**Setup:**
Ubuntu 6.10 running on an AMD and Windows XP SP2 running on an i386.  I have Gigabit NICs connecting through a NetGear GS605 using Cat 5e cabling.
Windows XP PC has a 3Com Gigabit 3C940 on board NIC running the latest driver 1.0.0.46 dated 7/31/2003.
XP PC has VMWare installed.
The Ubuntu PC is acting as the local browser master according to the smb log file.

**Problem Solving Steps Tried:**
- Swapping the cables out.  I had some Cat 5 cabling which was giving me problems making the 1 GB connection at all.
- Changing the ports used on the switch.  This had no effect.
- Altering the MTU settings (this would only work on XP since the kernel I am running prohibits changing the MTU setting above 1500)
- Tried disabling the NetBIOS over TCP/IP.  This appeared to increase the transfer speeds in 100baseT by about an extra 1 MB/s (now at just over 8MB/s).  No noticable effect on the 1000baseT transfer, which is still at 20KB/s (is this an improvement??)
- Tried removing the QoS packet scheduler in the Connection Properties and this did not change anything.
- Disabled the XP firewall and intrusion detection software. No change.
- Removed all extraneous services (I needed to clean this crud out anyway).  No change.
- Disabled the Internet Connection Sharing (should not have had this on to begin with).  No change.


Not sure what to try next.  Any ideas?

---

