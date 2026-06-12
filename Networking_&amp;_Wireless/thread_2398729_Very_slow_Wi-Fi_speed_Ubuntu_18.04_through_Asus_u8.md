---
title: "Very slow Wi-Fi speed Ubuntu 18.04 through Asus u8b-n13"
date: 2018-08-16
forum: Networking &amp; Wireless
---

### Post by sinsoff on 2018-08-16
Previously, I've got windows on my PC and the speed was around 2 Mb/s through Wi-Fi.

Now, the speed is around 100-200 Kb/s. 

Firstly, I've tried every solution from this page [https://itsfoss.com/speed-up-slow-wi...ection-ubuntu/](https://itsfoss.com/speed-up-slow-wi...ection-ubuntu/) which could be connected with my problem. However, nothing has helped. 

I should mention, that it is not only about network speed. I've got the similar problem with connecting to my Wi-Fi router. 

I've checked some threads, but can't find a solution. Could you help me?

Below is the result of wireless-info script.

[https://pastebin.com/fWvDE1Yx](https://pastebin.com/fWvDE1Yx)

UPD.
I've used my phone as hotspot and the speed seems to be good. So, the issue should be caused by wifi router. I can't bring my PC closer to router, but with Windows all was good.

---

### Post by a2aaron on 2018-08-16
I had a similar problem to you. I have not fixed my internet fully, but perhaps my thread can help?

[https://ubuntuforums.org/showthread.php?t=2398415](https://ubuntuforums.org/showthread.php?t=2398415)

I found that adding ```

options iwlwifi 11n_disable = 1
```

[FONT=arial]to /etc/modprobe.d/iwlwifi.conf helped bring my internet from 0.5 Mbps to around 10 Mbps.



If you can, try hooking up an Ethernet cable to your computer and router. If you still get poor speeds perhaps it is a router based issue?

Alternatively, see if another network has better speeds (a non-hotspot network). If the speed improves you might have some sort of Quality of Service feature on your router that you can investigate.
[/FONT]

---

### Post by sinsoff on 2018-08-17
Thank you so much @a2aaron. Now, I have got the expected speed. It's weird that after almost 10 years of 802.11n existence we've got this problem.

---

### Post by huanshutan on 2019-02-25
I am not sure if you have found the solution. But I can share my solution here.....
Go to check which wifi channel your pc is connecting, 5GHz or 2.4GHz.
sudo iwlist channel
If it's 5GHz, change it to 2.4GHz.
I can set different wifi names for 5GHz and 2.4GHz in my router, which make me easy to connect 2.4GHz wifi channel. And then my wifi speed immediately jumps to 83 Mbps from 1 Mbps!
If your router can do this, you have to find a way to force your pc to connect to 2.4GHz wifi channel.

---

