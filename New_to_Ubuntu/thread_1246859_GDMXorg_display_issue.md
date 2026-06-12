---
title: "GDM/Xorg display issue"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Linuxson25 on 2009-08-22
Hi

I recently "cloned" the Ubuntu installation on my laptop, LG LW60, with remastersys....and tried installing it on my desktop pc, AMD64, GeForce9600GT,2GB RAM....ect.
When I load kdm, it boots up perfectly right into the desktop.
But when I try gdm - gnome - all I get is a white screen with the mouse pointer on it.
I have tried reconfiguring gdm, xorg, un-installing compiz, and re-installing gdm....but to no avail.

Checked xorg logs, and this was the report it gave me: [http://pastebin.com/d73405482](http://pastebin.com/d73405482)

I would really appreciate some input on this, as I would like to continue using GNOME, instead of KDE, cause the desktop it a bit buggy....keeps on crashing




Thanx

---

### Post by PmDematagoda on 2009-08-22
Hmm, I think you might be providing the log from the install you cloned since the driver in use is the Intel one(atleast according to the log), which is highly unlikely if the card you're using is an Nvidia 9600GT, could you please delete the logs and try and obtain a proper one?

Also, can you post the contents of:-
```
cat ~/.xession-errors
```

---

### Post by Linuxson25 on 2009-08-22
This is the new output in my xorg.log file.
Hope it helps.

[http://pastebin.com/m493e5deb](http://pastebin.com/m493e5deb)

---

### Post by Linuxson25 on 2009-08-22
> **PmDematagoda said:**
> Hmm, I think you might be providing the log from the install you cloned since the driver in use is the Intel one(atleast according to the log), which is highly unlikely if the card you're using is an Nvidia 9600GT, could you please delete the logs and try and obtain a proper one?

Also, can you post the contents of:-
```
cat ~/.xession-errors
```
Oh yeah....I tried to get that info you wanted with [B]cat ~/.xession-errors
[/B]Just tells me that no such file/dir exists
Don't know if I tried this correctly?
But thanx

---

### Post by PmDematagoda on 2009-08-23
> **Linuxson25 said:**
> Oh yeah....I tried to get that info you wanted with [B]cat ~/.xession-errors
[/B]Just tells me that no such file/dir exists
Don't know if I tried this correctly?
But thanx

Sorry, my bad, the command is:-
```
cat ~/.xsession-errors
```
and the Xorg log seems to be ok, except for the fact that you are not using the proprietary Nvidia driver which means that applications like compiz will not run anyway(but this should not prevent you from logging in).

---

### Post by Linuxson25 on 2009-08-23
Hmmmmm....thought it would be something like that as well, so I tried it with that wording...still same result.

But thanx anyway, got it sorted out :)
Looks like Compiz as creating all the con-"fusion"....lol
Just uninstalled it completely on my laptop, did another copy with remastersys, and installed it on my desktop. HEY PRESTO!!!
It worked!! Just re-installed compiz, tried the normal setting, let it download the relevant NVidia driver for my card, and that was it


Thanx for all the help

---

