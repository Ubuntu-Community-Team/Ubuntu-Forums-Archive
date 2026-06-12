---
title: "B43 Firmware Unistalled itself?!"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by FZag on 2014-09-11
Hello guys,

I'm creating this topic mainly out of curiosity for what I experienced today. I take my laptop pretty much everywhere, and since I installed Ubuntu 14.04 LTS my Wi-Fi always worked beautifully well. Today at work, however, my computer suddenly lost access to the Wi-Fi in the middle of the afternoon - it was not that the computer was trying to connect to a network and for some reason couldn't, what was really happening was that my Wi-Fi connectivity had completely disappeared and the computer couldn't even see the numerous Wi-Fi networks in the building. As every good naive user, I restarted the computer with the hope that it would solve the problem, and surprise surprise: I see some warning messages on start-up telling me that the system could not find the firmwares B43!

Happily enough I was able to get a wired connection and reinstall the firmwares which decided to "go on vacation"... Now, could someone please explain to me how the hell this happnened? It really made me start thinking about how much I can trust the Ubuntu system since firmware installations disappear suddenly! By the way, this whole situations happened after the system updated, but I have no proof that these events are linked.

Best,

---

### Post by wildmanne39 on 2014-09-11
Broadcom had lssues with it being included in linux-firmware-nonfree so it had to be removed.

---

### Post by varunendra on 2014-09-11
It seems that you, like hundreds of others here (oh, we suggested them so :() installed the firmware with "linux-firmware-nonfree" package. If so, the disappearance of firmware was an intentional and unfortunate decision. Please see this bug report : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882)

Even if you installed the "linux-firmware-nonfree" package for some other purpose, its update may cause the entire /lib/firmware/b43 directory to disappear. But I'm not very sure about that.

Right now, the new (actually the 'Old') method to install the b43 firmware is (with a wired or some other internet connection) -
```
sudo apt-get install firmware-b43-installer
```
..or 'firmware-b43legacy-installer' in some cases (see the sticky).

Or, for systems with no working internet connection, it must be installed manually, something like this : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

Hope it answers your curiosity, and gives you an idea what to do next time.

---

### Post by FZag on 2014-09-11
I see! Thanks for your replies, guys. I guess I understand the problem a little better now. :)

Best,

---

### Post by varunendra on 2014-09-11
Please mark the thread as [SOLVED] using "Thread Tools" link above the top post if you think you got the answer. Thanks!

---

