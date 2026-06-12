---
title: "Bluray Player?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Malt Frisky on 2011-05-11
Hi there

Was wondering if Ubuntu has a blu-ray player.

Got a Sony Vaio with Blu-ray disc drive but can't figure out how to start the film?

Thanks

---

### Post by seawolf167 on 2011-05-11
You should do a couple things, run the following commands

```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
sudo apt-get install ubuntu-restricted-extras
```

I suggest then installing and using VLC to watch your movies

```
sudo apt-get install vlc
```

---

### Post by Malt Frisky on 2011-05-11
Hey

I've installed the packages and I've already got VLC downloaded but still no joy.

---

### Post by Ocxic on 2011-05-11
In VLC have you tried the "open disc" option from the "media" menu. if you have what happens?

---

### Post by m_duck on 2011-05-11
From what I remember, getting Blu-rays to play on Linux is an absolute pain. I've never tried any of it, but unless there have been any recent developments it seems like a lot of hassle.

[Here](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD) is the Ubuntu Community Documentation on the matter for you perusal.

---

### Post by K_45 on 2011-05-11
You won't get it working until you crack the protection with MakeMKV and stream it to VLC, which is still working last time I checked.

---

### Post by Quackers on 2011-05-11
I've used MakeMKV before but it states that it's a 30 day trial. Did I get the wrong one?

---

### Post by K_45 on 2011-05-11
> **Quackers said:**
> I've used MakeMKV before but it states that it's a 30 day trial. Did I get the wrong one?

According to this:

[http://www.makemkv.com/download/](http://www.makemkv.com/download/)

that is the idea, you need always get the latest version when time is up.

---

### Post by Quackers on 2011-05-11
Understood :wink:
Thanks.

---

