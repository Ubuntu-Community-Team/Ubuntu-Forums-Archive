---
title: "Ubuntu 17 WiFi slower than windows 10 (dual boot)"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by yanbanan123 on 2017-10-27
So I finally dual booted Ubuntu 17 with Windows 10, and I have noticed that the WiFi is allot slower on Ubuntu than on Windows. I have tried allot of "solutions that helped others but did not help me.

I can provide any info you need.

[http://paste.ubuntu.com/25832779/](http://paste.ubuntu.com/25832779/)

Speed tests:
Windows10: [http://beta.speedtest.net/result/6745876130](http://beta.speedtest.net/result/6745876130) (my room "above the room with the router")
Ubuntu17: [http://beta.speedtest.net/result/6745990830](http://beta.speedtest.net/result/6745990830) (in the same room with the router "didn't even load in my room")

---

### Post by Autodave on 2017-10-27
Please go to the sticky note (right above where you have your post): [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and do what it says and report back here. The3re are sooooo many wifi issues and so many wifi adapters, the only way someone will be able to assist you is with the information you need to provide according to that post.

---

### Post by yanbanan123 on 2017-10-27
There i added the paste.

---

### Post by yanbanan123 on 2017-10-28
I added speed tests

---

### Post by yanbanan123 on 2017-10-28
> **Autodave said:**
> Please go to the sticky note (right above where you have your post): [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and do what it says and report back here. The3re are sooooo many wifi issues and so many wifi adapters, the only way someone will be able to assist you is with the information you need to provide according to that post.

All done

---

### Post by wildmanne39 on 2017-10-28
Please do:
```
echo "blacklist rtl8723_common" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot is that better?

---

### Post by yanbanan123 on 2017-11-01
> **wildmanne39 said:**
> Please do:
```
echo "blacklist rtl8723_common" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot is that better?

It seemed to help at first. I could connect from my room but the internet was really slow. Now I can barely connect and internet bacicly doesn't work

---

### Post by jeremy31 on 2017-11-01
Also see if [https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389](https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389)
HP has been using rtl8723be chips with ona antenna

---

### Post by yanbanan123 on 2017-11-01
> **jeremy31 said:**
> Also see if [https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389](https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389)
HP has been using rtl8723be chips with ona antenna

Thank you so much! It works and i can see all the networks that i was able to see on windows! Wifi in my room on Ubuntu is sooo fast like thank you so much!!

---

