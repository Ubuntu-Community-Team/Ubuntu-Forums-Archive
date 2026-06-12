---
title: "Linksys WiFi help needed urgently"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by davidkoorn on 2005-11-16
Hi all,

Here is a brief description of the problem: I can't get my Linksys Wireless-G WPC54G ver. 1.2 to work.

I've been browsing, googling etc. found info telling me the card won't work, telling the card should work.

I'm a total newbie to Ubuntu (or linux for that matter) so i need someone to give me a few hints or a sort of guide about howto.

Many thanks in advance...
Cheers David:KS 

--------------------------------
When everything is coming your way
You're in the wrong lane

---

### Post by fervanhuis on 2005-11-16
check if it works under wxp there are some problems with this type in combination with the firmware, I made the switch to a wag354...perfect.

---

### Post by davidkoorn on 2005-11-16
[QUOTE=fervanhuis]check if it works under wxp there are some problems with this type in combination with the firmware, I made the switch to a wag354...perfect.[/QUOTE]

Windows XP? No problem, worked like a sunshine. But i just kicked xp from my laptop..

---

### Post by Lambert on 2005-11-16
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

You need to install ndiswrapper. This will start off telling you to download and compile from a site. You probably don't need to do that. Just pop the install disk back in, open synaptic from system>admin, click reload, search for ndiswrapper, install.

From there skip to the section that says install. For all commands add sudo before them as this gives you admin priveledges to run the commands.

When you get to the configure interface section, before trying the command line options you can click on system>admin>networking, highlight the device, click properties, add settings, click ok, then activate.

If you don't connect or problems along the way come back here with any erros or results.

Include output from terminal commands

iwconfig
ifconfig
ndiswrapper -l
sudo lshw -C network

Another link: [http://ch.tudelft.nl/~arthur/wpc54g/](http://ch.tudelft.nl/~arthur/wpc54g/)

---

### Post by captainzott on 2007-09-29
I had same problem my network setupas it only showed WEP security option for the wag354g - even though I had it set up for WPA. Solution to set the WAG354 up for WEP security, (put [http://192.168.1.1/](http://192.168.1.1/) in your internet browser to access), make a note of the hexadecimal security code, go back to network setup and feed in the hex code, save, reboot and it worked a treat.
Not quite as good security as WPA, but still it's either that or nothing !

---

### Post by kevdog on 2007-09-29
I have both version 2 and version 3 cards and call tell you that the bcmwl5.inf/sys driver combination work well with ndiswrapper.  If you need instructions, how please let me know.

---

