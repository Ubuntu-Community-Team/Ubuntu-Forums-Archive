---
title: "Ndisgtk And Ndiswrapper Problem"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by standingstill on 2007-02-25
Hi...i've been an ubuntu user now for about one week. I AM COMPLETELY NEW TO LINUX! please go slow and use small words. here we go...

so i'm trying to get my linksys WPC54G v1.2 wireless card working. i'm trying to use the ndisgtk utility to set this up. i've downloaded the drivers from the linksys site. i run ndisgtk and when the window prompts me to 'install a new driver' ...i browse to my desktop and find the driver (LSBCMNDS.inf)...hit install...and the window doesn't populate with the new driver. this is the error msg i get inside my terminal:

fred@Sluggo:~$ sudo ndisgtk

(ndisgtk:5052): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
modprobe config already contains alias directive

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


can someone help me navigate this problem? i'd really, really appreciate it. 

thanks in advance!

fred

---

### Post by pebo on 2007-02-25
Haven't tried ndisgtk but I got this card working like this on an old thinkpad using the 80211g drivers: 
Blacklist BCM43xx in /etc/modprobe.d/blacklist. 
Downloaded 80211g.zip [ftp://ftp.support.acer-euro.com/notebook/...vers/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/...vers/80211g.zip) and copied to thinkpad. Uncompressed the zip file.
cd'ed to 80211g folder. You must be in the folder when running the following commands as ndiswrapper needs some of the additional files.
```
sudo ndiswrapper -i bcmwl5a.inf
sudo ndiswrapper -l (output should give 'driver installed, hardware present')
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
wlan0 should now show up in ```
ifconfig -a
```
hth!

---

