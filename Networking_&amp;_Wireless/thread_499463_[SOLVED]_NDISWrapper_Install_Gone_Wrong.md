---
title: "[SOLVED] NDISWrapper Install Gone Wrong"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Het Irv on 2007-07-12
I Followed the Instructions on the Ubuntu Page for a install W/out a internet connection and installed the Three Packages but when I type ndiswrapper -v into the terminal I get an error about no version specified or something of that nature.

HELP PLEASE

---

### Post by Het Irv on 2007-07-12
I have already tried Uninstalling and Reinstalling the Packets.
Oh and I am running Fiesty Fawn

Please Help me I am but a lowly n00b.

---

### Post by Het Irv on 2007-07-12
Bump.   Apparently this a not so simple problem.  Please Someone help.  I have been ](*,) for days.

---

### Post by nichipet on 2007-07-12
What does ndiswrapper -v tell you? Can you paste the error message?

Also, which page are the instructions from? Is it this one: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by FearTheSmurf on 2007-07-12
I have same problem here is my error message


neil@Linuxlappy:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
neil@Linuxlappy:~$

---

### Post by Het Irv on 2007-07-12
Thanks for that last post i did not want to have to restart and get back into Linux.  That is the same message that i get and those are the instuctions

---

### Post by kevdog on 2007-07-12
You can either proceed or you have to compile from source.

Im not sure where you got your installation from, but it seems like now a days, I see a lot of versions of ndiswrapper 1.38.  The most recent release is 1.47.  The only way to get this is to compile and install from source (which isnt hard).

Im not aware of any frank problems with 1.38.  The error you are getting is because the utility package is missing, however the user-space utility is still present -- its version 1.38.  You can continue to proceed if you want, since in my experience I havent found a problem when the utilites package wasnt installed.

---

### Post by FearTheSmurf on 2007-07-13
I installed Ndiswrapper from the synaptics so the version on there must be out of date. I will try it from source and see where that gets me.
 Even with this error message my wireless connection is still functioning in a way as it can detect that there are networks there but will not connect, it picks out straight away weather i enableor disable the WEP key so somthing is happening:confused:

---

### Post by nichipet on 2007-07-13
Also, you can try the instructions for setting up wifi from this blog:

