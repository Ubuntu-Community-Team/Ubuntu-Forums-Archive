---
title: "Wireless working with WG511 (China / Marvell Chipset), but not with hidden SSID, WPA"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by null815 on 2007-11-11
Once more a post on the notorious WG511 PCMCIA wireless card. The good news is: I've got it working. The bad news is: it took some time and not everything is right yet.

First of all, it is important to know that I am referring to the "Made in China" version with the Marvell chipset. 

lspci identifies it as:

Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

(See this post for an exhaustive explanation, sorry, German only: [http://de.gentoo-wiki.com/WG511#Identifizieren_der_Karte](http://de.gentoo-wiki.com/WG511#Identifizieren_der_Karte) - it is important to notice that there are three versions of the card, two of which claim to be made in China, but only one with the Marvell chipset)

Knowing this, you can forget about the above card being supported out of the box. The good news is that I did not have to blacklist prism54 (as suggested by many threads), because it was not even loaded during boot.

Hence, I installed ndiswrapper, and after trying for a few hours using the Netgear drivers (v2.6.03, v3.2), I ended up using the ones provided by Marvell itself, available here: 

[http://people.freebsd.org/~wpaul/marvell/](http://people.freebsd.org/~wpaul/marvell/)

With these drivers, installation was pretty much straightforward and in line with the usual

sudo ndiswrapper -i <drivername.inf>
sudo ndiswrapper -l (to check the driver was loaded & works - output should be something along the lines of 'mrv8335 : driver installed | device (11AB:1FAA) present')
sudo ndiswrapper -m
sudo nano /etc/modules (add a line containing ndiswrapper to have it load at boot time)

As of now, I am able to connect to my network using GNOME NetworkManager, to suspend / hibernate, and use WEP. Hidden SSIDs and WPA are not working yet (as discussed in other threads). My next steps will be to go and try a manual setup using steps from this post:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by buntunub on 2007-12-19
Any further progress with this?

---

### Post by John Jason Jordan on 2007-12-22
> **buntunub said:**
> Any further progress with this?
Yes, I finally got it working on Gutsy x86_64. It took a long time because I needed to find a 64-bit Windows driver, and Marvel/Netgear do not make such. I found one here:

[http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

Evidently SKD is a German outfit that uses the Marvel 88w8835 in some product of theirs, and they wrote a 64-bit Windows driver for it. (Download the SK-54C1 Windows XP and 2000 x64 driver, Version: 3.2.0.7, System: Windows, Date: 07.01.2005 if you're using Gutsy x86_64. Otherwise use one of the other 32-bit drivers.)

Once you have the drivers (the .inf and the .sys file) put them both in the same folder. I put them in /home/jjj/Software/Ndiswrapper. Then you install ndiswrapper from Synaptic (if it's not listed in Synaptic it's because you don't have all the repositories enabled - do so in System > Administration > Software Sources. Once you have ndiswrapper installed you need to add the driver with:

sudo ndiswrapper -i /home/jjj/Software/ndiswrapper/<drivername.inf> 

You just do it with the .inf file. The other one will be included automatically if it is in the same folder. The above command has the path to where I put the file on my computer; change it as appropriate for where you put it.

If the command goes OK, then do:

sudo modprobe ndiswrapper
ndiswrapper -l

The last of those two should show the device present and the driver installed.

And finally, do 

sudo ndiswrapper -m

And then 

sudo gedit /etc/modules

This command will open Text Editor with root privileges and load the /etc/modules file. Add "ndiswrapper" (without quotes) to the end and save the file.

Reboot and your WG511 v2 card should work. You should see a green light flickering on it and when you do:

iwconfig

It should show the card. Also open System > Administration > Network and you should see the card. When you click on Properties it should show a drop-down box where the available networks are visible. Select the one you want to connect to, and you're off and running.

If the card does not work, post back with what went wrong and the point at which it failed.

---

### Post by buntunub on 2007-12-28
Glad you got it working, and posted the howto for those who will undoubtedly be suffering from the same ills.

---

### Post by FullMetalManiac on 2008-03-05
Hi.  I tried your method, but, even though  I have both files in one directory, it comes up with a No such file or directory , ndiswrapper, line 181 error, when I run the above mentioned command as: 

"sudo ndiswrapper -i /home/[my username]/Software/ndiswrapper/wg511v2.inf"

Is there anything that I can do to avoid this?

"Made in" label is China, and I have tried the recommended Win 2000 and Win XP driver sets.

---

### Post by John Jason Jordan on 2008-03-05
> **FullMetalManiac said:**
> Hi.  I tried your method, but, even though  I have both files in one directory, it comes up with a No such file or directory , ndiswrapper, line 181 error, when I run the above mentioned command as: 

"sudo ndiswrapper -i /home/[my username]/Software/ndiswrapper/wg511v2.inf"

Is there anything that I can do to avoid this?

"Made in" label is China, and I have tried the recommended Win 2000 and Win XP driver sets.
If it's not finding the .inf file my biggest bet is that you have made a typo in specifying the folder where the .inf file is located. To eliminate this possibility, do "cd /home/[yourusername]/Software/ndiswrapper. Once you are in the folder do a "ls- la" to verify that you are in the right folder and the files are really there. If so, then just do the "ndiswrapper -i wg511v2.inf" without bothering with the path. In fact, you can just type "sudo ndiswrapper -i <tab>" and the tab should fill in the name of the file (you may have to give it f the first letter as a hint before the tab).

Try the above first. If you are sure you don't have any typos and the file is really there, post back. I probably won't know the answer, but maybe the above will reveal something or someone else will have a suggestion.

---

### Post by silverfox08 on 2008-03-23
just wanted to say thanks for this!  I was on Fedora 7 for a while, and just decided to trash that setup and installed ubuntu 8.04.  I  hadn't been able to get this card (WG511v2-Marvell) working under Fedora for some reason.  I may have had something else botched up.  I was able to get the card working in ubuntu in about 5 min with this post (and a few others).

Any luck on wpa security on the card?  I'm using WEP right now, but would like to get wpa working.

---

### Post by derekge on 2008-04-21
This is helpful as I have run across the same made in china / taiwan problem.

Thanks.

---

