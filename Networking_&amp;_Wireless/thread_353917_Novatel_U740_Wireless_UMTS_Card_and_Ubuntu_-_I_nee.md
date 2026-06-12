---
title: "Novatel U740 Wireless UMTS Card and Ubuntu - I need help!"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by applecookie on 2007-02-05
Hi there...

I tried to get this card work in Edgy. The hardware overview shows this card alread and with modprobe I managed it to bind it to ttyUSB0. But when I use
find /dev/ |grep ttyU*

I don't see it. Also I can't get it work with my wvdial.

What can I do? Can somebody please help me? In windows this card already works fine. I tried several workarounds but I did'n get it working in linux.


Regards
Frank

---

### Post by compiledkernel on 2007-02-05
Check this thread [http://ubuntuforums.org/showthread.php?t=253466](http://ubuntuforums.org/showthread.php?t=253466)

---

### Post by applecookie on 2007-02-06
Hi.

I already did. I had it already to get a carrier, but once it does, another message "carrier lost" arrives.

Something goes wrong.

The most problem is: This novatel is my only internet connection on this pc. That means, I can't download via synaptic or apt as long, as this card refuses to work. So I can't get i.e. gnome-ppp.
I only can manually download tools in an internet café. But I don't have any clue (beginner) how to compile or to manage any depencies.

Frank

---

### Post by applecookie on 2007-02-07
I of course re-read the complete (!) thread (51 pages...) which you gave me before.
I'm confused after all.

My problem is still, that lsusb does not recognize an device "novatel hdspa card".

Yesterday I tried to fix it with Mandriva Linux 2007. It at once recognizes my card and I can make a internet connection via network drake (KDE).
The only thing is that I have to re-install the internet-connection every time, I reboot.

If I would know, where mandriva saves it's configuration for this connection, I maybe may transfer it to ubuntu.

In the hardware information in mandriva I have the same information abount my card, as in ubuntu - but in ubuntu I can't get it work...

Is there anyone here in this forum, who managed to make a novatel merlin u740 work in Ubuntu???

Regards
Frank

---

### Post by applecookie on 2007-02-11
Now I got it - Hurra!!!

Look here. I posted it in german. If you want the hints in english, just send me a mail:

[http://www.ubuntu-forum.de/thread.php?postid=103613#post103613](http://www.ubuntu-forum.de/thread.php?postid=103613#post103613)


Regards
Frank

---

