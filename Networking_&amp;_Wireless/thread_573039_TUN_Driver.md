---
title: "TUN Driver"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by atwin on 2007-10-11
Does anyone know if the TUN driver is installed by default in ubuntu?

And also, where can I find the following libraries: libgpg-error and libgcrypt.  I tried looking them up but the sites are all obsolete and non-existant.

I am trying to install the VPNC software on my Laptop.


Thanking you all in advance for any help,


atwin

---

### Post by PaulFr on 2007-10-12
In Feisty, I see the vpnc as well as the libgcrypt11 and libgpg-error0 packages readily available. vpnc is available in the **universe** repository. Use **aptitude search gpg** and **aptitude search vpn** to get the list of related packages.

BTW, here is the link to the original libgcrypt and libgpg-error libraries - **[http://www.gnupg.org/(en)/related_software/libraries.html](http://www.gnupg.org/(en)/related_software/libraries.html)** - only useful if you want to compile the source yourself.

However, I do not know much about the TUN driver you mentioned.

---

