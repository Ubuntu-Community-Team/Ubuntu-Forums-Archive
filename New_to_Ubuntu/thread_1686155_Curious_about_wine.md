---
title: "Curious about wine"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by redandgreen on 2011-02-11
I've just installed spotify under wine and noticed that I didn't need to use admin privileges to do so. This isn't any kind of security risk, is it? Wine is just an emulator, and nothing I run on it can effect my ubuntu install? 

More generally, if you (for some unfathomable reason) were in the habit of browsing the internet using a browser working under wine, would wine run the malware and greyware you'd run across? What would you see if you deliberately tried to run some sort of malicious program under wine?

---

### Post by tgm4883 on 2011-02-11
> **redandgreen said:**
> I've just installed spotify under wine and noticed that I didn't need to use admin privileges to do so. This isn't any kind of security risk, is it? Wine is just an emulator, and nothing I run on it can effect my ubuntu install? 

More generally, if you (for some unfathomable reason) were in the habit of browsing the internet using a browser working under wine, would wine run the malware and greyware you'd run across? What would you see if you deliberately tried to run some sort of malicious program under wine?

Actually, [Wine is not an emulator]("http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3")

You didn't need admin privledges because you installed spotify in your home folder. Your regular user has permission to do that.

---

### Post by jfreak_ on 2011-02-11
Just make sure none of you virtual  drives map to / . C:/ goes to /home/.wine/ . but check that nothing goes to /.

---

### Post by asmoore82 on 2011-02-11
**[COLOR="Purple"]W[/COLOR]**ine **[COLOR="Purple"]I[/COLOR]**s **[COLOR="Purple"]N[/COLOR]**ot an **[COLOR="Purple"]E[/COLOR]**mulator -

But yes, programs installed via wine go into your home folder so that no
admin privilege is required. In theory, this also prevents malicious code
from running via Wine and damaging your whole system.

However, it is easily possible that malicious code could run from Wine and
damage your personal files. To lock wine out of your files, you can run
```
winecfg
```Click the "Drives" tab,
and take away all drives but "C:"

---

### Post by redandgreen on 2011-02-12
Wow. I had no idea wine could be such a risk :( thanks everyone who replied, you've answered my questions and more.

---

