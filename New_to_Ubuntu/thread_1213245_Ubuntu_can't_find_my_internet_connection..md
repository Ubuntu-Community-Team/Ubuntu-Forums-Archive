---
title: "Ubuntu can't find my internet connection."
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Metalslave on 2009-07-14
I have a fresh Ubuntu-install, Vista dual-boot. The installation went fine and the only problem appears to be that Ubuntu can't find my internet connection. It tries and tries, but eventually gives up. 

All wires are connected and the connection works fine in Vista. It's a broadband connection that runs through a router. I *have* read the "Connecting to the internet" bit in the Ubuntu Help Centre and followed the advice there. I have *not* changed anything in the network settings, because I have no idea what I would change it to. Networking is enabled. The "auto eth0" connection is set to automatic DHCP.

Any help is welcome.

---

### Post by SonicSteve on 2009-07-14
First thing,

Right click the network Icon beside the clock and left click on "connection information"
What is your IP address, broadcast address,subnet mask,default route, and primary dns.

If you can't find this icon try this;
Click applications, accessories, and then on Terminal

type in;
ifconfig 

Mine gives me this,
steve@steve-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0a:cd:16:dc:6c  
          inet addr:192.168.100.20  Bcast:192.168.103.255  Mask:255.255.252.0
          inet6 addr: fe80::20a:cdff:fe16:dc6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304332106 (304.3 MB)  TX bytes:30049404 (30.0 MB)
          Interrupt:17 Base address:0xc800 
I have an address of 192.168.100.20 and you can see the rest.

We need to see if your properly getting the DHCP address info.

---

### Post by LewRockwell on 2009-07-14
rebooting your router may solve your difficulty

.

---

### Post by Metalslave on 2009-07-15
> **LewRockwell said:**
> rebooting your router may solve your difficulty.

I've tried that, but unfortunately it didn't help.

> **SonicSteve said:**
> First thing,

Right click the network Icon beside the clock and left click on "connection information"
What is your IP address, broadcast address,subnet mask,default route, and primary dns.

If you can't find this icon try this;
Click applications, accessories, and then on Terminal

type in;
ifconfig 

(snip)

We need to see if your properly getting the DHCP address info.

The "Connection Information" option is greyed out and I can't click on it. Typing in "ifconfig" gives me this.

anders@ubuntu:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:1e:4f:5a:21:45  
inet6 addr: fe80::21e:4fff:fe5a:2145/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100 
RX bytes:861 (861.0 B)  TX bytes:4230 (4.2 KB)
Memory:fdfc0000-fdfe0000 

And also this.

lo        
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B)  
TX bytes:240 (240.0 B)

If you have any further advice, then please keep in mind that I am in fact an absolute beginner.

---

### Post by superprash2003 on 2009-07-15
post output of **sudo dhclient eth0**

---

### Post by SonicSteve on 2009-07-15
Lets see what the output is from the previous post, but it seems most likely at this point you're using a Network Card that doesn't work "out of the box". It's possible that there are some easily installable restricted drivers but until you connect to the Internet we won't know. Yes and there is the catch, the very thing we are trying to fix is the very thing we need.

In the mean time before we jump off a bridge of assumptions type this in a terminal;
lspci

and post the terminal output so we can see what kind of devices your system has.

---

### Post by SonicSteve on 2009-07-15
> **Metalslave said:**
> I've tried that, but unfortunately it didn't help.



The "Connection Information" option is greyed out and I can't click on it. Typing in "ifconfig" gives me this.

anders@ubuntu:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:1e:4f:5a:21:45  
inet6 addr: fe80::21e:4fff:fe5a:2145/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100 
RX bytes:861 (861.0 B)  TX bytes:4230 (4.2 KB)
Memory:fdfc0000-fdfe0000 

And also this.

lo        
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B)  
TX bytes:240 (240.0 B)

If you have any further advice, then please keep in mind that I am in fact an absolute beginner.


What I see here is that your card isn't picking up any IP addressing. If your not a networking guy think of it this way. It's like moving into a new neighborhood and expecting to get your mail without registering your change of address with anyone. Without an IP address the same thing will happen, no communication...PERIOD.

I see no IPV4 information, only IPV6 which your router likely doesn't support. The fact that "address information" is greyed out likely means we have some tweaking to do.

