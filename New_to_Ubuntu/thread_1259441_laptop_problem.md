---
title: "laptop problem"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by dan13oct on 2009-09-06
Hi!
I recently installed ubuntu on my laptop and it's moving really slowly, like when i download a torrent i can't do anything else... or when i watch on youtube videos i can't watch them full screen because it looks like i am having on a fps game 15 fps, or when i press shut down i have to wait 5-6 seconds for the buttons to be activated.
I have a hp laptop 1.73 ghz 512 ram .
If you have any ideas  thanx!
Sorry if my problem is a common one and has allready  been solved and for my bad english.

---

### Post by hockeytux on 2009-09-06
Have you got just Ubuntu on it or Windows as well?

---

### Post by coldReactive on 2009-09-06
You're going to want something a little less demanding than Ubuntu. Did you try Xubuntu or Puppy Linux or Crunchbang Linux?

> **hockeytux said:**
> Have you got just Ubuntu on it or Windows as well?

Also this.

---

### Post by dan13oct on 2009-09-06
I have also windows xp installed on it. But i don't think the problem is my computer configuration because i had ubuntu installed on my amd k7 700 mhz 256 ram , and it worked better than on my laptop.
I have kiwi ubuntu installed because i have pppoe connection with my isp and on ubuntu i can't connect.

---

### Post by hockeytux on 2009-09-06
Ubuntu also worked on my 256MB RAM laptop but it was quite slow. Crunchbang is a really good option and also Xubuntu (though its a little heavier).

---

### Post by dan13oct on 2009-09-06
I would install a diferent linux version but it's the only one i know that i can use to connect to the internet using a pppoe connection on my isp.I used ubuntu but i can't connect.

---

### Post by hockeytux on 2009-09-06
Crunchbang and Xubuntu are based on Ubuntu so there shouldnt be any problems with setting up your connection.

---

### Post by dan13oct on 2009-09-06
There are problems because i can't connect using the terminal. And my isp doesn't offer suport for linux users.

---

### Post by swoody on 2009-09-06
You shouldn't have any issues running Ubuntu on your laptop. I have a very similar Compaq laptop with a 1.73 GHz Celeron M, and 512 MB Ram (recently upgraded to 2GB). I know your system should be able to run Ubuntu fine, as mine has for quite some time. With the onboard graphics it's not going to be as smooth as it could be, though. 

Are you experiencing any of these issues with XP?

Try going into System>Admin>Hardware Drivers, and making sure if there are any drivers available for your graphics that they are installed and active.

You may also want to make sure your graphics are turned down by going into System>Preferrences>Appearance and under the 'Visual Effects' tab, make sure it's set to 'None'. 

Have you run memtest or a HD diagnostic recently? You may want to give it a shot to make sure there's no issues with your RAM and HDD.

Try these out, and let us know if they help you out at all :)

---

### Post by dan13oct on 2009-09-06
On windows xp i have no problem. I have no visual effects and  at the hardware drivers window it's writen : "No proprietary drivers are in use on this system. "

---

### Post by swoody on 2009-09-06
Well that's very good to hear. You still may want to run memtest and a HD diagnostic to rule those out as well. Memtest can be run from the bootup menu, or a liveCD. Do you know offhand the manufacturer of your HDD? If not, run:

```
sudo lshw -C disk
```

and if you want to post everything under '*disk' we should be able to get you squared away with a reccomendation for a HD diagnostic :)

---

### Post by dan13oct on 2009-09-06
description: ATA Disk
       product: TOSHIBA MK6025GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: KA20
       serial: Z5MQ7492S
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=95aa95aa
This is all... But now i have another problem, my network card isn't recognized anymore after a restart.

---

### Post by halitech on 2009-09-06
a Pentium or Celeron 1.7gig machine will work just fine with Ubuntu even with just 512 meg of ram. What video and network cards do you have in your machine?
```
lspci
```

---

### Post by dan13oct on 2009-09-06
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I put it all here...

---

### Post by halitech on 2009-09-06
there are 2 fixes for the issue you are facing. Basically Jaunty shipped with a new xorg and the intel drivers don't work very well. 

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

for the network, what do you get for results with
```
sudo ifconfig
```

---

