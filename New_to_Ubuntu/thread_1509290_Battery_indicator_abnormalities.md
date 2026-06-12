---
title: "Battery indicator abnormalities"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by llakais on 2010-06-14
Hey guys,

The little battery icon on the top panel of my desktop doesn't seem to be working properly.

It says the laptop battery is charged, but the icon doesn't disappear, even though I have that option selected in the corresponding preferences.

But the plot thickens when I look at the "Power Statistics" info:

**State** says "fully-charged"
**Energy** says "59.6 Wh"
**Energy when empty** says "0.0 Wh"
**Energy when full** says "620.1 Wh"
**Energy (design)** says "60.7 Wh"
**Percentage** says "9.6 %"
**Capacity** says "100.0%"

I'm confused as to what the difference is between "Energy when full" and "Energy (design)".  It's also weird how it says the battery is fully charged yet only at ~10% of capacity.  Could this be why the icon doesn't disappear even when I leave the computer plugged in overnight?

Here're some more details that might help:
[LIST]
[*]I'm running 10.04 via the Wubi app for Windows.
[*]My laptop is a Thinkpad Lenovo T410, with a few customizations, one of which is a battery with an upgraded capacity.
[*]When I accessed the "Power Statistics" menu, my computer had been plugged in all day, so I'm almost positive the battery actually is charged to capacity.
[*]Both the laptop and battery are brand new - about a week old - so the battery capacity should not have deteriorated significantly by now.
[/LIST]

This oddity isn't affecting my computer's performance, so it's not a major issue, but it is something I'd like to try and sort out.  Any and all help will of course be much appreciated!

Thanks! :D

---

### Post by llakais on 2010-06-15
I forgot to mention before that this hasn't always been a problem.  I can see in the graph on the "History" tab of the "Power Statistics" info that the computer recognized at one point that the cell was 100% charged.  For the past 2+ days it stops at 10% charged.

Anyone have any insight on this?  Thanks again.

---

### Post by underware on 2010-06-15
I also have the same problem on my Gateway LT21 Netbook. It always says Critical Battery. I think its Ubuntu bugs.

---

### Post by llakais on 2010-06-15
Ok, this is gonna make me sound really stupid, lol, but I tried rebooting for the first time since I had the problem, and it's fixed now.  :oops:

I still don't know what caused the problem to begin with, or if it could be solved as easily for you, underware (nice username, hehe).

Anyway, it works for me, at least for now.

---

### Post by kid1000002000 on 2010-06-16
tried that too. rebooting fixes it, but it comes back... not sure how or why...

---

### Post by llakais on 2010-07-09
This has now happened again - I can't figure out what could possibly be causing it.  Any ideas?  The indicator still gets stuck at 10% charge, even though the actual battery seems to be charging completely.

The battery is a SANYO 42T4791 if that helps, although it looks like others are experiences the same issues, presumably with different equipment.  Let me know if there is any more info I could provide that might be helpful.

Thanks so much, guys.

---

### Post by mörgæs on 2010-07-10
The battery indicator showing strange values is a known bug. 

There is a report here
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258)
(and others in Launchpad)

---

### Post by llakais on 2010-07-10
> **mörgæs said:**
> The battery indicator showing strange values is a known bug. 

There is a report here
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258)
(and others in Launchpad)
Aha!  Thanks for pointing that out.

It's certainly not a huge deal, but it's awesome to know people are aware of/working on it!

---

