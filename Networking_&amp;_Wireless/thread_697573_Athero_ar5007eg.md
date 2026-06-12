---
title: "Athero ar5007eg"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by surf3r1 on 2008-02-15
I'm new to ubuntu and just getting used to change from windows. I've installed gutsy gibbon and searched for my wireless card in order to use it but it wasn't listed in 'network'. Hardware information displayed it as ar5006eg although it's ar5007eg instead. Looked for some information on madwifi.com but that seemed complicated for begginers.
Finally i found this link [http://ubuntuforums.org/archive/index.php/t-662877.html](http://ubuntuforums.org/archive/index.php/t-662877.html) and followed the instructions to install madwifi driver. As that page is sorted under 'archive' I decided to post here. I got stuck at point 7. (type ''sudo modprobe ath_pci'' to insert the driver as kernel module). On that i received  error (something like ath_pci not found.. not sure right now). Still, in 'network' now i can see wireless adapter. 
Some questions. How to make this command "sudo modprobe ath_pci" work (i tried it later - nothing happens- maybe I need to clean install the driver?)?
Why is my built in card in hardware information shown as ar5006eg?
How to check if madwifi drivers are installed correctly and what version are they?
Finally, how to connect to an acces point with open access  - no wep or wpa (I don't see that option in 'network' wireless card /properties)?
What about ath_hal, do I need to disable it?

---

### Post by psychotux on 2008-05-24
> **surf3r1 said:**
> I'm new to ubuntu and just getting used to change from windows. I've installed gutsy gibbon and searched for my wireless card in order to use it but it wasn't listed in 'network'. Hardware information displayed it as ar5006eg although it's ar5007eg instead. Looked for some information on madwifi.com but that seemed complicated for begginers.
Finally i found this link [http://ubuntuforums.org/archive/index.php/t-662877.html](http://ubuntuforums.org/archive/index.php/t-662877.html) and followed the instructions to install madwifi driver. As that page is sorted under 'archive' I decided to post here. I got stuck at point 7. (type ''sudo modprobe ath_pci'' to insert the driver as kernel module). On that i received  error (something like ath_pci not found.. not sure right now). Still, in 'network' now i can see wireless adapter. 
Some questions. How to make this command "sudo modprobe ath_pci" work (i tried it later - nothing happens- maybe I need to clean install the driver?)?
Why is my built in card in hardware information shown as ar5006eg?
How to check if madwifi drivers are installed correctly and what version are they?
Finally, how to connect to an acces point with open access  - no wep or wpa (I don't see that option in 'network' wireless card /properties)?
What about ath_hal, do I need to disable it?
 
All good questions...

I've got the same card in my Acer Aspire 4520 but can't get it to work either.

Sad part of it is I bought it to run ubuntu, but am using it to type this right now.
Running Vista....

Ironic isn't it?

---

### Post by scottro on 2008-05-24
That rather infamous card can be a nuisance.  In addition to some of the excellent guides on these forums, I have my own page on it.

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

Important note--the 2.6.26 kernel (and possible some 2.6.25 ones) don't build with the madwifi snapshot. 
On the good side, judging from some postings on the trouble ticket, it may, hopefully soon, be merged into the regular madwifi releases.

---

### Post by psychotux on 2008-05-26
> **scottro said:**
> That rather infamous card can be a nuisance.  In addition to some of the excellent guides on these forums, I have my own page on it.

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

Important note--the 2.6.26 kernel (and possible some 2.6.25 ones) don't build with the madwifi snapshot. 
On the good side, judging from some postings on the trouble ticket, it may, hopefully soon, be merged into the regular madwifi releases.


Well the same night that I wrote this about 20 mins after this was written it Blew Up completely, Just up and quit would boot into the Splash Screen then went "BLACK".... :mad: ....

So the next day I took it back to Wal Mart got my money back and came home and Ordered me a Dell Vostro.
With the same card the Dell 1490 Wifi that they put in their Open Source Laptops.

The only thing that might cause me a little trouble is the intergrated ATI Radeon Xpress 1150 Video Card.

But I've used ATI Radeon Cards in Linux before so it's not like it's anything NEW..... :lolflag:

But in any event Thanks for the heads up....

---

### Post by liquerLOVER on 2008-06-04
I'm running on Hardy Heron. This works for Acer Aspire 4520 with Atheros AR5007EG. With this kind of installation, you doesn't need to connected to internet. I install this for THREE times to make sure I didn't left any steps before i'm post this on the forums. If there is any mistake, please inform me because i'm a TOTAL newbie with Linux. This is my fifth week with Linux.

First, download this madwifi from this link:

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

Secondly, extract it to your home folder.

Third, you need to add your install CD as a installation source. Just follow the instruction below:

System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories &#8594; Third Party Software &#8594; Add CD-ROM.

Next, just wait fow a few minutes until the package manager have finish working. You will notice a grey colour "gear" beside the wireless network symbol on the top panel when it still working. If you place the cursor on that gear, it will saying "a package manager is working." After the package manager had finish, it will disappear automaticaly.

For the next step:

sudo apt-get install g++

Then, it will ask conformation from you to install or not. Just type "y" and press enter.

Next step:

cd madwifi-nr-r3366+ar5007/
sudo make
sudo make install
sudo modprobe ath_pci
gksudo gedit /etc/modules

After that, add this line at the bottom: ath_pci

Save, exit and reboot and PRESTO !!!

I'm not too sure whether this work for other laptop with AR5007EG or other AR5007. If this works, thank all the family member in this forum & me. However, if it doesn't works for you, try to look for other solution in this VERY-VERY friendly and caring family forums.

p/s: Can anyone help me with my graphic card? I'm using GeForce 7000m. Now I'm on Ubuntu with 800x600 screen. Post me a working solution. OK dude??? Chowlobetty...

---

### Post by scottro on 2008-06-04
There is now a brand new snapshot that also works with 64 bit. 

It's at [http://www.madwifi.org/ticket/1679](http://www.madwifi.org/ticket/1679)  way way down towards the bottom of the 200 plus thread ticket.

---

