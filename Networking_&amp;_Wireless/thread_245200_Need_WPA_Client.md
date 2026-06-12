---
title: "Need WPA Client"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by seekyrr on 2006-08-27
Installed DD6.06 Desktop edition.  It detected my wireless card fine, but under the networking options I only saw WEP.

I am running WPA PSK and need that option.

Is there a Gnome Client for that?

Thanks

Seek

---

### Post by NetworkGuy on 2006-08-27
Look into WPASupplement.   It might be installed.  I currently don't use so I'm not sure how to configure it.

---

### Post by seekyrr on 2006-08-27
Thanks, I found that the WPA_supplicant was installed but still could not see a WPA option.

Installed the WPA-GUI package, but it returns an error that it cant talk to the wpa_supplicant.

Seek

---

### Post by funchords on 2006-08-27
This has recently become very easy.  Do 

sudo apt-get install network-manager-gnome

which should replace the current gnome nm-applet with one that has WPA functionality.  network-manager-gnome will also install network-manager as a dependency.

---

### Post by seekyrr on 2006-08-27
Ty, tried that but still no go.

Reading around I see its a pretty common problem, still trying though.

Seek

---

### Post by insane_alien on 2006-08-27
hopefully edgy will support it by default make things a lot easier. i still haven't got WPA to work. 128bit WEP will do for now.

---

### Post by xander848 on 2006-08-27
This worked for me.

[http://ubuntuforums.org/showthread.php?t=125150&highlight=wpa+howto](http://ubuntuforums.org/showthread.php?t=125150&highlight=wpa+howto)

---

### Post by funchords on 2006-08-27
What wireless card do you have, exactly?

---

### Post by seekyrr on 2006-08-28
Its a Proxim 8470-WD B/G Gold card.  It uses the Atheros chipset.

It appears I do not have a wpasupplicant.conf setup.  I see a few examples in the docs folders.  Anyone know where I would put a default one for the system to use?

Seek.

---

### Post by veganmasochist on 2006-08-28
Hi I hope someone can help me.  I have a laptop running Ubuntu 6.06 LTS, and I cannot get the gnome-network-manager to give me a WPA option, the only security options are WEP.  I have wpa_supplicant and wpagui installed, I can see my network.   I do have the /etc/default/wpasupplicant file with ENABLED=0.  Does anybody know what the problem is or how to help?

My wireless card is an XteraSys XN-2423G.  It works fine with WPA in Windows.

Thanks,

Mikey

---

### Post by funchords on 2006-08-28
> **seekyrr said:**
> Its a Proxim 8470-WD B/G Gold card.  It uses the Atheros chipset.

It appears I do not have a wpasupplicant.conf setup.  I see a few examples in the docs folders.  Anyone know where I would put a default one for the system to use?

Seek.

Usually, it's /etc/wpa_supplicant.conf ... but you can put it elsewhere (like /etc/wpa_supplicant/config) because you always specify the config file when you launch the process.  

for example: **wpa_supplicant -Bw -c /etc/wpa_supplicant.conf -D madwifi -i ath0**

do **man wpa_supplicant** and **man wpa_supplicant.conf** for help.  See also [http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/")

BTW, that card should work with NetworkManager 0.6.2 and the Dapper-installed version of wpa_supplicant (**sudo apt-get install network-manager network-manager-gnome wpasupplicant**).  Reboot after installing so that the NetworkManager detects the card.  No configuration file required.

---

### Post by seekyrr on 2006-09-07
Reimaged the system and did the sytem updates then the command line apt get.  Rebooted and worked this time.

sudo apt-get install network-manager network-manager-gnome wpasupplicant


Ty much!

Seek

---

