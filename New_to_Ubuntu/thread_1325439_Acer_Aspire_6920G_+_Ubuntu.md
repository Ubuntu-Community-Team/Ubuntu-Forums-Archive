---
title: "Acer Aspire 6920G + Ubuntu"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Lerwazorz on 2009-11-13
Please Excuse me :-k but I'm BRAND NEW NOOB TO LINUX. I've wanted to try it for a long time. I've change my 250GB hardrive for a 500GB for EXACTLY that purpose. After instaling ubuntu 9.04 (as an app alongside Vista Home Premium) I find out that there are no drivers for the instaled hardware, nothing on Acer's usually helpfull site. I would like at least to get the modem's driver (still using dial up) so that I could go on the web and check out the goodies in the ubuntu language. 
PLEASE DO NOT LET A NOOB DOWN; any help is EXTREMELY welcome or atleast let me know where to go.

regards & GOD BLESS

---

### Post by delcypher on 2009-11-13
When you say there are no drivers? What's not working, apart from your modem?

You might be able to get your modem working if you enable restricted drivers but unfortunately need internet access for that. Your best bet would probably be to connect your laptop via ethernet (that usually works out of the box) to a router or a computer sharing its internet connection.

Get your internet connection running then update your repository sources
by going to Applications > Accessories > Terminal , then type
```
sudo aptitude update
```

Then go to:

System > Administration > Hardware Drivers

then see if you enable any drivers.

I hope this helps you. If you need help setting another computer to share its internet connection then me let me know and I'll try and help out.

---

### Post by Lerwazorz on 2009-11-16
Thanks Delcypher
I will be coming back to you once I've tried that.
GOD BLESS

---

