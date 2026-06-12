---
title: "lenovo 3000 c200 8922-2FU WLan isuses"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by tfarinella on 2007-09-16
ill start off by saying im not a newbie i just give up ive tried allot on this


1st off theres 3 or 4 different wireless cards that come with my exact model number so that leaves me confused :confused:

so i tried using ndiswrapper with the xp version of the exe from the site i managed to extract the filed and in the driver folder these 2 different .inf files i tried both but the thing is the so called "detected" driver is still in use the whole time

so how am i supposed to do this??? :confused:

---

### Post by noob12 on 2007-09-16
To get the specific device information, use
```

lspci -nn

```
or if it is a usb device use this:
```

lsusb

```
If you need help with specifics, post the output.

Generally **sudo lshw -C network** will show you what driver has claimed the card if any.

If the native driver is claiming the card, you can prevent that driver loading by default by adding a blacklist line for it in **/etc/modprobe.d/blacklist**.

---

### Post by tfarinella on 2007-09-16
ok i gotta login to it to do that (on a dual boot) so give me a sec

no i despise USB internet i think its stupid

im gonna deffinately blacklist that dang native driver thats been driving me nuts

---

### Post by tfarinella on 2007-09-16
ok so output of **sudo lspci -nn** shows that the propper driver to use is** broadcom dell wireless 1390 WLAN**

hope that helps

ps. sorry if i double posted




EDIT....

the command **sudo lshw -C network** shows it is using the same driver as the one listed it the previous command why did i not see this before????

so it has the right driver now how to configure it????

---

### Post by noob12 on 2007-09-17
I'd recommend you follow this thread here:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

