---
title: "Ubuntu not working properly on EeePC"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Ornatipes on 2009-07-06
I just bought an Asus EeePC 900HA and decided to replace Windows XP with the netbook remix of Ubuntu 9.04.  Although I am not at all familiar with terminals and command line interface I succeeded in preparing a bootable usb stick and installing Ubuntu.  The system booted up and seemed to work but unfortunately there are some things that don't work;

1  There is no sound at all.  I have the volume control on the applet at maximum but there is nothing showing sound is available

2  Videos in Firefox do not play,  could this be related to the lack of sound?

3  I can receive messages in Evolution but no fiddling with the preferences has allowed me to send messages.

I have looked through some forums and help files but get lost understanding the commands and files that are mentioned.  Any easy to follow suggestions to fix these issues would be welcome!

---

### Post by NE Key on 2009-07-06
Eeebuntu is the "re-mix" specifically designed for the eee machines.

[http://www.eeebuntu.org/]("http://www.eeebuntu.org/")

Why not give it a go. (It works on my 900A).

---

### Post by esalnoj on 2009-07-06
Type the following (each line separately) in Accessories->Terminal:

```
lspci

lsusb
```

Post the output in code tags.

Also, what brand of graphics/sound card do you have? Intel and ATI have known support issues with Jaunty. Just search the forums.

-Esalnoj

---

### Post by Ornatipes on 2009-07-06
> **esalnoj said:**
> Type the following (each line separately) in Accessories->Terminal:

```
lspci

lsusb
```Post the output in code tags.

Also, what brand of graphics/sound card do you have? Intel and ATI have known support issues with Jaunty. Just search the forums.

-Esalnoj

The output is;

ornatipes@Kryten:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

and;

ornatipes@Kryten:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I hope you can help with this information.  I don't know what graphics/sound card it has, there is no information in the manual.

Thanks for your help.

---

### Post by Ornatipes on 2009-07-06
> **NE Key said:**
> Eeebuntu is the "re-mix" specifically designed for the eee machines.

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Why not give it a go. (It works on my 900A).

I did try this version first but it would not boot properly from the usb stick. The title screen displayed briefly then dropped to command line messages including information that things were missing.  The netbook remix was a next resort. I may give it another go, at least I get more experience with the system.

---

### Post by entire on 2009-07-06
hmm. it'š working on my eee fine. everything of that you said. and i installed original ubuntu 9.04.. :)

/yes. i know i'm not helping - i wanted to show off. :D

---

### Post by Ornatipes on 2009-07-06
> **entire said:**
> hmm. it'š working on my eee fine. everything of that you said. and i installed original ubuntu 9.04.. :)

/yes. i know i'm not helping - i wanted to show off. :D

That's OK, we all need to do that now and then.  

Thanks for that anyway, I now know that it should work on my eee.

---

### Post by Coombabah on 2009-07-06
I've had a look at some of the eee customised versions but like the original 9.04 better. I only have multimedia issues when customising xorg for large virtual screen sizes to use an external monitor but this is not just an issue with the eee.

---

### Post by esalnoj on 2009-07-06
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

in your lspci means your audio card is detected.

To check modules/drivers, I credit prshah, but run the following in terminal and post:

```
aplay -l
lsmod | grep snd
```

As a side note, do post something similar to generic@computer_name in your posted output, where "generic" is your system login name and "computer_name" is your system's public name.

---

### Post by Ornatipes on 2009-07-07
I originally made the bootable usb stick on a Mac so I tried reloading Eeebuntu onto the usb stick using Ubuntu on the Eee (yes, I worked out how to get and use Netbootin) and it seems to work now!  Thanks to all for the help and suggestions.  Looks like I am on the way to learning more about this system.  ;)

---

### Post by aysiu on 2009-07-07
There's an Intel audio bug in Ubuntu 9.04.

This fix may help you:
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44)

---

