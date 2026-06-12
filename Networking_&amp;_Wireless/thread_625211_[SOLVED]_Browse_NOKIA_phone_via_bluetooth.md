---
title: "[SOLVED] Browse NOKIA phone via bluetooth"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Virgofenix on 2007-11-27
I'm trying to browse my NOKIA phone using bluetooth. I am using blueman. Everytime I click browse, an error, "obex://[00:18:0f:b4:1c:ed]" is not a valid location., always appears. What does that mean?

---

### Post by tuque on 2007-11-27
You need to install the module, gnome-vfs-obexftp

Either install using Synaptic Package manager or open a terminal and enter;

sudo apt-get install gnome-vfs-obexftp


You will then be able to access your phone

---

### Post by lawentzel on 2007-11-28
Just adding that this worked PERFECTLY for me as well.  Thank you Virgofenix.  Does anyone know if there is any applications to synchronize your phone numbers from your cell phone to some other application on Ubuntu?  Thanks!

Lee

---

### Post by Spoker on 2007-12-01
I just want to add:

THANK YOU! It works perfectly now.
Great!!!

---

### Post by Virgofenix on 2007-12-01
Works fine for me too. Thanks a lot tuque.

---

