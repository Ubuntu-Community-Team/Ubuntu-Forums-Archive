---
title: "Ubuntu cant find wireless nextwork"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by tallbus1 on 2009-06-01
The title says it all, I am using an old(2005ish) Compaq laptop Ubuntu was partitioned and installed  by Wubi 9.04 i believe...I click the little network thing at the top right, and my network doesnt show up I have no idea what to do

---

### Post by tallbus1 on 2009-06-01
bump

---

### Post by jrothwell97 on 2009-06-01
First, check your wireless card is switched on.

Is there an empty 'wireless' section in the menu which drops down from the network manager icon? If not, you may need to install additional software (drivers) to get it to work.

Alternatively, your router could simply have SSID broadcast disabled, in which case you'll have to enter things manually. Go to System/Preferences/Network Connections.

Good luck.

---

### Post by tallbus1 on 2009-06-01
Actually the wireless menu is blanked out...like i cant click it as is the wired one....I have my wireless card turned on...do i need that ndiswrapper or whatever

---

### Post by starcannon on 2009-06-01
Well lets see whats showing up first.

```

iwconfig

```
and
```

sudo lshw -C network

```
post the output of those commands in a codebox if you can.

GL

---

### Post by tallbus1 on 2009-06-01
Ill get back to you as soon as possible im currently studying for a test as well so youll have to forgive me.

---

### Post by tallbus1 on 2009-06-01
ashton@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extension

ashton@ubuntu:~$ sudo lshw -C network
[sudo] password for ashton: 
  *-network:0      C          
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a5:6c:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ef:a3:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:f6:94:eb:02:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I also realized that in Windows there is a small Blue button to activate my network card that won't turn on when i press it in ubuntu... these are the results of an iwconfig and sudo lshw -C network thing

---

### Post by tallbus1 on 2009-06-01
Bump...I'm sorry for being so annoying, but id really like to figure this out.

---

### Post by tallbus1 on 2009-06-01
Sorry for the quadruple post, but my computer uses something called "HP Wireless Assistant" to connect to the internet is there a driver i can use to make this little blue light turn on (turn on my wireless card), and further connect to the wireless network im on.

When i go under network adapters in my Device MAnager in windows i get these three things:

1394 Net Adapter
Broadcom 802.11b/g WLAN
Realtek RTL8139/810x Family Fast Ethernet NIC

---

### Post by tallbus1 on 2009-06-01
bump

---

### Post by shizumasa14 on 2009-06-01
Which release are you using?

---

### Post by kerry_s on 2009-06-01
did you install the firmware?

**sudo apt-get install b43-fwcutter**

---

### Post by tallbus1 on 2009-06-02
Im using the new 9.04 I think its Jaunty Jackalope, Ill try this firmware, even though i have no idea what it will do lol :) Ill get back to you

---

### Post by tallbus1 on 2009-06-02
so i did

sudo apt-get install b43-fwcutter

And it says it can't find the package...

---

### Post by tallbus1 on 2009-06-02
Switching between my OS's is really getting annoying I need to figure something out...

---

### Post by bodhi.zazen on 2009-06-02
It appears your net work card is working, at least it is listed in iwconfig.

Now configure it :)

Are you using WEP / WPA ?

---

### Post by tallbus1 on 2009-06-02
I dont know the difference, I know i sound stupid, but I'm not sure, if you could explain it to me.

---

### Post by tallbus1 on 2009-06-02
Also i added bodhi.zazen to Yahoo...if youd like to help me there

---

### Post by tallbus1 on 2009-06-02
bump

---

### Post by tallbus1 on 2009-06-02
Just so people know, I'm going to continue bumping this until somone decides they want to help...

---

### Post by halitech on 2009-06-02
just so you know, bumping a thread every 5 minutes will get you attention but not the attention you want from the mods

have you checked the restricted drivers to see if its there?

System>Administration>Hardware Drivers

---

### Post by starcannon on 2009-06-02
> **halitech said:**
> just so you know, bumping a thread every 5 minutes will get you attention but not the attention you want from the mods

have you checked the restricted drivers to see if its there?

System>Administration>Hardware Drivers
+1 the Hardware Drivers utility should handle that card no problem.

Just go to:
System>Administration>Hardware Drivers
[IMG]http://img30.imageshack.us/img30/724/hardwaredriversmenu.png[/IMG]
Then Choose Your WiFi Card from the list in this Window (yours will have different hardware listed than mine does.
[IMG]http://img211.imageshack.us/img211/1783/hardwaredrivers.png[/IMG]

You may need to do a quick Reboot, can't remember for sure, its been awhile since I dealt with a restricted WiFi card, but anyway, once its loaded, you should then be able to see Hotspots listed when you click on the Network Manager Applet in the upper right hand corner of your Desktop(top toolbar, right hand side).

GL and Have Fun.

---

### Post by tallbus1 on 2009-06-02
Actually there is absolutely nothing there...I'm not sure what to do, Ive also tried a couple apt-get's and it says it cant find the packages do you think the install is corrupt? (I used WUBI)

---

### Post by starcannon on 2009-06-02
First, it may be useful to get online with an ethernet cable, this will allow you to update and download any required items.

Second if you still get nothing available in the Hardware Drivers utility, then you can always try Ndiswrapper, I've had great success with it in the past as well.

```

sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9 b43-fwcutter

```

P.S. I included fwcutter in the command, again you will have to have an internet connection going to pull this off correctly, some or all of this may be on the cd, but it won't neccessarily be the same version as contained in the online repositories.

GL and have fun.

---

### Post by tallbus1 on 2009-06-02
So I have to be on an internet connection to use the above commands?

---

### Post by starcannon on 2009-06-02
> **tallbus1 said:**
> So I have to be on an internet connection to use the above commands?
I would recommend it, that or if they are available on the CD, not sure what all is on the CD to be honest, I just use it to install, then I plug in an ethernet cable and grab my updates, and restricted drivers that way.

---

### Post by tallbus1 on 2009-06-02
I sent you a PM, but it said it wasnt able to find that package so im going to have to do it manually from windows because i dont have acess to an ethernet, i need you to tell me how.

---

### Post by imilio123123 on 2009-08-31
I had the problem that installing the "new" ubuntu 9.04 from Dell my wireless didn´t (do not) work at first and in "  System -->  Administration  --> Hardware drivers  " I activated it and worked (I had to re-start the laptop).

The thing is that I just migrated to Linux --> to Ubuntu and I don´t know much about the "Terminal", many solutions searched before are for me too difficult to solve with the terminal,  so this was really easy to do, [  but I think I was lucky to see there my wireless card (I could also see my nvidia card but nothing else, so, really lucky I think)  ]

Anyway, thank you "  Starcannon  " for your post about " Hardware Drivers ", I just didn´t know about it.

---

