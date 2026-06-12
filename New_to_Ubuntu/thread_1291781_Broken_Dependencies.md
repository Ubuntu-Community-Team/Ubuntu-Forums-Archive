---
title: "Broken Dependencies"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Khakilang on 2009-10-15
Currently I been getting broken dependencies whenever I update or download software. Can anyone tell what is the problem? Attached is the screenshot below. 

[ATTACH]131992[/ATTACH]

Appreciate if anyone could help.

---

### Post by garvinrick4 on 2009-10-15
You have to tell the people what version you are using. Are you testing 9.10 doing
daily upgrades? Tell them your hardware video card, motherboard and such. 
 Some one has the answer if you give them something to go by.  Good luck partner
and have a nice day.

---

### Post by wojox on 2009-10-15
Looks like you need to install Firefox-3.0 first.

---

### Post by oboedad55 on 2009-10-15
> **wojox said:**
> Looks like you need to install Firefox-3.0 first.

It looks like the color scheme of karmic. Which version of Ubuntu are you using?

---

### Post by Susp on 2009-10-15
Hi.

As I see, your Firefox is installed but is not configured properly.
One may name such package "Broken". So what I'll suggest you is to configure Firefox package, before trying to install anything which depends on it.
In order to do this open a terminal and try:

```
sudo dpkg-reconfigure firefox-3.0
```

Also I'd recommend you to check out what is going on by typing

```
aptitude
```

in your terminal. See if it reports broken packages or dependency problems.
Cheers

---

### Post by vipulkelkar on 2009-10-15
try this in the terminal

sudo apt-get install -f

---

