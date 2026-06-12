---
title: "TEW-443PI Help!"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by mrirv on 2007-08-13
Hello, I am new to the Ubuntu community.

I have a P4 running Mythtv on it.

I am having some problems with setting up a Trendnet TEW-443PI wireless card on Feisty, I did notice there were some of you that are having some problems also.  Is there and answer out there?

The system see's the card, but I get no scans of any available connections out there.

That can't be true because I am running XP systems through a Linksys WRT54GS wireless router.

I have tried: network manager and wicd but no go!

Help!

---

### Post by noob12 on 2007-08-13
My guess is that you will need to use the Windows driver with ndiswrapper.

Posting the following will let us see what the underlying hardware really is and usually what driver you have associated (if any):
```

lspci -nn

sudo lshw -C network

```
Then people on the forum can guide you through installing the right driver.

---

