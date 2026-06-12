---
title: "Before SAMBA (w/ VMware) there must be networking - how can I validate that bit?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Phrawm48 on 2007-07-03
I'm drowning...

I have a working instance of VMware Server installed under Dapper and can run W2K Pro with ease.  W2K can also use Ubuntu's wide-area connection to access the Internet.  So far, so good.

I also have a second VMware network interface configured.  Ethereal sees it in action, trying to find "friends".  What I can't do is use Samba and that second VMware network i'face to access my Linux files.

My first problem, I think, is that I'm not sure that my VMware-to-Ubuntu networking infrastructure is setup right.  Can anyone advise what pieces of network "plumbing" I need to get in place *before* I try getting Samba to work?

- What sorts of supplementary networking components (ports? firewall? DHCP?) do I need to get in place so that W2K under VMware will start talking with Linux and vice versa?

-  How can I best validate basic network VMware-Linux host operation?

Note that I've already gone back and forth through the myriad sets of "setting up Samba" instructions without success.  This is the primary reason I suspect that the requisite network plumbing isn't setup right...

Cheers & thanks,
Ric
SFO

---

### Post by Gallows on 2007-07-04
Phrawm

What vmnet is your virtual XP box running on?  Bridged (vmnet0) or NAT (vmnet8)?  What IP address have you given the VM and what IP address is the vmnet device using?

Get that information and from the VM ping the Ubuntu box and from the Ubuntu box ping the VM.  Post back your results and i *might* be able to help you

---

### Post by Phrawm48 on 2007-07-04
Thanks so much -- I'm still trying to figure out what's missing.

First, I've an excerpted screenshot from VMware -- [2007-07-04_VMware-Enet-02.png]("http://ubuntuforums.org/attachment.php?attachmentid=37324&stc=1&d=1183588342") -- of the second "LAN" connection.  More to the point, the connection is **Host Only**, **/dev/vmnet0**.

If I boot the VM machine and run Window's *ipconfig*, I get this:

> C:\Documents and Settings\VMware01>ipconfig

Windows 2000 IP Configuration

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : localdomain
        IP Address. . . . . . . . . . . . : 192.168.63.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : localdomain
        IP Address. . . . . . . . . . . . : 172.16.74.12
        Subnet Mask . . . . . . . . . . . : 255.255.255.
        Default Gateway . . . . . . . . . : 172.16.74.2
On the Ubuntu side, if I run ifconfig, I get this (excerpted):
> 
ric@ric-desktop:~$ ifconfig
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.63.1  Bcast:192.168.63.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.74.1  Bcast:172.16.74.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Okay, now:[LIST]
[*]I _can_ ping from Ubuntu to 192.168.63.1 (the Windows machine running under VMware?)  Also, *tracepath* indicates that the machine is immediately "next door".
[*]I _cannot_ ping from the Windows machine running under VMware to 172.16.74.1 (Ubuntu?)[/LIST]So W2K via VMware doesn't "see" Ubuntu.  I suspect there's some piece of networking missing.


Notes:

I normally run Firestarter on Ubuntu, but can only ping from Ubuntu if I disable or simply quit *Firestarter*.  So for now *Firestarter* is completely disabled.

While gathering the preceding information, W2K under VMware was successfully connected to the wide area via the LAN 1 connection which in turn connects through Ubuntu's wide-area connection.  So basic networking, aside from the "local" problem works properly.

Finally, I also attached a Zip'ed copy of my smb.conf file just in case that turns out to be handy.

Cheers and thanks again
Ric
SFO

---

