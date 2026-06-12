---
title: "T-Mobile internet dongle 620 on Ubuntu?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by dcalvani on 2010-10-02
hi everyone,

on Monday I'll try Lubuntu on a Thinkpad T42 - hopefully it'll work. I'm wondering if a T-Mobile Broadband USB Stick 620 will work on Lubuntu (T-Mobile UK). 

sorry I don't seem to find any reference on this dongle and Linux. What I'll do in any case I'll run the OS live cd before installing, but I'm not sure I can actually test the dongle in the process? If I can't, anything I should do (after installing the OS) if the dongle doesn't work/Lubuntu can't see it/etc?

Thanks!

---

### Post by waynefoutz on 2010-10-02
> **dcalvani said:**
> hi everyone,

on Monday I'll try Lubuntu on a Thinkpad T42 - hopefully it'll work. I'm wondering if a T-Mobile Broadband USB Stick 620 will work on Lubuntu (T-Mobile UK). 

sorry I don't seem to find any reference on this dongle and Linux. What I'll do in any case I'll run the OS live cd before installing, but I'm not sure I can actually test the dongle in the process? If I can't, anything I should do (after installing the OS) if the dongle doesn't work/Lubuntu can't see it/etc?

Thanks!

just click on the network icon by the clock. You should get a drop down menu of all your wi-fi networks and one that will refer to your broadband card. click on it, it will ask you what country you are in, who your carrier is, then connect. That is if all goes well. It should. Ubuntu's Network-Manager app is pretty slick.

---

### Post by dcalvani on 2010-10-03
thanks waynefoutz

this is what I did: 

- clicked on "create VPN (connection)"
- selected "Mobile broadband"
- chose Britain UK + T-Mobile
- chose plan "default" (unless I need to enter a plan manually)
- ticked off "connect automatically" + "all users allowed"

how do I launch the connection now? If I click on the network icon it's not there (if I click again on "create VPN (connection)" I find it listed under mobile broadband...

also if I go do StartMenu>Disk Utility I find the T-Mobile dongle listed as 

"ZTE MMC Storage (firmware 2.31)"

but it also says

- capacity: no media detected
- smart status: not supported

any idea?

---

### Post by dcalvani on 2010-10-03
I've just come across 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728)

but do not know if the Huawei E620 mentioned in the bug description is the same make as the T-Mobile I'm using (I've had a look at its T-Mobile box and it says

Mobile Broadband USB stick 620 HSDPA 7.2 model MF637 (works on Windows and Apple Mac)

In any case I just don't understand the workaround: what are the missing data I need to install?

---

### Post by Hippytaff on 2010-10-03
Test it with the live CD, if it works excellent, if it doesn't you get to fix it :-D

---

### Post by dcalvani on 2010-10-03
sorry I seem to be getting carried away, I've also come across a seemingly related web page: 

[http://packages.ubuntu.com/search?keywords=usb-modeswitch](http://packages.ubuntu.com/search?keywords=usb-modeswitch)

if it IS related (at least to trying to have the T-Mobile dongle work - not sure about the bug description) can anyone tell me how to proceed from here? I mean, what package should I install for LUBUNTU 10.04 and how do I install it? 

if it's not...I'm lost!

---

### Post by dcalvani on 2010-10-03
I did test it with the live CD (Lubuntu 10.04)...

---

### Post by Hippytaff on 2010-10-03
> I did test it with the live CD (Lubuntu 10.04)...

did it work?

---

### Post by dcalvani on 2010-10-03
No Hippytaff it didn't 

plz see my 2nd post:

[I]thanks waynefoutz, this is what I did: 

- clicked on "create VPN (connection)" 

- selected "Mobile broadband"

(etc)[/I]

---

### Post by Hippytaff on 2010-10-03
Sorry - getting confused :-s

sounds like you will have to do the mode switch procedure

---

### Post by dcalvani on 2010-10-03
no problem :) 

what's the "mode switch procedure"? 

The thing is that - whatever that is - I'd have to try it out on a live cd "test" session (the thinkpad T42 has Win XP on it but it came without installation CD...and the T-Mobile dongle is my only internet connection...)

---

