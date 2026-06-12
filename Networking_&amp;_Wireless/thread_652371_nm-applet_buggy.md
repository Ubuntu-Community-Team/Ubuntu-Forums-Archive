---
title: "nm-applet buggy"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by stealthc on 2007-12-28
I've had to remove encryption from my wireless network because my dad has a laptop running windows me, and a crappy network card which doesn't seem to like using encryption.  I threw the encryption on there because people were leeching off our network, so I figured it would get rid of them till I had the time to figure out why my router was being so damned buggy.  Well I got the encryption off, network manager in windows for my laptop works like a snap all I had to do was manually remove the encryption settings; which was pretty easy and straight forward to do.  I get into gutsy and it behaves as though it is still using a password.

Ok so I try to remove the password from keyring manager.  No luck net still won't work.  Then I try to change the ssid of my router.  It still sees the connection under the old ssid.  So I used gconf-editor and started deleting keys in there (under system, network, etc).  Then I forced it to connect to a network with the new ssid, and it connected fine.  After a restart it stops working and I can't force it to use my network anymore which sucks.

windows continues to have no problems.  So how do I reset network data so it behaves like it did when I had a fresh install?  I even tried changing the mac address of the router and that didn't work (but then maybe that's why it won't connect to the modified SSID, because it retained old settings for that and won't update).  Whoever the hell made this nm-applet like this, it's retarded.  It works the first time but is enough to annoy any network administrator.

I tried uninstalling nm-applet and reinstalling it.  I tried to find folder and things kicking around in etc, under network for example (there were a few folders in there, I had a look and couldn't find any clues.

---

### Post by stealthc on 2007-12-28
ok I fixed by going into synaptic and re-installing network manager and gnome extensions for network manager.  The retarded thing is, what let me get into my network the last time seemed to work fine in order to allow me to connect to my network, which gave me the opportunity I needed to get synaptic to work.  The network manager now sees the correct ssid for my network.  Of course, if I change the configuration again I bet you I get this problem again (which sucks).

I bet you when I change ssid on my router, it'll still think it's the old ssid.  Maybe I'll lose my internet connection, yay!

---

### Post by stealthc on 2007-12-28
same thing worked again got ssid back to old setting but this is real aggrivating.

In the picture, ssid was actually "StealthNet".  When this was selected I had a net connect, but it would not appear unless I chose "connect to other wireless network", which I would type in "StealthNet" and it would appear in the list and I would have working connection, like in the picture.  Thing is, signal strength for "StealthNetA" is actually for "StealthNet", and the 0 signal for "StealthNet" isn't very accurate because my connection works fine with it selected.  My connection did not work for "StealthNetA" which would appear in that list automatically.  I wouldn't be-able to connect (obviously because that ssid no longer actually exists).

WTF I gotta reinstall network manager whenever I'm connecting to a network with settings that have changed?

---

### Post by erfahren on 2007-12-28
take a look at the file /etc/network/interfaces

you might need to clear out any settings in there

the only thing that needs to stay in there is the part:
```

# The loopback network interface
auto lo
iface lo inet loopback

```

I set up my Wifi by this HowTo which may be helpful for you (in some way, I don't know), anyway...
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

This probably isn't really applicable either but is a very comprehensive howto, may come in handy sometime:
[How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by stealthc on 2007-12-28
Yeah I did that, it came automatically that way with just those lines.  I bet you once I get my ubiquity pcmcia card in I'm gunna be suffering from problems again....
Still it's gunna be real aggrivating re-installing all the time.
FYI, if I connect to a network and the settings remain stable (and I'm sure there's some sort of thing for the router stored in a file, believe bsid or something like that, or mac address....somethin) that is used to attach ssid, encryption and other settings to the router, so if ssid changes it won't update.  Hence that screenshot snippet I posted.  But then how to fix this?

---

