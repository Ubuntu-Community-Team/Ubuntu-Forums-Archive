---
title: "3Com Wireless Problems..."
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by tobyclemson on 2005-04-29
Hello,

I installed the Hoary Hedgehog late this afternoon and am very pleased with it so far. I am currently having problems getting my 3Com OfficeConnect Wireless 11g PCMCIA Card (3CRWE154G72) installed. I am sure you hear this a lot but I am relatively new to linux and have had lots of trouble in the past. 

So far I have been following the instructions in [this post](http://ubuntuforums.org/archive/index.php/t-11273.html) but have not succeeded. I will copy the message here so that you do not have to find it.
> 
I got this card to work using the ndiswrapper:

make sure that ndiswapper is installed with the synaptic package manager

You will also need a copy of the windows driver, which you can get from the 3com web site, you will need to install the driver with ndiswapper.

(my copy was held on /mnt/3com/extract3)
ndiswrapper -i /mnt/3com/extract3/disk1/Driver/3c154g72.inf

To get it to work:
rmmod prism54 (remove prism54, as i think this stops ndiswrapper working)
rmmod ndiswrapper (just incase)

modprobe ndiswrapper

I used the gui to system->administration->networking to configure the card
and set the ESSID via the properties button andto active the card.

some other useful commands are:
dmesg (for error messages)
iwconfig
iwlist wlan0 scan
ifconfig wlan0 up

I am running Linux ubuntu 2.6.10-5-686
with 3com hardware given by
lspci | grep 3com

0000:02:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)

lspci -n
0000:02:00.0 0280: 10b7:6001 (rev 01)

Okay, ndiswrapper is installed and apparently running. I have the windows drivers and have installed them using ndiswrapper. Upon running 'ndiswrapper -l' to list the installed drivers, it lists the relevent driver and says that it is invalid. I tried to carry on with the instructions incase they would solve this problem to no avail. When I get to 'modprobe ndiswrapper' I get the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

So I take it that the ndis wrapper is not set up. This is my problem. I am using a Dell Inspiron 8600 and the card needs to connect to my ADSL router which is connected to the rest of my network. It uses 128bit WEP in the form of a passphrase. 

Your help with this problem would be greatly appreciated as I often have problems with wireless on linux and it is quite infuriating,

Thanks,
Toby Clemson

---

### Post by tobyclemson on 2005-05-16
Just incase anybody has the same problem as me I thought I would post my solution.
For my particular wireless card, using the ndiswrapper driver wrapper I initially had a few problems. I will outline them below and say how I solved each of them:

3com driver installation: don't forget that case sensitivity...the driver names are in capital letters and if you specify lowercase then the installation only half completes. MAKE SURE YOU ARE ACCURATE IN NAMING THE DRIVER FILE

prism54 clash: apparently ndiswrapper is not compatible (i,e, can't be run at the same time as) the prism54 driver. This might just  be with my wireless card...I am unsure. Hence the prism54 module needs to be blacklisted. To do this you need to:

```
sudo gedit /etc/hotplug/blacklist
```

and add the following to the bottom of the file then save

```
prism54
```

ndiswrapper conf generation problem: This was the main problem I had. Apparently ndiswrapper has an error in compiling the conf files required to use the wireless card. To solve this you need to edit the conf file and remove the line with a single | symbol on it as this causes problems when you try to modprobe ndiswrapper. Just look through the conf files in the directory:

```
/etc/ndiswrapper/<drivername>
``` 

REMOVE THE ROGUE PIPE AND THEN:

```
modprobe ndiswrapper
``` 

and the drivers should work fine. Then you can use whatever wireless configuration method you need (Gnome GUI or iwconfig in a terminal) and you should be okay.

I hope this is of help to somebody. The information here is from a number of other posts so credit is not all mine.

Thanks
Toby Clemson

---

### Post by toddncl on 2005-05-26
Thanks for that Toby, worked a treat!

---

### Post by DeMi on 2005-07-14
It worked for me too! I had the same problem. 

Respect! and big thx!!

---

### Post by grid.block on 2006-01-10
everything worked well but i cant get root permitions of the conf file with the rogue pipe in it. i can see the pipe but i cant delete it or remove it. when i use ```
Sudo gedit <filename.conf>
``` i says that the file dosent exist. i have tried re-writeing it several times but no help. the filename is: 

10B7:6001:10B7:6001.conf

And i do know that *nix is case senstetive.. cant get any longer.. any help would do great. :KS

---

