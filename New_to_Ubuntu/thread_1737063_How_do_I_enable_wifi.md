---
title: "How do I enable wifi?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by n96 on 2011-04-23
This should be something very easy to fix. When I go to he internet icon and click on it, it says 
wireless network 
Wireless network is disabled

It worked a few days ago. I tried to fix it by reinstalling Ubuntu, but that did nothing.  I guess it is such a simple problem that nobody bothered to write a page about it. 

I am a complete newbie so have mercy.

I have Ubuntu netbook 10.10 (I think, might be 10.04 but I'm quite sure it is 10.10)

---

### Post by frup on 2011-04-23
There should be a soft key on your keyboard that allows you to enable and disable the wireless. If it just suddenly stopped working maybe you pressed this by mistake. If that doesn't fix it something more problematic may be happening.

---

### Post by josephmills on 2011-04-23
you can also see if its enabled or disabled  by pressing **ctrl+alt+t**
then entering in ```
rfkill list all 
``` you will get a list like this ```
0: hp-wifi: Wireless LAN
	Soft blocked: **no**
	Hard blocked: **no**
1: phy0: Wireless LAN
	Soft blocked: **no**
	Hard blocked:[b] no
[/b]
```
as you can see nothing is blocked if there is a **yes** then something is blocked

---

### Post by n96 on 2011-04-23
> **josephmills said:**
> you can also see if its enabled or disabled  by pressing **ctrl+alt+t**
then entering in ```
rfkill list all 
``` you will get a list like this ```
0: hp-wifi: Wireless LAN
	Soft blocked: **no**
	Hard blocked: **no**
1: phy0: Wireless LAN
	Soft blocked: **no**
	Hard blocked:[b] no
[/b]
```
as you can see nothing is blocked if there is a **yes** then something is blocked

```

0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: yes
1: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no

```

After pressing the wifi enable / disable key, all the hard blocked switched to no, however, the soft blocked are both still yes. 

The wifi icon is still saying wifi is disabled.

---

### Post by frup on 2011-04-23
The nm applet may be disabled there too.

I find on my laptop if I hit that button by mistake, it doesn't come back for ages, I usually just restart.

---

### Post by josephmills on 2011-04-23
try ```
rfkill unblock all
``` dont reboot though

---

### Post by n96 on 2011-04-23
> **josephmills said:**
> try ```
rfkill unblock all
``` dont reboot though

Thank you so much. You saved me from more days of boredom :)

Thank you to everybody else who helped.

---

### Post by josephmills on 2011-04-23
could we see a ```
sudo lshw -C network
```Thanks

---