It's quite possible that we will need to download a few things using your windows install, and transfer them to the Ubuntu install. A usb flash drive might be the easiest least confusing way.

---

### Post by Metalslave on 2009-07-15
I have no idea how, but this problem appears to have solved itself. I exited Vista and booted into Ubuntu to try your suggestions and watched in wonder as it finally picked up my connection. There was a brief message about my system or connection having something Ubuntu "didn't like", but it was gone so quick, I didn't have time to read it properly.

It seems stable, though, so I'm happy. Thank you for your help.

---

### Post by LewRockwell on 2009-07-15
> **Metalslave said:**
> I have no idea how, but this problem appears to have solved itself. I exited Vista and booted into Ubuntu to try your suggestions and watched in wonder as it finally picked up my connection. There was a brief message about my system or connection having something Ubuntu "didn't like", but it was gone so quick, I didn't have time to read it properly.

It seems stable, though, so I'm happy. Thank you for your help.

this has been an issue with an ever-expanding number of people

it has even been the experience of a number or higher profile reviewers

not only that, but it has happened with folks utilizing more than one OS

makes you wonder what's going on...

---

### Post by SonicSteve on 2009-07-15
It sounds like the ARP tables on certain routers is having trouble with the fact that the same network card is connecting with more than 1 computer name and OS associated with it. Or perhaps something isn't being cleared on the Ubuntu side of things, when the ubuntu machine tries to connect to the router perhaps it's being refused. I bet if you specified IP addresses, DNS etc you would have no issues. Of course as long as the IP you specify is in the same range as the router.

---

### Post by NOTAGEEK on 2009-07-15
i am not trying to confuse or hijack this thread in any way but i have had my share of connection issues too...

since this thread has not been tagged solved by the op let me know if i can post my details here or it would be better to start a new thread im ok with either or...

thanks...

---

### Post by NOTAGEEK on 2009-07-15
> **NOTAGEEK said:**
> i am not trying to confuse or hijack this thread in any way but i have had my share of connection issues too...

since this thread has not been tagged solved by the op let me know if i can post my details here or it would be better to start a new thread im ok with either or...

thanks...


nevermind ill start a new thread on this issue 2morrow...

thanks...

---

### Post by lavinog on 2009-07-15
> **LewRockwell said:**
> this has been an issue with an ever-expanding number of people

it has even been the experience of a number or higher profile reviewers

not only that, but it has happened with folks utilizing more than one OS

makes you wonder what's going on...

I thought there was an issue with windows leaving the card in a weird state upon shutdown, for the wake on lan feature:
[http://ubuntuforums.org/showthread.php?t=1081818](http://ubuntuforums.org/showthread.php?t=1081818)
[http://bbs.archlinux.org/viewtopic.php?pid=280823](http://bbs.archlinux.org/viewtopic.php?pid=280823)

---

### Post by Metalslave on 2009-07-16
> **NOTAGEEK said:**
> ...since this thread has not been tagged solved by the op...

Right. Sorry about that. I didn't know I was supposed to do that, but it's taken care of now. I added [SOLVED] to the OP. I couldn't see any option to edit the thread title.

The problem *is* solved, sort of, but I couldn't explain how, if asked.

> **lavinog said:**
> I thought there was an issue with windows leaving the card in a weird state upon shutdown...

I'm obviously not a technically gifted man, but my initial connection problems occurred right after the install, ie I didn't pop into Vista inbetween the install and booting into Ubuntu for the first time. When Ubuntu finally did pick up the connection, I had been using Vista right before.

So, if Windows leaves the card in a funny state, it does not appear to be consistent?

---

### Post by lavinog on 2009-07-16
> **Metalslave said:**
> 
I'm obviously not a technically gifted man, but my initial connection problems occurred right after the install, ie I didn't pop into Vista inbetween the install and booting into Ubuntu for the first time. When Ubuntu finally did pick up the connection, I had been using Vista right before.

So, if Windows leaves the card in a funny state, it does not appear to be consistent?

If I remember correctly, the problem happens only when you reboot from windows into ubuntu. If you shutdown the computer, then boot into ubuntu, it should work fine.

---

### Post by LewRockwell on 2009-07-16
it's just the most recent effort by that other OS to wonk *nix...

.

---

