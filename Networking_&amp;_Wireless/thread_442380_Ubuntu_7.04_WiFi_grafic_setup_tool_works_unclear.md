---
title: "Ubuntu 7.04 WiFi grafic setup tool works unclear"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by ddkk on 2007-05-13
Hi!

I have following problem.

Finally I'v get the Internet connection using 7.04 + WiFi USB stick MSI US54SE
But it works just w/o any encryption.

So, I have 2 opportunities to setup my WiFi connection:
1) Automatically (just selecting in menu name of founded WiFi networks)
2) Manual management (where I can tune all settings)

1st - is not for me, cause I need to use static IP address (my router don't give it to me automatically)
2nd - is for me. And it works... but partly.

In manual management window there is no possibility to select WPA or WPA2 (I don't talk about EAS/TKIP - it's just a dream). Just WEP.
But if I select in tray's network menu "create new network connection", then where are paradise: WPA/WPA2 personal/enterprise etc.... But no settings for static IP data (just in automatic mode)!

Closed-loop in the hell named as "Ubuntu's full WiFi support"??

So, of course I have found: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Sorry, but I'm "stupid Windows user" and I just want to make everything w/o "terminal".
Is it possible in my case? May be I haven't find all setup tools somewhere?

Thanks!

---

### Post by wieman01 on 2007-05-14
Static IP support does not quite work yet... at least I could not get it to work using NetworkManager. No idea if anybody else has.

---

### Post by ddkk on 2007-05-14
Static IP - works. Using network grafic tool (NetworkManager). I can establish connection between PC and WiFi-router. But I can't use WPA or WPA2 together! Just 'cause there is no such option in NetworkManager!

Hey, Ubuntu's Guru, any ideas? =)

---

### Post by wieman01 on 2007-05-14
> **ddkk said:**
> Static IP - works. Using network grafic tool (NetworkManager). I can establish connection between PC and WiFi-router. But I can't use WPA or WPA2 together! Just 'cause there is no such option in NetworkManager!

Hey, Ubuntu's Guru, any ideas? =)
There is an option ("manual configuration") in Feisty which you are supposed to use no matter what encryption method you use (WEP, WPA, unsecured, etc.), however, it does not seem to work at the moment. So as far as I know, all you can do is configure WPA manually if you require a static IP. You have to live with it for the time being I am afraid.

---

### Post by ddkk on 2007-05-14
So, as I see the new Ubuntu have a lot of comfortable grafic tolls, such as "Add program" and "Update wizard".

But still have some "childhood disease", like:
- Problem with WiFi network configuration (static IP, encryption)
- Sill some video problems (but situation much better than earlier)
- etc.

Such small issues are a barrier for most part of users which try to migrate from Windows to a Linux. 'Cause today, the most major thing for users are:
- To see anything on there monitors (no video problems)
- To surf the WWW and to communicate with their colleagues and friends (no problems with network setup)

So, are we waiting 7.10?! :confused:

---

### Post by wieman01 on 2007-05-14
> **ddkk said:**
> So, are we waiting 7.10?! :confused:
That's what I'll do.

---

