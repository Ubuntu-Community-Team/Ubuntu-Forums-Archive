---
title: "using ndiswrapper"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by LuckyDem on 2006-08-21
"couldnt copy /WIN2K/rt61.inf at /usr/sbin/ndiswrapper line 135"

what is going on here anyone? can u help?

---

### Post by lupine_nickt on 2006-08-21
It's having problems copying the file. Are you running running it as root (i.e. under sudo)? Does the file exist?

xF,

...Nick

---

### Post by LuckyDem on 2006-08-21
thnks. Yes the file exists, I am just not sure if its the correct inf or not. hell I am a newbie, I aint sure of anything... was using ndiswrapper following commands i found online. just trying to my wireless to work. thanks

---

### Post by az on 2006-08-21
What guide did you use?

Try this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It sounds like you did not use sudo.

---

### Post by windquest on 2006-08-31
> **LuckyDem said:**
> "couldnt copy /WIN2K/rt61.inf at /usr/sbin/ndiswrapper line 135"

what is going on here anyone? can u help?

I had the exact problem. Without going into all the details, the solution was to totally remove ndiswrapper. Follow the instructions  from ndiswrapper and then reinstall. After much frustration it worked well.

---

