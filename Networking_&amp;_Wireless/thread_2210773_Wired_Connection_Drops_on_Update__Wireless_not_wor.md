---
title: "Wired Connection Drops on Update / Wireless not working at all"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by dave106 on 2014-03-12
Hello,

I am brand new to Ubuntu / Linux and this forum.  I hope someone can help me with this weird issue:

I recently installed 13.10 on my Dell Inspiron B130 Laptop after upgrading RAM to 2GB.  Upon installation, I noticed that the wireless connection was not working so I used wired.  As it was installing, I kept seeing the "wired internet connection disconnected" notification.  I just ignored it and thought it was normal because the install seemed to keep going ok.  Now, the wireless still doesn't work and the wired drops off whenever I try to do any Ubuntu Updates.  I can use Firefox, and used testmy.net to test the wired connection and it was fine.  But as soon as I try to do ANY kind of update (system, drivers, etc.) the wired connection disconnects during the update process.  Ubuntu One works, Firefox works, basically anything that uses internet works except for Ubuntu updates and driver downloads.  HELP!:?:

EDIT- Sorry, but I wanted to make it clear that my Cable modem / and WiFi Router have nothing to do with this issue.  The WiFi is working on all other devices (phones, Surface) and ethernet is working fine on my PC.

---

### Post by varunendra on 2014-03-14
Welcome to Ubuntu Forums Dave!

For wireless issue, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

For the Ethernet, please post the output of -
```
sudo lshw -C network -sanitize
ifconfig
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

