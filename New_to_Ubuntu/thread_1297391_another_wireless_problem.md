---
title: "another wireless problem"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by jm5 on 2009-10-21
hi guys, i'm kinda new at the linux game(not that great at windows either) and have installed ubuntu successfully on a few machines now, including all of mine. i convinced my co-worker to try it on his laptop after we had problems with xp not re-installing properly and i cannot for the life of me get the wireless to work.  it is a dell inspiron 6000 with an intel pro/wireless 2200bg card. im pretty new with the whole terminal/commands thing and i tried to follow a few tutorials but it never ends up going like the author describes. thanks in advance.

here is some common outputs ive come up with:

-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:df:e2:59  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fedf:e259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4091023 (4.0 MB)  TX bytes:949530 (949.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

---

### Post by coolbrook on 2009-10-21
**03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)**

I did a quick search and it looks like at least one person resolved the matter according to end of this bug report:

[https://bugs.launchpad.net/ubuntu/+bug/285837](https://bugs.launchpad.net/ubuntu/+bug/285837)

---

### Post by jm5 on 2009-10-21
thanks for the reply, i went ahead and ran the same command that person did (sudo modprobe -i ipw2200) and nothing happened, the command promp just comes back up, and the wireless still doesnt work.

---

### Post by jm5 on 2009-10-21
i also ran this command, it appears that my firmwear is not present, right?


-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:df:e2:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:5d:b8:84:67:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by coolbrook on 2009-10-21
Does ifconfig produce the same result?

---

### Post by pgar23 on 2009-10-21
Judging from the output of ifconfig, it looks like you do not have the wireless internet up and running. Do you have your drivers installed for the card?

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

Try that and if no luck still, post back.

---

### Post by jm5 on 2009-10-21
ifconfig produces this:

-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:df:e2:59  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fedf:e259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4091023 (4.0 MB)  TX bytes:949530 (949.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by pgar23 on 2009-10-21
check out my reply above ^^^^^^

---

### Post by jm5 on 2009-10-21
> **pgar23 said:**
> Judging from the output of ifconfig, it looks like you have the wireless internet up and running. Do you have your drivers installed for the card?

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

Try that and if no luck still, post back.

i found that on google too, this is as far as i get with that

chandler@chandler-laptop:~$ sudo apt-get install linux-headers-$(uname -r) module-assistant gcc-4.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-15-generic is already the newest version.
E: Couldn't find package gcc-4.0
chandler@chandler-laptop:~$ sudo module-assistant
sudo: module-assistant: command not found
chandler@chandler-laptop:~$

---

### Post by pgar23 on 2009-10-21
My bad, didnt really read that howto. It is actually very old. Haha "Please note that since Ubuntu Dapper, ipw2200 drivers are included in the standard kernel"

---

### Post by coolbrook on 2009-10-21
There's data transfer over what could be an ethernet connection. Is/was there a network cable attached from the laptop to the router?

---

### Post by pgar23 on 2009-10-21
What version of ubuntu are you running?
in terminal type:
```

$uname -r
```

---

### Post by pgar23 on 2009-10-21
[http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200)

---

### Post by jm5 on 2009-10-21
> **coolbrook said:**
> There's data transfer over what could be an ethernet connection. Is/was there a network cable attached from the laptop to the router?

yes im on ethernet right now

---

### Post by jm5 on 2009-10-21
> **pgar23 said:**
> What version of ubuntu are you running?
in terminal type:
```

$uname -r
```
im on jaunty, that command didnt work for me

---

### Post by pgar23 on 2009-10-21
> **jm5 said:**
> im on jaunty, that command didnt work for me

OK, your good anyways, you have a linux kernel that is runnning 2.6.xxx+.

[http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200)

you will have to do a little reading and studying, as I dont know much about configuring wireless networks.

---

### Post by jm5 on 2009-10-21
> **pgar23 said:**
> OK, your good anyways, you have a linux kernel that is runnning 2.6.xxx+.

[http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200)

you will have to do a little reading and studying, as I dont know much about configuring wireless networks.
Just to be sure we are on the same page here, the problem I'm having is that when I left click the network manager the no wireless networks show up, it doesnt even say wireless as if i don't have a wireless card installed.

---

### Post by pgar23 on 2009-10-21
run this:
```
sudo lsmod | grep ipw2200
``` and post the output here.

---

### Post by jm5 on 2009-10-21
chandler@chandler-laptop:~$ sudo lsmod | grep ipw2200
[sudo] password for chandler: 
ipw2200               151112  0 
ieee80211              38344  1 ipw2200

---

### Post by pgar23 on 2009-10-21
Ok, since that command returned an output, this means that your driver is in fact installed and working. Give me a minute to search the web and find out what to do next.

---

### Post by coolbrook on 2009-10-21
Please have a look, in particular at posts 17-20, and let's discuss.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1226663&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1226663&page=2)

---

### Post by pgar23 on 2009-10-21
Possible malfunction of your network monitor, it happens sometimes. To check if your wireless is working:
try System > Admin > Network Tools
there will be a tab that say ping. Click the tab, enter in your ip address. then hit enter. Does it return anything?

---

### Post by pgar23 on 2009-10-21
> **jm5 said:**
> im on jaunty, that command didnt work for me

> **coolbrook said:**
> Please have a look, in particular at posts 17-20, and let's discuss.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1226663&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1226663&page=2)

No, that guy ended up having trouble with his cardbus and the wrong headers.

---

### Post by jm5 on 2009-10-21
but reading that post made me look in the bios(duh!) the wireless was off but now that it is on it is still not working, oh well I'll try again tomorrow

---

### Post by pgar23 on 2009-10-21
If the wireless card is turned off in BIOS, it will NOT be magically turned on in Ubuntu.

> Re: Intel Pro/Wirelss 2200BG not working in 9.04 
I have a Dell Latitude D610 also with what I suspect is the same 2195 / 2200 wireless card. I got my wireless working in 9.04 by setting the wireless card to be "On" on bootup in BIOS.

---

### Post by coolbrook on 2009-10-21
> **pgar23 said:**
> If the wireless card is turned off in BIOS, it will NOT be magically turned on in Ubuntu.

We've established that.

> **jm5 said:**
> I'll try again tomorrow

Agreed.

---

### Post by pgar23 on 2009-10-21
> **coolbrook said:**
> We've established that.
Buzz off or offer help!

---

### Post by pgar23 on 2009-10-21
When you try tommorow...
1.) Be sure that the wireless card is turned on in BIOS.
2.) Boot Ubuntu.
2.5) Disconnect your ethernet cable.
3.) System > Admin > Network Tools , Ping tab, enter your IP Address (if it returns anything then that means that your wireless is turned on)
4.) Right-click Network Monitor and tick the box that says "Enable Wireless" (if you cannot,  System > Preferences > Network Connections > Wireless Tab > + ADD, Enter your network info manually)
After said has been done, should work.

