---
title: "Ubuntu 10.04 Networking Question...."
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Foamdad on 2010-11-22
I just installed Ubuntu 10.04 on my Dell 1520 Laptop and I can't get ANY networking to happen (wireless or ethernet). I did a lshw -C network and this is what I got:

WARNING: you should run this program as super-user
    *-network
            description: Network controller
            product: BCM4328 802.11a/b/g/n
            vendor: Broadcom Corporation
            physical id:  0
            bus info:  pci@0000:0c:00.0
            version 03
            width 64 bits
            clock 33MHz
            capabilities: bus_master cap_list
            configuration:  driver=b43-pci-bridge latency=0
            resources:  irq:17  memory: fe8fc00-fe8fffff memory: f0000000-f00fffff(prefetchable)
     *-network
            description: Ethernet Interface
            product: BCM4401-B0 100Base TX
            vendor: Broadcom Corporation
            physical id:  0
            bus info:  pci@0000:03:00.0
            version 03
            serial: 00:21:70:6b:ed:59
            width 32 bits
            clock 33MHz
            capabilities: bus_master cap_list ethernet physical
            configuration:  broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
             resources: irq:17 memory:fe5fe000-fe5fffff

iwconfig:

l0             no wireless extensions.


eth0         no wireless extensions.


What am I missing. Any help would be appreciated.

---

### Post by spikoley on 2010-11-22
Post the results of *ifconfig -a*.

```
ifconfig -a
```

Are you trying to connect with wireless or ethernet?

---

### Post by Foamdad on 2010-11-22
> **spikoley said:**
> Post the results of *ifconfig -a*.

```
ifconfig -a
```Are you trying to connect with wireless or ethernet?

ifconfig -a:

Link encap: Ethernet HWaddr 00:21:70:6b:ed:59
UP BROADCAST RUNNING MULTICAST  MTU: 1500  Metric:1
RX packets:0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 0 (0.0 B)  TX bytes 0 (0.0 B)
Interrupt: 17

Link encap: Local Loopback
inet addr: 127.0.0.1  Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING  MTU: 1500  Metric:1
RX packets:12 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 12 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 720 (720.0 B)  TX bytes: 720 (720.0 B)

I'm actually trying to do either. I can't seem to get a connection on either wireless or internet. And there are no wireless connections available int he network manager.

---

### Post by nm_geo on 2010-11-22
I am sure you have toggled the left side button (wireless) on the laptop. Right?

---

### Post by Foamdad on 2010-11-22
> **nm_geo said:**
> I am sure you have toggled the left side button (wireless) on the laptop. Right?

I'm really sorry. I don't know what "left side button" you're referring to. I am using a dual-boot setup and the wireless works fine on Win. It just seems like I can't get ANY networking going (wired or wireless).

---

### Post by nm_geo on 2010-11-22
Okay the left side has a button switch that controls wireless wifi on most dells.  So the you can connect with the  on both direct and wireless?  Were you able to connect with the CD or Flash drive with Ubuntu?

