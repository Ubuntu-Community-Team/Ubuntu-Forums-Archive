---
title: "[SOLVED] Printer Sharing w/ Ubuntu Server"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Joeb454 on 2008-09-24
I can't remember the last time I posted a support request thread...anyway here goes!

I have my home network setup, with an Ubuntu server acting as a samba share for everybody, a backup server for my laptop (using rsync to the admin account I setup originally :)) as well as a web server (sort of...).

Anyway, I realised yesterday only 1 PC could print anything, and that's a Windows PC that's not on 24/7, so naturally this is no good. I've searched the internet for how to do this, but 99% of the guides are for the GUI method, and it's a headless server.

I have, however, managed to get the printer seen and shared out to the network, however it's very temperamental when printing. I managed to print out from Ubuntu on my laptop, and my brother's Vista desktop. Though the print jobs take an age to go through, and I can't figure out why. From the Vista partition on my laptop, the jobs just never went through at all :confused:

If anybody could help I'd be very grateful :)

---

### Post by superprash2003 on 2008-09-24
are you using the security = share option in samba? are you using the cups printing via samba?

---

### Post by Joeb454 on 2008-09-24
> **superprash2003 said:**
> are you using the security = share option in samba? are you using the cups printing via samba?

Yes I have that set in samba. And it is cups printing yes.

---

### Post by HangMan101 on 2008-09-24
out of personal experience forget sharing through samba. it's a huge pain to configure and manage printers on a headless server.

use the "internet printing protcol (ipp)"


and to access cups you can use [http://serverip:631/](http://serverip:631/) 
you may need to enable remote access:
connect to the server (i assume you use ssh)
```

sudo cupsctl --remote-admin
sudo cupsctl --remote-any

```
// first line enables remote administration of cups
// second line enables remote printing with ipp

now you can use ipp from any pc
ubuntu desktop just asks for the server hostname/ip when you use ipp no extra drivers needed

for windows connect to a network printer and use [http://serverip:631/printers/YOURPRINTERNAME](http://serverip:631/printers/YOURPRINTERNAME)
you may need to install a driver(for windows) i suggest you use you original driver (Any postscript driver should work because cups will convert it for you if needed side effect of postscript driver is that you can't access printer specific features)

---

### Post by cariboo on 2008-09-24
I had a similar problem when I hooked up my Laserjet 5P. I found a solution through google that works for me. I had to change the interfaces to:

```
interfaces = lo  eth0
```

and uncomment:

```
bind interfaces only = true
```

and uncomment:

```
guest account = nobody
```

Now everything works as it should.

Jim

---

### Post by Joeb454 on 2008-09-25
I'll give both of these a try when I get home later :)

---

### Post by richmelk on 2008-10-07
Windows recently crashed on my desktop so I installed ubuntu. The printer works fine on this computer. it is wired to a wireless router. I would like to be able to print to this printer with my laptop which is wireless and also uses ubuntu as a os. I'm new to this os so how do I go about getting my laptop to print to the printer that's hooked to my desktop?

---

### Post by graphius on 2008-10-13
I tried > sudo cupsctl --remote-admin
and it asked for the root password. I tried my sudo password, but it would not work.

I don't really want to enable root access...

Am I being a noob, is there something obvious I am missing?

---

### Post by Joeb454 on 2008-10-15
cupsctl didn't work for me, I don't know why, but it wasn't installed, so I sort of skipped that part :p

---

