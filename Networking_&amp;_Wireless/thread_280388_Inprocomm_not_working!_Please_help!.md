---
title: "Inprocomm not working! Please help!"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by priddeal on 2006-10-19
Afternoon all! I am a noobi to Unix and i am running a Inprocomm wireless card in my toshiba l10. I have read all the previous posts on ndiswrapper and have managed to get it to use my xp driver. 

sudo ndiswrapper -l - this gives me both driver and hardware present.

i have also added ndiswrapper to the modules file and have added the alias.

i can  e my wireless devie in networking as wlan0 and it shows me wireless networks i can connect to. But this is where everything goes wrong it just will not connect no matter what i do!

Please help me because i really dont want to have to go back to microsoft!

Thanks Phil.](*,)

---

### Post by priddeal on 2006-10-19
^^bump

---

### Post by priddeal on 2006-10-20
anyone?

---

### Post by priddeal on 2006-10-20
please help!

---

### Post by jexworks on 2006-10-23
Hi guys, I'm a bit of a newbie myself but after much frustration I have my Toshiba Satelite with Inprocomm wireless working on an encrypted connection using ndiswrapper. I wrote everything down as I did it so here we go -

After installing Ubuntu 6.06 from the CD the first thing is to download all the updates using your wired connection, I'm saying to do this first because if you update the kernel you'll have to rebuild ndiswrapper so you might as well save yourself the trouble and be up to date before you start.

Once that's done start a console and type in uname -a and make a note of the kernel version you're running. Then start the Synaptic Package Manager and search for each of these one at a time marking for install if they're not already - build-essential, linux-headers and ndiswrapper-util. The linux header version is the one that matches the kernel version you wrote down earlier.

Now download ndiswrapper itself from here -
[http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.27.tar.gz?download](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.27.tar.gz?download)
I used Ark to extract it to my home directory, the directory it creates is ndiswrapper-1.27. I'm assuming that you already have the Windows drivers (inet2220.inf and i2220ntx.sys - if not email me and I'll mail them over to you) I put them in the same directory so I wouldn't have to remember any paths :-) nice and easy!

Now compile ndiswrapper -
cd into the directory containing the source
~/$ cd ndiswrapper-1.27
then compile
~/ndiswrapper-1.27$ sudo make install
load the driver
~/ndiswrapper-1.27$ sudo ndiswrapper -i inet2220.inf
write the module information
~/ndiswrapper-1.27$ sudo ndiswrapper -m
I had to manually add the reference
~/ndiswrapper-1.27$ sudo nano -w /etc/modules
and add ndiswrapper at the end like this -
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper

I rebooted at this point to test if the module actually loaded properly, I couldn't say if that made a difference or not.

After trying for hours on and off to get it to connect I finally discovered that it doesn't like 64-bit encryption on the wireless connection. So I changed the encryption on the router to 128-bit. I also couldn't get it to save the settings via the console so I used the networking tool in system admin to set the ESSID and encryption string. This also won't save unless you create a location. Don't forget to change the default gateway to wlan0.

All is well now and the wireless reconnects happily after reboot etc. Hope that helps somebody

---

