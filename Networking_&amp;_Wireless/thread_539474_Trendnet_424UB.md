---
title: "Trendnet 424UB"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Nullox on 2007-08-31
Well I just gout my Ubuntu I'm 99% ready to install it I just need to know if my WiFi Adaptor works with it. I have a Trendnet Tew 424 UB the back of it says:
TEW - 424 UB H/W:2.0R
I was also wondering if you guys find a driver please post the link.

Mind you I don't have the CD for it.

---

### Post by noob12 on 2007-08-31
What will help is if you plug it into a USB port on your Ubuntu host and type the command

```
lsusb
```

and post the resulting output on the forum.  That will tell us the specific type of device and what kind of driver is required for it.

---

### Post by Model Rockettier on 2007-08-31
i have a trendnet 424UB as well, the drivers come on a CD, which i have, i am not sure what type of drivers they are, but i am going to try to get it installed on ubuntu 7.04 (if someone gets it working for kubuntu 7.04, let me know)

---

### Post by pnh on 2007-08-31
I have the same device and would like to get my computer
(Ubuntu 6.06) on my wireless network. I've read all the postings
regarding installation on this list, but am still confused about
how to do it. There is much conflicting information. One person
says "it just works", while another suggests downloading and
compiling this and that, with no further explanation about how
to do this and how to see if it is working. For example, in one
of the "how-to"s, there is this line:

> 2. Install ndiswrapper (so you can install the Windows networking
> driver (the extension that ends in .inf)
> I install it EASILY with Automatix (under Driver).

Huh? I guess I'll have to find the how-to for that too.
A complete step-by-step protocol and/or a flow chart would be nice. 

Thanks.

-Paul.

---

### Post by Model Rockettier on 2007-08-31
well, I'll tell you what happens

---

### Post by Model Rockettier on 2007-09-01
ok, so i got it working, i am not exactly sure how but basically, i connected to the internet (wired) and downloaded just about every wifi program the add/remove program thing had (including ndiswrapper, which is very important), then through ndiswrapper, i installed the inf driver file (you can find the one i used @ [http://www.modelrockettier.com/linux/driver/](http://www.modelrockettier.com/linux/driver/) with the other 2 files there also on the desktop.  i then just basically fiddled around a short bit with the utilities, then wifi-radar (app) picked up a signal, then i went into the help menu and followed the instructions in connecting to the internet section 1.2.1, then 1.2.2 and after that 1.1([http://www.modelrockettier.com/linux/](http://www.modelrockettier.com/linux/) , sorry for the wierd format, it's the 1 the print-to-file used), hope that helps.

---