if not...
**Helpful Wireless Links**  

Understanding Wireless  -http://beginlinux.com/appsm/wireless_m/1011-understanding-wireless

Network Relationship   -http://beginlinux.com/appsm/wireless_m/1142-network-relationship

Network Connections   -http://beginlinux.com/appsm/wireless_m/1139-network-connections

Wireless Security    -http://beginlinux.com/appsm/wireless_m/1010-wireless-security

Wireless Router    -http://beginlinux.com/appsm/wireless_m/1012-configure-a-wireless-router

Wireless Channels  -http://beginlinux.com/appsm/wireless_m/1140-wireless-channels

Wireless Range   -http://beginlinux.com/appsm/wireless_m/1141-wireless-range

Ubuntu Wireless  -http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup

**Wireless Tools**

WiFi Radar   -http://beginlinux.com/appsm/86-wifiradar/794-wifiradar

iwconfig  -http://beginlinux.com/appsm/wireless_m/1148-iwconfig

iwlist   -http://beginlinux.com/appsm/wireless_m/1149-iwlist-

---

### Post by jm5 on 2009-10-22
> **pgar23 said:**
> When you try tommorow...
1.) Be sure that the wireless card is turned on in BIOS.
2.) Boot Ubuntu.
2.5) Disconnect your ethernet cable.
3.) System > Admin > Network Tools , Ping tab, enter your IP Address (if it returns anything then that means that your wireless is turned on)
4.) Right-click Network Monitor and tick the box that says "Enable Wireless" (if you cannot,  System > Preferences > Network Connections > Wireless Tab > + ADD, Enter your network info manually)
After said has been done, should work.



