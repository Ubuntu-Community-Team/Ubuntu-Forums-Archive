---
title: "Xubuntu fails to install on Gateway PC"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by MisterLambda on 2009-06-19
I installed Xubuntu on my other PC that so desperately needs it. XP can barely run on this thing and it has 256 MB of Ram! Anyways, Wubi install worked up to the 90% of Ubiquity. Then the monitor barfed random pixel garbage, and Ctrl+Alt+Backspace doesn't work, nor did the tty keys. It seems like it's doing background tasks, but I can't see. When it looked like it was done, I couldn't see the buttons, afraid they didn't work or the keyboard didn't, cold booted back into the install, it reinstalled Xubuntu.... again.... before failing. Any help? I uninstalled it, but I could try again.

Here are the specs:

[LIST]
[*]256 MB of RAM
[*]2.4 Ghz single-core Celeron
[*]Intel integrated graphics chipset
[/LIST]
I'd love it if you could help. It can boot, as it could get in Ubiquity.

---

### Post by t0p on 2009-06-19
Can I suggest that you forget using wubi and do a regular installation to hard disk?  You can do a dual-boot if you need to keep windows on that machine.

---

### Post by MisterLambda on 2009-06-19
Disc drive doesn't work, and USB is out of the question, it can't boot from USB.

---

### Post by wpshooter on 2009-06-19
Fix or buy a new CD-ROM drive.

---

### Post by MisterLambda on 2009-06-19
I'm trying to avoid spending, as I have to save up for something.

---

### Post by MisterLambda on 2009-06-21
Also, one thing. I don't want to commit to a partition to find out it doesn't work.

---

### Post by LewRockwell on 2009-06-21
not sure where you are at, but cd drives are dime-a-dozen here(region commonly known as north america)

I've got dozens waiting for the next trip to the electronics recyclers

still, I'm wondering exactly why you haven't attempted to put more ram in that machine since ram is also a throw away item here as well

why don't you tell us what you've got and where you're at so that someone might be able to assist you more effectively and perhaps even directly

they might even be your next door neighbor

it is a small world after all

---

### Post by MisterLambda on 2009-06-21
My disc drive cable is broke, and I can't install memory without the system acting funky. I was at the 90% point, install crashes, hard reset in xubuntu, loops back to the installer. Uninstalled xubuntu for a while.

---

### Post by halitech on 2009-06-21
if WUBI isn't working you can try Unetbootin in windows to do a linux install. The plus side is you aren't limited to Ubuntu (will also download and install Debian, Redhat, Suse and more)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by MisterLambda on 2009-06-22
Unetbootin still uses partioning. I don't want to partion, in case the install failed.

---

### Post by halitech on 2009-06-22
unless the power goes out or you have other hardware issues then there is no logical reason why the install would fail.

---

### Post by MisterLambda on 2009-06-22
It crashed in Wubi, so it will be probably the same, and power goes out sometimes.

---

### Post by halitech on 2009-06-22
and it crashed probably because of this
> Intel integrated graphics chipset
the newer versions of Ubuntu don't play well with some intel chipsets so Unetbootin would at least give you the option to install an older version to get you running.



just something I'm noticing here, it almost seems like you are trying to convince yourself to not install ubuntu by coming up with excuses on reasons not to even though you say you want to install it. If I'm wrong, my apologies but thats the way I see it.

---

### Post by egalvan on 2009-06-22
> **MisterLambda said:**
> My** disc drive cable **is broke,
**I can't install memory without the system acting funky**.
 I was at the 90% point, install crashes, hard reset in xubuntu, loops back to the installer. Uninstalled xubuntu for a while.

Again, we don't know where you are at, but an IDE cable is definitely a throw-away item...

Any Mom&Pop repair shop is sure to have a drawer full of these...

Even at someplace like Best Buy, or Fry's, if you ask nicely at the repair desk, they might give you one for free...

This is in North America, and Your Mileage Will Vary in other countries...

As for your system **acting funky** with more RAM, sound like deeper hardware problems to me...

---

