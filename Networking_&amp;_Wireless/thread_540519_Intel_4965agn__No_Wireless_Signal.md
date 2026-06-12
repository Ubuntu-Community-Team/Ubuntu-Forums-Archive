---
title: "Intel 4965agn  No Wireless Signal"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by Rapid_Fire222 on 2007-09-01
Okay so im new to Linux and have just set my Toshiba Satellite A205-S4617 laptop to duel boot between Ubuntu 7.04 Feisty and  Windows Vista. Now the problem is that Ubuntu dose not recognize the wireless card. I have a  Intel Corporation PRO/Wireless 4965 AGN Network Connection  wire less card. I have tried installing the Ndiswrapper and the windows xp driver. Like its said in some of the forums. It says its installed. But when I use the ndiswrapper -l command to check it. It reply back invalid driver. I still have no wireless so could some shed some light on this problem.

---

### Post by Rapid_Fire222 on 2007-09-01
help someone why wont any one answer me

---

### Post by comacozi on 2007-09-01
maybe no one actually knows?

---

### Post by moopere on 2008-02-17
> **Rapid_Fire222 said:**
> Okay so im new to Linux and have just set my Toshiba Satellite A205-S4617 laptop to duel boot between Ubuntu 7.04 Feisty and  Windows Vista. Now the problem is that Ubuntu dose not recognize the wireless card. I have a  Intel Corporation PRO/Wireless 4965 AGN Network Connection  wire less card. I have tried installing the Ndiswrapper and the windows xp driver. Like its said in some of the forums. It says its installed. But when I use the ndiswrapper -l command to check it. It reply back invalid driver. I still have no wireless so could some shed some light on this problem.

Gutsy (Ubuntu 7.10) has native 4965 support, give that a try.  Works fine here on a Dell 1520 (with intel 4965) except the wireless 'light' on the lappy doesn't turn on, but nevermind the wireless itself is fine and 'just works' without fiddling around.

Regards,
Craig

---

### Post by quini on 2008-02-19
> **moopere said:**
> Gutsy (Ubuntu 7.10) has native 4965 support, give that a try.  Works fine here on a Dell 1520 (with intel 4965) except the wireless 'light' on the lappy doesn't turn on, but nevermind the wireless itself is fine and 'just works' without fiddling around.

Hi.  I had a similar problem with my LG LW20 (it's got an ipw2200); it was solved adding the following text to a file in /etc/modprobe.d/

```
root@quinilg:/# cat /etc/modprobe.d/ipw2200
options ipw2200 led=1
```

Maybe that trick is also useful to you  ;)

---

### Post by pwn on 2008-02-20
This is an old thread and when he had this problem, Gutsy wasn't released officially, I have the same card and had the same problem in Fiesty. Works out of the box in Gutsy.

---

