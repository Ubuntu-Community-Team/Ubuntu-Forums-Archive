---
title: "Toshiba Tecra 8000 No Net Connection. Screen shots provided."
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by delichef on 2007-06-07
Hi:
I am a new Linux user, and have just installed Xubuntu on a 10 year
old Toshiba Tecra 8000, with a 20GB hard drive and 128MB or memory.

My laptop is wired to a Linksys WRT54G router, but does not get an
Internet connection. The cable is OK as I tested it on my other new laptop.

I have gone into Network Settings and selected automatic configuration, see url to my website for screen shots.

[http://tinyurl.com/2nrxnn](http://tinyurl.com/2nrxnn)

Can anyone suggest what I may have to do to connect to the net?

Thank you for any assistance you may provide.

The Deli Chef.

---

### Post by renzokuken on 2007-06-07
you could try runnins from the terminal

```
sudo ifdown eth0
``` then
```
sudo ifup eth0
```

and see if that connects you

---

