---
title: "Wireless link strength meter, gnome plugin/tutorial?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by dardack on 2007-06-12
So as i've posted in my thread and a couple others to help others, I've needed to uninstall Network-manager to get the wireless connection drops to stop.  If i go manual i don't have a dropped connection issue.  Aparently, i'm not the only one, and i think there is a bug report for it.  Anyways, i would like to have a strength meter icon like NM gives on the gnome panel, next to the sound thingy.  Just a strength meter, nothing like that manipulates the network, can chance having connection drops again.  I know that it can be parsed from iwconfig and the link, i don't want to have to open a terminal and than in my head figure out what 22/92 comes out to in a percentage (24%, and i just want a quick glance to determine the strength).  Also i've read that NM isn't always accurate (it wasn't for me it would report 77% but only be like 17/92 i'm on oether side of house and 17/92 works great for me just want to know).  Anyways, my secondary major behind my accoutning degree was CS.  So i do have some knowledge, just because i went with accounting my skills have shall we say declined.  So if no one knows of a strength meter plugin for the gnome panel, could someone point me to a place that has tutorials on writing a gnome panel plugin?  I believe i could figure out how to parse the data from iwconfig and get the 22/92 run the division on it.  Just need a way to display the 24% in the gnome panel.  (and if i felt daring actually making a meter and not just displaying a number).

PS Sorry for the length of this post, i tend to ramble alot.

---

### Post by tturrisi on 2007-06-12
The way that Signal is handled is done by the wifi driver, not the connection manager.  Different drivers (for chipsets) report the Signal using different math formulas because there is no one 80211 standard for reporting signals.  Some drivers base the Signal on the max that the chipset supports & some base it on the max that 80211x supports.  Thus, depending on the device & the driver, the reported Signal may be very inaccurate.   That being said, there are a number of wifi applets that report Signal in % values.

Commandline version:
1. create a launcher
2. config it w/ an icon and for the command use this script in /home/scripts/signal.sh
```
#!/bin/sh
# make this script executable in order to use it
iwconfig ath0 | grep Quality  # where ath0 = your device name
```
3. config launcher to run in terminal

GUI Signal meters:
gnome-netstatus-applet  (search synaptic)
[http://www.gnomefiles.org/app.php/GTK_ACX_Tool](http://www.gnomefiles.org/app.php/GTK_ACX_Tool) (ACX chipsets)
[http://www.gnomefiles.org/app.php/Wireless_Applet](http://www.gnomefiles.org/app.php/Wireless_Applet)
search "wireless" in synaptic

Conky:
Conky has support for wireless devices and will output the Signal as a %.
In your conky.rc use this:
```
Wifi Signal: ${linkstatus ath0}% # where ath0 = your device name
```

---

### Post by dardack on 2007-06-12
OK thanks i'll look at that.  As far as the launcher, that's not what i meant.  I meant like the singnal strength meter for Network-manager being an icon next to the date/time/sound thing in the upper panel on the right.  I want to have an icon just constantly display the percentage.  Those that you listed might do what i'm asking tho so i'll check them first.  Thanks.

---

### Post by ugm6hr on 2007-06-12
I know you were not looking for a NM replacement - but I had the same intermittent dropped connection as you (with Atheros5005G chipset) with NetworkManager.

I solved it with Wicd - version 1.2.9 testing (not the "stable" 1.2.7), which is slightly less flashy than NM, but also comes with a systray applet to show the connection strength.  It sometimes requires you to manually select the interface (e.g. ath0 rather than wlan0) and correct the wpa-supplicant driver (e.g. wext rather than hostapd), but it works very well.  You just need to add the applet to startup and reboot.

As for the connection strength - I think it is the madwifi driver - it never reports more than 30%, but seems to work without any problems at all, everywhere in the house.

If that interests you:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

PS: You need to uninstall NM or wifi radar to make it work.

---

### Post by dardack on 2007-06-12
Oh so wicd solved it and comes with an applet.  Nice i'll check it out.  NM and radar are uninstalled.  I run a script i created everytime i log into get on internet.

---

### Post by dardack on 2007-06-12
I have no applet signal meter.  I can connect, is there an option for it?

---

### Post by dardack on 2007-06-12
nvm i found it

---

