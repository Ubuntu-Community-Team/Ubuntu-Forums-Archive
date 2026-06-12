---
title: "Problem connecting to Internet"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by pjfliii on 2007-08-10
Hi! I am a new member and also have very little to no knowledge at all of ubuntu. I have three computers at home for which I setup a LAN (wired & wireless). Two comps use windows XP, while the third uses Ubuntu, which my son set up a year ago. Unfortunately my son is already abroad studying. 
  Recently, my D Link router (model DI 524), about 3 years old, konked out. I replaced it with the same model D-Link router. After configuring the network (using the wizard), my two computers using windows XP, are working well and have no problems connecting to the net. However, the comp using Ubuntu can't seem to access the net. I noticed too that the port LED which the Ubuntu computer is connected to the router, does not light up, unlike the other 2 computers. I'm sorry if I am using the wrong computer terminologies, but I am really not that computer savvy.  As I said, I have very very little knowledge of Linux. I tried everything but same result.
  Please help! Thanks

---

### Post by misconfiguration on 2007-08-16
Hello,

What exactly do you mean by you've tried everything?

I assume the network is setup VIA DHCP (your router assigns IP's automagically) correct?

Is the Ubuntu machine the one with wireless, your description is kind of vague albeit it seems as if it is wired directly to the routers switch. Is there any way you could past the output of a few things?

```
sudo cat /etc/resolv.conf


sudo cat /etc/hosts

sudo ifconfig eth0 
```

---

