---
title: "Can't connected to my wired network, but I could before..."
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by TracyO on 2008-02-25
Hello,

I am trying to connect to the wired network at my work, but I can't, and I can't figure out why.  I was connected previously for a day, but on current attempts, it will not work.  I have checked with other computers, and I have the correct IP address, mask subnet, and DNS--the same as before.  Upon ping-ing, it looks like something is up with the DNS, as it could not find ubuntu.com.  The suggested number in that help section simply returned no pings.

The first day when it worked, the computer was searching for a connection, but now it doesn't search, and I am not knowledgeable to know what the difference might be.  

Any ideas why this might be?

Thanks in advance!

---

### Post by Iowan on 2008-02-25
Post results from **ifconfig** and the contents of **/etc/network/interfaces**.

---

### Post by TracyO on 2008-02-26
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:08:74:05:CD:6A   
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:11 Base address:0x4c00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1344 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1344 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:115200 (112.5 KB)  TX bytes:115200 (112.5 KB) 

 /etc/network/interfaces 
bash: /etc/network/interfaces: Permission denied

---

### Post by Iowan on 2008-02-27
You'll need to open **/etc/network/interfaces** file in an editor, then copy/paste the results - sorry I neglected to mention that...

---

### Post by TracyO on 2008-02-27
Sorry, but can you go into more detail on the editor?  I only know how to run commands from the terminal, and that told me permission denied with this command.

---

### Post by Iowan on 2008-02-27
Yup.  I like **nano**, so (from a terminal) you could type```
sudo nano /etc/network/interfaces
``` (**sudo** is probably not required).  I'm not on linux - so going from (poor) memory... Highlight the text, then use a pulldown to copy to clipboard.  You should be able to paste from the clipboard into the Forum message editor (here...).

Don't forget to close the editor - being careful NOT to save any changes that might have slipped in.

---

### Post by TracyO on 2008-02-27
Since I'm working on the internet on one computer at the moment, and mine is right next to me, I'm just going to type what it says.

GNU nano 2.0.6   File: /etc/network/interfaces

auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.0.20
netmask 255.255.255.0







[ Read 26 lines ] etc.

---

### Post by cacycleworks on 2008-02-27
I'm in the same situation. My work notebook has been on the wired LAN at my work since I first installed Gutsy Tribe 3. No problems since ... 

Then yesterday, the wired LAN stopped working. 

For whatever reason, this Dell running Kubuntu 7.10 will not connect through the Belkin wireless router. It has on every other router attempted. This isn't really an issue, since I've got the drop at my desk.

So today, I spent an hour verifying that the docking station, wiring and the port are working correctly. The problem is, indeed, in my notebook. 

