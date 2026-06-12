---
title: "[SOLVED] how do I get my wifi driver to work?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by gabriella on 2008-06-11
Hi,

I recently downloaded Hardy 8.04 and installed it without problems. I have the infamous Broadcom 43XX wirlesscard in my laptop and can't get it to work. So I read around here and followed the instructions I found. 

I.E. I used a wired connection. Then and using the install CD I went to System/Administration/Hardware drivers, found it listed, clicked on enable and it prompted me to configure B43 FWcutter then fetch and extract. I did all this and it told me "changes succesfully applied" and the enabled box for the driver was now checked. 

I then rebooted and the drivers no longer there! What am I doing wrong here?

Gabriella

---

### Post by Ayuthia on 2008-06-11
> **gabriella said:**
> Hi,

I recently downloaded Hardy 8.04 and installed it without problems. I have the infamous Broadcom 43XX wirlesscard in my laptop and can't get it to work. So I read around here and followed the instructions I found. 

I.E. I used a wired connection. Then and using the install CD I went to System/Administration/Hardware drivers, found it listed, clicked on enable and it prompted me to configure B43 FWcutter then fetch and extract. I did all this and it told me "changes succesfully applied" and the enabled box for the driver was now checked. 

I then rebooted and the drivers no longer there! What am I doing wrong here?

Gabriella
Can you post the results of lspci -nnm|grep 14e4?  This command is to run at the Terminal.  It will help to confirm that your card works with the current kernel.

You can check and see if the firmware is installed by checking /lib/firmware.  There should be a folder for b43 and b43legacy in there with files in it.

Please also post your lshw -C network.  It will also help us see if your wireless card is set up correctly.

---

