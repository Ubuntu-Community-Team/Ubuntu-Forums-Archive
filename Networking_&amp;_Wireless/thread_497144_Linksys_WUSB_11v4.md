---
title: "Linksys WUSB 11v4"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-09
I have a Linksys USB wireless-B network adapter.

I want to install it on this Feisty Fawn (7.04) box.

I have just switched my friend's laptop over to Ubuntu ('twas a Toshiba Satellite 1905-s304), but MS is gone, daddy-o!

Eventually I have to get the wireless working on the laptop, but to learn how, I must post here, as the laptop has no internet access until I figger' it out.

Any help much needed

Bye-the-by, the laptop's hard disk had a ms corrupted mbr and kept giving the BSOD message: Unmountable_boot_volume. So we killed MS with Ubuntu, but now I am at a loss, as all I have ever used is dial-up.

I found some stuff about the ndiswrapper, but haven't the driver for this device, if it ever even had one.

---

### Post by Mark_in_Hollywood on 2007-07-09
Progress?

In updating apt, I saw that a new Automatix wanted installing, so I did that. Checking through A/X I found the ndiswrapper could be installed thru A/X. So I did that.

1. Do I need the Win XP driver from Linksys?

found at:
[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper)

If that is the correct driver, what do I do with it? (please, please, please, don't say shove it up . . . )

---

### Post by Mark_in_Hollywood on 2007-07-10
Does the xp driver get extracted in usr/src/ndiswrapper or lib/module?

---

### Post by kevdog on 2007-07-10
No -- extract the driver in your home directory somewhere.  It will be installed so it doesnt matter initially were the drivers are put.

Once extracted do the following
cd *directory where drivers are located*  <--Make sure .sys and .inf file are present
sudo ndiswrapper -i ****.inf <---Substitute name here

Check if installed properly
ndiswrapper -l  <--Post if there are errors

Place module into kernel
sudo depmod -a <---Post if there are errors
sudo modprobe -i ndiswrapper

Check if module inserted appropriated
dmesg | grep ndiswrapper <--- Post if errors

Load modules at startup
sudo ndiswrapper -m
sudo echo "ndiswrapper" | tee -a /etc/modules

Reboot
If things are not up and running modifications to /etc/network/interfaces and /or /etc/iftab may be needed. Please post these files along with lshw -C network if unsuccessful.

---

### Post by Mark_in_Hollywood on 2007-07-10
I was ready to 

sudo ndiswrapper -i WUSB11v4.inf

when on double-checking your advice, to be sure the .sys was there, too, I noticed:

mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ ls
LSPMUSB.cat  M4301A.sys    NETUSB.SYS    vnet58l.sys   vnetusbl.sys
LSPMUSB.inf  mdusb.out     NETUSBXP.SYS  vnet58lx.sys  vnetusbxp.sys
LSPMUSB.sys  netrfm2k.cat  PRISM9x.SYS   vnetu9xl.sys  [COLOR="Blue"]WINXP[/COLOR]
m4301a.cat   NETUSB.inf    PRISMXP.SYS   VNETUSBA.SYS  WUSB11v4.inf


but no file: WUSB11v4.SYS

please advise.

---

### Post by kevdog on 2007-07-10
The inf and sys files dont necessarily have to have the same prefix.  You can just try and install it anyway if you want -- you will get an error if something is wrong.  If you want to get real technical about it, you can read the .inf file (its an ASCII formated file) and search the file -- somewhere within the file will be named the specific sys file it is linking to.

---

### Post by Mark_in_Hollywood on 2007-07-10
Every command worked until the very last:

mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ echo "ndiswrapper" | tee -a /etc/modules
tee: /etc/modules: Permission denied
ndiswrapper

---

### Post by kevdog on 2007-07-10
I must have typed it wrong ... Preface the same command with sudo

---

### Post by Mark_in_Hollywood on 2007-07-10
mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ sudo echo "ndiswrapper" | tee -a /etc/modules
tee: /etc/modules: Permission denied
Password:
ndiswrapper
mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ 


Please note that there is a WINXP subdirectory in all this mess. 

mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers/WINXP$ ls
LSPMUSB.SYS  PRISMUSB.SYS

I don't know why I include this, but I'm being thorough!

---

### Post by Mark_in_Hollywood on 2007-07-10
Just to see what happened, I plugged the device into the USB port:

mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers/WINXP$ lsusb
Bus 001 Device 007: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter

Bus 001 Device 004: ID 13fe:1a00  
Bus 001 Device 006: ID 04b8:010f Seiko Epson Corp. Perfection 1250
Bus 001 Device 005: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 002: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 001 Device 001: ID 0000:0000 

so it is on the bus

---

### Post by kevdog on 2007-07-10
As far as your previous problem with the tee command, just do this

gksu gedit /etc/modules

Add one line at the bottom of the file if not already there
ndiswrapper

Thats the way I used to do it!

Upon a reboot, post the following (if not working):
lshw -C network
/etc/network/interfaces
/etc/iftab

Thanks

---

### Post by Mark_in_Hollywood on 2007-07-10
Kevdog:

You da' MAN!

Its up and running. I did add the ndiswrapper into the file, but it was working before that, too.
Presumedly, I need the ndiswrapper line for full functionality.

Thank you so much for sticking with me. It's grueling when you're lost (as I'm sure you know).

Anyway, now on to my pal's laptop and kiss the bsod goodbye!

---

### Post by kevdog on 2007-07-10
Not sure what you did to make it work, but great.  Enjoy linux.  Just help another poor sap out in the forums once in a while if you could.

---

