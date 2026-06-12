---
title: "Belkin Wireless G+ USB adapter"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Lemuel111 on 2009-06-01
Hi folks I am totally new to Linux and the way it runs. I have read Ubuntu Kung Fu and looked at my help in Ubuntu Jaunty but I am still having problems getting connected to the internet via my Belkin wireless G+ device. I have download a number of items which are supposed to help (RutilTv0.14; gtk+-bundle_2.16.1-20090419_win32.zip; rtl8185; wpa_supplicant-0.4.9) but the 'read me' suggest you should only use these if you know what your doing (which I don't!!). Plus I don't know how to install them. Can anyone help or otherwise I will get into trouble with my wife for wasiting time with Linux instead of using Windows!!

---

### Post by mapes12 on 2009-06-01
In my experience the problem can usually boiled down to an unsupported wifi adapter. Here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Good luck.

Mark

---

### Post by Lemuel111 on 2009-06-01
Thanks Mark. I've got WiCd onto my desktop but how do I install it??

---

### Post by Lemuel111 on 2009-06-01
I appear to have installed Wicd as i have the symbol present on my top bar but I am still not connecting to the internet. In Applications I click on wicd but nothing happens. What do I need to do next?
Thanks in advance.

---

### Post by superprash2003 on 2009-06-01
post output of** lshw -C network** from the terminal

---

### Post by Lemuel111 on 2009-06-03
I typed sudo Ishw -C network & then Ishw -C network and both times it just said "command not found"

---

### Post by Lemuel111 on 2009-06-03
I've made sure that I have completley removed network manager & network manager gnome and then reinstalled wicd. I checked terminal & towards end it says
 "setting up wicd (1.5.9)..
ls:cannot access/opt/wicd/encryption/configurations/: No such file or directory
*Starting Network connection manager wicd                                                       {fail}

Processing triggers for man-dib ...."

Any suggestions??

Thanks in advance

---

### Post by LewRockwell on 2009-06-03
> **Lemuel111 said:**
> I typed sudo Ishw -C network & then Ishw -C network and both times it just said "command not found"

```
sudo lshw -C network
```

(that's little L little S little H little W)

that should help

---

### Post by Lemuel111 on 2009-06-03
I got a bit more 'processing' that time but when I click on wicd still nothing.

---

### Post by LewRockwell on 2009-06-03
> **Lemuel111 said:**
> Hi folks I am totally new to Linux and the way it runs. I have read Ubuntu Kung Fu and looked at my help in Ubuntu Jaunty but I am still having problems getting connected to the internet via my Belkin wireless G+ device. I have download a number of items which are supposed to help (RutilTv0.14; gtk+-bundle_2.16.1-20090419_win32.zip; rtl8185; wpa_supplicant-0.4.9) but the 'read me' suggest you should only use these if you know what your doing (which I don't!!). Plus I don't know how to install them. Can anyone help or otherwise I will get into trouble with my wife for wasiting time with Linux instead of using Windows!!

I'm usually hesitant to assume what all your makes and models and part numbers and software and operating systems are.

but really...all those things take the guessing and assumptions away...and make it easier for US to HELP you...

say you see an ad in the newspaper "car for sale, doesn't run"...

now think about how many questions could be asked regarding "car" "sale" and "doesn't run"...

to wit, I've got a 1909 Ford Model T for sale that won't run(and you're not going to just run down to autozone for parts either)

[http://www.time.com/time/specials/2007/article/0,28804,1658545_1657686_1657663,00.html](http://www.time.com/time/specials/2007/article/0,28804,1658545_1657686_1657663,00.html)

---

### Post by LewRockwell on 2009-06-03
[https://answers.launchpad.net/ubuntu/+question/41400](https://answers.launchpad.net/ubuntu/+question/41400)

your output from "sudo lshw -C network" should have been something like what is found in the link above

---

### Post by Lemuel111 on 2009-06-03
Sorry didn't quite get the gist. Do you need more details? I am using Ubuntu jaunty with dual boot win xp (although since dual booting windows no longer works! hall.dll fault!). I am using them on a Asus desktop. Does that help?

---

### Post by Lemuel111 on 2009-06-03
The read out says "*-network DISABLED"

---

### Post by coffeeaddict22 on 2009-06-03
Hi Lemuel,
We need to see the output to help.  For instance, ```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:xx:xx.x
       **logical name**: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes **driver=e1000e **driverversion=0.3.3.3-k6 firmware=1.1-2 ip=192.168.2.3 latency=0 **module=e1000e** multicast=yes

```
is what mine puts out.  The info includes the logical name, the module and the driver.  We know your card isn't working, you've told us that; without more info, and more specific info we can't help.  For instance, I've got 2 other "network" interfaces; one is used by virtualbox and one by the pan.  I expect them to be "disabled" because of my setup at present; we don't know what yours is.  There's no point giving advice if we don't know what the problem is, and what it isn't.  So can you post back the info asked for?

---

### Post by Lemuel111 on 2009-06-04
That should be fine. I'll have to copy it all out as I am using my laptop not my desk topl. Thanks.

---

### Post by Lemuel111 on 2009-06-05
Right at long last here is the read out:-


   luke@luke-desktop:~$ sudo lshw -c network 
    *-network DISABLED      
         description: Ethernet interface 
         product: SiS900 PCI Fast Ethernet 
         vendor: Silicon Integrated Systems [SiS] 
         physical id: 4 
         bus info: pci@0000:00:04.0 
         logical name: eth0 
         version: 90 
         serial: 00:11:2f:d1:4b:d8 
         size: 10MB/s 
         capacity: 100MB/s 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s 
    *-network DISABLED 
         description: Ethernet interface 
         physical id: 1 
         logical name: pan0 
         serial: ee:07:37:21:91:b9 
         capabilities: ethernet physical 
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
  luke@luke-desktop:~$

---

### Post by Lemuel111 on 2009-06-05
Sorry its taken so long but my laptop was playing up - Windows! If I can get everything working in Ubuntu and running fine then I would gladly say goodbye to Windows on my laptop too, so I wouldn't have to worry about all the virus checks and the slowing down of the processor as it does them!

---

### Post by Lemuel111 on 2009-06-06
I did the lshw -C network command and this is the read out. Are you able to see where the problem is?

luke@luke-desktop:~$ sudo lshw -c network 
    *-network DISABLED      
         description: Ethernet interface 
         product: SiS900 PCI Fast Ethernet 
         vendor: Silicon Integrated Systems [SiS] 
         physical id: 4 
         bus info: pci@0000:00:04.0 
         logical name: eth0 
         version: 90 
         serial: 00:11:2f:d1:4b:d8 
         size: 10MB/s 
         capacity: 100MB/s 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s 
    *-network DISABLED 
         description: Ethernet interface 
         physical id: 1 
         logical name: pan0 
         serial: ee:07:37:21:91:b9 
         capabilities: ethernet physical 
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
  luke@luke-desktop:~$


Thanks

---

### Post by 3rdalbum on 2009-06-06
Hmm... that's not good, your device is not showing up. Are you sure it's plugged in?

What's the output of:

```
lsusb
```

That command should tell us what is being recognised on USB.

Unplug the device, wait 30 seconds and plug it back in, and give us the output of this:

```
dmesg | tail
```

This gives us the last few lines from your kernel log. If there are any problems initialising the device or stopping it from being recognised, the kernel should log it.

You should copy and paste the commands in rather than just retype them.

---

### Post by Lemuel111 on 2009-06-06
Lsusb =
   
  Bus 001 Device 005: ID 0b27:0601 Ritek Corp. 
  
  Bus 001 Device 002: ID 4317:0711  
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 002 Device 007: ID 413c:4003 Dell Computer Corp. Axim X30
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  luke@luke-desktop:~$ 
  
   
  dmesg | tail =
   
  luke@luke-desktop:~$ dmesg | tail
  
  [  415.354159] usb 2-2: USB disconnect, address 24
  
  [  415.357867] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
  
  [  415.357901] ipaq 2-2:1.0: device disconnected
  
  [  420.912034] usb 2-2: new full speed USB device using ohci_hcd and address 25
  
  [  421.150313] usb 2-2: configuration #1 chosen from 1 choice
  
  [  421.152623] ipaq 2-2:1.0: PocketPC PDA converter detected
  
  [  421.194208] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
  
  [  433.156094] usb 2-2: USB disconnect, address 25
  
  [  433.159269] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
  
  [  433.159297] ipaq 2-2:1.0: device disconnected
  
  luke@luke-desktop:~$

---

### Post by Lemuel111 on 2009-06-07
Can you see where the problem is? 

Thanks

---

### Post by 3rdalbum on 2009-06-07
Either Linux can't see the device, or it believes it to be some sort of accessory for the iPaq PDA. Are you sure the device actually works, is plugged in and turned on?

In any case it appears to be beyond my abilities. I only buy wireless devices that work out-of-the-box in Linux, like Atheros-based devices, RTL-8187 devices, or the D-link DWL-G122 that I just bought. The D-link was $AUD9.95 new on eBay, maybe see if you can grab one of those?

---

### Post by Lemuel111 on 2009-06-07
Yes the device works fine in Windows on the same computer without any problems. 

Anybody else have any suggestions as to where the problem might lie? 

Thanks

---

### Post by Lemuel111 on 2009-06-07
I do have a PDA which it is obsioulsy recoginisng but I'm surprised its not picking up the Belkin adapter.

---

### Post by LewRockwell on 2009-06-07
I've read and reread the three pages in this thread and I still can't figure out what hardware you're working with and the model number of this device that you are trying to integrate into your system?

From what I've read, and with no more information to go on that what's already been posted, I'd say the device you are attempting to use linux with...is ONLY compatible with WINDOZE...

If it were my equipment I'd throw the Puppy Linux live-run CD in and if it worked with Puppy then I would continue trying to make it work with other *nix distros...if it DIDN'T work with Puppy...well, I'd get one that was compatible with *nix...

---

### Post by Lemuel111 on 2009-06-07
The device details listed on it are 802.11g - 125 HSM. The number on the back is CE0560; MAC address = 001CDFAFD75F; model no.F5D7051 P10650-C.

I didn't understand the last thing you were saying. I have the live ubuntu CD but what is the Puppy live cd? Sorry but I am totally new to Linux. 

thanks in advance.

---

### Post by LewRockwell on 2009-06-07
> **Lemuel111 said:**
> The device details listed on it are 802.11g - 125 HSM. The number on the back is CE0560; MAC address = 001CDFAFD75F; model no.F5D7051 P10650-C.

I didn't understand the last thing you were saying. I have the live ubuntu CD but what is the Puppy live cd? Sorry but I am totally new to Linux. 

thanks in advance.

I googled "F5D7051" and came up with this saga that I looked over briefly but didn't read, it should give you an idea of what you're up against.

[http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/](http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/)

Then, you ask about Puppy Linux which, of course, is also easily found via a quality search engine.

Here is a link to the download page:
[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

Here is a direct ftp link that should be ready to download immediately:
[ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.2.1-k2.6.25.16-seamonkey.iso](ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.2.1-k2.6.25.16-seamonkey.iso)

---

### Post by LewRockwell on 2009-06-07
something else I found:

[http://kahrn.wordpress.com/2009/05/27/belkin-f5d7051-usb-wifi-and-linux/](http://kahrn.wordpress.com/2009/05/27/belkin-f5d7051-usb-wifi-and-linux/)

---

### Post by Lemuel111 on 2009-06-08
Thanks for those but unfortuantley i am still struggling carring out some of the suggestions as I don't know the basics for Linux. Being new to Linux I could do with a set of step by step instructions for dumbies. I also have the problem that wicd is not working e.g. "starting network connection manager wicd   {fail}."

I go to these different forums but they all seem to assume you have a basic understanding and I just seem to be going round in circles because I get so far down the suggestions & then come a cropper with not knowing how to do something.

If anyone has the patience to take me through step by step and bear with my lack of knowledge and the occassional break (as I don't always get to the computer evey night) then that would be much appreciated. 

Thanks

---

### Post by Lemuel111 on 2009-06-09
Anybody free to help us with this. I would really like to get sorted with Linux but at this rate I'm starting to get itchy feet of going back to Windows. 

Thanks

---

### Post by abn91c on 2009-06-09
remove the PDA before you try to connect

---

### Post by Lemuel111 on 2009-06-09
I've removed the pda and lsusb only recognises the following (it goes when the wifi adapter is removed):-
Bus 001 Device 002: ID 4317:0711

---

### Post by LewRockwell on 2009-06-09
These methods have been tested under Fedora, Ubuntu and BackTrack 4. All of the following should work in almost any linux distribution to get a Belkin F5D7051 (or possibly similar device) working in Linux for WiFi access.

By default the F5D7051 conflicts with 3 drivers (the rt* set of drivers). These drivers must be disabled, rndis_wlan must be loaded and then hopefully the strange problems will go away.

1. Remove Conflicting Drivers
rmmod rt2500usb
rmmod rt2x00lib
rmmod rt2x00usb

2. Reinsert the device

3. Load rndis_wlan
modprobe rndis_wlan


someone recently had success with this procedure

---

### Post by Lemuel111 on 2009-06-09
All I get is "ERROR: Module rt2500usb does not exist in /proc/modules"

---

### Post by Lemuel111 on 2009-06-09
I tried the other commands & this is what came out:-

   luke@luke-desktop:~$ rmmod rt2500usb
  
  ERROR: Module rt2500usb does not exist in /proc/modules
  
  luke@luke-desktop:~$ rmmod rt2x00lib
  
  ERROR: Module rt2x00lib does not exist in /proc/modules
  
  luke@luke-desktop:~$ rmmod rt2x00usb
  
  ERROR: Module rt2x00usb does not exist in /proc/modules
  
  luke@luke-desktop:~$ modprobe rndis_wlan
  
  WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
  
  WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
  
  WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
  
  WARNING: All config files need .conf: /etc/modprobe.d/blacklist.old, it will be ignored in a future release.
  
  WARNING: Error inserting cdc_ether (/lib/modules/2.6.28-11-generic/kernel/drivers/net/usb/cdc_ether.ko): Operation not permitted
  
  WARNING: Error inserting rndis_host (/lib/modules/2.6.28-11-generic/kernel/drivers/net/usb/rndis_host.ko): Operation not permitted
  
  FATAL: Error inserting rndis_wlan (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rndis_wlan.ko): Operation not permitted
  
  luke@luke-desktop:~$

---

### Post by ptn107 on 2009-06-09
If you're running Ubuntu 9.04 try installing these packages and rebooting:
linux-firmware
linux-backports-modules-2.6.28-11-generic

---

### Post by Lemuel111 on 2009-06-09
According to Synaptic manager I already have Linux firmware. I will have to download linux-backports-modules-2.6.28-11-generic onto my laptop and put it onto a usb stick to put onto my desktop. What is the best way of installing linux-backports-modules-2.6.28-11-generic from my USB stick to desktop?

Thanks.

---

### Post by Lemuel111 on 2009-06-09
CanI install the files from the USB stick and if so how?

Thanks

---

### Post by ptn107 on 2009-06-18
Download the file from:
_[linux-backports-modules-2.6.28-11]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-11-generic_2.6.28-11.12_i386.deb")_ for the 32-bit version
_[linux-backports-modules-2.6.28-11]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-11-generic_2.6.28-11.12_amd64.deb")_ for the 64-bit version

Copy the file to the USB stick and then over onto the desktop of the other computer you wish to install it on.  From that computer open a terminal (Applications -> Accessories -> Terminal) and type:
```
cd Desktop/
sudo dpkg -i *.deb
```

---

### Post by Lemuel111 on 2009-06-18
I download and installed but still nothing.

---

