---
title: "Ubuntu 10.04 wifi fix"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by prokoop on 2013-11-06
[COLOR=#000000][FONT=Helvetica Neue]I have IBM ThinkPad T20 2647 [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]150Mbps USB WIRELESS LAN card 802.11 b/g/n (RT3070) [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Ubuntu 10,04 [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]problem is that I dont see any wifi networks, so I cant connect to internet. I dont have any instalation disc or drivers for this wifi usb. [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]This is my first experince with ubuntu, too, so if you can explane me it step by step. Thanks[/FONT][/COLOR]

[http://www.youtube.com/watch?v=jUeEW2bw0iM](http://www.youtube.com/watch?v=jUeEW2bw0iM)
this is how it looks like


[COLOR=#000000][FONT=Helvetica Neue]Please help me[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-11-06
Ubuntu 10.04 has reached 'end of life' and no longer supported.

---

### Post by prokoop on 2013-11-06
thats only version of ubuntu which I can to boot on laptop

---

### Post by sudodus on 2013-11-06
A. Please specify the data of your computer:

- cpu, ram (size) and graphics chip

B. and how you intend to use it (internet, word processing ...)

and you can get more precise advice to find a suitable linux distro/flavour/version. Only if you are ***not connected to the internet***, you can be safe without security updates (as with Lubuntu 10.04).

-o-

I can check the specs at a web page, but there might variations within [COLOR=#000000][FONT=Helvetica Neue]IBM ThinkPad T20 2647 [/FONT][/COLOR](at least RAM size)

[http://www.cnet.com/laptops/ibm-thinkpad-t20-2647/4505-3121_7-1800008.html](http://www.cnet.com/laptops/ibm-thinkpad-t20-2647/4505-3121_7-1800008.html)

It is below the general specs for Ubuntu based systems with graphical desktop environments according to this link [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640") so I would recommend ***Knoppix*** or ***Puppy Linux*** or ***Tiny Core Linux***.

Maybe you can try the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") and install the tarballs for ***Bodhi linux*** or ***LubuntuCoreSaucy***. Those tarballs will install with 128 MB, but will be quite slow. Or build something from the Ubuntu 12.04 LTS or 13.10 ***mini.iso***.

---

### Post by ibjsb4 on 2013-11-06
> **prokoop said:**
> thats only version of ubuntu which I can to boot on laptop

This post seems to indicate its your 'savage driver'.

[http://ubuntuforums.org/showthread.php?t=2074649&p=12483813&viewfull=1#post12483813](http://ubuntuforums.org/showthread.php?t=2074649&p=12483813&viewfull=1#post12483813)

---

### Post by prokoop on 2013-11-06
[COLOR=#000000]Thanks[/COLOR]
[COLOR=#000000]Yes, It is that laptop, with all specs, only my has 20GB HDD[/COLOR]
[COLOR=#000000]I need it only for internet and documents, Angry Birds [/COLOR]:grin:
[COLOR=#000000]I had installed Puppy too, it worked fine with wifi, but it looks so iritated if you understand me [/COLOR]:grin:
[COLOR=#000000]I'll try with Lubuntu, but only what I ask is wifi and internet with no problems[/COLOR]

---

### Post by sudodus on 2013-11-06
I think you will have problems installing ***Lubuntu*** with only 128 MB from the Lubuntu iso files. But it will work with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"). I have tested it in an old Compaq with Pentium II (400 MHz), so I know that the CPU and RAM are not limiting the installation. See also post #4.

You can also read about the ***mini.iso*** at this link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by prokoop on 2013-11-07
I had no problem to install Lubuntu 13 but I still do not have access to WiFI, maybe will direct wired network fix it?

---

### Post by sudodus on 2013-11-07
Yes, wired internet (ethernet) is more standardized and likely to work out of the box. Having an internet connection, you *might* be able to find and install a driver for your wifi chip.

---

