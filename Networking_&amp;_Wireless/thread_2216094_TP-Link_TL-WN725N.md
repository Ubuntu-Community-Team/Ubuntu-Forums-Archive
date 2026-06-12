---
title: "TP-Link TL-WN725N"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by Xentime on 2014-04-10
**I'm very new to using USB-based network adaptors so please excuse my ignorance in advanced.**

I recently purchased the listed adapter and plugged it into the computer but there were no visible responses to the new device. I searched the forum for help but certain bits of information didn't match-up so I've been a bit hesitant in applying any suggested fixes. I understand that the information below it what is usually requested. Help would be much appreciated.

```

lsusb
ID 0bda:8179 Realtek Semiconductor Corp.

```

```

uname -r
3.11.0-19-generic

```

```

lsb_release -d
Ubuntu 12.04.4 LTS

```

---

### Post by drpjkurian on 2014-04-10
Is "ID 0bda:8179 Realtek Semiconductor Corp." the only output after entering lsusb in terminal?

---

### Post by Xentime on 2014-04-10
The full results of the command are as follows:

```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 003: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1532:0034 Razer USA, Ltd 
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0c45:64ad Microdia 

```

---

### Post by varunendra on 2014-04-10
To give us a wider picture of the situation, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Xentime on 2014-04-10
Thanks in advanced for the assistance. I followed your script guide and posted the report on the Ubuntu Pastebin. Here is the link:

[http://pastebin.ubuntu.com/7232395/](http://pastebin.ubuntu.com/7232395/)

---

### Post by chili555 on 2014-04-10
I believe my esteemed colleague varunendra will refer you here: [http://forums.linuxmint.com/viewtopic.php?f=53&p=845420](http://forums.linuxmint.com/viewtopic.php?f=53&p=845420)

You have the same device and require the same fix. You probably also need:```
sudo apt-get install linux-headers-generic build-essential
```

---

### Post by Xentime on 2014-04-10
Ooh my god, thanks so much that did the trick!! Thank you all for the assistance. :KS

For future notice if anyone runs into the same problem, it was fixed by doing the following:

1. Open up the Terminal application. (Ctrl+Alt+T)

2. Enter the following (line-by-line):
```

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo modprobe 8188eu

```

I'm using Ubuntu 12.04 LTS on an Inspiron 15 w/ Intel i3 (Built in Q1/2014).


Again, thanks to you all! Truely appreciate it!

---

### Post by chili555 on 2014-04-10
Glad it's working. Don't skip the last post about re-compiling when there is a kernel update.

Please use thread tools at the top to mark Solved. Thanks to Varun who did all the hard work so I could swoop in heroically and steal the glory!

---

### Post by varunendra on 2014-04-10
I doubt I would have gotten time to even look up that driver before Sunday, and regardless of what you say, Dr. Chili, I bet you already guessed that. :P

*[Personal Note to Dr. Chili : Another hectic day about to begin, with nothing substantial to report yet. Thanks you so very much for being my guardian angel all the way and that of the posters who are stuck with me. :)]*

---

### Post by Xentime on 2014-04-11
> **chili555 said:**
> Don't skip the last post about re-compiling when there is a kernel update.

Aahh, thanks for the pointer. I very much skipped that bit of information in all honesty. xD This will save me a future headache. Hahaha!

---

### Post by chili555 on 2014-04-11
> **Xentime said:**
> Aahh, thanks for the pointer. I very much skipped that bit of information in all honesty. xD This will save me a future headache. Hahaha!Sometimes I read between the lines. Sometimes I scare myself! I'm glad you are all set.

---

