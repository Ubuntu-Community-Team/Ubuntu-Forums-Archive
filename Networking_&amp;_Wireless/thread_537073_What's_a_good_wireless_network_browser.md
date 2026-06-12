---
title: "What's a good wireless network browser?"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by TheAbyssDragon on 2007-08-28
I'm setting up the internet for a laptop which will be in use in multiple different wifi networks, so I'm looking for a good wireless scanner which can connect to wpa and wpa2 networks. Preferably with memory/presets for frequent networks (such as my home and school network) and possibly even auto connect. I realize Feisty Fawn makes this a lot easier, but unfortunately I am restricted to 6.10 Edgy due to issues I'm having with Feisty Fawn.

I've tried all of the wireless managers that come up using add/remove apps with poor results. For the moment, I'm using Kwlan because it's worked best so far. However, it isn't the most reliable and although I can connect to wpa and wpa2 networks without issue, I can't connect to a simple wep encryption.

What do you guys recommend I use to manage my wifi connection?

Thanks for any help!

---

### Post by bmartin on 2007-08-28
[WICD]("http://wicd.sourceforge.net"). It's not supported by Canonical (i.e. it's 3rd party unsupported software), but many people have had great luck with it.

[Here's a quick setup guide]("http://blakecmartin.googlepages.com/wicd.html") which creates links to the two programs (they're installed at /opt/wicd, strangely enough). The tray icon is very nice. It has auto-connect and WEP/WPA support. I've only tested it with WEP, though. You can enter a HEX key directly, but you should put an ASCII key in "double quotes".

Another nice program is wifi-radar. I used to use it until I found WICD. It's located in the Universe repository. You can install it using **sudo apt-get install wifi-radar**, and you can run it using **sudo wifi-radar**. [Here's a quick setup guide]("http://blakecmartin.googlepages.com/wifi-radar.html") for wifi-radar.

---

### Post by TheAbyssDragon on 2007-08-28
Thanks for the suggestion, I have wicd up and running and everything looks great. I used the terminal setup you linked without any issues. One thing though, it doesn't show in my tray.

---

### Post by Zorael on 2007-08-28
Well, wicd in itself doesn't have a tray icon, but that wicd-tray application makes up for that.

> sudo wget -O /usr/local/bin/wicd-tray [http://blakecmartin.googlepages.com/wicd-tray](http://blakecmartin.googlepages.com/wicd-tray)
sudo chmod 755 /usr/local/bin/wicd-tray

Then have Gnome autostart it by making an entry in the Sessions options, or make a symbolic link to it in ~/.kde/Autostart if you're one of us Kubuntulings. If you *want* it autostarted, that is. :)

---

### Post by TheAbyssDragon on 2007-08-28
I had already done the code, the adding it to sessions did the trick. Thank you for your help!

---

