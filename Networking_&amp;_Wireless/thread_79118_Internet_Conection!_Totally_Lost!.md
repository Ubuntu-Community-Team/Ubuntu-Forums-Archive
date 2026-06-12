---
title: "Internet Conection! Totally Lost!"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by luchiolb on 2005-10-19
Hi everybody.. I dont know how to configure mi internet conection. First of all, ubuntu didnt recongnize my Adsl Modem CA80-U, i dunno know how to make it work! Plz Help MEEE!!

---

### Post by matthew on 2005-10-19
I want to make this really simple because it sounds like you are pretty new. First I want to ask some questions to make sure everything is set up right, then we will try to configure your ethernet card.

1. Is the computer plugged in and turned on?
2. Is the adsl modem plugged in and turned on?
3. Is the modem plugged in to the wall?
4. Is the computer plugged in to the modem?

If the answer to all of these is "yes," we can move on.

On your main Ubuntu screen, at the top left you will find some menus.

Click System->Administration->Networking

A small window will pop up. Is your computer's network card shown? 

***If not***, we have bigger problems, post again with more information about your modem (does it use ethernet cable to connect to the computer or USB?), and your computer (open a terminal and type "lspci" and post the output here for starters).

*** If it is*** shown, highlight your network card (probably labeled "Ethernet Connection" with a line that says, "The interface eth0 is not configured."

Now click on the button labeled "Properties."

Another small window will pop up.

Check the square "Enable this connection."
Under Configuration choose "DHCP"
Click "OK" It may take a few moments to close. That's okay, just wait.

You will be back to the original pop up window for networking. Select your network card in the "Default Gateway Device" list. 
Now click "OK" Again it may take a moment to close.

You should now have internet access. Open firefox and test it out.

---

### Post by luchiolb on 2005-10-19
you are right.. i'm really new.. the modem and all that stuff is plugged, but one little problem.. the only way is connecting it by USB.. no ethernet then..
I really newbie in Linux..
how do i open a terminal? sorry for this questions!

---

### Post by The Headhunter on 2005-10-19
Go to the top menu, click on "Applications", then go to "Accessories" and click on "Terminal".

---

### Post by sickdude on 2005-10-19
type lsusb and you will see whats connected to your usb ports

---

### Post by luchiolb on 2005-10-19
lsusb outputed:
...
bus 002 device 002: ID 0572-cb00 Conexant System(Rock...

and some more stuff i dont remember.. jeje, do you need it all?

---

### Post by sickdude on 2005-10-19
well you can see if the connection between both devices is ok is you get output wich has to do with you usb device your connection is fine

then check all the lights if they are green well thats ok, but red or orange you may want to test some hardware

---

### Post by matthew on 2005-10-19
[quote=luchiolb]you are right.. i'm really new.. the modem and all that stuff is plugged, but one little problem.. the only way is connecting it by USB.. no ethernet then..
I really newbie in Linux..
how do i open a terminal? sorry for this questions![/quote] First, I am the one who should be apologizing for telling you to open a terminal and not telling you how.

At the top of your screen there is a menu. Go to it.
Select Applications->Accessories->terminal

A terminal window will open up. At the flashing prompt in the terminal type the following commands and then use cut and paste to post the output here like this: Please post everything the computer prints on the screen for each command.

```
matthew@mycomputer:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 21)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:06.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

matthew@mycomputer:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:2f11 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:009d Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
matt@ubuntu-matt:~$

``` 
You can make your post look nice in a box like this once you have pasted it. In the edit window that you are using to post, select the test you want in a box and then click the picture at the top of the edit box that looks like a #.

Here are the commands without all the other distracting stuff.
```
lspci
``` ```
lsusb
``` Also, tell us everything you know about the modem: brand name, model number, anything you can think of that might be interesting. Then we can look online for you and find out how to get it set up and running.

Hang in there! It gets easier with a little experience. I know it can be quite daunting at first. There are lots of nice and knowledgable people here (most more knowledgable than me). We can get this figured out.

Finally, I'm convinced the only stupid question is the one that isn't asked. Any questions you have are welcome.

---

### Post by luchiolb on 2005-10-19
Well.. it is a ADSL USB MODEM CA80U

```
luchio@Ubuntu-BsAs:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 002: ID 0572:cb00 Conexant Systems (Rockwell), Inc. E-Tech ADSL USB Modem v2
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0e8f:0002
Bus 001 Device 001: ID 0000:0000

```
```
luchio@Ubuntu-BsAs:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:09.0 Communication controller: Unknown device a159:0001
0000:00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

---

### Post by matthew on 2005-10-19
Hopefully someone else will jump in here and contradict me.

I searched and searched and it appears that it is possible to make your modem with with linux but it will be a major chore to do it. The best instructions I found are in Spanish in this page:

[http://www.preguntaslinux.usla.org.ar/showthread.php?tid=162]("http://www.preguntaslinux.usla.org.ar/showthread.php?tid=162")

Without going into the gory details the guy recomplied his kernel to add in support for that modem. (Plus, while I got the basics of the thread there, but my Spanish is a bit rusty...I don't think I could translate it adequately). Also, his modem has the same model number, but it is possible that while it is the same type it is not the exact same modem as the brand name is missing.

Honestly, this modem is likely to be a problem. There are some manufacturers that just don't produce drivers for linux and will not allow the linux community access to the data necessary to write adequate drivers so for that equipment hacks and difficult configuration is needed if it can be made to work at all. Conexant is notorious for this sort of behavior. Some of their products have been made to work...well, this page explains it a little bit.

[https://wiki.ubuntu.com/forum/hardware/Conexant]("https://wiki.ubuntu.com/forum/hardware/Conexant")

Unfortunately, the modem mentioned in the page is not the same as yours nor even the same type (ADSL).

If you want to do some studying and really delve into linux and try to figure it out there might be some information out there that I missed. I think you would be better off though finding an inexpensive ethernet card (I didn't notice in the output from lspci that one is installed) for your computer and an ADSL modem that will attach using it.

The other option is a sad one for us, but if you are committed to the modem you may be stuck with Windows. I sincerely hope someone else knows or can find another solution and will come in and prove me wrong.

EDIT: I did some more looking because I am just not satisfied with this answer...anyway, you migt find these links of interest.

[http://ubuntuforums.org/showthread.php?t=37252](http://ubuntuforums.org/showthread.php?t=37252)
[http://dsl.linux.it/ChipsetConexantUsb](http://dsl.linux.it/ChipsetConexantUsb)
--This one says the linux drivers will work for your model (0572:cb00) but that doesn't mean it won't be a hassle.

[http://www.google.com/search?hs=5xh&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=Conexant+usb+linux+0572%3Acb00&btnG=Search](http://www.google.com/search?hs=5xh&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=Conexant+usb+linux+0572%3Acb00&btnG=Search)

---

### Post by luchiolb on 2005-10-20
thanks very much.. i'll try to read and understand the links. Dont worry about the spanish, i'm from argentina.. jejeje. Maybe with that thing, i friend could help me o something, anyway thanks you very much. 

Byes!!

---

### Post by matthew on 2005-10-20
I hope it works out for you! By the way, I've been to Argentina. I spent three weeks in Buenos Aires with some travel on the weekends. Beautiful country and beautiful people!

---

### Post by drtvasudevan on 2005-10-20
my son had a USB modem and could not make any linux distro work with it.
extensive search led no where.
seems it is not possible to connect usb adsl modem and work with it.
let me know if any simple way is found.

tv

---

