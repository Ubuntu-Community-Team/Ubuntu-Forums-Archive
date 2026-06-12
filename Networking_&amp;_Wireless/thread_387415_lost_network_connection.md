---
title: "lost network connection"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by alalor1 on 2007-03-18
Hello,
I am a beginner/intermeditate user.  
I installed Ubuntu on my desktop computer, which is a homebuilt with an Athlon XP processor and 1 GB RAM.  I have two network cards, an on board Via and a Realtek on a PCI slot.  
On installation, both were found, got the information from the router automatically and everything works fine.  The Realtek is the one that is plugged to the cable to the router.  
A few days later, I decided to install Xfce and it went fine.  A couple of days later, it quit connecting to internet.
I tried disabling the via card, eth1, that did not help.  Giving eth0 a static IP didn't work either.
I don't know what else to try, the help section is not telling me how to diagnose this.
I know the card works fine because when I dual boot to winxp, everything works fine.
If anybody has any hints, please help me!
Alejandro

PS:  I am also having trouble using my DVD burner, it is not recognized as a lightscribe burner, even though I downloaded and installed the software, pointers here would also be appreciated.

---

### Post by alalor1 on 2007-03-18
I went to my interfaces file and cleaned it up, took out the loopback that somehow had been added to it, and now it works!:)

---

### Post by chili555 on 2007-03-18
You want to add the loopback device back in; it is needed for the computer to work correctly. It has nothing to do with ethernet or wireless, except possibly to hinder them if it's not in place. It wants to be thus: ```
auto lo
iface lo inet loopback
```

Hurry!

---

### Post by alalor1 on 2007-03-18
Well, thank you Chili, I added that to my interfaces file.
I hope it still works next time I boot up though.

---

### Post by chili555 on 2007-03-18
One way to find out: reboot and post back.

---

### Post by alalor1 on 2007-03-18
Well, honestly, I don't know, it works just as well with and without the loopback now.

---

### Post by chili555 on 2007-03-19
Unless you restarted networking or rebooted the computer, the revised information in your interfaces file wouldn't have much effect. I repeat my previous advice: you need lo. 

If I started just removing files and lines from configuration files that I don't understand, I'll bet that within 10 minutes I could have a system that wouldn't even boot or run. I'd have to reinstall. Afterwards, my interfaces file would certainly contain lo.

---

### Post by alalor1 on 2007-03-19
I appreciate your advice Chilli, 
I put the loopback instructions you gave me back in the file, and it worked fine all day yesterday, maybe a little slow, not sure if it was the computer or my network, but it worked.
I even showed my roommate and a couple of friends how cool Linux was, all it could do, etc.
But today I have the problem again.  Doesn't matter if they are at the beginning or at the end or if they are not there at all, it will not find my router.
I tried this 
sudo ifdown eth0
sudo ifup eth0
to try to reset the network, If I remember right it says it is looking for the DHCP on 255.255.255.255 port 67 then it waits a few seconds, goes again, and again, finally it says it can't  discover anything and it is sleeping. 
I am getting frustrated, I rebooted with the loopback in the top of the interfaces file, with it at the bottom, on gnome, on xfce, etc.  I don't know what else to try.  WinXP finds the network fine, I am typing on the same computer.
I have no idea what else to try.  Help please!!!

---

### Post by chili555 on 2007-03-19
Inspector Chili: "Round up the usual suspects." Let's see:```
cat /etc/network/interfaces
ifconfig -a
ping -c3 <your_router's_IP>
```

Is it confused because the onboard NIC and the add-in card are fighting for world supremacy? Did you disable the on-board NIC in the BIOS?

We'll get it going.

---

### Post by alalor1 on 2007-03-19
Crazy News Inspector Chilly,
I booted back into ubuntu linux and the network was working.
Now, if we can figure out what is wrong, so it stays networked every time I boot, that would be great.
I did not disable the built in card.  What would be better, to disable it or to take out the pci card that is much older?  I have two cards because I used to share the internet connection before we bought a router.  I don't need two cards any more.
This is what I got when I ran your commands:
al@mutt:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
al@mutt:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:F0:68:53:FC  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe68:53fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40473 (39.5 KiB)  TX bytes:6728 (6.5 KiB)
          Interrupt:177 Base address:0xf00 

eth1      Link encap:Ethernet  HWaddr 00:50:2C:A3:CC:FE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

al@mutt:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=0.775 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=0.762 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=0.786 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2027ms
rtt min/avg/max/mdev = 0.762/0.774/0.786/0.024 ms

By the way, I really appreciate all your help!!!
Just wondering, what is the loopback for?
what is ath0?
why do I have a wireless connection section there when I don't have a wireless card on the computer?
Thank you so much for all your help, I OWE you!
Al

---

### Post by chili555 on 2007-03-19
> Just wondering, what is the loopback for? That's our old friend lo, that we have been talking about. When it appears in ifconfig, it means it's set up and working. Good!
> what is ath0?
why do I have a wireless connection section there when I don't have a wireless card on the computer? When the defaults install, they make provision for all kinds of things you may, or may not have, such as wireless, RAID, bluetooth, printers, etc., etc. The start of a configuration is in place to be finished as soon as hardware, etc. is detected and Mr.Ubuntu says, "Hey, you have wireless! I'm ready for you!" If you don't anticipate having wireless, it will do no harm, and will speed up boot up by a few microseconds to remove ath0 and wlan0.
```
al@mutt:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:C0:F0:68:53:FC
inet addr:192.168.1.104 Bcast:192.168.1.255 Mask:255.255.255.0
ietc.
eth1 Link encap:Ethernet HWaddr 00:50:2C:A3:CC:FE
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
etc.
```I think this is telling us eth0, your add-in card is working and has an IP address. It also suggests your on-board card, eth1 is working and not connected; that's logical, because no CAT5 cable is attached.
> What would be better, to disable it or to take out the pci card that is much older?My preference would be the newer card and retire the older to the PVR you're going to build next. I just feel simple is better than complex. All bets are off if lspci -v tells you it's one of those swell Marvell Yukons. It's not that they are impossible, just very difficult to get going.

Otherwise, your configuration looks nearly perfect!

Let us know.

---

### Post by alalor1 on 2007-03-19
Hello,
Thank you for your advise.
I took out the PCI card.  
Everything is running fine after booting.  The ipconfig only shows the lo and the eth1, 
I hope the fight for world supremacy was what was creating all the problems.
If you ever come to central texas, we'll take you wakeboarding or sailing, your pick!
Thanks again for all your help.
Cheers,
Al

PS:  Now I am going to try to figure out how to install new themes, how to make my lightscribe dvd burner work and how to make the windows have the cool, transparent look...

---

### Post by chili555 on 2007-03-19
Glad it worked well. We all learn; you, me and the newbies who are reading over our shoulders. Thanks for your kind comments and, as we used to call it when I lived in Harris County, Texas, thanks fer thu invite.

---

### Post by alalor1 on 2007-03-20
Oh, that's really cool that you lived in the area.  Let me know when you come back to visit!

---

