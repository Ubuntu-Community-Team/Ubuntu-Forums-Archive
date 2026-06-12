---
title: "/etc/network/interfaces"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Desos on 2007-12-17
I recently was trying to fix my wireless card on and one of the fixes sugested by someone was to cahnge the /etc/network/interfaces file. This did not fix the problem, i later fixed it by doing somethign else but my internet does not work now because of the dodgy interfaces file (the .bak file is not the original either) . I lack the knowhow to edit it myself i wondered if there was a command or something that would automaticaly generate one depending on my hardware.

---

### Post by ubutufan on 2007-12-17
After having a number of similar problems I concluded that the best configuration for my /etc/network/interfaces file is the following

auto lo
iface lo inet loopback

and nothing else
Any connection attempts create their own entries in this file
Let us know if it works

---

### Post by csat on 2007-12-17
I'd suggest you to clarify your message giving us information about the hardware and software you are having troubles with. Maybe the result of a command line typed through out a console, like lspci -v would be also handy to someone trying to figure out what is going on.

---

### Post by Desos on 2007-12-17
ubutufan you are a godsend, thank you.

csat i was going to but i caught myself copying from the terminal on my laptop and trying to paste into firefox on my desktop (which is the only computer i had wiht internet access) but thanks anyway.

---

### Post by ubutufan on 2007-12-17
You are welcome. Just mark this as solved as others will also benefit

---

### Post by csat on 2007-12-17
> **Desos said:**
> ubutufan you are a godsend, thank you.

csat i was going to but i caught myself copying from the terminal on my laptop and trying to paste into firefox on my desktop (which is the only computer i had wiht internet access) but thanks anyway.

Ok, I am happy you've sorted it out helped by ubuntufan.

Cheers

---

