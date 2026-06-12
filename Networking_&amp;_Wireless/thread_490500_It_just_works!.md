---
title: "It just works!"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by hove99 on 2007-07-02
I just bought a D-Link DWA-547 wireless 802.11n PCI card for my PC and a D-Link DWA-645 802.11n PCMCIA Card for my laptop. It didn't work out of the box, but no problem at all.

I just used the Add/Remove feature to add the graphical ndiswrapper "Windows Wireless Drivers" and pointed it to the .inf file. Then I added "ndiswrapper" to /etc/modules just in case and now it all works!

I also run Vista on my PC and I'm still trying to make the PCI card work there!!! So the statistics speak for themselves:

Install time in Ubuntu Feisty Fawn:            5 minuttes
Install time in Windows Vista:                     still counting since 19:00 mon 2. jul 2007

Ubuntu rules!

---

### Post by bojo42 on 2007-07-06
hi hove99,

i also got a D-Link DWA-547, but neither "Windows Wireless Drivers" nor the CLI of ndiswrapper work with the card. i always get a big freeze when i load the kernel modul.  :(

i use the .inf file from the cd and the latest from the dlink website. so i would like to known from you which .inf file you use and if networkmanager is working immediately after loading the kernel modul (ndisgtk does that automatically).

thanx in advance

PS: it works under windoze xp with the website driver, but seems to have some stabilty problems.

---

### Post by hove99 on 2007-07-08
Hi

I use the one supplied with the driver CD. I just copy the folder "Driver" with the three files to my hdd and use gtkndis to point to the inf file. By the way, I use Ubuntu 7.04 32-bit. There are no drivers for 64-bit yet.

If this does not work, I have also had success with a script version:

> 
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -l
sudo sh -c 'echo "ndiswrapper" >> /etc/modules'


, and then reboot. You could maybe do this without rebooting using:

> 
sudo modprobe ndiswrapper


Regards

---

### Post by bojo42 on 2007-07-11
thanks for your reply. it's funny that my driver from the cd also won't work on windows, i get also a freeze there.

for ubuntu my configuration is the same as yours (feisty 32 bit) and i tried it in the same ways, ndisgtk and ndiswrapper CLI, when i load the ndiswrapper during boot i get also a "nice" freeze. #-o

you may allow me to use your inf file by attaching it to the thread?

greetings

---

### Post by hove99 on 2007-07-12
I have attached the folder containing three files, one of them is the .inf file I have used. I'm not sure if you need the other files, but when I install I have all three files in the same folder.

I you running Feisty 32-bit? Because it does not work on 64-bit...

Having the folder on my computer, this is exactly what I do:

> 
sudo apt-get --assume-yes --allow-unauthenticated install ndisgtk
sudo ndiswrapper -i /path/to/folder/dwa547/net5416.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
sudo sh -c 'echo "ndiswrapper" >> /etc/modules'


, and then REBOOT. I also have the package "build-essential" installed.

---

### Post by DO55 on 2007-08-13
im new with lnux

where i must save the folder ?

---

### Post by cmon on 2007-09-28
> **hove99 said:**
> I have attached the folder containing three files, one of them is the .inf file I have used. I'm not sure if you need the other files, but when I install I have all three files in the same folder.

I you running Feisty 32-bit? Because it does not work on 64-bit...

Having the folder on my computer, this is exactly what I do:



, and then REBOOT. I also have the package "build-essential" installed.

Hi
I tried your method of installing my DWA - 547, (I used the driver you attached in your post and ndiswrapper 1.48 ) but when I tried to enable my wireless connection in the network manager my whole system froze. I tried rebooting my computer, but when Ubuntu was booting up it froze again. I did it several times but I couldn't get past the boot up screen with the loading bar.

The only way to get my Ubuntu to boot up again was to disconnected the card from my computer. And whenever I connect it again Ubuntu won't work.

Any thoughts about why my card won't work? 
I'm running Ubuntu 7.04 at the moment but I'm thinking of trying Ubuntu 7.10 instead, maybe it got better support for this card?

---

### Post by kingdevil on 2007-12-18
> **hove99 said:**
> I just bought a D-Link DWA-547 wireless 802.11n PCI card for my PC and a D-Link DWA-645 802.11n PCMCIA Card for my laptop. It didn't work out of the box, but no problem at all.

I just used the Add/Remove feature to add the graphical ndiswrapper "Windows Wireless Drivers" and pointed it to the .inf file. Then I added "ndiswrapper" to /etc/modules just in case and now it all works!

I also run Vista on my PC and I'm still trying to make the PCI card work there!!! So the statistics speak for themselves:

Install time in Ubuntu Feisty Fawn:            5 minuttes
Install time in Windows Vista:                     still counting since 19:00 mon 2. jul 2007

Ubuntu rules!


But your pcmcia DWA-645 works on your laptop(gutsy gibbon)?


> 
It didn't work out of the box, but no problem at all.

I don't undestand it. What's its meaning?

---

### Post by ounas on 2008-02-05
Try removin network-managerand then install wicd 

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

and madwifi  [http://madwifi.org/]("http://madwifi.org/")


-Ounas
:guitar:

---

### Post by jzraikes on 2008-02-08
Well I've got 64-bit Ubuntu. What can I do?

I really don't want to have to change to 32-bit, so is there any way of using this card in 64-bit Ubuntu?

Thanks in advance.

---

### Post by hvollebregt on 2008-04-09
I had problems getting this driver to work for my DWA-547 card, but got it to work finally. But I have two problems left now:

1. it only works on 11Mbs bit rate, while I have an n router. It should work at least at 54 Mbs.

2. it works only when I am *very* close to the router (a few meters). When I am in my living room, which is two storeys down in my house, it doesn't work. Signal strength is 20% (according to ifconfig) but internet just doesn't work. My old card (Linksys WMP11, supporting only wireless b)*does* work in my living room, with a signal strength of 60%. 

Any thoughts? Am I doing something wrong?

---