ifconfig does not list my eth0. There have been no recent changes (other than if it did an update and I didn't notice). I looked at /etc/network/interfaces and it was normal ... eth0 and eth1 were set to auto and get the ip from dhcp. running etc/init.d/networking start or restart do not bring eth0 to life.

When I find out what the fix is, I'll post it... 

I'm really bummed about this ... we've had 2 serious failures that appear to be in the OS this week. Our main server was running Dapper LTS and when the update updated the kernel, the box would kernel panic upon startup. Awesome. After a couple hours of head scratching, we installed gutsy server. Thankfully, we keep careful notes on configuration and perform occasion casual backups.

yaaaay,
chris

---

### Post by Iowan on 2008-02-27
TracyO:
Try adding the line ```
auto eth0
``` to the **/etc/network/interfaces** file, then (from command line) **/etc/init.d/networking restart**.

---

### Post by cacycleworks on 2008-02-27
My notebook is back on the LAN. I was getting a bit desperate, so am not exactly sure what caused the fix. Will isolate variables tomorrow. I sent tones on the cable, used a bypass cable (that didn't work), tried rebooting and a few other tricks I have to convince KNetworkManager to work when it gets stupid. None of that worked.

Possible changes:
- moved to different port in switch, double check original to positively prove/disprove the port.
- went back to the docking station. It has shown occasional issues, so any troubleshooting starts with taking notebook out of it and connecting everything to it directly.
- I did end up rebooting about 10 times. I prefer to shutdown to move the notebook to or from the docking station.

I was about to give up and plugged in the ethernet cable again for one last try. This time, ifconfig saw eth0:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8B:D4:66:60
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fed4:6660/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1882 (1.8 KB)  TX bytes:5365 (5.2 KB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:1B:77:45:92:E3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:18 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:82 (82.0 b)
          Interrupt:17 Base address:0x2000 Memory:fe8ff000-fe8fffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1948 (1.9 KB)  TX bytes:1948 (1.9 KB)

$ sudo /etc/init.d/networking restart
[sudo] password:
 * Reconfiguring network interfaces...                                                                                              RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6162
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:8b:d4:66:60
Sending on   LPF/eth0/00:18:8b:d4:66:60
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:8b:d4:66:60
Sending on   LPF/eth0/00:18:8b:d4:66:60
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.101 -- renewal in 2147483648 seconds.

```                                                       

There was a looong pause after the DHCPDISCOVERs and I thought it would fail... then I was on and could ping out to the Net. 

I hope this is a bad port in the switch. I get very bad feelings when computers I need begin to act up. I was already trying to judge what was going to be installed tonight... now I can "just work".

---

### Post by TracyO on 2008-02-29
All right.  I did what you asked, but I don't know how to save the change in the nano.  When I did the next command,   /etc/int.d/networking restart comes up absolutely blank minus the headings.  Going back to /etc/network/interfaces/ of course, auto eth0 is not there.

I've posted some commands I've been running through Ubuntu troubleshooting.  Let me know if they shed any light.  I noticed that it says my network is disabled, and I don't know if that should be so or not.  Today, I'm using a USB wireless card (from WiBi), so I've been playing around with the two.  In one spot last night, the card picked up a signal, but the internet pages would not show.  Currently in another place, it says I'm connected, but it gets no signal.  I'm pretty sure it's got to be the same problem within my Dell laptop between wired and wireless.

Also, in troubleshooting, it mentioned to look out for ESSID: “” which I have.  However, I checked, and I do have WPASupplicant installed, and for manual setup, you need to be connected to the internet.  =/


tracy@tracy-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
tracy@tracy-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:08:74:05:CD:6A   
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:11 Base address:0x4c00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
tracy@tracy-laptop:~$ sudo lshw -C network 
  *-network                
       description: Ethernet interface 
       product: 3c905C-TX/TX-M [Tornado] 
       vendor: 3Com Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 78 
       serial: 00:08:74:05:cd:6a 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.0.20 latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:40:0c:00:61:62 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
tracy@tracy-laptop:~$ ping 82.211.81.158 
connect: Network is unreachable

---

### Post by Iowan on 2008-02-29
IIRC, **nano** should have a list of commands at the bottom of the screen.  I'm gone for the weekend, so I can't check my machine, but it's <CTRL>something, I think.  That's one of the things I like about **nano **, nice to have the list there - my memory is getting full.

---

### Post by TracyO on 2008-02-29
From what I can tell, it saves on it's own.  Here is what my /etc/network/interfaces says:

 GNU nano 2.0.6         File: /etc/network/interfaces                           
 
auto lo 
iface lo inet loopback 
 
 
 
iface eth0 inet static 
address 192.168.1.13 
netmask 255.255.255.0 
 
 
auto eth0 

So it's there.  I do sudo nano /etc/int.d/networking restart and get:
 GNU nano 2.0.6          File: /etc/int.d/networking                            
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
                                  [ New File ] 
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos 
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell 
  
(Essentially, nothing.)  Any ideas?  Have a good weekend, Iowan, and thanks for the help.  (You, too, Cacycleworks.)

---

### Post by TracyO on 2008-03-02
Hi Cacycleworker,

Now I've had a little more time to go over what happened with your computer and what may have been the possible solutions.  Here's what I've got based on all of the possibilities you mention.

I know my problem is not the port because I've tried different ones in totally different places (inside the office and other internet cafes).  I've also tried the port from which my co-worker's computer has been working fine with no result.  I now have a Wifi card for my computer, and that's been picking up a signal in some places, but webpages still don't load.  It's got to be the same problem whatever it is.

Tell me more about the docking station.  Do you mean the router or is it something else?

From what I can see from ifconfig, there's no problem in recognizing eth0.

I noticed that your networking restart was a little different than mine.  Here´s what I got:

tracy@tracy-laptop:~$ sudo /etc/init.d/networking restart

[sudo] password for tracy:

 * Reconfiguring network interfaces...   [OK]

---

### Post by TracyO on 2008-03-03
Sorry for all the posts.

I've been searching around other forums for information.  No success yet, but here's some other things I tried—just giving you the most information possible.


tracy@tracy-laptop:~$ ping [www.yahoo.com](www.yahoo.com) 
ping: unknown host [www.yahoo.com](www.yahoo.com) 
tracy@tracy-laptop:~$ dig [www.google.com](www.google.com) 
 
; <<>> DiG 9.4.1-P1 <<>> [www.google.com](www.google.com) 
;; global options:  printcmd 
;; connection timed out; no servers could be reached 
tracy@tracy-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: 3c905C-TX/TX-M [Tornado] 
       vendor: 3Com Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 78 
       serial: 00:08:74:05:cd:6a 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=3c59x ip=192.168.0.20 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes 
tracy@tracy-laptop:~$ sudo route add default gw 192.168.0.1 
[sudo] password for tracy: 
tracy@tracy-laptop:~$ sudo route add default gw 192.168.0.1 
SIOCADDRT: File exists

---

### Post by Iowan on 2008-03-03
> **TracyO said:**
> 
So it's there.  I do sudo [COLOR="Red"]nano[/COLOR] /etc[COLOR="Blue"]/int.d[/COLOR]/networking restart and get:
 GNU nano 2.0.6          File: /etc/int.d/networking                            

 Sorry for delay...  CTRL-O writes the file - I thought that was the command, but didn't want to give the wrong code... 
Once the file is changed, **sudo  /etc/[COLOR="Red"][COLOR="Blue"]init.d[/COLOR][/COLOR]/networking restart** should do the trick.  With the **nano** in there, Ubuntu thought you wanted to edit the **/etc/int.d/networking** file - probably not what you want to do. The typo on** init.d** kept you from editing the existing file.

---

### Post by cacycleworks on 2008-03-04
> **TracyO said:**
> 
Tell me more about the docking station.  Do you mean the router or is it something else?

From what I can see from ifconfig, there's no problem in recognizing eth0.

I noticed that your networking restart was a little different than mine.  Here´s what I got:

tracy@tracy-laptop:~$ sudo /etc/init.d/networking restart

[sudo] password for tracy:

 * Reconfiguring network interfaces...   [OK]

My docking station is [one of these from Dell]("http://accessories.us.dell.com/sna/products/Docking_Station/productdetail.aspx?sku=310-7704") for the D-series notebooks. I got it used off of eBay for $40. I know that the docking station (or THIS one) sometimes introduces bugs with my configuration, so I do not hesitate to bypass it when there are problems.

With this latest networking bug, I'm starting to think kubuntu is the source of my problems... the other fault I've ever had is that the external monitor connected to the dock would not come on. Before Gutsy, I has zero issues with this setup. I was surprised at how well the docking station works. The first time I booted up, it found the 19" monitor and the desktop resized accordingly. So I bought a 22" monitor (same great thing) and now have a 24" monitor.

I immediately bypassed the docking station and the fault persisted. The dock wasn't used until I had concluded all testing. I'm using it now.

Yes, it is normal that eth0 appears when running ifconfig. This is why I was a tad alarmed when it did not appear! 

The "fault" happened again today.
But with different symptoms.
- The first sign of problem was when the networking icon went to wireless. 
- I right clicked on it and the wired interface was not listed.
- eth0 was listed in ifconfig
- when I ran sudo lshw -C network, the networking icon went to the "wired" icon. 
- hovering over it and the popup shows "Manual network configuration". 
- right clicking on it shows normal options, but there is no "wired" choice that belongs at the top of the menu.
- along with the above strange behavior, it seems that my D630 can now reliably connect to the wireless router at work, something it could never before accomplish.

It would seem that kubuntu Gutsy 64 bit will lose its mind upon a start up and not see the wired connection, however once "primed" or bumped, it suddenly becomes active. 

Awesome. 

At least it seems I can use my computer... otherwise would have to go home or to an internet cafe.

:) Chris

---

### Post by TracyO on 2008-03-05
Iowan, 

Auto eth0 is saved in /etc/network/interfaces.

When I run the restart, it says resolving networking interfaces and then OK.  Still no internet.

---

### Post by TracyO on 2008-03-05
I'm still trying to figure this out.  From looking at answers on launchpad, I found this post:
[https://answers.launchpad.net/ubuntu/+question/8915](https://answers.launchpad.net/ubuntu/+question/8915)

When I run route, Gateway shows up with two asteriks below it.  If this is the problem, how do I edit it?  Gedit and Nano don't work, and I can't just arrow up into it either.

---

### Post by Iowan on 2008-03-05
Let's see if the easy way works...
System>Administration>Network>Wired connection>Properties>Gateway
or... click the "Manual network configuration" icon in upper right corner, then Wired connection>Properties>Gateway

---

### Post by TracyO on 2008-03-05
Thanks.  I ended up figuring out the easy way shortly after, but still no change--except that perhaps I affected my co-worker's ability to get on the internet.

---

### Post by cacycleworks on 2008-03-05
> **cacycleworks said:**
> 
- when I ran sudo lshw -C network, the networking icon went to the "wired" icon. 
- hovering over it and the popup shows "Manual network configuration". 
- right clicking on it shows normal options, but there is no "wired" choice that belongs at the top of the menu.


I had to do this again today to use my wired LAN connection. So I have now put the **sudo lshw -C network** command in a script I execute after login.

Chris

---

### Post by TracyO on 2008-03-06
Hey Chris,

Upon searching the forums and other help options, it looks like this is a problem within Gutsy.  I've had Gutsy since November and never had this problem, so I guess at this point, I'm just confused at why it didn't happen before.   It started after I started changing my network connections to configure it for work.  Everything looks quite normal with   the connections, yet somehow, they're not.  I'm still hoping I can find a way to fix it, but if not, I suppose I'll just have to hang in there for another month until 8.04 comes out.  Luckily, internet cafes are a viable option for me at this time.  I just really miss my podcast!

I really appreciate the help, suggestions, and commiseration.

Tracy

---

### Post by cacycleworks on 2008-03-06
Hi Tracy, 

Yes, I, too, have been without problems since Gutsy was first released. I did previously have problems with knetworkmanager connecting to various wireless networks. To address that, I created a "fix_wireless" script to effectively "spool" the wireless in kubuntu.

```
#!/bin/bash
PID=`ps aux | grep network | grep -v grep | grep -o "\b[0-9][0-9][0-9][0-9]\b"` && kill $PID
sudo ifconfig eth0 down
sudo ifconfig eth1 down
knetworkmanager --nofork &
```

Note that this is for Kubuntu and its KNetworkManager, but the ubuntu gnome equivalent might help you with any wireless issues.

The above did nothing for the misbehavior you and I both outline above concerning the wired interface.

:) Chris

---

