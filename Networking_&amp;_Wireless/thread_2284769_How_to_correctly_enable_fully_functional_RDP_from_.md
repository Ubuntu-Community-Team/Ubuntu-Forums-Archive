---
title: "How to correctly enable fully functional RDP from Windows 7 to Ubuntu 14"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by darts2 on 2015-07-01
Hi Everyone,

I have recently installed Ubuntu 14 onto a Desktop computer, and I now want to RDP to this desktop computer from a Windows 7 installation.

I found, and followed, a very useful tutorial which has allowed me to establish a connection - [https://community.hpcloud.com/article/using-windows-rdp-access-your-ubuntu-instance](https://community.hpcloud.com/article/using-windows-rdp-access-your-ubuntu-instance)

I am presented with the standard xrdp login window as shown below -

[ATTACH=CONFIG]262968[/ATTACH]

I then logon successfully as shown below -

[ATTACH=CONFIG]262969[/ATTACH]

However once my session is fully enabled all I see is a 'checkered' windows as shown below -


[ATTACH=CONFIG]262970[/ATTACH]


I figured that maybe I wasn't configured for an 'xsession' so I followed the instructions in the HP link to the very bottom, however after adding a correctly configured xsession file there way no improvement.

Can someone please suggest how to fix this issue?

Kind Regards,

Davo

---

### Post by nlee2 on 2015-07-01
I just use Desktop Sharing and vino-server on Ubuntu and a vnc client on Windows. Unless you have a special need for rdp ...

---

### Post by QIII on 2015-07-01
Hello!

When posting large images, please use the attachment functionality or include *only* the URL.

Many users have low-bandwidth connections, which mean the images download slowly, or data limitations, which means such images may be costly.

Thanks.

---

