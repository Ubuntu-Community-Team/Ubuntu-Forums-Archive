---
title: "[SOLVED] Need help getting sound from nVidia Corporation MCP61 on abit NF-M2PV"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by diablo75 on 2008-12-10
I just finished doing some heavy surgery on my computer.  I basicly have tossed away my old motherboard (which had a few PC slots) for an Abit NF-M2PV (which only has one slot, dedicated to my wireless adapter).

The soundcard built into this motherboard shows in lspci as:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

I've found [this thread]("http://ubuntuforums.org/showthread.php?t=546931") (which is over a year old) that says the card is actually a RealTek ALC861, and says I have to modify /etc/modprobe.d/alsa-base in order to get the card to work.

But because of the age of this post, I felt I should check in to see if there is a more up to date version for doing this since I am using Ibex, and not Feisty.

Thanks!

---

### Post by ohzopants on 2008-12-11
I'm fairly certain I have that exact sound chipset and it has worked "out of the box" for me since Feisty (I haven't upgraded to II yet).

I'm at work right now, but I'll confirm this when I get home.

---

### Post by diablo75 on 2008-12-11
Using [this post]("http://ubuntuforums.org/showthread.php?p=4263007#post4263007") I got it working perfectly.  Even the mic works.  For my chipset (a Realtek ALC888 )  I just:

```
sudo gedit /etc/modprobe.d/alsa-base
```

And then add to the bottom:

```
options snd-hda-intel model=6stack
```

Saved and reset.  I had to turn up my "Side" speaker levels in my mixer to get louder sound (which is a little odd) but it works.

---

