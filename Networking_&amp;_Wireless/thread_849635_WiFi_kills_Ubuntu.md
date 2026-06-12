---
title: "WiFi kills Ubuntu"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by qwallis on 2008-07-04
Hello,
      Firstly let me start off by saying that this in **not** a graphics problem. I know there are several threads talking about the same symptoms related to graphics cards, but I have just gone thru a clean install of Hardy Heron and have turned off/ disabled the non-free graphics drivers etc and the problem persists.
What happens is that after an unspecified time the screen / computer locks up and I can't do anything with it other than a hard re-set.
I have currently disabled Wifi, so I can post here: but the  computer is moving to the workshop soon and there I won't have the option of using an Ethernet cable, but will be connecting over WiFi using a friends router which is in the adjacent building so I need to get this problem solved before I can move the computer over. Any suggestions or help is much appreciated.

I'm using a D-Link DWL-G510 WiFi card (which I bought the day before yesterday as it supposedly supports Linux).

Cheers

---

### Post by qwallis on 2008-07-07
Anyone?

If no-one has a suggestion how this can be fixed I am looking at taking the card back (it's new) and buying a different one.

What cards can people recommend, which are known to work with 8.04 and the latest kernel?

---

### Post by peterdm on 2008-07-08
I'm having the exact same problem: D-Link card with texas instruments acx 111 card freezes my system. Unfortunately I have no solution yet either...

---

### Post by peterdm on 2008-07-09
If you want WPA-PSK, the solution is to use ndiswrapper with the windows driver and disable network manager. If you use WEP, you can probably stick to the standard acx driver (but I never actually tried that).

Read [this]("http://ubuntuforums.org/showthread.php?t=852225") thread for details.

Hope this helps,

Peter

---

### Post by qwallis on 2008-07-15
I have now been using ndiswrapper with the windows driver for three days without a glitch so far, so it looks like that was the way to go for me.
It's a shame that the integrated driver has serious problems, but at least there was a way round the problem for me.

One of the reasons I didn't want to use ndiswrapper was that I didn't think that there would be any signal strength information available (as that's been my experience in the past), so I was very pleased to see that all the features seem to be supported by ndiswrapper with this driver.

---

