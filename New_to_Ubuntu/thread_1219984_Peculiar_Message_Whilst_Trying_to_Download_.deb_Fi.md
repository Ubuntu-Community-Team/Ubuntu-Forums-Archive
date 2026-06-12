---
title: "Peculiar Message Whilst Trying to Download .deb File..."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-07-22
I went to download the Pidgin Facebook add-on, as is being discussed in another thread, but when I tried to download it (a .deb package) with GDebi Package Installer I got this error:

"/tmp/pidgin-facebookchat-1.60-3.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

Is the associated helper application GDebi?  Because I checked under Applications > Add/Remove and one of the two GDebi options was checked and installed.

---

### Post by moredhel on 2009-07-22
I don't know how to solve that problem, but in the mean time you could do dpkg -i <nameofpackage>

---

### Post by Wataru8675 on 2009-07-22
> **paddyoquinn said:**
> Yeah that can happen from time to time, its a bug between firefox and xulrunner i think, any way all you have to do is save the file to your hard drive then just go to it and double click it and gdebi will come up! :)
Regards 
Patrick

Oh, awesome, that worked!  Thanks a bunch. :D

---