### Post by dcalvani on 2010-10-03
- is it possible to simulate a "mode switch procedure" on a live cd session (I've found it in the Synaptics and it's probably like that found at [http://packages.ubuntu.com/search?ke...usb-modeswitch](http://packages.ubuntu.com/search?ke...usb-modeswitch))

- will it work on LXDE?

---

### Post by Hippytaff on 2010-10-03
I guess so, I've never done it myself, but your not installing any drivers or anything, just changing the mode of the usb effort, so should be able to do it via the live CD

---

### Post by dcalvani on 2010-10-03
I tried but cannot figure out how to change the mode - what exactly should I do?

---

### Post by Hippytaff on 2010-10-03
What does
```

lsusb

```
return with the dongle plugged in

---

### Post by dcalvani on 2010-10-03
here's what it does: 

[I]ubuntu@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b064 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0781:5408 SanDisk Corp. Cruzer Titanium U3
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

---

### Post by gandaran on 2010-10-03
> **dcalvani said:**
> thanks waynefoutz

this is what I did: 

- clicked on "create VPN (connection)"
- selected "Mobile broadband"
- chose Britain UK + T-Mobile
- chose plan "default" (unless I need to enter a plan manually)
- ticked off "connect automatically" + "all users allowed"

how do I launch the connection now? If I click on the network icon it's not there (if I click again on "create VPN (connection)" I find it listed under mobile broadband...

also if I go do StartMenu>Disk Utility I find the T-Mobile dongle listed as 

"ZTE MMC Storage (firmware 2.31)"

but it also says

- capacity: no media detected
- smart status: not supported

any idea?
why did you choose the VPN?
in the network manager go to the mobile broadband tab, click on add, now you must check that the wizard detected your modem, some dongles are detected in ubuntu as modems others don't, to correct this you will have to install usb-modeswitch, if you don't see the dongle in the wizard first window you have to install that package first then run again the setup wizard.
you may have to reboot the computer for the setup to work. 
then left click the panel network manager icon and click on your 
connection name to connect to internet

---

### Post by dcalvani on 2010-10-03
*you will have to install usb-modeswitch, if you don't see the dongle in the wizard first *

so I can't simulate this on a live cd session? I'm a bit paranoyd about installing Lubuntu to find out that I can't use internet + have to buy XP to reinstall it...

but I'll try now to do as you say on a live cd and see if the modem is recognized.

---

### Post by Hippytaff on 2010-10-03
if that doesn;t work I found this, but it is a potch, try the obvious stuff first

Below are the steps you may follow to work with your ZTE MF636:  

1. Boot without the MF636, wait for the system to stabilize, open a  terminal window, plug in the modem, wait 10-15 seconds and run the  command:  lsusb

If among the responds you see 19d2:0031 go to step 3.

2. The modem responds 19d2:2000 (as the internal CD drive or USB hub)  but we need the actual modem (19d2:0031). You may use a special program  called usb_modeswitch (see  [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)) but I preferred to  send the AT command AT+ZCDRUN=8 from a Windows PC to the modem (use  hyperterminal or add it as an extra init command through control panel).
This command turns off the AUTO RUN function of the internal CD, if you  want to return to default you have to send AT+ZCDRUN=9 (info taken from  [www.matt-barrett.com](www.matt-barrett.com)).

Test again the terminal command lsusb to be sure you have 19d2:0031

3. Make a new "rule" for MF636 to create the usbserial communication port (/dev/ttyUSBx).
From terminal run: sudo gedit /etc/udev/rules.d/90-zte.rules
copy paste the following lines (according to post#4 of [http://ubuntuforums.org/showthread.php?t=665332):](http://ubuntuforums.org/showthread.php?t=665332):)

ACTION!="add", GOTO="ZTE_End"
#
SUBSYSTEM=="usb", SYSFS{idProduct}=="0031",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
#
LABEL="ZTE_Modem"
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0031",
MODE="660", GROUP="dialout"
#
LABEL="ZTE_End"

Save and Exit from gedit.

4. Edit HAL info to see MF636 instead of MF628. From a terminal window:
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Search (ctrl-F) for 19d2, go to line after "<!-- ZTE MF628 HSDPA USB  dongle -->" and change usb.product_id from 0015 to 0031
Save and exit from gedit.
NOTE: this edit must be done again if an Ubuntu update restores the file 10-modem.fdi to defaults!

5. Remove modem from USB port, reboot, wait for the system to stabilize,  plug in the modem. After a while a message will appear over the Network  Manager icon (2 PC screens up right) and help you create a Mobile  Broadband connection. After created click to Network Manager icon, and  click to your provider.

Some debugging notes:
- If at step 5 the "message" not appears, try to make the setup manually (right click on icon and "Edit Connections")
- From terminal the command ls /dev/ttyU* will show you the usbserial  ports for the modem. There must be four (4) up to /dev/ttyUSB3 which is  our modem. If you boot with the modem attached you may have up to  /dev/ttyUSB2 and this needs extra modification to the 10-modem.fdi file  (the parameter usb.interface.number" int="3" must be changed to2).

---

### Post by gandaran on 2010-10-03
> **dcalvani said:**
> *you will have to install usb-modeswitch, if you don't see the dongle in the wizard first *

so I can't simulate this on a live cd session? I'm a bit paranoyd about installing Lubuntu to find out that I can't use internet + have to buy XP to reinstall it...

but I'll try now to do as you say on a live cd and see if the modem is recognized.
yes can do everything on the live cd including installing the package.
the only problem will be if you really need to reboot for the setup to work.

---

### Post by Hippytaff on 2010-10-03
why don't you set up a dual boot for the time being!?

---

### Post by desnaike on 2010-10-03
If you have a net connection install usb-modeswitch-data from package manager it will help.

---

### Post by dcalvani on 2010-10-03
Yes, dual-boot or else I'll keep XP for the time being: 

- can't find a "Network Manager" anywhere in Lubuntu (no wizard there to detect a modem other than the icon near the clock that detects wifi connections, but then the t-mobile dongle is not there);
- tried to download the package from Synptics: it didn't work = it looks like it's not possible to download packages on a live cd session (?)
- have no idea how what to do if I were to re-boot the machine (if I managed to download the package)
- Hippytaff: thank you so much for the solution: I'll try it out if I go for the dual boot; 
- I came across [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) but I'm not sure my dongle is in the list (it might be there under a different name). 

Thanks everyone for their help. Much appreciated! I'll try and post more on this as soon as possible :)

---

### Post by desnaike on 2010-10-03
You can install a deb file in a live cd environment good luck.

[http://dl.dropbox.com/u/4827426/usb-modeswitch_1.0.2-1_i386.deb](http://dl.dropbox.com/u/4827426/usb-modeswitch_1.0.2-1_i386.deb)

---

### Post by Hippytaff on 2010-10-03
when researching fixes this - *ZTE MF636 - *is yourdongle

---

### Post by dcalvani on 2010-10-03
you're right it's possible to install it on a live cd - wondering what went wrong the first time, maybe weak internet connection :) 
thanks again :) will try to work on it tomorrow

---

