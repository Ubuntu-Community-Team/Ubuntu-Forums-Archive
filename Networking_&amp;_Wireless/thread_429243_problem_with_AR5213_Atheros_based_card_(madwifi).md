---
title: "problem with AR5213 Atheros based card (madwifi)"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by UberIcarus on 2007-05-01
I had a dlink WNA 233 (I think?) and in any event it did not support either promiscuous mode or too much connectivity options, so I went ahead and bought a Ubiquiti SRC 300mW with antenna..., only one problem, Dhclient on it will not work. the moment I plug in the device avahi-autoipd starts  (which has broken connectivity for me before, when I first upgraded to Feisty, but previously unchecking the avahi box in network-admin has worked just fine at resolving this issue). My dlink of course works just fine, and does not start avahi when I stick it in, considering that I believed I had disabled avahi this is kind of a pain in the ***. I've used the default madwifi drivers, the most current stable release, and the svn release. no luck with *any* of these driver sets at getting the Ubiquiti to work,

any help would be *greatly* appreciated.

edit: also, because I wasn't so clear, I do *killall avahi-autoipd* too, but it starts back up every time dhclient fails.

---

### Post by UberIcarus on 2007-05-01
Bump. If anyone knows what's going on or can duplicate it...or even if *their* Ubiquiti works, and they could help me troubleshoot, I'd greatly appreciate it.

---

### Post by UberIcarus on 2007-05-01
bump again

---

### Post by UberIcarus on 2007-05-01
yet again

---

### Post by UberIcarus on 2007-05-02
okay, figured out what the problem was. This card seems to bounce around frequencies like *crazy*, so you have to manually set the channel and the bitrate in order for it to work, otherwise it just zooms around all the available frequencies.

Anyways, it's working now =)

---

### Post by UberIcarus on 2007-05-02
Posted that slightly too soon, heh. Anyways, the setting the channel and rate manually only seems to resolve the frequency on unencrypted systems. It's not working on WEP encrypted systems....which makes it slightly useless for wardriving....will check to see if it's also broken with WPA, which is also likely the case.

---

### Post by stu_edgar on 2007-05-09
Thought you might like some feedback at least :) 
When you say you need to manually set the channel etc are you doing that on the wifi card side or router side?
I can't remember seeing that data in a  control
Thanks Stu

---