[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

It's written for Ubuntu on a Dell Inspiron 1501, but maybe some of it will help, such as where to get ndiswrapper 1.47 from and how to set it up. Step 1 and Step 2, until the download from Dell, should apply to your setup. In fact, I suspect if you can find the Windows driver for your computer/wifi card, all of the blog should be helpful.

---

### Post by Het Irv on 2007-07-13
I Have tried continuing with the steps on the Ubuntu Instructions and When I type ndiswrapper -l I see a list with the driver i have just entered and a Message saying that this driver is invalid.  I copied the drivers to my home folder and inserted the wmp54gs.inf  into NDISWrapper per instructions.  I thing this is the right one but in this folder there is also a wmp54gsa.inf, wmp54gs.cat, bcmwl5.sys, bcmwl5a.sys.  Do i need to do any thing with these???


Why can't it just work out of the Box:cry:

---

### Post by kevdog on 2007-07-13
Try this

sudo rm -R /etc/ndiswrapper/ *

Then try to install the driver again

---

### Post by Het Irv on 2007-07-13
> **kevdog said:**
> Try this

sudo rm -R /etc/ndiswrapper/ *

Then try to install the driver again

This command effectively rewrote my home folder deleting every thing in it and on my desktop.   Was that supposed to happen? 

Also I am following the instuctions for the Dell Laptop and i was wondering what file I should replace their drivers with.

Thank for your help to this point

Hope this is fixed soon

---

### Post by kevdog on 2007-07-13
Im not sure how it deleted your desktop when your desktop folder is located at
/home/*username*/Desktop

and the command was for
/etc/ndiswrapper/*

---

### Post by Het Irv on 2007-07-13
Its Ok just letting you know.  I didn't lose anything unrecoverable.

But no suggestions on the driver file?

---

### Post by kevdog on 2007-07-13
Do you have a windows XP driver disk laying around somewhere?  I dont really know anything about your wireless card. (Or at least I forgot).  If you know the type of pci card you have you could also find them at the manufactures website or the ndiswrapper website

---

### Post by Het Irv on 2007-07-13
I have the disk that comes in the box with the Card itself.  I guess what I am asking is every other tutuorial has you use the .inf file and the tutorial for the Dell Laptop has you use a .exe file and i was wondering if i needed to find  a .exe file for my card (WMP54GS).  I don't see any files with the .exe extention that look useful

---

### Post by kevdog on 2007-07-13
Can you post the following

lshw -C network
lspci

Have we installed this card before??

---

### Post by Het Irv on 2007-07-13
I tried once or twice before but I kept getting an error.  Something about a line of code in NDISWrapper not a having something.  Sorry I can't remember exactly what it was.  Output for those lines in a few minuites

---

### Post by nichipet on 2007-07-13
> **Het Irv said:**
> I have the disk that comes in the box with the Card itself.  I guess what I am asking is every other tutuorial has you use the .inf file and the tutorial for the Dell Laptop has you use a .exe file and i was wondering if i needed to find  a .exe file for my card (WMP54GS).  I don't see any files with the .exe extention that look useful

In the Dell tutorial, you expand the EXE with unzip (or tar, I forget which, I'm not looking at it). Then you use an .inf file with the ndiswrapper command. Same as the Ubuntu instructions. I think we need details on the card, computer, etc. Is it a Broadcom card, what is the brand and model of the computer, then we can find the driver. There may be a more recent version of the driver, that could help too.

---

### Post by Het Irv on 2007-07-13
Here is the output you asked for and it looks like it answers some Questions.

Lshw -C network

*-network:0 UNCLAIMED   

       description: Network controller

       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 2

       bus info: pci@02:02.0

       version: 02

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master

       configuration: latency=64

       resources: iomemory:fe8fe000-fe8fffff irq:3

  *-network:1

       description: Ethernet interface

       product: 82562EZ 10/100 Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@02:08.0

       logical name: eth1

       version: 02

       serial: 00:0c:f1:d4:06:08

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes

       resources: iomemory:fe8fd000-fe8fdfff ioport:cf40-cf7f irq:20

and lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

02:00.0 Multimedia audio controller: Creative Labs SB Audigy LS

02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


P.S. don't know if this affects anything but i have blacklisted the default drivers already

---

### Post by kevdog on 2007-07-13
There are ways to open the exe file on linux

(unzip, cabextract).

You dont happen to have a windows box nearby that you could open the exe file with winzip and then copy and paste the winxp drivers to USB stick and transfer them??

---

### Post by nichipet on 2007-07-13
Ok, the instructions at [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html) should work as long as the Dell specific instructions are modified. I know these work, I've configured wifi on a Dell Inspiron 1501 running Ubuntu 7.04 with them about five or six times in the last week (reinstalls of Ubuntu, not ndiswrapper problems) and I'm using the wifi on it right now.

Try the instructions with these changes:

In Step 2: Get Needed Packages, replace "Get the Windows driver for your Dell 1501" with copy (with cp) the driver from the DVD for the wifi card (an .inf file) to your home.

Further in Step 2, replace "mv /home/YOUR LOGIN NAME/R140747.EXE /home/YOUR LOGIN NAME/.drivers" with cp the driver you copied into your home into /home/YOUR LOGIN NAME/.drivers

Follow the instructions until you are in Step 4: Install Drivers. Skip "unzip -a R140747.EXE" and "cd /home/YOUR LOGIN NAME/.drivers/DRIVER". Run the sudo ndiswrapper -i  command replacing bcmwl5.inf with your .inf file.

Everything else should work. If you run into a problem with these changes, show us what you typed and what the output was.

---

### Post by Het Irv on 2007-07-14
YEEYYEYEYEYYEYYYEYE!!!!!1

I am posting this from my Ubuntu install NOT my windows.  It works :).

I had to make two changes along with the ones suggested by nichipet

1.  If your card is a WMP54GS you also need to add the file bcmwl5.sys to the .drivers folder

2.  before the last restart in the instructions for the dell laptop add the type into the terminal
                  [I] sudo ndiswrapper -m

                   echo "ndiswrapper" | sudo tee -a /etc/modules[/I]

these lines tell Ubuntu to load NDISwrapper on boot

I will stay suscribed to this thread so that if anyone has any question I can help them.
Thank you to Kevdog and nichipet.

---

