---
title: "Wireless joy... and a few questions"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-15
After 3 days of downloading drivers, messing with iwconfig and dhclient and the like, I've finally got my wireless network dongle working (and with it, a massive sense of achievement) but....

... how do I make the settings permanent?

I got everything working with the original XP drivers and ndiswrapper, but I want the wlan0 configuration and driver to be permanent so it's working as soon as I turn on. How do I do this? Can it be done automatically by running something at terminal, or do I need to edit a file, and if so, is there a link to a help page so I know the format of the settings to put in it?

Will I need something to execute ndiswrapper at startup as well?

Help gratefully received - it'll turn me from a happy bunny to a delirious bunny (yes, its that easy!)

---

### Post by Greg2 on 2007-02-15
> **wej1971 said:**
> 
Will I need something to execute ndiswrapper at startup as well?
If you have it all set up and working properly, in terminal do:```
sudo ndiswrapper -m
```
WifiDocs:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
for this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

