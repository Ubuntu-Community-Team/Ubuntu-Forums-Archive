---
title: "SIP Clients Ekiga &amp; Twinkle not working in Ubuntu 9.10 Karmic"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by aslam on 2009-11-23
I have a new installation of ubuntu 9.10 Karmic along with windows 7. Before i was using Jaunty. Twinkle and ekiga both was working well on jaunty with third party sip accounts. But in Karmic it  fails to register any sip accounts. It always shows failed to register error(timed out). 
I tried remove and reinstall the packages and everything but no change. In windows still working good. 
Any body can help!!!

---

### Post by kaapstorm on 2009-11-26
It seems Ekiga has been replace by Empathy in Karmic.

On my clean install of Karmic, I found that the required SIP library was not installed by default. This is easily remedied:

```
sudo apt-get install telepathy-sofiasip
```

Then log out and log in again in order to add your SIP account to Empathy.

---

### Post by atrus on 2009-12-05
> **kaapstorm said:**
> It seems Ekiga has been replace by Empathy in Karmic.

On my clean install of Karmic, I found that the required SIP library was not installed by default. This is easily remedied:

```
sudo apt-get install telepathy-sofiasip
```

Then log out and log in again in order to add your SIP account to Empathy.

Empathy really doesn't do a very good job with SIP yet. It certainly doesn't work for me.

That said, ekiga isn't working any more either. Not sure why.

---

### Post by afrodeity on 2010-07-03
Discovered the secret to Twinkle last nite.

1. You need an asound.conf file in /etc

2. It requires a stun server i.e stun.ekiga.net

---

