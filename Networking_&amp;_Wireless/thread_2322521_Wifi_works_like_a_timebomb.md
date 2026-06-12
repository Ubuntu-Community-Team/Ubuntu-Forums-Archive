---
title: "Wifi works like a timebomb"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by B._Bishop on 2016-04-28
Hi I'm running 15.10 on a 2in1 Acer switch laptop which was not easy to install, but with a lot of help from this forum I managed to do so. Once everything was installed, everything worked well enough for me to work on this machine and do my basic tasks, with just sound and touchscreen not working. Also Ubuntu recognized my internal Intel wifi adapter and with it, recognized wifi networks and connected to them, but wasn't able to actually send data over it.

I use a realtek 11n usb adapter, which worked very well at first. I thought why not disable the onboard adapter since i don't use it? I did and still no problem, can't find it anywhere within Ubuntu to switch it back on though.

Since the updates a while back, I can still connect to any network, but after a while it simply doesn't send or receive any data anymore. It still shows to be connected but no sites are found or data down or uploaded.

No consistency in amount of time or data. When downloading using torrents, this problem appears a long sooner than without.

disabling network connections and re-enabling doesn't work, I really have to restart the whole machine in order to solve it for another minute.

If anyone could please help me solve this problem I would be ever so grateful! Thank you very much in advance!

ps I have the adapter connected in a usb hub, tried with another hub, and without a hub at all, doesn't make a difference. It heats up but reboot and it works again, so probably not a physical problem...

---

### Post by gnusci on 2016-05-01
I had a similar problem with a realtek, it did only work with wicd:

[https://launchpad.net/wicd](https://launchpad.net/wicd)

---

### Post by B._Bishop on 2016-05-04
Thank you very much!
Sorry for the late reply, but i've been travelling. I have just installed it and hope this will solve the problem. Thank you!

---

### Post by chili555 on 2016-05-04
Do you think you've fully trouble-shot the Intel? I have or have had 3-4 and they work perfectly.

---

### Post by B._Bishop on 2016-05-04
Oh no, not at all, but I have just reinstalled ubuntu after more than ten years of using windows, on a machine that even expert linux users have trouble with installing.
I still have no sound installed on it and the touch screen doesnt work properly, but I am glad that I'm not running Windows 10 anymore...

---

### Post by chili555 on 2016-05-04
If you'd like to troubleshoot the Intel, detach the USB wireless, reboot and then run and post the wireless_script. [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) Be certain that, before you run the script, the wireless key combination or switch is set to enable wireless.

I'm fairly confident we can get it going.

---

