---
title: "save drive in a usb pendrive to live cd (12.04/14.04)"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by mariana3 on 2014-06-30
Hello  ):P how are you? 


i have a Live cd Ubuntu 12.04 LTS


type this command
[INDENT]lspci -nn -d 14e4:[/INDENT]


Show my My Network controller:
[INDENT]02:00.0 Network controller [0280]: [COLOR=#800080]**Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] **[/COLOR](rev 03)[/INDENT]


This live CD have an addicional drive to Wireless network card **[COLOR=#800080]Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] [/COLOR]**(rev 03)


_[COLOR=#0000ff]I want to save[/COLOR][COLOR=#0000cd] this drive[/COLOR] [COLOR=#800080]**broadcom bcm43xx1.0 (5.10.91.22)** [/COLOR][COLOR=#ff0000][that is working in ubuntu 12.04] [/COLOR][COLOR=#0000cd]in a usb pendrive[/COLOR][COLOR=#ff0000] to use in  [/COLOR][COLOR=#0000cd]a live CD[/COLOR] [COLOR=#ff0000]of the actual ubuntu 14.04 version[/COLOR]_ .


](*,)  How do i do that?  ](*,)


Thank you so  much

---

### Post by sudodus on 2014-06-30
Welcome :-)

Proprietary drivers are not easy to use in live systems, but there are work-arounds.

1. Try Ubuntu 14.04 LTS, which is two years newer, and might be able to use a driver for your Broadcom device 'out of the box'.

2. Install a system into a USB pendrive (a fully installed system), where it is possible to install drivers for network, graphics etc in the same way as in any installed system.

Maybe someone else can add tips and work-arounds (for example, I don't know if it would work in a persistent live pendrive).

See also this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by mariana3 on 2014-07-01
Hello, ):P

Thank you so much!

Yes, 


I´ve downloaded a live cd 14.04 LTS.

The step by step is:

    1- System settings
    2- System
    3- Software & updates
    4- additional Drivers
    5- Broadcom corporation airport extreme
    6- Using broadcom 802.11 linux sta wireless driver source from bcmwl-kernel-source (proprietary)
    7- Apply change 

This is not working.[-X

So I try 12.04 LTS

The step by step:

    1- System settings
    2- Hardware
    3- additional Drivers
    4- Broadcom STA wireless driver
    5- Broadcom STA wireless driver
    6- tested by the ubuntu developers
    7- license: Proprietary

This is working=d>

[COLOR=#800080]**So, i want to transfer do 12.04 to o 14.04**[/COLOR]

can you help me?:redface:

---

### Post by sudodus on 2014-07-01
Ubuntu 12.04 LTS works for you, so stay with it and be happy! It will be supported until April 2017 and it is well debugged and polished :-)

Do you want to upgrade it into 14.04 LTS? In that case why, when 12.04 works but not 14.04?

I do not think a driver made for 12.04 works with 14.04, because the two versions use different kernels, and I think a driver must match a kernel.

-o-

Do you want to run

1. a live system, or a persistent live system

2. or an installed system into a USB drive or into an internal drive?

---

### Post by mariana3 on 2014-07-07
Thank you very much for your answer.\\:D/

I really wanted to test it.

As i told you, i cannot teste because 14.04 doesnt have a driver to my wireless board.

**[COLOR=#800080]How do I find in the LIVE CD the driver of 12.04 and test it in the 14.04?[/COLOR]**



Thank you so much for such assistent!;)

---

### Post by sudodus on 2014-07-08
I do not think a driver made for 12.04 works with 14.04, because the two  versions use different kernels, and I think a driver must match a  kernel.

But maybe ... see these links about wifi (to sticky threads)
[URL="http://ubuntuforums.org/showthread.php?t=370108"]
Before posting in Networking & Wireless[/URL][URL="http://ubuntuforums.org/showthread.php?t=2214110"]

How to install a driver for the Broadcom series of PCI wireless cards[/URL]

---

