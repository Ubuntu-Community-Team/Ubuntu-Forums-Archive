---
title: "Cannot connect to Wi-fi"
date: 2016-06-06
forum: Networking &amp; Wireless
---

### Post by joe219 on 2016-06-06
Hello,

I'm a new Ubuntu version and i decided to try the latest version of Lubuntu installing it and using dual boot , but i cannot connect to wifi...i've tried going to the alternative drivers enabling my wireless device but it says there are not alternative drivers.

My laptop's model is Acer Extensa 5620z

---

### Post by howefield on 2016-06-06
Thread moved to the "*Networking & Wireless*" forum.

Please read [this sticky thread]("http://ubuntuforums.org/showthread.php?t=370108") and provide the info asked for in the wireless script.

---

### Post by joe219 on 2016-06-06
I'm sorry but how do i exactly ''execute'' this wireless script ? All i see is a big wall of text(which is the script?)...

---

### Post by joe219 on 2016-06-06
I tried following the steps but when i run the script and when i open it again all there is , is something like "####### wireless info start#######" and nothing else happens.

---

### Post by jeremy31 on 2016-06-06
Ok, welcome to the forums
Lets get some basic info from terminal commands
```
lspci -nnk | grep -iA2 net; rfkill list all; nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
```

Use code tags when posting the info as it will preserve the format and prevent smilies, see my signature

---

### Post by RobGoss on 2016-06-06
> **joe219 said:**
> Hello,

I'm a new Ubuntu version and i decided to try the latest version of Lubuntu installing it and using dual boot , but i cannot connect to wifi...i've tried going to the alternative drivers enabling my wireless device but it says there are not alternative drivers.

My laptop's model is Acer Extensa 5620z

Do you have a wired connection that you're able to connect with? if you do open up **Software & Updates** and choose** Additional drivers, **it will look for the necessary drivers that may help you get your WiFi connected

---

