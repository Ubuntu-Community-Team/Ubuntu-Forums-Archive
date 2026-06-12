---
title: "wireless kernel files deleted - how can I replace them?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by HieronymusBosch on 2008-08-19
I just got an old computer from a friend with ubuntu installed.  One of the first things I wanted to do was set up the internet connection.  Initially, I pulled a wireless card from my other computer, a ZyXel card, and tried to get it to work.  Ubuntu only sort of recognized it (it could connect to open networks but could not load anything and ifconfig did not show any indication of the card), so I followed a tutorial on how to get ubuntu to recognize the card.  About half way through, the tutorial listed the command:

"rm -r /lib/modules/'uname -r' /kernel/net/ieee80211"

I followed the tutorial and deleted all the references to ieee80211 in that directory (apparently they conflicted with what had to be done) but in the end, the system still didn't recognize the card.  I've since established a connection through another computer by cross over cord and I've ordered another card that is said to be compatible (and work 'out of the box').  

I want to undelete what I deleted, as I assume it will affect how the other card will work.  Is it possible to repair the kernel and write the files back in or did I mess things up?

Hiero

---

### Post by Sam Lars on 2008-08-19
I'd suggest doing
```
sudo aptitude reinstall linux-image-
```
and add after the dash (no space) what you get from
```
uname -r
```

There's a way to put that command in there automatically but I can't figure it out. [-(

---

### Post by Ayuthia on 2008-08-19
> **Sam Lars said:**
> I'd suggest doing
```
sudo aptitude reinstall linux-image-
```
and add after the dash (no space) what you get from
```
uname -r
```

There's a way to put that command in there automatically but I can't figure it out. [-(

You use the back quote:
```
sudo aptitude reinstall linux-image-`uname -r`
```

What I generally do when a tutorial tells me to remove files is to move them to my home directory so that if something should go wrong, I can always copy them back.  

Another thing is if they ask you to remove a module, sometimes it is better to blacklist them in /etc/modprobe.d/blacklist instead of removing them.  This will only work if the guide is not building a new version of that module.

---

