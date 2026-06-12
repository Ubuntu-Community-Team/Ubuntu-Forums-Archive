---
title: "Cannot Wrap the Wireless Driver"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by EduMan on 2007-11-08
Hi!

I am an absolute beginner in Ubuntu. I installed the 7.1 version in dual boot with XP home last week. I have a wireless connection in XP with a Netgear wg311v3 card. The connection works. 

After installing Ubuntu, I tried to configure the wireless card in the Linux OS, but I haven't succeeded yet. Here is the information I collected so far:


warden@DeskMatrix:~$ lspci|grep Marvel

02:0e.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

warden@DeskMatrix:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:47:EF:F2:F2  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


warden@DeskMatrix:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

 
warden@DeskMatrix:~$ lsmod

Module                  Size  Used by

ndiswrapper           185240  0 


Synaptic shows that the following are installed:

ndiswrapper-common version1.43-lubuntu2, and
ndiswrapper-utils-1.9 version 1.43 lubuntu2

When I try to install the wireless driver (wg311v3.inf) with the command

sudo ndiswrapper-i wg311v3.inf

I get a message which says that the command is not recognized.

Where do I go from here?

---

### Post by kevdog on 2007-11-08
> 
sudo ndiswrapper-i wg311v3.inf

This command should be 
sudo ndiswrapper -i wg311v3.inf

Second check your ndiswrapper version
ndiswrapper -v

---