tried all of that, but no luck, if I right click the network monitor there is no enable wireless option,  when i run ifconfig I only see the eth0 for the ethernet, when I ifconfig my own(not this one) dell laptop that has a working wireless connection i get eth0 and something else also for wireless, i think it is wlan or sumthing.

---

### Post by bkratz on 2009-10-22
> **jm5 said:**
> tried all of that, but no luck, if I right click the network monitor there is no enable wireless option,  when i run ifconfig I only see the eth0 for the ethernet, when I ifconfig my own(not this one) dell laptop that has a working wireless connection i get eth0 and something else also for wireless, i think it is wlan or sumthing.



Sorry to interrupt, since I really don't know what is going on, but didn't you originallly  want to run iwconfig rather than ifconfig, that is why it is showing all the activity. iwconfig just shows the wireless (I think).  It reallly looks like there might also a switch on the adapter or keystoke option, not just the bios switch. 

Also, it was a while ago when I did it all, but I think you have to go to edit connections (right click on the icon) and set up the connection with "edit connections" before the wireless button option is available.

If I am off base please ignore my interruption.

---

### Post by jm5 on 2009-10-22
> **bkratz said:**
> Sorry to interrupt, since I really don't know what is going on, but didn't you originallly  want to run iwconfig rather than ifconfig, that is why it is showing all the activity. iwconfig just shows the wireless (I think).  It reallly looks like there might also a switch on the adapter or keystoke option, not just the bios switch. 

Also, it was a while ago when I did it all, but I think you have to go to edit connections (right click on the icon) and set up the connection with "edit connections" before the wireless button option is available.

If I am off base please ignore my interruption.

thanks for the input i ran iwconfig and here it is

chandler@chandler-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

chandler@chandler-laptop:~$

---

### Post by jm5 on 2009-10-22
i was thinking of reinstalling ubuntu, if i do what are somesteps to take after it is freshly loaded?

---

### Post by pgar23 on 2009-10-22
re-installing ubuntu will not solve your wireless problems. Let me look around and I will post back in a minute k?

---

### Post by pgar23 on 2009-10-22
This will turn your wireless on. Hopefully.

try this:
```
 sudo iwconfig wlan0 up
``` Then check the network monitor and see if you are manually able to enable the wireless options.

---

### Post by bkratz on 2009-10-22
> **jm5 said:**
> thanks for the input i ran iwconfig and here it is

chandler@chandler-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

chandler@chandler-laptop:~$



Sorry to interrupt again, but here is a page from Chili555 regarding the card.

