---
title: "Belkin F5D6020 Version 3 Wireless Card"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by Picklegnome on 2005-09-01
I just bought a Belkin wireless card from newegg.com, thinking I would get a Version 2 card.
Well, of course they sent me a Version 3, and they don't accept returns, so I'd like to get this to work. This card apparently uses a Realtek chipset.
When the card is in the Cardbus slot, the Device Manager says it recognizes it. How do I set up everything to connect to my home network?

I don't have internet access on the laptop, so if you give me instructions to get a new package, I'd appreciate it if you could direct me to the .debs.

I do have the latest ndiswrapper, but I can't find the driver on the CD they sent with the card. I'm not sure what the extension would be.

Thanks for your help!

---

### Post by Lambert on 2005-09-02
The driver will end with extension .inf

If you have ndiswrapper installed all you need is to find the driver (driver_name.inf) on the cd and follow the instructions here.

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

If you run into trouble you may want to google using linux + driver or card name or chipset or the error message you get. Or use the search function here in the forums.

---

### Post by Picklegnome on 2005-09-03
Well, I've gotten ndiswrapper and the driver installed, and I go to the Networking screen. I configure the card, and try to open Google in Firefox. Nothing. Not once throughout this process did my card show any sign of activity.
I have no idea what to do, and if this doesn't end up working, I'm going to have to switch back to Windows 98, as this is the only way I can hope to connect to the internet (which seems to be the only way to effectively update Ubuntu and it's packages).
Thanks for your help, everyone.

---

### Post by nemarona on 2005-09-07
Hi, I just got my Belkin F5D6020 v3 card working under Ubuntu :-). It was a matter of following the instructions at the ndiswrapper Wiki, [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page), and checking the list of cards known to work. Three alternatives were offered, and the one that worked for me was somehow "mixing" the Belkin drivers with the realtek ones. Weird, isnt't it?

To be more explicit: First I put Bel6020.inf and rtl8180.sys in one folder (which I called realbel ;-)). Then I opened Bel6020.inf in a text editor and changed every appearance of "Bel6020.sys" with "rtl8180.sys" (you have to be root to do that: open a root terminal and do "gedit Bel6020.inf"). After that I just followed the instructions given in [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper). I had to reboot before the card started working.

Good luck!

---

### Post by suoko on 2006-02-02
works great for me too!!
By following nemarona's instruction it's working on my dapper.

I took realtek windows xp driver (rtl8180.sys) from here.
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

and bel6020.inf from windows

---