Maybe this link will help
[https://help.ubuntu.com/8.04/internet/C/networking-enable.html](https://help.ubuntu.com/8.04/internet/C/networking-enable.html)

---

### Post by yankysunny on 2010-11-22
Is the wifi LED is on or not? Try to reset that button as asked by nm_geo
Is this your first time[In Ubuntu] to connect to internet after you installed Ubuntu , if not have you set any keyring?

---

### Post by max00355 on 2010-11-22
make sure all the hardware drivers are installed you can find them in Synaptic Packet Manager and install broadcom that should help

---

### Post by Foamdad on 2010-11-22
> **yankysunny said:**
> Is the wifi LED is on or not? Try to reset that button as asked by nm_geo
Is this your first time[In Ubuntu] to connect to internet after you installed Ubuntu , if not have you set any keyring?

No. Network light isn't on and I have not been able to connect to the internet w/ Ubuntu since I installed (wired or wireless). I have not set a keyring.

There is no reset button for the wireless on my 1520.

---

### Post by yankysunny on 2010-11-22
How you are connecting to the internet? are you able to see any wireless icon on the top right panel?

---

### Post by spikoley on 2010-11-22
> **Foamdad said:**
> No. Network light isn't on and I have not been able to connect to the internet w/ Ubuntu since I installed (wired or wireless). I have not set a keyring.

There is no reset button for the wireless on my 1520.

My Dell laptop has a blue fn key that works like a shift key.  Does yours have one?  Look for it in the the lower left hand corner of the keyboard and the WiFi button should be near the F2 button.

---

### Post by Foamdad on 2010-11-22
> **yankysunny said:**
> How you are connecting to the internet? are you able to see any wireless icon on the top right panel?

Ok. Some clarification:

I have installed Ubuntu 10.04 as a dual-boot to my laptop. On that system, I am not able to connect to the internet either wirelessly or wired when I boot into Ubuntu. When I boot into Windows, I am able to connect just fine. I am currently posting from my desktop.

"are you able to see any wireless icon on the top right panel?"

I'm assuming you mean the Network Manager? Yes, I can see that but there are no connections listed. Under "wired" it says "Disconnected". When I connect a ethernet cable, Ubuntu tries to connect to the network, but fails. There is no "wireless" option available.

Sorry if I'm not being very clear. I'm new at this and am trying to get this to work.

---

### Post by nm_geo on 2010-11-22
Did you check the Network Manager in the upper right panel?
Right click on the Icon.

---

### Post by Foamdad on 2010-11-22
> **spikoley said:**
> My Dell laptop has a blue fn key that works like a shift key.  Does yours have one?  Look for it in the the lower left hand corner of the keyboard and the WiFi button should be near the F2 button.

I've seen the buttons on other Dell's, but this doesn't have any wireless indicator on/in the keyboard area. It does have a WiFi indicator below the power/HD Led's on the right side of the keyboard, but it doesn't light when I boot into Ubuntu (it does when I boot into Windows and have connectivity). Its really weird.

---

### Post by Foamdad on 2010-11-22
> **nm_geo said:**
> Did you check the Network Manager in the upper right panel?

Yup. I'm not getting anything. Even when I'm directly connected to my modem w/ a network cable.

---

### Post by nm_geo on 2010-11-22
So you right clicked on the Icon and what did you see?  I right click on mine and if I disable Network my wifi goes out too.

---

### Post by Foamdad on 2010-11-22
> **nm_geo said:**
> So you right clicked on the Icon and what did you see?  I right click on mine and if I disable Network my wifi goes out too.

Right-clicking brings up dialog box:

Enable Networking (checked)
Enable Notifications (checked)
Connection Information (dark)
Edit Connections...
About

---

### Post by yankysunny on 2010-11-22
The options in network manager is greyed out?As u said disconnect option. If it is not then u r connected.
It should be weird that if Ubuntu didnt installed drivers for both.

---

### Post by yankysunny on 2010-11-22
> **Foamdad said:**
> Right-clicking brings up dialog box:

Enable Networking (checked)
Enable Notifications (checked)
Connection Information (dark)
Edit Connections...
About
on left click?

---

### Post by nm_geo on 2010-11-22
These what I see and I am working on wireless right now.  You installed Ubuntu from what media and did you do md5sum check on the iso?

Enable Networking (checked)
Enable Wireless (checked)
Enable Notifications (checked)
Connection Information - Not dark give connection info
Edit Connections...
Abouts

---

### Post by Foamdad on 2010-11-22
> **yankysunny said:**
> on left click?

Wired Network
 disconnected
VPN Connections -->

---

### Post by Foamdad on 2010-11-22
> **nm_geo said:**
> These what I see and I am working on wireless right now.  You installed Ubuntu from what media and did you do md5sum check on the iso?

Enable Networking (checked)
Enable Wireless (checked)
Enable Notifications (checked)
Connection Information - Not dark give connection info
Edit Connections...
Abouts

I was a dummy and let Ubuntu instal the "wubi" and do a direct partition/install. I didn't really see an option for letting me run it from an image or memory stick. I may have missed it tho.

---

### Post by nm_geo on 2010-11-22
Foamdad I would try to connect to the wired connection again and check the network
manager icon. When i first got my Ubuntu up from a live flash drive I went right on line with the wired connection, but my driver needed changing on my wireless.  Perhaps someone with more experience will come to you assistance.  I don't mind at all but I know very little about the command line information on starting up the network or wireless.

---

### Post by spikoley on 2010-11-22
> **nm_geo said:**
> Foamdad I would try to connect to the wired connection again and check the network
manager icon. When i first got my Ubuntu up from a live flash drive I went right on line with the wired connection, but my driver needed changing on my wireless.  Perhaps someone with more experience will come to you assistance.  I don't mind at all but I very little about the command line information on starting up the network or wireless.

I agree.  It is easier to get the wired connection working first.  You might have to update your wireless drivers online.

---

### Post by yankysunny on 2010-11-22
open the terminal and do this for the wired
```
ifconfig eth0{or whtevr u have for ur ethernet} up 
```

---

### Post by nm_geo on 2010-11-22
> **Foamdad said:**
> I was a dummy and let Ubuntu instal the "wubi" and do a direct partition/install. I didn't really see an option for letting me run it from an image or memory stick. I may have missed it tho.

You can download the iso to a live flash drive from the main Ubuntu website. If you have a spare USB flash drive it will come in handy anyway.  From the live USB you can try to connect with the wired connection first.  Then you will also have Gparted which you can use to do your partitioning on the hard drive too.  It is just an option that worked well for me.

I am booting Fedora 14 as well now, but Gparted saved me on my first bad install of Fedora.

---

### Post by nm_geo on 2010-11-22
Foamdad here is one more command line try.

```
sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start                      
```I have no idea if it will work but it will not hurt from where you are right now.

---

### Post by Foamdad on 2010-11-23
Thanks for all the good advice. I finally got the connection going. SOLVED.

---

### Post by nm_geo on 2010-11-23
Foamdad what exactly helped you get it fixed?  Just wondering.. I looked back and noticed you were not getting the logical name for eth0 and thought about some more stuff to try.  Did you do a re-install from a live CD or USB? Again I am curious.

---

