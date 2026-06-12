---
title: "Random WIFI disconnects and resume after a few mins."
date: 2018-03-06
forum: Networking &amp; Wireless
---

### Post by babuubabuu on 2018-03-06
Hi
I have experienced random WIFI disconnects and resume a few mins later automatically. I don't know why I can't push my wifi information directly here but here it is

[https://paste.ubuntu.com/p/rPFKVtXx8k/](https://paste.ubuntu.com/p/rPFKVtXx8k/)

I have tried 2 of these posts below but none of them work for me.

[https://ubuntuforums.org/showthread.php?t=2343827](https://ubuntuforums.org/showthread.php?t=2343827)

[https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues-with-realtek-adapter](https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues-with-realtek-adapter)

Please help.

---

### Post by kc1di on 2018-03-07
First thing I would try would be to turn power management off (it is currently turned on) This is how to do that. 
[HTML]Open this file with your text editor, let's use nano for example:

sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
By default there is

wifi.powersave = 3
Just change it to a value of 2.

The change will be active upon the next reboot.

The values for the powersave field are:

NM_SETTING_WIRELESS_POWERSAVE_DEFAULT (0): use the default value
NM_SETTING_WIRELESS_POWERSAVE_IGNORE (1): don't touch existing setting
NM_SETTING_WIRELESS_POWERSAVE_DISABLE (2): disable powersave
NM_SETTING_WIRELESS_POWERSAVE_ENABLE (3): enable powersave
[/HTML]

---

### Post by chili555 on 2018-03-07
Most concerning is that you have two SSIDs (routers) with the same name:

```
TVS_5G           <MAC 'TVS_5G' [AC1]>  Infra  40    5200 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2       yes     * 
TVS_5G           <MAC 'TVS_5G' [AC17]>  Infra  149   5745 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no       
```

In your logs, we see the wireless roaming, and thereby disconnecting and re-connecting, among the two looking for a better connection. Reminds me of my old girlfriend!

If you have administrative privileges over these routers, I suggest that you rename them to TVS_5Ga and TVS_5Gb or some such. Connect to TVS_5Ga and I'm confident that all your disconnects will be over.

If you are unable to rename them, then bind Network Manager to the stronger of the two like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Please let us hear back after making these changes. Any improvement?

---

### Post by babuubabuu on 2018-03-08
Wow such a lovely community. I will try these solutions and give the feedback back as soon as possible.
Thank you. I really appreciate it.:D:D:D

---

### Post by babuubabuu on 2018-03-11
It's work like a charm.
My problem was switching between two access points as chili555 said.
Thanks again :grin:

---

