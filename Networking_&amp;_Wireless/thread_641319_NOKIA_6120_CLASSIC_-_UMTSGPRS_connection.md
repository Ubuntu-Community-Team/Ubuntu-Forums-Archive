---
title: "NOKIA 6120 CLASSIC - UMTS/GPRS connection"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by ribico on 2007-12-15
Hi Ubuntu guys..

I recently got a Nokia 6120 Classic, and I was worried about getting my laptop online since the phone is pretty new and no experiences are available on the web.

Well, it worked at the first try !

Connect you mobile phone via the USB cable, and choose "PC Suite".

install GPRS Easy Connect ver 3.0.1 ([www.gprsec.hu](www.gprsec.hu))

in the configuration panel choose:
phone NOKIA 6125
choose your operator -> in my case Vodafone (Italy)
port USB-ACM 01 (/dev/ttyACM0) -> I am using the USB cable provided with the phone
Dynamic DNS: yes
Connection speed: 2.147.483 (2.048 Mb/s)

save configuration and from the main window click on Connect button.

Enjoy web surfing !

every now and then I get a connection error, just unplug the phone a re-plug it to solve.

---

### Post by raimennendez on 2008-01-09
Can you connect via umts or only via gprs? I'd buy this 6120 in order to connect my ubuntu guitsy, it's a good idea?

---

### Post by Gabriele Ribichini on 2008-01-11
umts too, it works perfectly.

---

### Post by Chuq on 2008-01-11
That website says the project is now closed, it still has a link to the download however.

Once downloaded I get a dependency error when I try to install it.  It seems to be after libgtk-1.2.

```
./INSTALL: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

It seems I have libgtk-2.0.

Can I install libgtk-1.2 concurrently with 2.0 - or probably a better question in the long term - is GPRS EC's source available, has someone taken over maintenance of it, and is this program available via a package manager (which will auto-resolve dependencies?)

---

### Post by raimennendez on 2008-01-14
Ok thanx. I just bought the 6120. I'd like to connect this night with the italian Wind. Someone experienced some problem? It's sufficient to replace the vodafone parameters with the parameters given by [www.155.it?](www.155.it?) I don't have an internet connection in my place and i'd like to know all problems before I leave my office.

thanx

Rai

---

### Post by raimennendez on 2008-01-14
One other question: ubunt has alla Perl modules needed by GPRS_Easy_Connect_301/?

---

### Post by ribico on 2008-01-27
raimennendez, I guess that selecting Wind (Italy) from the menu makes the deal !
I installed GPRS Easy connect without any trouble, I believe that all needed modules are available in Ubuntu repository.

---