[http://ubuntuforums.org/showpost.php?p=8045946&postcount=3](http://ubuntuforums.org/showpost.php?p=8045946&postcount=3)

The OP never did respond so I suspect it turned out ok and he just ignored the received help.  Anyway, since the card doesn't seem to appear, did you check to see if there was some switch that had to be turned on?

---

### Post by bkratz on 2009-10-22
> **pgar23 said:**
> This will turn your wireless on. Hopefully.

try this:
```
 sudo iwconfig wlan0 up
``` Then check the network monitor and see if you are manually able to enable the wireless options.



Sorry again, but I think on the 2200 card the interface is known as eth1,  anyway, found another interesting one which might be relevant.

[http://ubuntuforums.org/showpost.php?p=7866113&postcount=7](http://ubuntuforums.org/showpost.php?p=7866113&postcount=7)

---

### Post by pgar23 on 2009-10-22
@ Jm5:

try this:
[http://beginlinux.com/desktop_training/ubuntu/1119-network-set-up](http://beginlinux.com/desktop_training/ubuntu/1119-network-set-up)

---

### Post by jm5 on 2009-10-22
> **bkratz said:**
> Sorry again, but I think on the 2200 card the interface is known as eth1,  anyway, found another interesting one which might be relevant.

[http://ubuntuforums.org/showpost.php?p=7866113&postcount=7](http://ubuntuforums.org/showpost.php?p=7866113&postcount=7)


I tried all the commands on that page, nothing worked, this is getting pretty frustrating

---

### Post by pgar23 on 2009-10-23
Try this post   ^^^^^ above.

---

### Post by jm5 on 2009-10-23
ok so i opened up network tools just like the tutorial and i see etho1 and it looks good, loopback (lo) is there, and there is an unknown device(pan0) too, it has all zeros in the fields for ip address, ect.  i tried to set it up but its just not seeing the wireless card.

---

### Post by jm5 on 2009-10-24
Is there anyway to find a local ubuntu expert to look at this computer?  all the computer guys that I know dont know anything about linux

---

### Post by pgar23 on 2009-10-24
you dont need a local computer expert. You need to search these forums for a solution to your problem. Search the forum for a similar problem to yours, then private message the guy who solved the problem. Send him/her a link to this thread and request help.

---

### Post by jm5 on 2009-10-24
> **jm5 said:**
> i also ran this command, it appears that my firmwear is not present, right?


-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:df:e2:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:5d:b8:84:67:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


ok I'll do some more searching but i had a question, going back to this post i see three devices, the ethernet  interface, a network controller and the last ethernet interface i guess is my wireless card and it says "firmware=N/A"  what does that mean?

---

### Post by bkratz on 2009-10-24
> **jm5 said:**
> ok I'll do some more searching but i had a question, going back to this post i see three devices, the ethernet  interface, a network controller and the last ethernet interface i guess is my wireless card and it says "firmware=N/A"  what does that mean?



The last entry is regarding bluetooth-- I believe it means personal area network (pan)not really sure but it is bluetooth related and not related to your situation.

---

### Post by bitlock76 on 2009-10-24
Here's a long shot...there's some good information at the link below regarding troubleshooting drivers.  While it doesn't address your exact issue, you may be able to extract something that you can use to help resolve your problem.

[http://at76c503a.berlios.de/support.html](http://at76c503a.berlios.de/support.html)

---

### Post by pgar23 on 2009-10-25
I kno that we already tried this but, if we do it and it ends up working, you won't be upset..
Try:
```
sudo modprobe ipw2200
```
and:
```
sudo iwconfig eth0 up
```
after running those two, can you rigth click the network-monitor and enable wireless? or can you see any wireless networks when you left click the monitor?

---

### Post by pgar23 on 2009-10-25
Also, read this bug report, very similar symptoms of your case:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261886](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261886)

---

### Post by jm5 on 2009-10-26
> **bitlock76 said:**
> Here's a long shot...there's some good information at the link below regarding troubleshooting drivers.  While it doesn't address your exact issue, you may be able to extract something that you can use to help resolve your problem.

[http://at76c503a.berlios.de/support.html](http://at76c503a.berlios.de/support.html)

thanks for the help but I think that page is a little over my head, i had trouble making sense of all that or where to start

---

### Post by jm5 on 2009-10-26
> **pgar23 said:**
> I kno that we already tried this but, if we do it and it ends up working, you won't be upset..
Try:
```
sudo modprobe ipw2200
```and:
```
sudo iwconfig eth0 up
```after running those two, can you rigth click the network-monitor and enable wireless? or can you see any wireless networks when you left click the monitor?


I got this when i tried that again:

chandler@chandler-laptop:~$ sudo modprobe ipw2200
[sudo] password for chandler: 
chandler@chandler-laptop:~$ sudo iwconfig eth0 up
iwconfig: unknown command "up"
chandler@chandler-laptop:~$ 

I still get no " enable wireless " when I right click the monitor and no "wireless networks" when i left click it.  maybe I have a bad card? its hard to believe so many people have  had no issues out of the box with this card and I cant get it to work at all.

---

### Post by bkratz on 2009-10-26
As I said earlier I believe your wireless should be called eth1. Following is an interesting article which may be of some interest and possible help

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by anewguy on 2009-10-27
Did anyone check in admin network and see if the wireless is there and if roaming is active?

Dave :)

---

### Post by jm5 on 2009-10-27
> **anewguy said:**
> Did anyone check in admin network and see if the wireless is there and if roaming is active?

Dave :)

could explain in a little more detail on how to do this?

---

### Post by jm5 on 2009-10-27
-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:df:e2:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:5d:b8:84:67:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I was looking at this again and I noticed that network1 (the wireless card) is "unclaimed and doesnt have a logical name, why is that?

---

### Post by jm5 on 2009-10-27
> **bkratz said:**
> As I said earlier I believe your wireless should be called eth1. Following is an interesting article which may be of some interest and possible help

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)


"For people first setting up their connection, please note that the above also lists the driver used for the network card. In the example above, the driver used is ndiswrapper. If your network device comes back UNCLAIMED or there is no driver listed, then you have not correctly installed the driver for your device. You must review the procedures for installation of your wireless driver."

this kinda answers my question above, so I guess my drivers is not properly installed, ok so how do I figure that out?

---

### Post by jm5 on 2009-10-27
thanks again to everyone that is responding to this post

---

### Post by bkratz on 2009-10-27
> **jm5 said:**
> thanks again to everyone that is responding to this post


[http://ubuntuforums.org/showthread.php?t=1285401&highlight=2200BG](http://ubuntuforums.org/showthread.php?t=1285401&highlight=2200BG)



This is a posting of someone with the same wireless card.  See the post #9 to see what your 

sudo lshw

should look like. Note that the driver used is ipw2200.  he did not use ndiswrapper at all.  If worse comes to worst perhaps he would answer a PM as to what steps he took.

Still looking.  Do you see the same with the above command? (except for the driver of course)

---

### Post by jm5 on 2009-10-27
> **bkratz said:**
> [http://ubuntuforums.org/showthread.php?t=1285401&highlight=2200BG](http://ubuntuforums.org/showthread.php?t=1285401&highlight=2200BG)



This is a posting of someone with the same wireless card.  See the post #9 to see what your 

sudo lshw

should look like. Note that the driver used is ipw2200.  he did not use ndiswrapper at all.  If worse comes to worst perhaps he would answer a PM as to what steps he took.

Still looking.  Do you see the same with the above command? (except for the driver of course)
maybe I didnt read the post well enough but it appears he didnt have a wireless problem but a dvd playback issue, anyhow this is what I came up with:

this is his

*-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:06:04.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:22:63:0e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.7 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

this is mine

*-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0 maxlatency=24 mingnt=3

---

### Post by anewguy on 2009-10-28
Please post back the output of the following command, as you *should* be using the ipw2200 driver already:

dmesg | grep ipw2200

I've seen other posts where there are error messages in the log from the driver and it doesn't load the device.

Dave :)

---

### Post by jm5 on 2009-10-28
chandler@chandler-laptop:~$ dmesg | grep ipw2200
[   11.372484] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.372488] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.488808] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.488817] ipw2200 0000:03:03.0: setting latency timer to 64
[   11.489587] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.489640] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   11.612429] ipw2200: Unable to load ucode: -22
[   11.612443] ipw2200: Unable to load firmware: -22
[   11.612447] ipw2200: failed to register network device
[   11.617241] ipw2200 0000:03:03.0: PCI INT A disabled
[   11.617259] ipw2200: probe of 0000:03:03.0 failed with error -5
chandler@chandler-laptop:~$

