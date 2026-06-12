---
title: "Oddities with wireless networking"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by mengfei on 2007-03-03
Hey all

I've switched completely over to ubuntu, with just a thorn in the side of having wireless working very strangely for me.

Here's what has happened.

I ordered the 2wire wireless PCMCIA for my thinkpad t22, because it uses the hermes chipset just like the orinoco gold.

I figured that would work just great.

However, network-manager would refuse to show any wireless signals being broadcasted in my area.

After searching throughout google and the forums, I gave up on the card, and realized I have had for a while a USB dongle: the NetGear MA111.

Using the guide at wiki.ubuntu.com, I finally had the ability to see wireless signals aroudn me!

However, I could not connect to any of them.

I searched more, as I did with the 2Wire, and tried upgrades from dapper to edgy, etc. But still nothing.

I gave up, and went to back to Windows Xp for... oh I'd say 2 hours, haha, and decided to give it my all on wireless for Ubuntu.

This time, I've installed Edgy, without configuring my 2Wire PCMCIA card at all.

I installed network manager, but I still do not see a single wireless signal.

I decided to type it in manually in this time, and lo and behold! I connected!

The connection seemed to only last a few minutes though, because I was unable to connect afterwards.


Anyone have any ideas why this is? Or similar experiences?

Much appreciated! Even if I can't get wireless working, I suppose I'll live without the convenience of Internet... somehow...

---

### Post by teaker1s on 2007-03-03
network-manager-gnome will not work if either
1) ethernet cable connected
2)interfaces under system>administration>networking are configured

---

### Post by mengfei on 2007-03-03
Well... that wasn't the case for either of those.

Actually, network manager never picks up that i am wired.

In fact, right now i'm on ethernet cable, and it shows the little exclamation point.

I know wifi radar does not pick up any networks either.

Kwirelessmanager is the only one that does... yet says I'm not associated or something

But hey, thanks for the reply!

---

