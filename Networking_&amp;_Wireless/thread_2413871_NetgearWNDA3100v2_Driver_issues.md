---
title: "NetgearWNDA3100v2 Driver issues"
date: 2019-03-03
forum: Networking &amp; Wireless
---

### Post by micheat1023 on 2019-03-03
Hello, this is my first post on the forum so if I'm violating any rules please feel free to remove or relocate the thread. Anyways, I have a WNDA3100v2 N-Wireless adapter that I have used for several years since before I built my first computer and I'm really happy with the performance of it and don't wish to buy a new one. I was aware that this device has some driver trouble on Linux, but I found a couple of solutions online, however, they were a little out of date and didn't end up working out for me. I'm using Ubuntu 18.04 tried using ndiswrapper and the driver file provided here: <a href="https://ubuntuforums.org/showthread.php?t=2052594" target="_blank">https://ubuntuforums.org/showthread.php?t=2052594</a> I followed the first few suggestions and steps the users did there, but still couldn't get it working. Please, any help would be greatly appreciated! Thanks in advance!

---

### Post by chili555 on 2019-03-03
If you get this or any other device working with ndiswrapper in any modern, not end-of-life kernel version, gcc version, etc., I shall be quite surprised.

Are there any clues here?```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by micheat1023 on 2019-03-03
[ATTACH=CONFIG]282681[/ATTACH][ATTACH=CONFIG]282682[/ATTACH]These are the results of the commands. It seems like the driver is installed and recognized the device, but just isn't initializing?

---

### Post by chili555 on 2019-03-03
I have no other suggestions. You have an XP-era driver trying to work in a much newer kernel and gcc version. ndiswrapper hasn't been well-supported for many years. Sorry.

---

### Post by micheat1023 on 2019-03-03
I figured :( well thanks anyways for your help. Fortunately my dads friend lent me an old wifi adapter that I can use for extended terms

---