---

### Post by anewguy on 2009-10-28
As you can see from the error messages, your device is not getting activated.  Let me search again for the threads that mentioned checking dmesg for the errors and see what they did to fix the problems.  I'll get back to you.

Dave :)

---

### Post by sandyd on 2009-10-28
quoting from
[http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL)
very bottom section.
 
```
12.  COMMON TROUBLESHOOTING TIPS
-----------------------------------------------
 
1.  The following Unknown symbol in module error appears when running the
load script:
 
[root@localhost ipw2200-1.0.7-pre10]# . load
Unloaded: ieee80211 ieee80211_crypt_tkip ieee80211_crypt_ccmp ieee80211_crypt_wep ieee80211_crypt
insmod: error inserting './ipw2200.ko': -1 Unknown symbol in module
 
CAUSE:  One or both of the following kernel configuration files may still have
entries from old installations. Follow the removal instructions in the
section above titled UPGRADING FROM PRIOR VERSIONS.
    /lib/modules/`uname -r`/build/include/linux/autoconf.h
    /lib/modules/`uname -r`/build/.config
 
 
2.  The following error appears in the dmesg kernel ring buffer output:
ipw2200: ipw-2.4-boot.fw load failed: Reason -2
**ipw2200: Unable to load firmware: -2**
ipw2200: failed to register network device
ipw2200: probe of 0000:02:03.0 failed with error -5
 
CAUSE: this may be due to any one of the following reasons:
-  firmware in wrong location or wrong firmware version. Follow the
   instructions in the section LOADING FIRMWARE VIA HOT-PLUG above.
-  sysfs may not be mounted. Follow the instructions in the SYSFS section
   above.
 
 
3.  The following error appears when I try to compile the driver.
make[1]: Entering directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make: *** [modules] Error 2
 
CAUSE: make sure that the kernel source is installed on your machine
 

```
 
