---
title: "easy way to create .ISOs?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by klemperal on 2008-12-12
It seems that unfortunately many Linux burners won't burn DVD video unless they are in .ISO format.  I also haven't found a burner that will create .ISO from the contents of VIDEO_TS /Audio_TS folders.  Is there a program or script that will allow me to create ISOs from a right click or something simple like that?

---

### Post by binbash on 2008-12-12
mkisofs -o /tmp/cd.iso /tmp/directory/ 

change the directories.

---

### Post by sneeks on 2008-12-12
its already in your system mate,kb3 copy,it will do what you want it to do no problem.
as for burning iso dvd's,or backing up dvd's,k9copy.
this is a better way as it will be read by all dvd players.

---

### Post by marshall.robert on 2008-12-12
> **binbash said:**
> mkisofs -o /tmp/cd.iso /tmp/directory/ 

change the directories.

examples like this are not helpful...


you should already have the software installed, its called Bresaro and sits in the Audo/Video section of your applications menu. it should handle all your needs as long as you dont need anything specialist.

---

### Post by klemperal on 2008-12-12
> **sneeks said:**
> its already in your system mate,kb3 copy,it will do what you want it to do no problem.
as for burning iso dvd's,or backing up dvd's,k9copy.
this is a better way as it will be read by all dvd players.

Thanks, K3B did the trick.

> you should already have the software installed, its called Bresaro and sits in the Audo/Video section of your applications menu. it should handle all your needs as long as you dont need anything specialist.

Bresaro didn't work for me.  Apparently its pretty well documented that in Intrepid Brasero won't burn video DVDs.  I probably should have mentioned that before I made my original post.  Anyway, thanks for the reply.

---

### Post by sirjoebob on 2008-12-12
Alternatively, when a CD is inserted and the icon is on the desktop, you should be able to right-click it and select "copy disc"

Then change "copy disk to" to file image. It is built in and very easy to do.

---

