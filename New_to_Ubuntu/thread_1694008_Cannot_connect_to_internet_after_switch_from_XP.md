---
title: "Cannot connect to internet after switch from XP"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by P-nut on 2011-02-23
Firstly, hello. :P

This is my first post here and I should be treated as an absolute beginner, not just with Ubuntu but with computers. I know bits and bobs but better to forget that for now. 

Today I have got rid of XP and installed Ubuntu, installation went fine but cannot connect to the internet. I have looked at many forums and guides on the internet but they dont seem to start at a basic enough level for me to have any idea what is going on.

I will give any information asked for but to start...

Ethernet Interface - SiS900 PCI Fast Ethernet

Wired Connection to a Belkin Router

Worked fine on XP before swap to Ubuntu

ping -c 3 ubuntu.com gives reply unknown host ubuntu.com


Hope that is enough to give atleast a start.

Thanks,

Peanut

---

### Post by SnickerSnack on 2011-02-23
Found out what your router's ip address is, and enter it into a web browser (no need to www. or any such prefix, just enter it in the format xxx.xxx.xxx.xxx and hit enter); this should bring you to the router's configuration page.

In your router's settings, can you find any reference to the ubuntu machine

Is your router using DHCP (dynamic host configuration protocol)?  There will be some reference to this somewhere on the router's settings page, and it shouldn't be hard to tell whether is enabled.

What happens when you run

```
ping -c 1 xxx.xxx.xxx.xxx
```

(the router's ip address) in the command line terminal?

---

### Post by P-nut on 2011-02-23
Ok, so I tried the ip address in browser but says cannot establish a connection with the server...

Tried ping but says Network is unreachable

---

### Post by josephmills on 2011-02-23
ok so when you installed ubuntu did you have it hard wired in? also is do you have wifi? If so is your wireless card on, or recognize  by the ubuntu?

---

### Post by P-nut on 2011-02-23
No this computer does not have wireless. 

I was using the internet right till I rebooted to install Ubuntu, didnt touch anything but it said there was no connection when it was installing it. The cable was still in.

---

### Post by josephmills on 2011-02-23
ok go to 
Applications -> Accessories -> Terminal    
then type in lspci     and copy and paste that. also you can type in ifconfig  and that should help,

---

### Post by P-nut on 2011-02-23
On different computer so typed it out...

00:00.0 Host bridge: Silicon Intergrated Systems [SiS] 661FX/M661FX/M661FX Host (
rev 11)
00:01.0 PCI bridge: Silicon Intergrated Systems [SiS] Sis AGP Port (virtual PCI-t
o-PCI bridge)
00:02.0 ISA bridge:  "               "              "          "    SiS963 [MuTIOL Media IO] (r
ev 25)
00:02.1 SMBus:        "               "              "          "    SiS961/2 SMBus Controller
00:02.5 IDE interface: "             "              "          "    5513 [IDE]
00:02.7 Multimedia audio controller: "          "          "    AC'97 Soun 
d Controller (rev a0)
00:03.0 USB Controller: "           "              "          "   1.1 Controller (rev
0f)
00:03.1  "         "      "                "               "         "     "        "           "
0f)
00:03.3  "         "      "                "               "         "   2.0 Controller
00:04.0 Ethernet controller: "      "               "         "   SiS900 PCI Fast Et
hernet (rev 91)
00.08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (
rev 11)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11
)
00:09.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200SE] (
rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Seconda
ry) (rev 01)


ifconfig
Eth0 Link encap:Ethernet HWaddr 00:11:2f:6f:48:45
       inet6 addr: fe80: :211:2fff:fe6f:4845/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:876 errors:0 dropped:0 overruns:0 frame:0
       TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:109793 (109.7kb) TX bytes 31893 (31.8KB)
       Interrupt:19 Base address:0x8800

LInk encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1048 errors:0 dropped:0 frame:0
TXpackets:1048 errors:0 dropped:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:8156 (81.5KB) TX bytes:81560 (81.5KB)

ahhhhh haha

---

### Post by grahammechanical on 2011-02-23
There should be a network manager icon on the top panel to the right. Do you see it? It is like 4 conical arcs radiating upwards. It will have a red exclamation mark against it. When you are connected by cable the icon will change to 2 arrows going in opposite directions.

Do a right click on the icon. Is there a tick mark against the line Enable Networking? If there is not a tick mark then click Enable Networking to put the tick mark there. Tell us what happens.

If there is a tick mark there then click Enable networking to remove the tick mark and then click it again to put it back. It sounds silly but switching off and then switching on activates the network adapter in the motherboard. Tells us what happens.

Try rebooting the machine. When the OS is loaded try switching the modem/router off and on.

If the network icon is not there go to System>Preferences>Startup Applications and look for Network Manager in the list and select it to put Network Manager as a startup application. Reboot. Tell us what happens. The OS will give system messages. What messages are you seeing.

Regards.

---

### Post by P-nut on 2011-02-23
Ok, it was ticked so I unticked and reticked, did a little flashing thing like it was searching and then came up with "Wired Network - Disconnected you are now offline"

Rebooted, turned off router and back on, came back and nothing happened, I disabled and reenabled networking to get it to search again but just came up with same message "Wired Network - Disconnected you are now offline"

