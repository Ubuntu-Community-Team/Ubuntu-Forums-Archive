---
title: "Must manually activate wireless to start it"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by quip on 2005-08-07
I recently installed Hoary, updated everything, and got my wireless going (madwifi).  However, for some reason, my wireless card comes up, starts scanning for an ap, but won't associate on any, including mine.  It is set as active, with the proper SSID and wep key, with dhcp enabled.  If I open up the network settings tool, and click "deactivate", followed by "activate", it does just fine.  What gives?  What file should I edit?  I'm used to Slackware, but I don't know my way around Ubuntu yet.

---

### Post by odin on 2005-08-08
edit /etc/network/interfaces

---

### Post by quip on 2005-08-08
Ok, any idea on what to add/remove to/from it?

---

### Post by mzaz on 2005-08-08
There should be a couple lines to identify your card. I would think it would look like this (if you are using dhcp)

auto eth1
iface eth1 inet dhcp

---

### Post by quip on 2005-08-08
Yeah, I figured that out.  However, what would I add to what I've already got?  Right now, my stanza that includes my wirless interface looks like this:

```
#The primary network interface
iface ath0 inet dhcp
wireless-essid ****
wireless-key ****

auto ath0
``` 

I just added the following line between the last wireless config command and the auto ath0 line:

```
up pkill dhclient ath0 && ifconfig ath0 down && ifconfig ath0 up && dhclient ath0
``` 

and all is well.  But this seems like an ugly way to get around the problem.  Surely there is something that I am missing...

---

### Post by odin on 2005-08-09
It should actually be enough with this :

auto ath0
iface ath0 inet dhcp
wireless-essid ****
wireless-key ****

but try this:

auto ath0
iface ath0 inet dhcp
pre-up iwconfig ath0 essid ****
pre-up iwconfig ath0 key s: ****
pre-up iwconfig ath0 key open

and have a look to /usr/share/doc/ifupdown/example/network-interfaces.gz so you can see the thousands of options you have.

---