### Post by timcredible on 2008-06-11
i have a broadcom card (don't know model number), i just installed ndiswrapper from synaptic, then just pointed to the .inf file for my wireless card that was already on the windows partition of the laptop, and rebooted, worked.

---

### Post by gabriella on 2008-06-12
> **Ayuthia said:**
> Can you post the results of lspci -nnm|grep 14e4?  This command is to run at the Terminal.  It will help to confirm that your card works with the current kernel.

You can check and see if the firmware is installed by checking /lib/firmware.  There should be a folder for b43 and b43legacy in there with files in it.

Please also post your lshw -C network.  It will also help us see if your wireless card is set up correctly.

Hi,

I ran both those commands but will hold of posting them for now as it seems it's a all a moot point.

I checked under /lib/firmware and there are no b43 folders there at all. So the question is why not, what did I do wrong? I followed the b43 fwcutter instructions and the response "changes succesfully applied"  and then the b43 driver box enable seemed to imply I'd done it correctly.

Gabriella

---

### Post by Ayuthia on 2008-06-12
> **gabriella said:**
> Hi,

I ran both those commands but will hold of posting them for now as it seems it's a all a moot point.

I checked under /lib/firmware and there are no b43 folders there at all. So the question is why not, what did I do wrong? I followed the b43 fwcutter instructions and the response "changes succesfully applied"  and then the b43 driver box enable seemed to imply I'd done it correctly.

GabriellaI am not for sure why it did not work.  Can you check and see if b43-fwcutter is installed?  You can check in Synaptic.  If it is installed, we could try and run the installer again from the Terminal:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```This will require a working internet connection.  It will ask you if you want it to find the firmware for you.  Select yes and it should install the firmware for you.

---

### Post by gabriella on 2008-06-12
> **Ayuthia said:**
> I am not for sure why it did not work.  Can you check and see if b43-fwcutter is installed?  You can check in Synaptic.  If it is installed, we could try and run the installer again from the Terminal:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```This will require a working internet connection.  It will ask you if you want it to find the firmware for you.  Select yes and it should install the firmware for you.

OK I couldn't find b43-fwcutter under /usr/share/synaptic but it is there in /usr/share

I ran the installer from the terminal and it got files. I just checked and in /lib/firmware there are now folders: b43 and b43 legacy

One thing has changed now in that the blue wifi light will turn on and off but still wont function. The results of the commands you initially sugested are pasted below. Thanks

mbdb@m2000:~$ lspci -nnm|grep 14e4

05:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Hewlett-Packard Company [103c]" "MX6125 [1356]"

mbdb@m2000:~$ 



mbdb@m2000:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:05:00.0

       logical name: eth0

       version: 10

       serial: 00:c0:9f:f3:97:78

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.70 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

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

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:14:a5:29:d2:c2

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

mbdb@m2000:~$

---

### Post by Ayuthia on 2008-06-12
> **gabriella said:**
> OK I couldn't find b43-fwcutter under /usr/share/synaptic but it is there in /usr/share

I ran the installer from the terminal and it got files. I just checked and in /lib/firmware there are now folders: b43 and b43 legacy

One thing has changed now in that the blue wifi light will turn on and off but still wont function. The results of the commands you initially sugested are pasted below. Thanks

mbdb@m2000:~$ lspci -nnm|grep 14e4

05:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Hewlett-Packard Company [103c]" "MX6125 [1356]"

mbdb@m2000:~$ 



mbdb@m2000:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:05:00.0

       logical name: eth0

       version: 10

       serial: 00:c0:9f:f3:97:78

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.70 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

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

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:14:a5:29:d2:c2

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

mbdb@m2000:~$

Try the following:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```
Let me know if you can see anything.

---

### Post by gabriella on 2008-06-12
> **Ayuthia said:**
> Try the following:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```
Let me know if you can see anything.

Not much! just this:

mbdb@m2000:~$ sudo depmod -ae
mbdb@m2000:~$ sudo modprobe b43
mbdb@m2000:~$ sudo ifconfig wlan0 up
mbdb@m2000:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:29:d2:c2
Sending on   LPF/wlan0/00:14:a5:29:d2:c2
Sending on   Socket/fallback
mbdb@m2000:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

mbdb@m2000:~$ 

I do appreciate your time on this ..thanks!

---

### Post by Ayuthia on 2008-06-12
I think that we might need to try the NDISwrapper route.  The 4318 rev 02 card has been playing well with Hardy.

I would recommend using this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").  You will need the driver in step 2a.

---

### Post by gabriella on 2008-07-02
> **Ayuthia said:**
> I think that we might need to try the NDISwrapper route.  The 4318 rev 02 card has been playing well with Hardy.

I would recommend using this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").  You will need the driver in step 2a.

Sorry, I've been dealing with a family crisis so havn't had time. I'll try rhe ndiswrapper route although I'm a tad intimifated! Will see what happens. Thanks

---

### Post by gabriella on 2008-07-07
hmmm...?
Following the insrtuctions on that link I get the following error messages:

Step 1:
sudo apt-get install ndiswrpaaer-utils-1.9
"E: couldn't find package ndiswrapper-utils-1.9"

and in Step 2A:

"E: couldn't find package cabextract"

And I did have the install CD in as well
any ideas?

---

### Post by gabriella on 2008-07-07
OK Ayuthia? or anyone else who help? I'm getting close...

I've learnt up and installed ndiswrapper (via snyaptic pacage mgr) and cabetract. I've downloaded the files and it confirms its done but then it says it can't find it! see below:

Tell me what I'm doing wrong!


23:53:58 (147.29 KB/s) - `sp34152.exe' saved [4494456]

mbdb@m2000:~$ cabextract sp34152.exe
sp34152.exe: library not compiled to support large files.
sp34152.exe: library not compiled to support large files.
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
mbdb@m2000:~$ sudo ndiswrapper -i bcmw15.inf
[sudo] password for mbdb: 
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by Ayuthia on 2008-07-08
> **gabriella said:**
> OK Ayuthia? or anyone else who help? I'm getting close...

I've learnt up and installed ndiswrapper (via snyaptic pacage mgr) and cabetract. I've downloaded the files and it confirms its done but then it says it can't find it! see below:

Tell me what I'm doing wrong!


23:53:58 (147.29 KB/s) - `sp34152.exe' saved [4494456]

mbdb@m2000:~$ cabextract sp34152.exe
sp34152.exe: library not compiled to support large files.
sp34152.exe: library not compiled to support large files.
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
mbdb@m2000:~$ sudo ndiswrapper -i bcmw15.inf
[sudo] password for mbdb: 
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
That usually means that you are not in the same directory as the bcmwl5.inf file.  I cannot remember if cabextract creates the sp34152 folder for you or not.  If it does, you will need to go into there and see if the bcmwl5.inf file is there.

---

### Post by gabriella on 2008-07-09
> **Ayuthia said:**
> That usually means that you are not in the same directory as the bcmwl5.inf file.  I cannot remember if cabextract creates the sp34152 folder for you or not.  If it does, you will need to go into there and see if the bcmwl5.inf file is there.

I can't find a SP34152 folder. 

However, in /home/mbdb folder(mbdb is my usser acct name) I have bcmwl5.inf bcmwl5.sys  sp34152.exe  and a whole load of other bcmwl and bcm43 files etc etc. There is also a bcm43xx folder.

I rather new to this (but learning fast) so what do I enter in terminal to point ndwrapper to them as in step 3 of the Feisty_No-Fluff instructions?
(is it possible to do this from the GUI now? just curious)

Oh, and the blue wifi light does now turn on but thats as far as it goes

---

### Post by spimby on 2008-07-09
> **gabriella said:**
> Hi,

I recently downloaded Hardy 8.04 and installed it without problems. I have the infamous Broadcom 43XX wirlesscard in my laptop and can't get it to work. 

Gabriella

I'm not sure this will help or not, but I have a Compaq with the Broadcom BCM4306.  When I initially installed the B43 FWcutter I failed to check the box in the upper left hand corner that said fetch and extract.  I was then in the "*I can check the box but it won't stay checked!*" hell.  I uninstalled and then reinstalled. Same thing. I then did a complete removal (including configuration files) using the synaptec package manager. I then re-installed it and made sure to check the box this time.  And it worked. 
\\:D/

---

### Post by gabriella on 2008-07-10
> **spimby said:**
> I'm not sure this will help or not, but I have a Compaq with the Broadcom BCM4306.  When I initially installed the B43 FWcutter I failed to check the box in the upper left hand corner that said fetch and extract.  I was then in the "*I can check the box but it won't stay checked!*" hell.  I uninstalled and then reinstalled. Same thing. I then did a complete removal (including configuration files) using the synaptec package manager. I think re-installed it and made sure to check the box this time.  And it worked. 
\\:D/

hmmm...it might. I now have vague memory of something like that happening but I've tried so many things and checked this that and the other I forget. I would have prefered to do it using the GUI method. That said I'm enjoying using terminal, just that I realy a 101 tutorial to speed up the process, hence my last comment!

I've also loaded all these files now which have yet to work. I'm seriously considering what you said but taking it a stage further and wiping the partition and doing a clean fresh install. But hey..at least the blue wireless light comes on now! This is all on my laptop, I haven't even considered my desktop yet!

Compaq Presario M2000
BC4318
Hardy 8.04

---

### Post by gabriella on 2008-07-12
> **Ayuthia said:**
> That usually means that you are not in the same directory as the bcmwl5.inf file.  I cannot remember if cabextract creates the sp34152 folder for you or not.  If it does, you will need to go into there and see if the bcmwl5.inf file is there.

Well I went through the whole ndiswrapper routine again and evrything worked this time. I don't know what happened first time but now I have the wifi fully functioning! Many thanks for your help!

---

### Post by gabetz08 on 2008-07-14
i have been having the same problem with my wireless card 
greg@Ubuntu:~$ lspci -nnm|grep 14e4
06:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4303 802.11b Wireless LAN Controller [4301]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [12f3]"

i try to connect and the thing spins for a little bit and the light for my wireless card turns on and off every once in a while. any suggestions? thanks in advance.

---

### Post by gabriella on 2008-07-16
> **gabetz08 said:**
> i have been having the same problem with my wireless card 
greg@Ubuntu:~$ lspci -nnm|grep 14e4
06:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4303 802.11b Wireless LAN Controller [4301]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [12f3]"

i try to connect and the thing spins for a little bit and the light for my wireless card turns on and off every once in a while. any suggestions? thanks in advance.

I can't answer advise you as I pretty new to this. What I suggest is you go through the same steps recommended to me by Authia after my original question. Using first the GUI method and then if that doesn't work then the ndiswrapper route. ndiswrapper worked for me the second time around (dont know why it didnt first time).

---

### Post by Bob Stine on 2008-07-20
> **gabriella said:**
> OK Ayuthia? or anyone else who help? I'm getting close...

I've learnt up and installed ndiswrapper (via snyaptic pacage mgr) and cabetract. I've downloaded the files and it confirms its done but then it says it can't find it! see below:

Tell me what I'm doing wrong!


23:53:58 (147.29 KB/s) - `sp34152.exe' saved [4494456]

mbdb@m2000:~$ cabextract sp34152.exe
sp34152.exe: library not compiled to support large files.
sp34152.exe: library not compiled to support large files.
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
mbdb@m2000:~$ sudo ndiswrapper -i bcmw15.inf
[sudo] password for mbdb: 
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
You report that you installed cabextract from the Synoptic package manager.

How?  I'm trying to do this, and it's not at all obvious.

Thanks!

---

### Post by gabriella on 2008-07-25
> **Bob Stine said:**
> You report that you installed cabextract from the Synoptic package manager.

How?  I'm trying to do this, and it's not at all obvious.

Thanks!

Hi,

Go to System/Administration/Synaptic Package Manager. Then in the window upper right under pacakge you just scroll down until you get to Cabextract and check the box on the left and follow the steps for instalation. Hope this helps

Gabriella

---

### Post by uberlube on 2008-07-25
For anyone trying to install broadcom wireless use the howto in my sig.

---

