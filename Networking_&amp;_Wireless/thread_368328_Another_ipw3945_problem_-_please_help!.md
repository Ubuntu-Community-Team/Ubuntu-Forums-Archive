---
title: "Another ipw3945 problem - please help!"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Lorenz on 2007-02-23
Hi guys!

I read there are quite a lot of problems with the ipw3945 - well, here is another one and I guess it is a challenge for you!

The laptop I use is an IBM/Lenovo T60 with Ubuntu Edgy Eft.

Wifi worked out of the box. Well, almost. I installed KNetworkManager and managed to connect to my home wifi network using the WEP passphrase. However, the connections is very fragile - if I look at the output of KWifiManager it shows me 100%, 90% and then down to 0%. This repeats every ten seconds. So, for about 5 seconds I'm connected, then the signal is lost, it seems.

This is very annoying - I basically cannot surf the net, not use gaim, etc.

Please help me with this issue, I just switched to Ubuntu yesterday, without my wifi I'm basically lost! I also searched this forum for hours already and didn't find someone with the same problem.
I'd really appreciate any help with this!

Thanks,
Lorenz

---

### Post by Lorenz on 2007-02-23
Help would be needed really urgently, I can't connect via cable atm and the wireless just works enough to make a post here!

---

### Post by Lorenz on 2007-02-23
I need to bring this up again.
I heard so much about how helpful the community is - help me a bit please, I wanna believe that Ubuntu is good!

That's how it looks like!

[[IMG]http://img64.imageshack.us/img64/9237/screenshotfi7.th.png[/IMG]](http://img64.imageshack.us/my.php?image=screenshotfi7.png)rl]

---

### Post by wobster on 2007-05-08
I can confirm this behavior for a Acer TM 3022. I had ipw3945 blacklisted on Edgy and had to load it manually post-bootstrap otherwise the boot-up occasionally hung-up. Now, on Feisty, there are not crashed anymore but still the connections are extremely fragile (means: totally unusable). A loaded ipw3945 draws the whole networking unusable even.

---

