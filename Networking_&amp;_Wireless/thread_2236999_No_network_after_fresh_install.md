---
title: "No network after fresh install"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by newholm1 on 2014-07-30
Hi there. I reinstalled my OS last night, and when I had finished the network had disappeared. I then installed another version, and the problem remains. My router is fully functional, and I accessed it using my netbook, which is still receiving a signal. The network cannot see my desktop, and all the network menus are blank. I have been using 12.10 but it is no longer supported, so I would like to end up with 12.04 or 14.04 for long term support. Please help!

---

### Post by varunendra on 2014-07-30
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by newholm1 on 2014-07-30
Thanks, will do that after work. It's not a wireless connection however, it's an ethernet.

---

### Post by varunendra on 2014-07-30
> **newholm1 said:**
> It's not a wireless connection however, it's an ethernet.

The script can still provide a lot of useful info. But to save you the trouble of reading long instructions, please post the outputs of the following commands instead -
```
uname -mr
sudo lshw -numeric -C network
ifconfig -a
nm-tool
lsmod
```

..within 'Code' tags as recommended in my first post please. :)

---

### Post by newholm1 on 2014-07-31
Ah. In an embarrassing "call in the engineer, then everything works fine" type way, everything seems to be working fine now. Guess it must have been teething troubles! I've installed 14.04 now, and all seems well. Thank you for your time and advice!

---

### Post by varunendra on 2014-07-31
Congrats! And thanks for saving 'Me' the trouble of guessing and posting.. :p

---

