---
title: "Linksys WPC11 (ver. 3) and WPA"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by MartenH on 2005-07-24
Hello,

I'm an experienced computer user but have not much prior experience with linux systems. I've installed ubuntu on my Laptop (Dell Latitude C800) to finally get up to-date with linux and I figured Ubuntu would be a good start.

Everything worked perfectly right away which is splendid, even my linksys PCMCIA card was recognized and operational at once.

Now to the problem. I am running a wireless network where I would like WPA encryption. I have the setup working for my other computers but opened it up to make sure I got ubuntu working. Now that it is, I want to add WPA again and configure this on Ubuntu too.

I've found  wo guides for doing this [Ubuntu Wiki](https://wiki.ubuntu.com/WPAHowto?highlight=%28wireless%29%7C%28wpa%29) (Method B) and [Ubuntu Forum](http://www.ubuntuforums.org/archive/index.php/t-31418.html)

However I am unable to get either working. I've seen many notes of ndiswrapper however if my card was already found upon installation I shouldn't need this, right?

Could anyone help get through this?  ](*,)

---

### Post by MartenH on 2005-07-24
I ran the lsmod command and under pcmcia_core i found (among other things) ocinoco_cs which I assume is the driver ubuntu currently uses. 
Is this assumption correct?

(The others were 3c574_cs, pcmcia and yenta_socket) 3c574 is most likely for the 3com pcmcia card I'm using for the TP link.

orinoco and 3c574 is also listed under pcmcia.

After looking at the documentation of wpasupplicant found [here](http://hostap.epitest.fi/wpa_supplicant/) I came to the conclusion that my driver wasn't supported and this resulted in my faliure to get wpa working. 
Is sthis asumption correct?

I am now trying to install ndiswrapper instead since this is supported by wpasupplicant.

It tells me to download the driver for my card from linksys.
I downlaoded the driver with WPA support, upacked it on my windows-box (since it was a self-extracting .exe file) and copied lswlnds5.inf LSWLNDS.CAT and LSWNDSX.SYS to the ubuntu machine. I then proceded to do ndiswrapper -i iswlnds5.inf which says that it installs the driver. However, if I then do ndiswrapper -l is says:
lswlnds5  invalid driver!


Should I have download the WinXP driver without WPA support instead since this comes from the wpasupplicant instead? What else might I be doing wrong?

If anyone can help me explain what kind of debug output and settings that might be helpful for you if I posted here I will do so asap.

Thanks

---

### Post by MartenH on 2005-07-24
I tried with the regular (non-WPA) driver fom linksys too but it ends up the same way. ndiswrapper -l reports it as invalid. What am I doing wrong? Do I need to remove the driver currently used by the card first? How do I do this?

---

### Post by MartenH on 2005-07-24
I am now trying the driver for the chipset on the card (realtek) and not the linksys driver as shown in the list [here](http://ndiswrapper.sourceforge.net/mediawiki-1.4.6/index.php/List). However I still belive the driver ubuntu installed for my card out of the box might be interearing and should be removed. If so, how do I do this?

The driver is now listed and says net8180 driver present, but I lack the "hardware present" part. I tried adding 'orinoco_cs' and 'orinoco' to the hotplug blacklist but that didn't help.

---

