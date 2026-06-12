---
title: "Help! Cannot connect to wifi."
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-01-31
I am currently running Ubuntu 10.10. It's been working great for 3 months. No problems at all. 

Suddenly, as I was working on my homework an hour ago, my internet just... died. Now I can't do my homework.

What could be the problem? I CANNOT get it to connect to my wifi network, even though the WPA2 key is correct. This has never happened before! Why did it decide to die on me?

I'm posting this from my wife's Mac, which can access the internet on our router, so I know it's not that. Please help me.

I can see the network, just can't get on.

---

### Post by squenson on 2011-01-31
Try to change the password in the router and see if you can connect.

Then I would reboot the wi-fi router to the factory defaults (after saving the values of the current parameters on a piece of paper), in order to see if it works. Then I would create a password and try the connection.

---

### Post by libssd on 2011-01-31
Try deleting the config file for your WiFi connection, then re-connect. I've been experiencing what sounds a lot like your problem recently due to a flaky Apple Airport Express. The key to figuring out that the problem exists with the AAE, rather than with the computer is that the same thing was happening on two different computers.

---

### Post by Ranger_Joe on 2011-01-31
Ok,
I'm going to call this one solved. I wasn't going to reset the router because the Mac in the home could connect just fine. So, I thought there's no way that could be the problem.

Turns out, it was. Once I reset the router and rebooted my computer, I was able to connect via wifi network again. I guess it just got a little buggy for a second.

---

### Post by squenson on 2011-01-31
It was a nice trick to avoid doing your homework... :lolflag:

---

### Post by libssd on 2011-01-31
Yup, I've been unplugging the damned AAE a lot lately. I can see no pattern to why it flakes out, but it's been happening more frequently lately.

It's an old model (only 802.1b/g), so I'm going to try replacing it with a Cisco-Linksys  WRT400N, which not only supports 802.1N, but also has two separate radios. I'm hoping for both better reliability and throughput. If not, back to Amazon it goes.

---

