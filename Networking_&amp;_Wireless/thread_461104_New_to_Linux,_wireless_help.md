---
title: "New to Linux, wireless help"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by dardack on 2007-06-01
So i just decided to try out Linux on my desktop.  I do you knoppmyth for my pvr.  I can't get my wireless working.  I've searched the forums for WUSB11 v2.8 and read most of them.  Most of them say to start out with running lsusb.  Mine doesn't display the linksys.  I get (i'm at work so couldn't copy and paste)
2 rows of 0:0:0 or something like that
1 row of numbers like 1:2:3:4 (not exact i knwo) logitech wireless device (for my mouse/keyboard)
1 row of 0:0:0
then a row of numbers with no words after.  1:2:3:4

It was wierd.  When i first booted the Ubuntu CD, the networking options had a list:
Wirless
Wired
Modem

I have my wireless modem hide the broadcast of the ID but i don't have WEP, so i set it at ESID to my network ID, and jsut left the password for WEP blank (there was no option for disabled).

I read a post about unplugging it and rebooting.  When i did that, it no longer found the wireless.  WHen i went to networking options it only had wired/modem.

I booted into Windows and it didn't find the device either.  I unplugged it and replugged it in in Windows and it found it in windows.  Rebooted into Ubuntu and again the networking found it, but again when i ran lsusb i got the same information.

I so far have liked the ease of the Ubuntu install, but am thinking of trying Fedora to see if WUSB11 will work for me in there.  I mean i'm willing to try anything if anyone has any ideas.  Also incase, lspci doesn't have the USB device listed either.  When i plug in my USB DVD drive, it finds it properly.  So it only doesn't list the Wireless usb.  I want to migrate off from windows but i move this computer all over my house (it is a desktop but on wheels) so need my wireless working if i want to get off from windows.

Sincerely,

MacNean

---

### Post by dardack on 2007-06-01
Um i know this is in response to my own post but should i download Ubuntu 6.06 and try it?  Seems that 7.04 has a lot of issues with this and I've read where people says it works right out of box on 6.06.

---

### Post by WieboJJ on 2007-06-01
I have the same issues with wireless on my laptop, but I used ndiswrapper to install my drivers...when I reboot my card doesnt seem to be recognized, but a simple 

sudo modprobe ndiswrapper

gets is working again, which i added to /etc/rc.local to get to run on startup.  I'm new to Ubuntu as well, but is there a variation of the modprobe command you could use to fix your problems? maybe worth checking...?

sorry i cant be of help...

.wieb




quick edit, after looking at other posts it seems you can add your driver after modprobe to reload the module...

maybe that will help.....you can find module name with 

lsmod |more

g/l

---

### Post by dardack on 2007-06-01
Wieb,
couple questions.  Is this on Ubuntu 7.04?  Can you post me what your lsusb says?  Can you post the link or how you got it working?  And is it v2.8? or different?

Thanks so much would love to get this working.

-MacNean

---

### Post by dardack on 2007-06-01
So the usb adapter is working here is my output (xxx out my username and my essid)

```

xxxx@xxxx-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:13:A9:1D
                    ESSID:"XXXXXXXXXHomeNetwork"
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Signal level=90/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

xxxx@xxxx-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:13:ae:d9
Sending on   LPF/wlan0/00:0f:66:13:ae:d9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
bogus UDP packet length: 556
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
xxxx@xxxx-desktop:~$ 

```

So why is it trying to get DHCP from 255.255.255.255 when i connect the wire it does:

```

Listening on LPF/eth0/00:e0:4c:d6:5f:ac
Sending on   LPF/eth0/00:e0:4c:d6:5f:ac
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.10.10 port 67

```

Which my router is on 192.168.10.10.  Can anyone give me a clue?

---

### Post by dardack on 2007-06-02
[bump]  anyone? i noticed someone else in forums had the 255.255.255.255 wireless issue.

---

### Post by dardack on 2007-06-05
Ok just for prosperity or if someone else has the same issues (basically i can get online, just not the way I like).

I have my wireless not broadcast the ESSID.  You have to know my ESSID to connect.  So in Ubuntu, i selected Manual Configuration, put in the ESSID information, etc.  And those were the errors/problems i posted above.  Once i enabled ESSID broadcasting and switched the Configuration to roaming mode I could connect.  It asked me for my WEP key, put it in and am now online.  I would rather my router not broadcast my ESSID but I guess this will do for now.

---

### Post by georgeskar on 2008-05-06
okay i am trying Linux ubunta out made the live cd to boot from in demo mode and cannot configure my wireless connection. Something they say about fw cutter. I work it my wireless card on vista fine. are there internet protcols on ubuntu? how can i get the internet up and running?

---

### Post by Het Irv on 2008-05-06
> **georgeskar said:**
> okay i am trying Linux ubunta out made the live cd to boot from in demo mode and cannot configure my wireless connection. Something they say about fw cutter. I work it my wireless card on vista fine. are there internet protcols on ubuntu? how can i get the internet up and running?

Because of the way the kernel is burned into the disk you can't get wireless to work on the Live CD.  What Card/Chipset do you have?

---

### Post by Morty007 on 2008-05-06
> **Het Irv said:**
> Because of the way the kernel is burned into the disk you can't get wireless to work on the Live CD.  What Card/Chipset do you have?

Forgive me for asking Irv, but your positive on this? I am running 8.04 from the live cd and can't get my wireless working, but I thought others here said that you can do it from the live cd.

---

### Post by Het Irv on 2008-05-06
Positve? No, but I have never been able to use the restricted drivers (fwcutter), in the Live CD.  If your wireless driver is already in the Kernel, (Intel for example) wireless will work for you in the Live CD.  

I could be compleatly wrong, this is only based on my own experience.

---

### Post by georgeskar on 2008-05-07
> **Het Irv said:**
> Because of the way the kernel is burned into the disk you can't get wireless to work on the Live CD.  What Card/Chipset do you have? object wise i have a linksys card with antenae. i tried with tthe live cd you make sense of it yeah its a cd no change can be made. ok i am going to install it and see if i things change.  thanks how can i extract a file in the treeminal from one folder to the next is my next question.

---

### Post by Het Irv on 2008-05-07
If you have a Linksys WMP54g(s) with a broadcom chipset, you should be able to use the restricted drivers.
Follow these instructions once you get up and running

First lets find out what kind of chipset you have
```
lspci
```
look for something that looks like a wireless card, it might have "804.11 abg" "ralink" or "broadcom" in the line. Just because you have a linksys card doesn't mean that Linksys will be in its name.  If you cannot find the card, just paste the output here I will help you.

The easiest way to get a wireless card to work is using the restricted drivers, found under Hardware Drivers in 8.04.  Unfortuneatly, to get them to work you need to be hooked to a internet connection, or have downloaded the firmware somewhere eles and moved it to this computer, this is easy enough if you have a jump drive or somewhere you can temporarily hook to an ethernet connection.

If you already have the firmware downloaded, the restricted driver dialog box has an option to use a local file, just copy and paste the file to the desktop, and then point the dialog box to that file.

If you have any problems let me know, I have a Linksys card in my computer at home, so I know how to get it to work.  Trust me, it is much easier now than it was a year ago with Fisty.

---

