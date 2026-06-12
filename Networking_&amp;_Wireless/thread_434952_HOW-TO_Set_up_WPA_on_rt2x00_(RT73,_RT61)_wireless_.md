---
title: "HOW-TO: Set up WPA on rt2x00 (RT73, RT61) wireless adapters using rutil"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by morbid88 on 2007-05-06
Okay, I've been trying on and off for the last six months to set up a WPA connection on my wireless network, using my built-in rt73 card.

If you've been having trouble like me, and network-manager doesn't do the job for you, try this.

I wracked my brains over wpa_supplicant, network manager, and god knows what else before I got it working today.


This should work for all the Ralink - derived cards, such as the rt61, the rt2570 etc. etc.

Using the drivers from serialmonkey, you need to get RUtil, which is a gui utility for configuring the drivers.

you can get that here: [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

download the .tar file, and untar it to any directory.
Make sure you have the GTK2 development libraries, using the commands

```
$sudo apt-get install libgtk2.0-dev
```

As well as the g++ compiler:

```
$sudo apt-get install g++
```

They don't seem to be installed by default.

Then, from withing the directory where you extracted RUtil, you run the following commands:

```

$./configure.sh
$make
$sudo make install

```

this will install RUTIL on your system (you can run it using "rutil" at a command line or add a menu shortcut), and will work pefectly with your drivers.

You might have to reboot, and I would suggets getting rid of network-manager, knetwork-manager or wifi-radar, as they MIGHT conflict with the program, and they don't really work well with rt2x00 drivers *anyway*

According to the documentation, you don't need to run the program as root, as it will prompt you for a root access password when necessary. this is NOT the same as your sudo password, apparently, so be sure to either run it with "sudo" or set up a password for root (this isn't done in a default ubuntu installation.)

Good luck!

---

### Post by spartan777 on 2007-06-22
how can i set this up to use wpa? the only option i see in my setting in rutilt is for WPA. also, is it necessary to have this start at boot?

---

### Post by Octavian.C on 2007-06-22
Thanks for giving me another option in trying to get my wifi card to work.
Will update on how its going, Im installing now.

---

### Post by Octavian.C on 2007-06-22
Set it up fine, and ran fine.
I then tried to do a site survey and it crashed, but then I rebooted, and it works great!
I havnt uninstalled network manager and there doesnt seem to be any problems... Network manager thinks im not connected, while the rautil thinks I am.

Thankyou Very much for this, This solution worked, where others didnt.

---

### Post by morbid88 on 2007-06-23
> **spartan777 said:**
> how can i set this up to use wpa? the only option i see in my setting in rutilt is for WPA. also, is it necessary to have this start at boot?

Not sure I understand your question. Are you asking about WEP?

The thing is that Network Manager can handle WEP with RT73 -based cards. It has a problem with WPA. So if you're using WEP just use net manager or command line.

As for start at boot - you don't have to. I still pop open a command line and ron the utility with the -P option (which loads a presaved profile).

---

### Post by spartan777 on 2007-06-24
i want to use wpa to encrypt my wireless network, but it appears rutil doesn't support that. when i'm trying to create a profile, the only two options I get for encryption are none and WEP. I would much rather use WPA as I'm aware of the security flaws of WEP.

---

### Post by morbid88 on 2007-06-24
> **spartan777 said:**
> ... but it appears rutil doesn't support [wpa]. when i'm trying to create a profile, the only two options I get for encryption are none and WEP....

Rutilt supports WPA. I use it myself. Strange that its giving you that problem.
Are you creating a profile from an existing available network that shows up in your scan?

Make sure that the access point is set to WPA.

---

### Post by bsf on 2007-06-24
sir, you are a genious!!! i spent atleast 2 days working on this, i almost convinced dad to use WEP !!

My driver is tl-wn321g. works like a charm!

---

### Post by morbid88 on 2007-06-24
I nearly went bald with frustration.

But I can't seem to do this with Feisty, only on edgy. I read that the Serialmonkey drivers don't like hyperthreading and multi-core.

J.

---

### Post by daniel_summers on 2007-06-24
> **bsf said:**
> sir, you are a genious!!! i spent atleast 2 days working on this, i almost convinced dad to use WEP !!

You don't want to do that.  :)  There's a technique discovered about a month or two ago now that cracks 50+% of WEP in 1 minute, and 98% in 2 minutes.  Steve Gibson explains the technique in his [Security Now podcast]("http://www.twit.tv/sn89") (episode 89).

---

### Post by spartan777 on 2007-06-24
yeah, my adapter is the WUSB54GR, and the chip in there is the RT73, so it must be the driver.

daniel_summers: yes, I listen to SN and ep 89 is exactly why I don't want to use WEP, even though I live on a relatively traffic-free street.

