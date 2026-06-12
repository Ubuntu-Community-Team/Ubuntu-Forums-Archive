---
title: "Error installing Picassa"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by gatordude on 2009-06-21
Linux newbie and I am trying to install Picassa, I used this for my reference [http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html)
When I ran the first comand  (wget -q -O – [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add  -)   ,  I get this error,    gpg: no valid OpenPGP data found.

I wasnt sure if that was what I was supposed to get and I continued on with the instructions and of course it didnt work.

I have tried almost of the photo tools available in the install manager but they really dont compare with Picassa's features.

PLease advise.

---

### Post by zvacet on 2009-06-23
You can download it without repos from [here.]("http://picasa.google.com/linux/download.html")Choose deb package witch is right for Ubuntu version you use (32 or 64 bit).

---

### Post by 73ckn797 on 2009-06-23
> **zvacet said:**
> You can download it without repos from [here.]("http://picasa.google.com/linux/download.html")Choose deb package witch is right for Ubuntu version you use (32 or 64 bit).
+1 on this source.

Here is a simple way to do it once you have down loaded the package. If you have enabled "Gdebi Package Installer" in the menu, you can easily install it. Gdebi is the GUI for installing "deb" files.

Go to System/Accessories/Main Menu. From there you can enable "Gdebi Package Installer" in the "System Tools" section.

---

