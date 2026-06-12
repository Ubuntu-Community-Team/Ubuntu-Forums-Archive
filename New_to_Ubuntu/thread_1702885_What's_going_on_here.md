---
title: "What's going on here?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-08
Ok, another noob from a Windows background here. Being from a Windows background, I find the following completely ludicrous:

:~$ modinfo rtl8187
ERROR: modinfo: could not open /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko: No such file or directory
:~$ locate rtl8187.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko

What's the reason that I would get a 'no such file' error, then upon locating the file am informed that it is in the location I've just been informed it is not?

---

### Post by uRock on 2011-03-08
With the modinfo command, you need to give it the full directory path.```
modinfo /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko
```

---

### Post by Torp3x on 2011-03-08
Same error occurs. The rtl8187.ko file is not there, but 'locate rtl8187.ko' is pointing me to where the file isn't.

---

### Post by uRock on 2011-03-08
Try adding sudo in front of it. ```
sudo modinfo /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.
```

---

### Post by Torp3x on 2011-03-08
Yeh, I'm using sudo. I've been trying to get aircrack working with my alfa usb with r8187 chip after having 100% success with it while running Backtrack. Ubuntu is less cooperative unfortunately. Is there an idiot's guide somewhere to getting the correct driver installed for this device? Apparently the one installed with Ubuntu 10.10 doesn't work with Aircrack.

---

### Post by uRock on 2011-03-08
This link may be helpful. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

There is a GUI in the Ubuntu Software Center that helps with installing Windows drivers via NDISWapper.

---

### Post by Torp3x on 2011-03-08
Thanks, it's not a windows driver though. Apparently the driver I need is the ieee80211 rtl8187 version. The driver installed with Ubuntu is the mac80211 version. This one needs to be removed or blacklisted before the ieee80211 will work properly. Trouble is, I removed rtl8187 but terminal still thinks it's there, as per my first post. 

Now for all intents and puropses, rtl8187.ko is gone but I can't get ieee80211 rtl8187.ko sorted because my system - somehow seems to think that the original rtl8187.ko is still there, even though I can't find it.

---

### Post by uRock on 2011-03-08
You may also try installing linux-firmware-nonfree package. That worked for my wireless nic.

---