---

### Post by morbid88 on 2007-06-25
Spartan777: I've only tried this on Edgy. Are you still using Dapper like it says on your post?

---

### Post by spartan777 on 2007-07-05
oops, no. I need to update that. I use fiesty.

also, it seems the driver for my rt73 usb adapter cuts out about 10-200 minutes into any session. this requires me to restart my computer. anyone have any suggestions? i'm about to return this piece of crap and get another brand.

---

### Post by spartan777 on 2007-07-05
I'm thinking maybe I could update the driver. If i update the rt73 driver, would I need to reinstall rutilt? also, rutilt doesn't come with any drivers itself, does it?

---

### Post by morbid88 on 2007-07-05
I tried it on Edgy. Couldn't get it to work. So I still run 6.10 (Dapper?). Try upgrading (actually a reinstall because the distribution uprgade doesn't work so well) and see if it works for you.

---

### Post by nandoc on 2008-01-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/34902](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/34902) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hola,
FINALLY... this applies to RT73 based dongles or similar (my case: TP-LINK TL_WN321g)
Thanks to all of you, after months of trial and error, and so many pages read:
This is based on:
[http://generacionlibre.es/?p=11#comments](http://generacionlibre.es/?p=11#comments) who based on:
[http://terminusblog.wordpress.com/2007/08/04/instalacion-de-dispositivo-wifi-linksys-wusb54gc-en-ubuntu-feisty/](http://terminusblog.wordpress.com/2007/08/04/instalacion-de-dispositivo-wifi-linksys-wusb54gc-en-ubuntu-feisty/)

So this goes in English and adapted, sort of a HOWTO:
1) Install:
    sudo apt-get install build-essential linux-headers-`uname -r`
2)Download:
    sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
3) Unpack the previous tar.gz ("home" would be perfect)
3) Change to the following directory:
    cd /rt73-cvs-yyyymmddhh/Module (based on where you unpacked it)
4) Make:
   sudo make
      Just ignore the message:
    !!! WARNING: Module file much too big (>1MB)
    !!! Check your kernel settings or use &#8217;strip&#8217;
5)   sudo strip -S rt73.ko
6)   sudo make install
7) Get rid off network manager:
    sudo aptitude purge network-manager
8) May or may not be necessary, to ease things??????
    sudo apt-get install rutilt
9) Turn off the wlan0 for a while:
    sudo ifconfig wlan0 down
10) Remove the following troublemakers:
    sudo modprobe -r rt73usb
    sudo modprobe -r rt2570
    sudo modprobe -r rt2500usb
    sudo modprobe -r rt2×00lib
11) Blacklist the above, this is a must, as pointed out by some of you, open an editor:
    sudo gedit /etc/modprobe.d/blacklist
12) Add to the end of the file:
    # Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
    blacklist rt73usb
    # Blacklist rt2570, as it causes conflicts with rt73
    blacklist rt2570
    # Other modules that break rt73
    blacklist rt2500usb
    blacklist rt2×00lib
13) Load the module:
    sudo modprobe -v rt73
14) Now you can play with RutilIT, click on menu: Applications/Internet/RutilIT...
or
15) Even better open interfaces:
      sudo gedit /etc/network/interfaces
16)Add the following lines (for auto DHCP) according to your personal set-ups, but make sure to block  (mask using #) all other references to eth0 or similar, if not this WON'T work:
     #auto eth0
     #iface eth0 inet dhcp
    auto wlan0
    iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwconfig wlan0 essid YOUR_SSID
    pre-up iwconfig wlan0 mode managed
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK=YOUR_PASS_KEY_IN_HEXADEC
Or (for manual DHCP)
    #auto eth0
    #iface eth0 inet dhcp   
    auto wlan0
    iface wlan0 inet static
    address 192.168.1.2 (or what ever yours is)
    netmask 255.255.255.0 (or what .....)
    gateway 192.168.1.1 (or what .....)
    pre-up ifconfig wlan0 up
    pre-up iwconfig wlan0 essid YOUR_SSID
    pre-up iwconfig wlan0 mode managed
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK=YOUR_PASS_KEY_IN_HEXADEC
17) Save the file,
18) Reboot and you should be connected

Hasta pronto, let me know,
Fernando

---

### Post by Chessmaster on 2008-02-05
Great "How-To". Good stuff.

Just curious, but what is "auto DHCP" and why would I want (or not want) to disable it. I am only using my wireless network to transmit songs to my stereo and connecting occasionally to a laptop. Should I, or should I not, disable "auto DHCP"?

Cheers

---

### Post by kevdog on 2008-02-05
auto DHCP means the interface is automatically brought up on boot and is going to request a dhcp address from the router.

---

