---
title: "hpw to completely remove kubuntu"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-08-21
I'm using Ubuntu however I wanted to try out Kubuntu. So I made

sudo apt-get install kubuntu-desktop

Now I had a look at it, liked it as well but made my decision for GNOME. Therefore I'd like to remove KDE again including all the KDE-programs kubuntu-desktop installed.
So I typed in:

sudo apt-get remove --purge kubuntu-desktop

Unfortunately all the KDE-programs are still here and I've got no ideal how to get rid of them...

What do i have to do?

---

### Post by SpockVulcan on 2010-08-21
In the Synaptic Package manager search: "Kubuntu" (without quotes) and mark anything there for complete removal.

---

### Post by phillw on 2010-08-21
Hi,
I'd suggest [I want GNOME back](http://www.psychocats.net/ubuntu/puregnome) Written by one of our really nice forum people.

Regards,

Phill.

---

### Post by rburkartjo on 2010-08-21
phil that did the trick tks

---

### Post by rburkartjo on 2010-08-22
just an after note. wine is completely removed so if you use you have to reinstall and you have to use this command to remove some obsolete packages after you have removed kubuntu
sudo apt-get autoremove. i also had to reinstall vlc, and googleearth. but good link i still might so back and try kubuntu again now that i know how to completely remove.

---

