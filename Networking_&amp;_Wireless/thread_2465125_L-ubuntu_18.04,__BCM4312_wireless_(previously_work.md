---
title: "L-ubuntu 18.04,  BCM4312: wireless (previously working) failed"
date: 2021-07-22
forum: Networking &amp; Wireless
---

### Post by mringer on 2021-07-22
The wireless was running for several months & suddenly stopped. AFAIK I
did what the instructions say to install a BCM 4312 card. I do not know what 
I have done to cause this. I have tried to paste the  wireless-info  text here.

[HTML]https://pastebin.ubuntu.com/p/QDxZXxwwRy/[/HTML]

My apologies if I should have posted the    .tar.gz    file. But  pastebin
did not offer this format. As instructed, I first did 

```
apt update
apt dist-upgrade
```

The symptoms are: if I boot my PC non-wired, I see the turning wheel icon for a few
minutes, then it stops & says "not connected". Then usually the wheel restarts & fails
again. If I boot wired, it first connects successfully, but then sometimes the wheel
reappears & it tries to connect wireless. This continues until I click on the wheel & 
tell it to disconnect the wireless. Also I think it sometimes misbehaves in different ways.

Our router is    aa.net.uk   17973

Please any advice? Thank you.

---

### Post by guiverc on 2021-07-22
Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that is now EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

A recent Ubuntu Weekly Newsletter
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)) highlighted *flavors* are now EOL.

Not all *flavors* gave EOL notices, but if you look they had dates provided already. eg. Xubuntu mentioned on [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) that EOL was 29-April-2021 (more accurately than Lubuntu's April-2021).

---

