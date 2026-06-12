---
title: "Connecting to a Network?"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by CatharSolus on 2010-02-12
Just installed Ubuntu on my Dell laptop and can't figure out how to get it to see the Dell PCMCIA wireless network card or how to configure it to access the wireless router. Can anyone give me some pointers or tell me where such instructions exist on the Ubuntu website?
 
Many thanks. Cathar.:popcorn:

---

### Post by gordintoronto on 2010-02-13
You need the *exact* brand and model of wireless card, then you can look it up in:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

In many cases, wireless "just works."  There's an icon on the top-right of the screen, near the volume control.  You right-click it, select "edit connections," wireless, add a connection.  You will need to know the id of your router, what type of encryption, and the password.

In other cases, there is a rather horrible procedure for using the Windows driver for the card.  The community docs tell you how to do it.  I've never had to use that procedure.

---

### Post by HPD2 on 2010-02-13
post the results of ```
ifconfig
``` and ```
sudo lshw -C network
``` that should help us a bit.

---

### Post by chf on 2010-02-13
Hello,

maybe this can help you: [http://ubuntuforums.org/showthread.php?t=1350588]("http://ubuntuforums.org/showthread.php?t=1350588")

see post #3.

best regards

chf

---

