---
title: "Why... why... why?... needless wireless pain with WEP and WPA..."
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by hdensley on 2008-05-14
I have two wireless adapters on my gateway 200arc laptop.  Both pick up signals, both work with unencrypted signals.

The thing that really bothers me, is that I can't connect using either WPA1 or WEP.  I just don't know why this has to be so hard.  I'm on version 8.04

the Intel adapter is Intel Pro 2100 - it's on eth1.  The SMC adapter is EZ connect SMCWCB-G - it's on ath0.

I don't have any clue whatsovere why this dosen't work; in lacking any other explanation, I've deducted that it's alien intervention - after all, Mark Shuttleworth did venture into space.  I'm wearing 

a tinfoil beanie to avoid misguided microwave beams.  Please help me, I'm going insane over this problem.  Thanks.

---

### Post by Guilden_NL on 2008-05-14
Which version?
Hardy?
Upgraded from Gutsy?
Now have problems?

Tell us more.

Hardy Hates Wireless.

---

### Post by Gias Kay on 2008-05-14
> **Guilden_NL said:**
> Hardy Hates Wireless.

Nope, I won't say that; it's the default gnome network manager's fault - it's just not working with encrypted wireless. And below is all you need:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The page has detailed instructions on installation so I'll spare it here.

---

### Post by Guilden_NL on 2008-05-14
> **Gias Kay said:**
> Nope, I won't say that; it's the default gnome network manager's fault - it's just not working with encrypted wireless. And below is all you need:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The page has detailed instructions on installation so I'll spare it here.
Fair enough.  I am am appalled at Hardy's install routine with its wireless issues and inability to understand a blacklist.

Thanks for the link. I've pointed another person to your link.  Haven't checked it out myself yet.  But will patter off now and check it out.

I'm quite put off by Hardy's networking mess, if you can't tell from my posts.

Again, thanks for the link. I'll  be positive and believe it will work.

---

### Post by hdensley on 2008-05-16
_I got it working!_
1) Installed Wicd
2) Used Wicd preferences to indicate the following - ath0, madwifi
3) input WPA key into Wicd within quotation marks " "

Thanks for your help.

---

