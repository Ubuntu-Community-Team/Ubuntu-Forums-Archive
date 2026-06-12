---
title: "Access Windows Shares"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by The Anomaly on 2007-03-17
Greetings,


I'm sure this has been posted multiple times before, however my searches didn't turn up the right thing. So, if you'll excuse my probable repetition...I need some help with this.

I have a network of three Windows XP run computers. I have this computer, which is running Ubuntu, set up on the network and I can access the internet. However, I'd like to access the shared documents on the Windows computers, and the Windows computers to access my computer. This is especially important because my computer is the computer used for all the back ups. It's a very basic network I have going...no DHCP, just a few computers connected with Cat 5 to a linksys switch.

How do I set this up? I mean, how do I share folders on this system so that they are accessible on the Windows computers and vice versa? This is about as basic as it gets, I'm sure...but I can't figure it out.


Thanks,
George C. Linderman

---

### Post by kidders on 2007-03-17
Hi there,

> **The Anomaly said:**
> I'm sure this has been posted multiple times before, however my searches didn't turn up the right thing.You're right... Windows filesharing is a common requirement. Of course, if you don't already know what to look for, you'd never find it.

The name of the application you want is **Samba**.

---

### Post by dbott67 on 2007-03-17
This document should get you going:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Dave

---

