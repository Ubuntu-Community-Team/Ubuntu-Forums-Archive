---
title: "Flash 9.0 problem with Browser MMORPG"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by 10Digits on 2009-06-26
Hi,

I am having a recurring problem for some days now, I have installed flash, gnash, swfdec into my browser...through the firefox notifications.The notification bar that pops up...I installed all that and now what I am getting is choppy flash videos and flash games and browser MMORPGS that do not play or do not load. Please help me ..

Thanks in advance....

Waiting for your reply....

---

### Post by lovinglinux on 2009-06-26
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.



---

### Post by 10Digits on 2009-06-26
You are a real angel , you know that???

Thanks it really helped and everything is working smoothly....Thank you...

---

### Post by lovinglinux on 2009-06-26
> **10Digits said:**
> You are a real angel , you know that???

Thanks it really helped and everything is working smoothly....Thank you...

:)

You are welcome.

---

