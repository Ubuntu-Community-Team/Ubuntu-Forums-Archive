---
title: "NetworkManager not starting wpa_supplicant?  Should it?"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by aminoz on 2007-01-06
I have a Dell 1200 laptop with a Broadcom 4319 wireless running Edgy.  I've been using the wireless successfully, with the 43Xx driver blacklisted - using nidswrapper/bcmwl5 instead and wpa_supplicant; with /etc/network/interface set up to invoke wpa_supplicant for my interface, and my network details in wpa_supplicant.conf.  Authentication is "WPA-PSK", whatever PSK means.

Then I learnt about NetworkManager on this site and decided to try it.  I commented out everything in /etc/network/interfaces and so on, and it worked well -- great!  But then last night I downloaded some Edgy upgrades that were automatically notified, mostly involving dbus, and now NetworkManager can't connect on boot-up.  The problem appears to be with wpa_supplicant.  On boot-up, it's not being started, which it must have been at first, presumably.  If I start it myself, (in which case the wireless seems to work ok) I appear to get two instances, eg:


amcb@amcb-laptop:~$ ps ax | grep wpa
 5429 pts/0    S+     0:00 wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf -d
 5493 ?        S      0:00 /sbin/wpa_supplicant -dd -g /var/run/wpa_supplicant-global
 5654 pts/1    S+     0:00 grep wpa
amcb@amcb-laptop:~$ 


The first instance is the one I manually invoked, showing the parameters I have for it; I don't know what the second instance is.  The key difference is the -Dwext parameter, some sort of subsidiary driver to do with key encryption, I forget.  (I picked it up from the usual perusals of this site, and the documentation that comes with wpa_supplicant in /usr/share when you install it.  I also notice I've left in wpa_supplicant.conf in my command line; presumably it's superfluous now; anyway whatever problems it might cause are not the issue here.)

Any comments?  Otherwise I will have to start the long process of investigating everything that happens with the dbus and network init scripts, which look very long and hairy to me.

---

