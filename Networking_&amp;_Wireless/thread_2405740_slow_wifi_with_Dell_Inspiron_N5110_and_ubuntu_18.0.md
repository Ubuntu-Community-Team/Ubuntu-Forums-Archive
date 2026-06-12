---
title: "slow wifi with Dell Inspiron N5110 and ubuntu 18.04.1"
date: 2018-11-10
forum: Networking &amp; Wireless
---

### Post by loucat on 2018-11-10
Hello!

I got a fiber optics network some months ago with 100 Mbps and I've noticed soon that the work macbook could get almost at that speed with wifi, but my Dell was much slower, like maximum 40Mbps.
At the time I had ubuntu 16 and windows 7 and it seemed they both got similar speed (with speedtest.net) so I assumed it was the wireless adapter and I bought an external usb one by tp-link.
Apart from the trouble of installing it in linux and disabling the embedded adapter, it seemed slightly better for a while.

For various reasons I then upgraded to ubuntu 18.04 and also I think my usb wifi adapter is not working anymore :( so I'm back to square 1, and also it seems in windows the speed is actually a bit better (like 40Mbps versus 25) which is really annoying :)

Do you think there's something I can do about it, or should I just buy a new laptop?
It would also be good to understand if this usb adapter is still working, it did something on windows switching to a new usb port, and then "disappeared" again.

wireless-info script report: [http://termbin.com/6e7o](http://termbin.com/6e7o)

Thanks in advance!

lou

---

### Post by jeremy31 on 2018-11-10
In terminal just do ```
cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by Autodave on 2018-11-10
Upgrading one release to another release rarely goes well and it usually takes a lot more time to fix things that got "broken" in the upgrade.  I always have at least 2 backups of my system and when the time comes to a new LTS release, I always do a clean install.

---

### Post by loucat on 2018-11-10
thanks @jeremy31! [http://termbin.com/6e7o](http://termbin.com/6e7o)

---

### Post by loucat on 2018-11-10
> **Autodave said:**
> Upgrading one release to another release rarely goes well and it usually takes a lot more time to fix things that got "broken" in the upgrade.  I always have at least 2 backups of my system and when the time comes to a new LTS release, I always do a clean install.

I don't think I would ever upgrade if I had to always backup and clean install :)
anyway the problems were pre-existent, not sure they're relative to the version, I may have lost the configuration though.
I should have written this thread before...

---

### Post by jeremy31 on 2018-11-10
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
You need to use the first command to disable Network Managers ability to enable wifi power management, you should change the wifi router encryption to WPA2 only and move it to channel 6 as it is now on a crowded channel 1

---

### Post by loucat on 2018-11-10
> **jeremy31 said:**
> See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
You need to use the first command to disable Network Managers ability to enable wifi power management, you should change the wifi router encryption to WPA2 only and move it to channel 6 as it is now on a crowded channel 1

Thanks so much for helping!
I've applied the changes, and although it feels quicker when loading web pages, if I use speedtest the results are similar or slightly worse. 
Is there anything else I can do?

---

### Post by jeremy31 on 2018-11-10
Run the script again, let's see if anything stands out

---

### Post by loucat on 2018-11-10
> **jeremy31 said:**
> Run the script again, let's see if anything stands out

I've run it again and noticed the channel hadn't changed, so I did that and still speedtest is not going well :(
This is the latest wireless-info after all the changes: [http://termbin.com/841z](http://termbin.com/841z)

Thanks!

---

### Post by jeremy31 on 2018-11-10
Do ```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by loucat on 2018-11-10
> **jeremy31 said:**
> Do ```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

done it. 
In terms of speedtest, it improved respect to the last run but I guess there are many factors in play.
It's 45Mbps now and it was 33Mbps before so it seems a lot, but overall today it spanned from 28 to 46 with up and downs. Still quite far from the 100Mps :(
Is the link speed found in the wifi network settings important? I can see it's 72 now but it varies.

---

