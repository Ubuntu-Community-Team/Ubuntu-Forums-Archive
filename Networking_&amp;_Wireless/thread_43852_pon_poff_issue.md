---
title: "pon poff issue"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by teumima on 2005-06-23
Hey guys

My internet disconnect once in a while. Which I reckon is normal when idle for a while sometimes.

So when I type sudo pon or sudo pon dsl-provider it should connect. It doesn't always work. In fact most of the time it doesn't.

sudo poff -a works.

The only way I can get it work is by rebooting.

Which doesn't make sense to me, because on reboot it connects right away. Isn't the boot action the same as pon?

Any ideas how to sort this out.

thanks

-amichai

---

### Post by alastair on 2005-06-23
Dialup/PPP is a right pain, still. Luckily I don't have to deal with it myself anymore (usually).

The problem might be lockfiles around, or pppd processes etc. If you get a disconnect, you might have an automatic "retry" set (pppd has a "persistent" option maybe), and if you manually try, it gets stuck/interferes. Perhaps look at what processes are running : ps axl (and check for pppd etc.).

Else, always check the system logs (/var/log/syslog) for a clue.

---

### Post by teumima on 2005-06-24
Yeah with cable it was much simpler. I might switch back to cable, although cable gets slow when the kids get back from home. 

What you say makes sense, because sometimes it reconnects by itself, but that usually fails too.

---

### Post by tristan on 2005-06-24
I found I got rid of most problems by installing gnome-ppp. If you keep a log window open with gnome-ppp you might be able to see if the problem is at your end or your provider's.

---

### Post by teumima on 2005-06-24
[QUOTE=tristan]I found I got rid of most problems by installing gnome-ppp. If you keep a log window open with gnome-ppp you might be able to see if the problem is at your end or your provider's.[/QUOTE]
 How does gnome-ppp work? replaced pppoeconf?

---

### Post by tristan on 2005-06-24
[QUOTE=teumima]How does gnome-ppp work? replaced pppoeconf?[/QUOTE]

Stupid me,  I didn't realise you were trying to to do pppoe and not ppp. I'm not sure that gnome-ppp will help you, it's essentially a nice front end to wvdial for dialing in using a modem.

---

