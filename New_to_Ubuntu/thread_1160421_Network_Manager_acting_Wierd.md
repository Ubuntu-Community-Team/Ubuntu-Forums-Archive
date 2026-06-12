---
title: "Network Manager acting Wierd"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by jayaramk on 2009-05-15
I installed ubuntu 9.04 on my lappy HP DV2736US which has nvidia Geforce Go 7150M graphics card and n force controller.. when i installed nvidia driver 173 or 180 using the add/remove programs and activating it in the restricted hardware... the network manager was acting wierd! the notifier does not update me with the updates.. no icon change... and i use broadband for my internet connection... before installing the graphics driver i had a connection auto eth0 in my network manager wired connection... but after activating it from the restricted drivers... that connection is lost.. i did not delete it.. it has gone automatically after installing the driver.. i use broadband connection and in order to use internet now.. i need to configure pppoe settings everytime using the terminal... only then i'm getting it!

what should i do now? for this kind of problem?

---

### Post by jayaramk on 2009-05-16
some one help plz....

---

### Post by linux6994 on 2009-05-16
Once connected to the Internet have you tried to reinstall the network manager?

sudo apt-get install network-manager-gnome network-manager

---

### Post by jayaramk on 2009-05-17
yes did it but the same error continues... is this a graphics driver issue?

---

### Post by jayaramk on 2009-05-18
hlpe me....

---

### Post by Sub101 on 2009-05-18
Have you tried to briefly uninstall the new Nvidia driver to determine if that is the problem?

---

### Post by jayaramk on 2009-05-18
yes nvidia is causing the problem...! now what should i do? i also tried using envy but it again brings the same fault....

by the way i installed ubuntu inside windows? does it also cause any problems?

---

### Post by Sub101 on 2009-05-18
You could try another network manager like WICD

---

