---
title: "Has anyone ever gotten a AR5006EG 802.11 b/g Wireless Card to work for 7.10?"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Vic! on 2007-12-19
Just curious because I know of at least 2 other people with issues in trying to get their wifi working with the same Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter ..if anyone knows how to do it and they would tell me id be very grateful.. thanx in advance!

vic

---

### Post by Vic! on 2007-12-20
is there any other forum that i should be looking at also to help me solve this?... madwifi's page is down right now i have tried to look there. thanx again!

---

### Post by grokwik on 2007-12-20
Check there, 

[http://ubuntuforums.org/showthread.php?t=643971](http://ubuntuforums.org/showthread.php?t=643971)

If it doesn't work, there's plenty of posts about that, try some of the others solutions (using ndiswrapper for example)...

---

### Post by grokwik on 2007-12-20
Furthermore, i just found that about ndiswrapper (search the text : AR5006EG) : 

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

Hope that help

---

### Post by GSF1200S on 2007-12-20
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Currently have a 48MBPS connection, and im posting this reply with this card.

All I had to do was check the driver in the restricted drivers manager and its worked perfect ever since. In the days of Feisty, I used to compile the latest stable madwifi drivers from source and I had no problems..

---

### Post by Vic! on 2007-12-20
thanx grokwik u had a big point on using ndiswrapper  actually i just kina got it to work using ndiswrapper its a little weird though because i have to type in the essid for the network manually so i can connect i cant use the default  network manager roaming option for some reason... its checked but not working.... gsf 1200s did you get it to work with just the restricted driver being checked?? thats interesting can u plz elaborate on that ....i would MUCH rather do it that way then i could use the default network manager like i do with my other compouter...
well this is what i did to get it working i got it from another thread here in the ubuntu forums i have to credit chalewa


>  chalewa  chalewa is offline
A Carafe of Ubuntu
	  	
Join Date: May 2006
Beans: 108
Re: Ubuntu 7.10 on Sony Vaio: Wireless problem
Ok, here is my howto to get this thing working...

basically i followed some tutorials for other cards and systems, and tried to remember what i could about ndiswrapper from when i used it many moons ago.


but this is what i did.

first i disabled the restricted drivers that ubuntu installs... system > restricted driver managers, then just uncheck the atheros driver and disable it.

then i installed ndiswrapper, (get it from synaptic or command line if you choose) then i installed ndisgtk to install the windows driver which i got from here...

[http://blakecmartin.googlepages.com/...-32-0.2.tar.gz](http://blakecmartin.googlepages.com/...-32-0.2.tar.gz)


to install the driver simply load up ndisgtk from the command line and hit install driver, and browse to the location of the inf file you extracted from above.

after you have done this, verify that you have in fact installed the driver, and it is being recognized:

Code:

 ndiswrapper -l

if it is installed correctly, it should look something like this:

Code:

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


then, make sure that you have the restricted driver that ubuntu installs by default blacklisted

Code:

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

then to make sure ndiswrapper starts

Code:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

then restart your computer.


i personally use wicd to manage my networks, but you can use whatever you like.


now, i have been having some trouble getting the card to power up when i restart the computer. I am still working out the exact steps that need to happen everytime that one turns on and off their computer, but it seems to have something to do with toggling the wireless lan switch on and off. What i have done thus far is boot the system with the switch in the off positions, obviously ifconfig is not going to list the wlan0. then, i restart again, and flick the switch to on. for some reason, this seems to get it back on again.



with all this said, i assume that this is what most of you have been doing to get this card working in this laptop. I know that there was talk earlier of slower speeds with the net5211.inf driver, i never experienced any of this.



if this doesn't work, make sure that ndiswrapper isn't giving you any errors, and post what iwconfig outputs. maybe we will also be able to figure out how to keep this card on all the time.
__________________


the thread url is [http://ubuntuforums.org/showthread.php?t=621562&page=5](http://ubuntuforums.org/showthread.php?t=621562&page=5) its

---

### Post by Vic! on 2007-12-20
its not perfect but it works!!

---

### Post by GSF1200S on 2007-12-20
Yes, my way was a little more complicated than it should be for you. You see, I installed kdebase, so I didnt have the restricted driver GUI or even a network monitor. I downloaded a patch that adds a restricted driver option to the KDE control center and than just clicked the box to enable the card (had to reboot).

All you should have to do is go to the restricted driver manager in System>Administration and check the Atheros box. A reboot and you should be good...

---

