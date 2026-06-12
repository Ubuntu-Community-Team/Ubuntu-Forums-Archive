---
title: "gusty wireless stops working if idle"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by ghostandmachine on 2007-11-25
I have a Netgear WG511 V2 (made in China) that I got working with NDiswrapper. Everything works fine. The only problem is that if I leave my laptop idle for about an hour the wireless card goes into "broadcast mode" and the only way to get it working again is to restart. Thanks in advance.
-Eric

---

### Post by skoobee on 2007-11-26
I had the same problem with gutsy using a Broadcom 7 series WiFi card that worked fine with 'Feisty'.  Installed 'Gutsy', then installed BCM43XX-fwcutter and the wl_apsta.o file (one of many I tried) and it worked fine.  I then left it for 4-5 minutes and.... nothing!

I tried different versions of the wl_apsta.o firmware and the bcmwl5.sys file (current) and still no joy.  It seems that I even lose WiFi if I'm browsing and leave the page in the browser for more than a couple of minutes.

Did you try running **sudo /etc/init.d/networking restart** from the Terminal?  It seemed to work occassionally but not consistently for me.  I ended up reverting back to 'Feisty' and keep trawlng the forums for those more experienced linux users who are clever enough to sort this problem.  As a 'Noob' I'm afraid an answer is beyond me!

---

### Post by dethdeks on 2007-11-26
i have the same issue but mines after my systems been idle for about 30 mins to an hour. i used this walk through [http://ubuntuforums.org/showthread.php?t=529336&highlight=bcm43xx+error]("http://ubuntuforums.org/showthread.php?t=529336&highlight=bcm43xx+error") to get my card to work. but did a change. where it says to do sudo echo ndiswrapper > /etc/module i went into /etc and found modules and added the word ndiswrapper in it using gedit in root. and it starts up everytime i start up my pc the other way u have to do the last two lines of the walk thought where it says do sudo modprobe ndiswrapper, sudo echo ndiswrapper > /etc/module every time u restart your pc. but this should help u a bit n makes the idle time a bit longer before it drops you. also when mine drops me i usly try to connect to the network a few times n usly the second or third time it connects

---

### Post by tl3000 on 2007-11-26
I don't know if this issue is related but I had similar wireless disconnect problem with a WG511v1.  See my solution at this posting:

[http://ubuntuforums.org/showpost.php?p=3688341&postcount=3](http://ubuntuforums.org/showpost.php?p=3688341&postcount=3)

---

### Post by eddie-newbie on 2007-12-14
Ok, I had this problem.  Everytime I walk away at night, I wake up to find that the wireless network does not work and I can´t open programs in Gutsy 7.10 (Esp administrative tasks).

My laptop is a D630 with an Nvidia Quadro video card and Intel wireless card.  I installed the new nvidia drivers (and uninstalled the old ones) and the crashing was a little better.  However, it still crashed.

It is strange when ubuntu crashes after sitting idle and very hard to try to figure out what happened.  Oh yeah, I couldn´t shutdown or reboot my laptop after a freeze, I would have to do a hard reset.

I went home for the holidays however and my computer did not crash using a belkin router.  Currently I am using a Dlink 524 revision D1 router.

Anyway, I found a solution on a different website that seems to work so far.  It changes the wireless settings and drivers.

*note - I did not have errors when I ran iwconfig as the guy mentioned in his post below.

I copied the post below.
--------------------------------------------------------------------------------------------------------------------------------------
From
[http://dan.bodar.com/2007/12/29/more-ubuntu-710-notes-for-dell-d630/](http://dan.bodar.com/2007/12/29/more-ubuntu-710-notes-for-dell-d630/)

So the wifi seemed to work pretty well out of the box but I noticed after prolonged use it would just suddenly freeze and the only way to make it come back was to reboot. (You couldn&#8217;t even reload the module or restart networking stack).

You can tell if this will be a problem for you by running iwconfig: if you have lots of Invalid misc errors and the signal and noise levels are fixed at -60dBm then you will want to switch from the ipw3945 module to the iwl3945.

To try it out:

sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe iwlwifi_mac80211
sudo modprobe iwl3945

Now if you run iwconfig you should see wlan0 (plus wmaster0 which we&#8217;ll just ignore). If it&#8217;s called wlan0_rename then you run

sudo nano /etc/udev/rules.d/70-persistent-net.rules

Comment out the line reserving eth1 for ipw3945 module.

To make this all permanent you need to add the iwl3945 and iwlwifi_mac80211 modules to /etc/modules

sudo echo iwlwifi_mac80211 >> /etc/modules
sudo echo iwl3945 >> /etc/modules

And now stop the ipw3945 and dependencies from loading by blacklisting them

sudo echo blacklist ipw3945 >> /etc/modprobe.d/blacklist
sudo echo blacklist ieee80211 >> /etc/modprobe.d/blacklist
sudo echo blacklist ieee80211_crypt >> /etc/modprobe.d/blacklist
sudo echo blacklist mac80211 >> /etc/modprobe.d/blacklist

---