### Post by swoody on 2009-09-06
Well unfortunatley, Toshiba doesn't make their own HDD diagnostic tool. However, Hitachi's Fitness Test is supposed to work on any brand, and comes highly reccomended. You can download the CD Image (.iso file) from [HERE]("http://www.hitachigst.com/hdd/support/download.htm#DFT"), burn it to a CD, and boot straight from it.

Is your computer still under warranty by chance? If your slow Ubuntu, and your network card not being recognized are part of the same issue, this may be a hardware problem, possibly an issue that is just beginning with your motherboard. Did you run upgrades or do anything else to change the system just before the restart?

Does:
```
iwconfig
```
recognize your card at all?

---

### Post by dan13oct on 2009-09-06
eth0      Link encap:Ethernet  HWaddr 00:14:c2:e1:ff:de  
          inet6 addr: 2002:bc1a:c9f6:5:214:c2ff:fee1:ffde/64 Scope:Global
          inet6 addr: fec0::5:214:c2ff:fee1:ffde/64 Scope:Site
          inet6 addr: 2002:bc19:c046:4:214:c2ff:fee1:ffde/64 Scope:Global
          inet6 addr: fec0::4:214:c2ff:fee1:ffde/64 Scope:Site
          inet6 addr: fe80::214:c2ff:fee1:ffde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:380370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107684337 (107.6 MB)  TX bytes:1386020 (1.3 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:15:00:4a:5e:93  
          inet6 addr: fe80::215:ff:fe4a:5e93/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:800 (800.0 B)
          Interrupt:21 Base address:0xc000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.25.189.89  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:15548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:21144179 (21.1 MB)  TX bytes:1105046 (1.1 MB)

this is all but at the wired network tab : device not managed

---

### Post by dan13oct on 2009-09-06
The network card problem appeared 5 minutes ago... but i can connect thru a wireless network

---

### Post by halitech on 2009-09-06
your ppp0 connection is showing an ip address - inet addr:188.25.189.89 P-t-P:10.0.0.1 Mask:255.255.255.255

are you able to ping (without using the wireless connection) google.com or 74.125.67.100

---

### Post by dan13oct on 2009-09-06
yes i am able to ping google... i think because i have my wireless connection

---

### Post by halitech on 2009-09-06
make sure you disconnect the wireless and then try again.

---

### Post by dan13oct on 2009-09-06
i can ping google without my wireless connection but it's strange it disappeared from the wired networking and for several minutes i didn't have an internet connection

---

### Post by halitech on 2009-09-06
that might have been a glitch with your isp for a few minutes.

---

### Post by dan13oct on 2009-09-06
maybe but i didn't fix my biggest problem

---

### Post by swoody on 2009-09-06
You mean the lagging you're experiencing in Ubuntu? Did you try the links that halitech posted above?

> **halitech said:**
> [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by dan13oct on 2009-09-06
I tried [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) but i didn't have acces to save the file... and i don't know to import the GPG key

---

### Post by halitech on 2009-09-06
save what file?

---

### Post by dan13oct on 2009-09-06
after adding these lines 
 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

---

### Post by halitech on 2009-09-06
did you open the file with gksudo or just gedit /etc/apt/sources.list? If you didn't use gksudo you won't have rights so modify and save so open it with
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by swoody on 2009-09-06
To add the GPG key, you just have to run this in a terminal:
```
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
```
It'll ask you for your password, so enter it, and press 'enter' and you should be good to go. 

It sounds like you may have run the command without 'sudo' if it's giving you 'access' errors. Try it again and make sure to have 'sudo' in front of it.

---

### Post by dan13oct on 2009-09-06
I think i should install ubuntu from scratch and see if it works...

---

### Post by halitech on 2009-09-06
if it didn't work the first time it won't work the second time unless you install 8.04 or 8.10 instead of 9.04 and then don't upgrade

---

### Post by dan13oct on 2009-09-07
I installed 8.10 and it works fine ... but can i update because i can't use pigdin?

---

### Post by coldReactive on 2009-09-07
> **dan13oct said:**
> I installed 8.10 and it works fine ... but can i update because i can't use pigdin?

Did you update pidgin via PPA? Or did you leave it as-is?

PPA: [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

---

### Post by dan13oct on 2009-09-07
I did not update the program i will try it now.
Shoul i install all the updates or just pidgin?

---

### Post by halitech on 2009-09-07
if you upgrade to 9.04 you will be in exactly the same place you were when you installed 9.04. Stick with 8.10 and just upgrade pidgin.

---

