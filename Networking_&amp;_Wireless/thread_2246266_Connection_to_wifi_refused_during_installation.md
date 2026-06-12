---
title: "Connection to wifi refused during installation"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by Cubytus on 2014-09-29
Hello community, 

yesterday I wanted to reinstall Ubuntu Server 12.04 on a laptop. During installation, it asked me to select the primary interface, and for flexibility reasons, I selected wlan0. Then I entered the SSID to join, WPA-type security and typed the password, but it refused to connect, sending me back instead to the SSID question.

To put it in context, the machine has no trouble with Ubuntu Desktop, and uses a software RF switch (Bluetooth and wifi), which I leave on all the time, and is enabled from the BIOS. Nevertheless, during the installation, the wifi LED is off, which isn't abnormal by itself as Linux makes it flash on only when there's activity. Even with some Linux experience, I have no clue what is going wrong.

Any insight on this issue?

---

### Post by jeremy31 on 2014-09-29
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Follow the instructions to download and run the wireless script, you will likely have to use the without internet instructions

---

### Post by Cubytus on 2014-09-30
Thanks for the quick reply, but the post you pointed me to refers to known-problematic wifi chips. This machine uses a rather standard Ralink RT2790 that never had any issue with Desktop version of Ubuntu 12.04 before I upgraded it to 14.04, even during installation.

I read
[http://pastebin.com/y3zengxE]("http://pastebin.com/y3zengxE")
[http://unix.stackexchange.com/questions/116914/what-driver-is-being-used-by-a-wireless-usb-adapter]("http://unix.stackexchange.com/questions/116914/what-driver-is-being-used-by-a-wireless-usb-adapter")
[http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%282790%29]("http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%282790%29")

And *lsmod* in Desktop version does show *rt2800* is being used. Is the driver absent from Ubuntu Server at installation time?

---

### Post by jeremy31 on 2014-09-30
> **Cubytus said:**
> Thanks for the quick reply, but the post you pointed me to refers to known-problematic wifi chips. This machine uses a rather standard Ralink RT2790 that never had any issue with Desktop version of Ubuntu 12.04 before I upgraded it to 14.04, even during installation.

I read
[http://pastebin.com/y3zengxE](http://pastebin.com/y3zengxE)
[http://unix.stackexchange.com/questions/116914/what-driver-is-being-used-by-a-wireless-usb-adapter](http://unix.stackexchange.com/questions/116914/what-driver-is-being-used-by-a-wireless-usb-adapter)
[http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%282790%29](http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%282790%29)

And *lsmod* in Desktop version does show *rt2800* is being used. Is the driver absent from Ubuntu Server at installation time?

Actually the post contained this ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

[/FONT][/COLOR]Please run in terminal and attach the resulting wireless-info.txt or tar.gz file

---

### Post by Cubytus on 2014-10-02
Well that would be hard now. For whatever mysterious reason, on second power-up, wifi finally connected without a hitch. Computer science surely isn't hard science.

Can't diagnose.

---

