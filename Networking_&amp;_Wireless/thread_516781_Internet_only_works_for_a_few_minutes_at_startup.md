---
title: "Internet only works for a few minutes at startup"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Angel700 on 2007-08-03
I have a Toshiba Satellite P205-S6337.  I got the ndiswrapper to pickup and install the wifi, my problem is that It only works for about 5 minutes when I first boot up.  In order for it to work again I have to restart the laptop.  Any suggestions?

---

### Post by noob12 on 2007-08-03
For starters, let's see what you're running.  
```

lshw -C network

iwconfig

ifconfig -a

ndiswrapper -v

ndiswrapper -l

```

Are you using NetworkManager or have you manually configured things in /etc/network/interfaces and the wpa supplicant configs?

Can you describe more about what happens when it "stops working"?

---

### Post by holdfenytolvaj on 2007-08-08
Hi,

I have a similar problem, although not i started the thread,
i continue...

For me the "internet stop working" means that every http request die out except,
ones from google/gmail/maps.google/php.net ...

I will post you soon what you requested, but first i describe a little bit more.
I can connect to the internet, torrent works, pop3 works, ping works,
all http request works for a bit. That means a small portion of the webpage loads but nothing more
like favico the title sometimes the text as well (exception above). It is the same for Opera and FF.
It is the same at work and home (for the same machine). I tried to install 
older (K/X/)Ubuntus as well. And also a different debian based distribution (UHU linux).
All the same. Same for wired or wireless net.

Now my only hope if something wrong with the kernel (???).
If anybody has any suggestion please let me know.

---

