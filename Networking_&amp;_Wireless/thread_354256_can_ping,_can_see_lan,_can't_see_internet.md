---
title: "can ping, can see lan, can't see internet???"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by TheGeneralsLounge on 2007-02-05
hi, im pretty much brand spankin new to Linux and Ubuntu. I have Ubuntu setup on three pc's and run the live cd from my home laptop. I can ping from all three pc's to [www.google.com](www.google.com) and [www.thegeneralslounge.com](www.thegeneralslounge.com) no worries, i cannot however, access the websites or use GAIM or any other web related... thingos.

I'd sort of like to get this issue fixed up ASAP as these three computers will be used as Linux (Ubuntu) promo tools in my shop ([www.TheGeneralsLounge.com](www.TheGeneralsLounge.com))

I have searched these forums for a week now and have tried everything, i thought i had the answer a few days ago but alas no joy.

If anyone else has had to fix these problems and now has Firefox and GAIM working - I'd appreciate a step by step solution (and donate some beers!).

regards,
TheGeneralsLounge

---

### Post by LotsOfPhil on 2007-02-05
Does wget work? Try
```

wget http://www.cs.princeton.edu/images/mainpage/CS_west_wall.jpg

```

---

### Post by ewankho on 2007-02-05
Maybe you have firewall blocking access to http and the protocal gaim uses?

---

### Post by TheGeneralsLounge on 2007-02-05
Thanks for your quick responses,
> **ewankho said:**
> Maybe you have firewall blocking access to http and the protocal gaim uses?

i don't think the firewall is blocking firefox as it seems to run ok when connecting to the local ruter admin page at 10.1.1.1.

As for you Mr Decepticon youuuu *points finger*. I trid that wget, it connected ok but it didnt recieve a response...:
i just tried that wget again to give you exact error but this time i got failed: no route to host.

---

### Post by Belfast on 2007-02-06
check your dns settings. make sure you have dns addresses configured in network settings

---

