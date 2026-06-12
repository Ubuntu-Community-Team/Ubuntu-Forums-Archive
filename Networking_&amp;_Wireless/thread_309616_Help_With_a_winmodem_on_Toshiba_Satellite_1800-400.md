---
title: "Help With a winmodem on Toshiba Satellite 1800-400"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by mtn on 2006-11-29
Hi, I'm having real trouble setting up the modem on my Toshiba Satellite 1800-400 laptop. If anyone can help with this, even to confirm that it is not supported, it would be fantastic.

I have been struggling with it on a and off for a couple of weeks now. Although I have broadband I am planning to give it to a friend that only had dial up.

I think it should be supported as this page on the Toshiba site suggests
[http://newsletter.toshiba-tro.de/main/main/MachineInfoAus.php?os=1&machine=119&devices=5&d_typ=208](http://newsletter.toshiba-tro.de/main/main/MachineInfoAus.php?os=1&machine=119&devices=5&d_typ=208)

I have also read the ubuntu winmodem wiki (as well as loads of other pages and how tos)...
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

...and run scanModem but it does not seem to tell me anything. I have included the out put from modemData.txt, in case someone that knows what they are doing has a look! This is doing my nut](*,) 

```
Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06.1 LTS  kernel 2.6.15-27-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
 scanModem update of:  2006_November_07
The modem symbolic link is /dev/modem -> ttySL0

USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.0.3
             and the compiler used in kernel assembly: 4.0.3


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.0
   kernel_headers base folder /lib/modules/2.6.15-27-386/build
Compressed files at: /usr/src/sl-modem.tar.bz2


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 14:00 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2006-11-30 01:47 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
```

---

### Post by PennYanPete on 2006-11-30
Hi mtn

I use an external modem and may not be able to help other than provide some info.


I think the scan modem output is telling you how to compile a driver. Maybe change the post topic to get more help.

Some good info here...[http://www.linmodems.org/](http://www.linmodems.org/)
[http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html](http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html)
[http://start.at/modem](http://start.at/modem)
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
[http://www.linuxant.com/](http://www.linuxant.com/) -> drivers -> Conexant (Conexant)
 
Hope this helps

PYP

---

### Post by eriefisher on 2006-11-30
Looking at that output it looks like a usb modem. Is it usb or onboard win modem?

---

### Post by mtn on 2006-11-30
thanks for your replies eriefisher's and pennyanpete, i'll have a look at the info. it is an internal (i should have provided more info!), so i'm guessing that is a pci modem!?

to be honest i didn't expect anyone to reply to this as sorting out software modems seem like such and ongoing and difficult problem, so thanks.

i am getting to the point that i am thinking of paying someone to sort this or buying a hardware pcmcia modem, as it sounds like that would work? but i am kind suborn and would like to solve this if possible and do an easy how to guide for others.

cheers, i'll post back to with how i have got on.

---

### Post by PennYanPete on 2006-11-30
At least your scan modem output doesn't say 
"not supported" so there is hope. Don't give up!

PYP

edit-look here-http://www.ubuntuforums.org/showthread.php?t=190728&highlight=sl-modem

---

### Post by mtn on 2006-11-30
> **PennYanPete said:**
> here-http://www.ubuntuforums.org/showthread.php?t=190728&highlight=sl-modem

this looks really promising, I'll have a go over the weekend. the other links were good info (a couple i had been to) but a bit beyond my abilities.

thanks again for the support

---

### Post by mtn on 2006-12-08
Hi,

Thanks for the help, I have been defeated by the software modem but have **solved the issue** by using an external modem.:) 

I got an old USRobotics 28.8 external serial modem from my dad over the weekend. It worked straight away and will do the job for now. One more user has switched to Ubuntu and seems to be getting on very well even if she is verging on being technophobic!

It annoys me (as a no very technical user) when I find a thread that sounds like it will solve my problem but the thread just ends with "solved" but do not then go on to explain how, so here is what I did!

Basically I plugged the modem in to the laptop via the serial port and then opened up System>Networking, selected the modem icon and clicked "properties". In the properties window I clicked the "modem" tab tried "auto detect" but the modem was not found so I selected /dev/ttyS0 as the "modem port", then entered the Internet provider phone number, user name and password in the "general" tab, clicked "ok" and then click "activate" in the "network settings" window. It worked first time - so happy it was this easy.

Cheers

---

