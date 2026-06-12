---
title: "Wireless connection issues (I am pretty sure Ubuntu detected the card)"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by jlombs on 2007-09-02
I have a linksys PCI 54G (first version) running on a Dell Inspiron 5100

I have switched back and forth between Ubuntu 7.04 and openSUSE 10.2 and they both seem to recognized the card.  

I am pretty much a linux noob.


Both OS detect the card and allow me to put in my wep creds (128 bit), but I  cannot connect to my network.  


I saw in a few posts someone tried installing wicd - I tried that and it totally messed up my network control panel and network settings (had to reinstall).

I didn't mess around with ndiswrapper yet because I don't think it is a driver issue (tell me if I am wrong), I think it is authenticating to the wep.

Any help would be greatly appreciated.

---

### Post by jlombs on 2007-09-02
This thread worked for me

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I didn't know the Linksys was using the Broadcom codecs.  I installed the KDE network manager - gave me much more information than the standard gnome network configuration tool.

Then my other issue was my WEP key.  You need to put in the passphrase, not the huge generate wep code

---

