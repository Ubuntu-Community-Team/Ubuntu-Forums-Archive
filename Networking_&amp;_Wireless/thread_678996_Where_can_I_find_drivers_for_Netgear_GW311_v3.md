---
title: "Where can I find drivers for Netgear GW311 v3"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by jplyons on 2008-01-26
Hello,

Back again with a better question. Where can I go to find a driver for
Gutsy v 7.10 which will allow it to detect a netgear wireless pci card
(GW311 v3)

I have some instructions on how to do this, but the site where they say to get it from
gives me a 404 error. 

Thank you.

---

### Post by pytheas22 on 2008-01-26
Do you mean wg311 v3, not gw111?

Do you know what chipset it uses?  To find out, use the lspci command and search for the line pertaining to your wireless interface.

Once we know that information, we can figure out what drivers the card should use.

---

### Post by jplyons on 2008-01-26
Hello Pytheas22,

Thank you for your interest. The card is GW311 v.3.  I did this command

$ lspci

this was the last item returned 

02:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Thank you again. I hope the above is helpful.

Joe

---

### Post by pytheas22 on 2008-01-26
alright, it looks like you have a card with a Libertas chipset.  I've never heard of them, but I did a search and apparently there's no Linux driver for that chip.  So you have to use a program called ndiswrapper, which will allow you to use your Windows driver for the card.

Here is a general how-to on using ndiswrapper and setting up your card with it: [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) .  It's a couple years old, and you should download the latest stable version of ndiswrapper, not the one mentioned in that tutorial.

And from ndiswrapper's website ([http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)), here is a link to Windows drivers that are supposed to work with your card: [http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip) .  Any Windows drivers for your card should work, but I would try those first: unpack the .zip file, open the folder containing the Windows XP drivers and when you get to step 4 of the tutorial that I referenced above, install the driver in that folder ending with the extension '.inf'

If you have trouble or are not yet familiar enough with Linux to be able to follow the how-to, let me know and I can try to walk you through the steps.  Basically everything should be the same, except the name of the Windows driver you will use and the version of ndiswrapper.

---

### Post by jplyons on 2008-02-02
Hello Pytheas,

I followed your instructions and finally succeeded in going wireless.


I got this zip and unzipped it....

[http://www.encore-usa.com/download/d...ME-2000-XP.zip](http://www.encore-usa.com/download/d...ME-2000-XP.zip) . 

I  extracted the WINXp  file ending with inf, I also extracted the same name
file ending with .sys.
It needed them both. They mvr8000c.inf and mvr8000c.sys.

Then I did >$sudo ndiswrapper -i <full pathname>

Then I did .$ ndiswrpper -l to see it it was there.

To save settings I did .$ sudo ndiswrapper -w

To start it up I did >$sudo modprobe ndiswrapper.

This made the device appear under my networking info.
I then had to configure it. I used manual config. It asked me for my wpa ID. I did not
understand this but I gave it my wep id instead. This worked.

All have to do now is to make this permanent beyond re-boots. Each
time now I reboot, I have to run modprobe and reconfigure. This is OK,
I hardly ever reboot.

Thank you again.

Joe

---

### Post by pytheas22 on 2008-02-07
I think that if you open the file /etc/modprobe.conf in a text editor and add the line "ndiswrapper" to it, it will automatically be loaded during boot.  If you need to run more commands you could always write a script and place it in the /etc/init.d/ directory, to make it also be run during boot.  If you do that however you should research it a little because there are certain places to put certain commands, and if you mess it up you can make your system not boot.  But as long as you get advice from someone who knows about boot-up scripts you should be ok.

EDIT: I was wrong; the correct file to edit is /etc/modules, not /etc/modprobe.conf.

---