not sure, but that might be related.

---

### Post by anewguy on 2009-10-28
Carlee, you're on the right track.  Several hits on the net suggest that a version of the firmware might be to blame, that it might be in the wrong location, etc..

Let's try something easy first - something mentioned on one of the threads as only a temporary fix - it doesn't work again on next boot:

sudo modprobe -r ipw2200

wait a few seconds

sudo modprobe ipw2200

check wireless again.

They also say that a certain version of the firmware-ipw2x00 package caused a problem, the solution being to remove it, and install via:

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)  looking for version 3.0 or 3.1.  

Right now I'm a little out of my comfort zone, as I've never had to work with any of the firmware like that before.  If someone out there is familiar with this process, please jump in.  If not, I'll keep searching for instructions and more info.

Dave :)

---

### Post by anewguy on 2009-10-28
Look in /lib/firmware, and see what is listed for ipw2xxx - (most probably ipw2200, but not sure).  Do any of them show as -3 something or are they -1 or -2 something?  I think this is where the above mentioned update to version 3.0 or 3.1 comes in - removing these modules and then installing according to the sourceforge link.

Dave :)

---

### Post by bkratz on 2009-10-28
> **jm5 said:**
> thanks again to everyone that is responding to this post

You might want to either watch or input into this current thread.

[http://ubuntuforums.org/showthread.php?t=1280992](http://ubuntuforums.org/showthread.php?t=1280992)

he is doing the same thing.

---

### Post by jm5 on 2009-10-29
> **anewguy said:**
> Look in /lib/firmware, and see what is listed for ipw2xxx - (most probably ipw2200, but not sure).  Do any of them show as -3 something or are they -1 or -2 something?  I think this is where the above mentioned update to version 3.0 or 3.1 comes in - removing these modules and then installing according to the sourceforge link.

Dave :)
  I tried the the sudo modprobe thing again but got nothing. here is my firmware folder:

[IMG]http://i225.photobucket.com/albums/dd213/jm686/Screenshot-firmware-FileBrowser.png?t=1256835106[/IMG]
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s225.photobucket.com/albums/dd213/jm686/?action=view&current=Screenshot-firmware-FileBrowser.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i225.photobucket.com/albums/dd213/jm686/Screenshot-firmware-FileBrowser.png%22%20border=%220%22%20alt=%22screen%20shot%22%3E%3C/a%3E[/IMG]

---

### Post by anewguy on 2009-10-30
I *think* you're at version 1.3, and from what I've seen looking around on the net, that can be a problem.  The suggestion is to go with the sourceforge info for installing version 3.0 or version 3.1 and then see how it goes.

Dave :)

---

### Post by jm5 on 2009-10-31
> **anewguy said:**
> I *think* you're at version 1.3, and from what I've seen looking around on the net, that can be a problem.  The suggestion is to go with the sourceforge info for installing version 3.0 or version 3.1 and then see how it goes.

Dave :)

sorry for the nubness but how exactly do I do that? just click the link and download it?

---

### Post by anewguy on 2009-10-31
Click the link.  Click either 3.0 or 3.1.  Scroll down and click I Agree on the licensing agreement - the download will start of a tgz file - save it to your desktop.

Next take a look at the link Carlee provided for the install - it should give you the info you need I hope.  Like I said a couple of posts back, I'm not really familiar with this and am out of my comfort zone - someone else may be able to help you better in removing the old firmware (including the modprobe -r as needed) files and getting the new going, but I *REALLY* don't know what I'm doing with this stuff - I just found some references on the net about your problem.  

I would really wait and see if someone more knowledgeable comes along, or,i like I did, do a google or yahoo search on ubuntu 9.10 ipw2200.  

EDIT:  For me to work with you on this, I would probably need to go with the windows driver files and use ndiswrapper.  If you would like to try that, just either get the driver files from your Windows install (if you have one), the driver disk, or download the driver files.  As I said, I really don't know what I'm doing with the firmware stuff, but I could easily help you try ndiswrapper.  Let me know.


Dave :)

---

