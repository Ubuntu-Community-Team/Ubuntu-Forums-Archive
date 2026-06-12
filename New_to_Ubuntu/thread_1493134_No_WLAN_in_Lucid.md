---
title: "No WLAN in Lucid"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2010-05-25
I did a clean install of Lucid on my old Compaq Deskpro.  Previously, I had Hardy installed and everything was working fine.  Now I cannot enable wireless (it is grayed out).  I have activated the Broadcom legacy driver but there seems to be no way to enable the WIFI.  Is there a command from the terminal to accomplish this.

---

### Post by Ozymandias_117 on 2010-05-25
If it's actually a kernel module problem, this won't help, but the command would be:
```
sudo ifconfig wlan0 up
```

---

### Post by Rex Bouwense on 2010-05-25
Thanks for the reply,  I did that, but I got Unknown error 132.

---

### Post by Ozymandias_117 on 2010-05-25
Post the results of ```
sudo lspci | grep Network
``` and I may be able to help you get the kernel module fixed.

---

### Post by Rex Bouwense on 2010-05-25
As requested:

---

### Post by Ozymandias_117 on 2010-05-25
From what I've found out... That isn't a very Linux friendly card :P What you will probably have to do, is download the windows drivers, use ndiswrapper with the windows drivers and blacklist the native drivers.

You might want to look at:
[http://ubuntuforums.org/showthread.php?t=399820]("http://ubuntuforums.org/showthread.php?t=399820")

If you need help understanding what to do from that, post back with your problem.

---

### Post by Rex Bouwense on 2010-05-28
> **Ozymandias_117 said:**
> From what I've found out... That isn't a very Linux friendly card :P What you will probably have to do, is download the windows drivers, use ndiswrapper with the windows drivers and blacklist the native drivers.

You might want to look at:
[http://ubuntuforums.org/showthread.php?t=399820]("http://ubuntuforums.org/showthread.php?t=399820")

If you need help understanding what to do from that, post back with your problem.

Sorry I took so long to get back here.  Ozymandias, your response struck a memory of activating the wireless in Hardy two years ago.  I dug through my notes and I still had the procedures and the code for activating it using ndiswrapper.  Two years is a long time for me to remember stuff so that is why I write it down or print it out and file it away for future reference.
I will mark this thread as solved and thanks again for your reply.

---

