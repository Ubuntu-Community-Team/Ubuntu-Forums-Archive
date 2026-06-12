---
title: "Getting Windows file sharing working"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by dbunder on 2008-06-15
New Ubuntu hardy install.  Haven't used it for a couple years (feisty, maybe)?  Trying to access a Windows XP share via nautilus and nothing is showing up.  Everything in windows is configured properly as far as sharing goes.  I remember this working out of the box on my old install, but not on this new install.  I checked to see if the samba packages were installed in ubuntu and everything looks fine to me.

Any tips on getting this working?  Rather not have to mess with config files and such - did enough of that with slack and I'm still a bit traumatised. :)

Thanks for any help.

---

### Post by superprash2003 on 2008-06-16
in nautilus type smb://x.x.x.x where x.x.x.x is the ip of the xp machine

---

### Post by dbunder on 2008-06-16
> **superprash2003 said:**
> in nautilus type smb://x.x.x.x where x.x.x.x is the ip of the xp machine

Just tried that and nothing shows up.

Here's all the samba packages installed (getting this from aptitude searches for smb and samba):

samba
samba-common
system-config-samba
smbclient
libsmbclient
smbfs

Am I missing anything?  On a previous ubuntu install all this stuff worked out of the box, no problem.

No firewall on my xp machine, btw.  And the shares show up on another windows box I have.

Thanks.

edit: just typed in the whole share name including IP address and path and it was able to access it/copy files, etc.  So it works, sort of.  I just want to be able to actually see my shares instead of having to bookmark them in nautilus or type them in every time.  Standard user-friendly stuff, yaknow?

---

### Post by dbunder on 2008-06-18
anything?  or should i abandon the idea of stuff actually working properly? :p

---

### Post by jonandrews on 2008-06-19
I've put a few step-by-step to XP/ Ubuntu networking on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

They should help.

---

