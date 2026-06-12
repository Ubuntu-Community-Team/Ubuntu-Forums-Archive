---
title: "Why does rebooting nuke my wireless connection?"
date: 2016-06-05
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-06-05
Hi all, I'm the same person in these two threads: [http://ubuntuforums.org/showthread.php?t=2316533](http://ubuntuforums.org/showthread.php?t=2316533) and [http://ubuntuforums.org/showthread.php?t=2320324](http://ubuntuforums.org/showthread.php?t=2320324) &#8212; my Acer laptop running Ubuntu really didn't want to get wi-fi but ultimately had to due to the efforts of many kind people.

What happens now is this: sometimes my computer crashes, and I do sudo reboot or am forced to hold the power button, but when I come back, my wireless doesn't work again. I go through the steps in the previous solutions and get back online in a while generally, although the last time there was a new error and I relied on a hint [here]("http://askubuntu.com/questions/607707/ath10k-installation") to rename firmware-4.bin as firmware-5.bin.

I've had other functionality lost after a restart too, including lightdm and then the GUI, neither of which I've gotten back yet. It's really aggravating.

**1. Why would it do this?**

**2. Is there some way to stop it? I.e., how can reboot safely if things start crashing, as they always do?**

---

### Post by jeremy31 on 2016-06-05
Ubuntu 16.04 may work better for you.  I know the wifi is supported in the 4.4 kernel but firmware is available with ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

You may find answers to why it crashes in the Hardware forum.  There is likely some errors that can be found looking in /var/log/dmesg.0 or even some of the archived dmesg files

---