---

### Post by josephmills on 2011-02-23
Ok go to back to Termanial and type in sudo apt-get install update      (this will update the os)          then go to System->Administration->  additional drivers 
install if you have too    then do it also I found this well looking around [http://ubuntuforums.org/archive/index.php/t-879934.html](http://ubuntuforums.org/archive/index.php/t-879934.html)

---

### Post by P-nut on 2011-02-23
Typed sudo apt-get install update 

Said:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package update

Addtional drivers said no proprietry drivers avaiable on this system

---

### Post by josephmills on 2011-02-23
what type of ubuntu are you using? and what kind of computer?

---

### Post by frotzed on 2011-02-23
From the top:

1) Grab your Ubuntu installation disk and boot from it, but don't install, just click the option to try Ubuntu.  Do you get an Internet connection booting from the disk?

2) If the answer to #1 is "yes", then I'd try installing Ubuntu again, may have been a botched install.

3) If the answer to #1 is "no" then look at the back of your computer where you plug the network cable in.  When that cable is plugged in to that port, are there lights on next to the port?  Typically you'll see a green and an orange light when the Network Card is making a successful connection to a router/modem/etc.

---

### Post by SnickerSnack on 2011-02-24
> **josephmills said:**
> Ok go to back to Termanial and type in sudo apt-get install update      (this will update the os)          then go to System->Administration->  additional drivers 
install if you have too    then do it also I found this well looking around [http://ubuntuforums.org/archive/index.php/t-879934.html](http://ubuntuforums.org/archive/index.php/t-879934.html)

> **P-nut said:**
> Typed sudo apt-get install update 

Said:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package update

Addtional drivers said no proprietry drivers avaiable on this system

This is because apt uses a network connection to install things.  No network connection, no downloading of new packages.

---

### Post by P-nut on 2011-02-24
>  Grab your Ubuntu installation disk and boot from it, but don't  install, just click the option to try Ubuntu.  Do you get an Internet  connection booting from the disk?No, there is not a connection when booting from cd

> look at the back of your computer  where you plug the network cable in.  When that cable is plugged in to  that port, are there lights on next to the port?  Typically you'll see a  green and an orange light when the Network Card is making a successful  connection to a router/modem/etc.     Yes, there is a green and orange light

> what type of ubuntu are you using? and what kind of computer?     Ubuntu is version 10.10

Not sure what you mean by what kind of computer. 

It is a desktop, what other information do you need/ how to find it.

---

### Post by josephmills on 2011-02-24
> **P-nut said:**
> No, there is not a connection when booting from cd

Yes, there is a green and orange light

Ubuntu is version 10.10

Not sure what you mean by what kind of computer. 

It is a desktop, what other information do you need/ how to find it.



hi there again p-nut when I said what kind of computer that you where using i ment this.
right now I am using a dell latitude D610   with  a intell m 1.73 ghz with 1 gig of ram 
to find out your cpu ( processor )   you go to the terminal and type in    
cat /proc/cpuinfo 
to look at ram  go to termainal and type in.
free -m

---

### Post by P-nut on 2011-02-24
Ok, sorry.

This is an Intel(R) Pentium(R) 4 CPU 3.06GHz with 2gb RAM

The computer was made up for me ages ago, is there a way to find out motherboard too? I assume that is important?

---

### Post by josephmills on 2011-02-24
> **P-nut said:**
> Ok, sorry.

This is an Intel(R) Pentium(R) 4 CPU 3.06GHz with 2gb RAM

The computer was made up for me ages ago, is there a way to find out motherboard too? I assume that is important?


to figure out your mother board and other things you can go to terminal and type in the following
sudo dmidecode | more

you will see at the bottom of the terminal   it will say more hit enter to get more info and q to quit

---

### Post by P-nut on 2011-02-24
Ok, motherboard is baseboard yes? 

Manufacturer: ASUSTeK Computer INC.
Product Name: P4S800MX

---

### Post by frotzed on 2011-02-24
Well, it obviously seems like a driver issue to me.  I'd first say to make sure there are no additional drivers available.  I've seen more than once that the driver needed was proprietary so Ubuntu didn't install it automatically. Go to System > Administration > Additional Drivers.

Edit: Though I should mention, the lack of a proper driver is typically in regard to the wireless NIC.

Edit2: Another thing... Can you ping your router?

---

### Post by Kixtosh on 2011-02-24
Can you click on:

Applications > Accessories > Terminal

Then, in the Terminal Window, type:
```
lspci
```
This might yield a long list, but somewhere in there you should see your ethernet card listed. My output on this (wirelessly connected) laptop looks like this:

```
itzme@itzme-ubuntu-tosh:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
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
[B][COLOR="Red"]01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
02:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
[/COLOR][/B]02:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:0b.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```

What result are you getting for your ethernet controller (my wired and wireless are highlighted in red)?

---

### Post by P-nut on 2011-02-24
Thankyou to everyone who has helped and commented. Was solved with great help from josephmills.

Thankyou, now I begin to explore Ubuntu.

---

### Post by Kixtosh on 2011-02-25
Please share the answer, if you can, so that others that stumble across this thread might find it useful too!

---

