---
title: "Can't access SAMBA shares from XP box"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by kooldino on 2008-02-01
Ok, so I figured this one out, but not totally.

I used the KDE Sharing control panel applet to set up a share.  In the advanced options, I added my username and group all over the place in an attempt to make it work.

Problem was, from the XP box, I couldn't connect to the share.  

Apparenlty, what I needed to do was to add run "sudo smbpasswd -a username" from the command line.

What I'd like to know is where that option is in the KDE System Settings sharing applet?

---

### Post by Sami_Sdata on 2008-02-01
You can make your life easier and install webmin.  I use it for most maintenance work on my network.  The module for samba shares handles all that for you.

---

### Post by kooldino on 2008-02-04
can't find webmin in adept...

Does it go by another name?

---

### Post by Sami_Sdata on 2008-02-06
[www.webmin.com](www.webmin.com) and choose the debian package.   I've used this on Redhat, Slackware, FreeBSD and now on Kubuntu.  Very handy for making changes to my home systems from work.

---

### Post by kooldino on 2008-02-08
Man, it's so much easier to just edit the smb.conf then go through the mediocre interface.

---

### Post by BLTicklemonster on 2008-02-08
> **kooldino said:**
> Man, it's so much easier to just edit the smb.conf then go through the mediocre interface.

No it's not. Been there, done that. (by that I mean not "gui is easier" because I agree, editing the file is easier, but what I mean is, it didn't work for me) Even tried webadmin.

The link in my sig is the only way I've ever gotten the XP boxes in my house to access my ubuntu box, ever.

also, I think that after 

sudo smbpasswd -a username

then 

sudo smbpasswd -e username

should be done, then restart and try it.

---

### Post by Sami_Sdata on 2008-02-08
It's only easier if you edit the files enough to remember the syntax.  Also, webmin puts modules for all the servers on the system in one place.  When you are making system changes at 3am while hopped on coffee and diet Mt Dew it's nice to have software handling the details.

---

