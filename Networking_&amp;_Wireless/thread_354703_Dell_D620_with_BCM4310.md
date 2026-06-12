---
title: "Dell D620 with BCM4310"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by Cirrocco on 2007-02-06
I have a Dell D620 with a Broadcom WLAN on board.
(XP Partition has no problems with this at all)

I followed several how to guides and didn't get very far.

after successfully running: ndiswrapper -i bcmwl5.inf

ndiswrapper -l
no driver installed.

wifi light is not on
this is the same driver windows xp uses but ndiswrapper doesn't seem to like it.

any ideas where I should go with this next?

---

### Post by usererror on 2007-02-06
> **Cirrocco said:**
> I have a Dell D620 with a Broadcom WLAN on board.
(XP Partition has no problems with this at all)

I followed several how to guides and didn't get very far.

after successfully running: ndiswrapper -i bcmwl5.inf

ndiswrapper -l
no driver installed.

wifi light is not on
this is the same driver windows xp uses but ndiswrapper doesn't seem to like it.

any ideas where I should go with this next?

The last time I had a Dell with a Broadcom card I had to use a different INF than the one Windows XP used.  Is that .inf you have listed above the one specified to use on by a thread on this forum?

---

### Post by Cirrocco on 2007-02-06
I've seen the name come up alot (forum search reveals 127 hits)

guides tell you to use one that comes in the cab you download from dell. - and that's what I did.

---

### Post by #Reistlehr- on 2007-02-06
i have an HP with the same exact wifi. i''ve been trying 3 monthhs, and nothing has worked, and no one seems to be able to off a helping hand either

i tried, ndiswrapper, fwcutter, um, and 2 other things i cant remmeber what they were called. im thinking of just going back to windows.

---

### Post by Cirrocco on 2007-02-06
yeah...this is ghey.

I understand that wifi manufacturers wish to not give away the secrets of the hardware, but the software too?

and what's up with the 30 step guides on getting ndiswrapper to work in conjunction with network manager with separate WPA support?

can't that all be merged into one tool?  does it exist already?  does it have a "load-up-a-windows-driver.inf" button? (yes I'm aware of ndisgtk)

I'm talkin': network-manager + ndiswrapper + ndisgtk + ethtool + that WPA thingy

---

### Post by yaidiot! on 2007-02-19
Cirocco,

I ordered the same braodcom with my D620. I bought it thinking it would work well in Linux (my Linksys WRT54GL runs linux, why should this be different?) Anyway, I tried fwcutter and NDIS wrapper, neither worked particularly well.

I finally decided to buy the Intel 3945. Plugged it in, booted into kernel 2.6.20 and gave my WPA key to gnome network manager. Everything worked -- No testing, tweaking or guessing. It just worked, first time!

I am glad I ditched the Broadcom. The Intel connection is rock-solid and fast. It was $40 well spent to me.

(One other note, the new Zydas driver works like a champ too. And far faster connection than with the windows driver. Wireless networking has come a long way in Fiesty.)

---

