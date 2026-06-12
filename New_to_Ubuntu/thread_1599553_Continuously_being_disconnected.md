---
title: "Continuously being disconnected"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by jengurule on 2010-10-17
Newly installed Ubuntu 10.10 is continuously disconnecting from the wireless internet.  When I reboot the the computer and it starts back up again, the signal is strong at 100%.  Typically less than five minutes later it will inform me that I am disconnected. 
 
I have reset my wireless router in an attempt to resolve the issue and changed the channel.  Neither one of these tactics resolved the issue.  None of my other computers in the house is having a problem staying connected, and are running off the same wireless connection.
 
Any suggestions?  Thank you for your time.

---

### Post by jengurule on 2010-10-17
Forgot to mention, once I get disconnected, it will not reconnect for me unless I reboot the computer.

---

### Post by Sealbhach on 2010-10-17
This is a common problem, and no doubt will be resolved soon, but you already have a thread open about this: [http://ubuntuforums.org/showthread.php?t=1599382&page=3](http://ubuntuforums.org/showthread.php?t=1599382&page=3)


```
gurule@gurule-Dimension-3000:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by empty_spaces on 2010-10-17
Have you tried changing the wireless security type between WPA2 / WPA / WEP / No security ?

---

### Post by jengurule on 2010-10-17
Okay, it is still disconnectin me; however, I find that I can right click on the recpetion bars on top and click the "enable networking" to wher there is no check mark next to it, then click it again to where it shows a check mark.   Or, I can do the same with the check mark on "enable wireless" It will then reconnect without havign to reboot.
 
This is the message I receive:
"Disconnected- You are now offline"

---

### Post by jengurule on 2010-10-17
Actually my first thread was in regard to the message "use this source" message I have been receivng when I am trying to install applications.  The disconnection was a secondary question.  With all due respect, am I out of ettiquette by creating a new thread with the specific issue?

---

### Post by jengurule on 2010-10-17
Yes, I did try removing the security, and that did not help.  :(  I stuck with WPA though.

---

### Post by jengurule on 2010-10-17
Found this online...think it would work?  Who am I kidding, even if it did work, I am not technically advanced enough to do it...

---

### Post by macem29 on 2010-10-17
have you tried switching the router to another channel ?

---

### Post by jengurule on 2010-10-17
Yes, I did switch to a different channel...
 
On my post above I notice that I failed to include the link
 
[http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html](http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html)

---

### Post by Sealbhach on 2010-10-17
> **jengurule said:**
> Actually my first thread was in regard to the message "use this source" message I have been receivng when I am trying to install applications.  The disconnection was a secondary question.  With all due respect, am I out of ettiquette by creating a new thread with the specific issue?

Sure, that's fine, just mark the old one as solved if you can.

I had a similar issue to you with 10.04, one of the recommendations was to install linux-backports-modules-wireless as suggested in this thread here:

[http://newyork.ubuntuforums.org/showthread.php?p=9239695](http://newyork.ubuntuforums.org/showthread.php?p=9239695)

However, that didn't work for me... I have a different wireless card though... I eventually solved it by purging everything and re-installing.

Before anything, please try this...

Install wicd, it is an alternative to network manager. It's quite easy to use, and will probably manage your connection better.

```
sudo apt-get install wicd
```

.

---

### Post by jengurule on 2010-10-18
I am a newbie here, when you say, "install wicd" then give a code...how am I going about that.  My apologies for the naivety.

---

### Post by jengurule on 2010-10-18
How do I mark the previous thread as "solved"?

---

### Post by Sealbhach on 2010-10-18
> **jengurule said:**
> How do I mark the previous thread as "solved"?

You cando that in Thread Tools I think.

That command I gave, you can run it in the terminal. Or you can install it from the Software Center if you like.

.

---

