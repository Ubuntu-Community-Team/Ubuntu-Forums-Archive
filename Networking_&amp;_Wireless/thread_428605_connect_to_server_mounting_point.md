---
title: "connect to server mounting point"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by arkangel on 2007-04-30
When doing a link to connect to server under the places menu (in gnome) 
In wich location are mounting these connections

I have a very big isntaller in one computer ,  and I mount my ssh connection and i want to isntall   without copying the whole installer

---

### Post by dmizer on 2007-04-30
using nautilus (places > connect to server) your shares are not actually being mounted.

try the directions here: [http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856)

also, if this is over a local network rather than across the internet, i suggest using nfs rather than ssh because it's way faster and because it's designed to do what you want to do.  don't slow yourself down with encryption unless it's absolutely essential.

to create and mount shares with nfs, use the 4th link in my sig.

---

### Post by arkangel on 2007-05-01
Thank it is working  !

I will try the  nfs  too

---

### Post by arkangel on 2007-05-04
curiousity:


in a local  net   why sshfs is slower than nfs ? it is only an encriptrion  issue?

---

