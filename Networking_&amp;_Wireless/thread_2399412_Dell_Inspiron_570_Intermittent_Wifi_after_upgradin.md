---
title: "Dell Inspiron 570 Intermittent Wifi after upgrading from 14.04-&gt;18.04"
date: 2018-08-24
forum: Networking &amp; Wireless
---

### Post by planeoldalex on 2018-08-24
Hi, I'm a relatively new Linux user with an old Dell Inspiron 570. I've had it for about a year, running 14.04, and haven't had a single issue. But a few days ago, I learned there were new versions of Ubuntu (I'm not on top of that stuff) and in one night, updated to 16.04, then 18.04. Now the wifi will only connect intermittently. If I restart the computer, it will be able to connect to my router or my phone's hotspot for around 5 minutes before it disconnects with the "Connection Failed message". Then it will keep trying and trying to connect to no avail. If I then turn off wifi for ~10min, it will be able to connect again for about 30sec, before failing with the same message. It has a Linksys WMP54G PCI adapter that came with the computer. I confirmed that both the adapter and the antenna were both seated correctly. The router is about 20 feet away through two walls, but again, it worked perfectly in this location when I was running 14.04. I also attached the "wireless-info.txt" file that I made from <a href="https://ubuntuforums.org/showthread.php?t=370108" target="_blank">https://ubuntuforums.org/showthread.php?t=370108</a><br>
<br>
I'm just not really sure where to start here, so any help would be appreciated! Thanks a ton!<br>
<br>
Alex H

---

### Post by praseodym on 2018-08-25
Please check
```

sudo iwconfig wlan0 power off
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot. Also check changing the channel in your router fixed to "1"

---

### Post by planeoldalex on 2018-08-26
Alright, that didn't do anything. What was it supposed to do?

Also, my roommate set up the router last year and changed the admin password and forgot it, so I don't think I can change any settings on the router. I'll keep trying though.

---

### Post by planeoldalex on 2018-08-26
I got back into the router settings and I changed the channel from auto-select to 1, but I still have the same issue. Are there other settings that you know should be changed?
Thanks,
Alex

---

### Post by Autodave on 2018-08-27
Let's try this:  Download 18.04 and either burn it as an .iso to a DVD or as an .iso to a USB stick and boot from you install medium. Choose Try Ubuntu when you get to that screen. Now, see if your wifi functions normally.  If it does, I would suggest that you back up EVERYTHING that you don't want to lose and do a clean install of 18.04.

I rarely find that an upgrade goes well. And you did an upgrade through a long series of other upgrades.  My guess is that a clean install will take care of your problem.

---

### Post by planeoldalex on 2018-08-27
I put ubuntu on a flash drive and did the "try ubuntu" option, but the wifi still didn't work. I'm really not sure what's going on here.

---

### Post by planeoldalex on 2018-09-26
If anyone comes to this thread later, I couldn't solve it. My (pretty uneducated guess) is that the wifi card/driver just doesn't work with anything newer than 14.04. I reverted back to 14.04 and it's worked perfectly since. The computer is nearly seven years old now, so I'm not too surprised.

---

