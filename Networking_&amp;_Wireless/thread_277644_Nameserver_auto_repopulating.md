---
title: "Nameserver auto repopulating"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by jpatt on 2006-10-14
I had  tried a using an open dns nameserver. Unfortunately, I lost the ability to connect to my local LAN. I did a clean re-installation ubuntu 6.0.6 and got my original IP restored. Out of the blue, the open dns number kept returning. I made changes to the network section without success. I made changes tat the file level without success. I can delete those numbers but they keep reappearing. I never even put the numbers in, they just magically reappear. any insight?

---

### Post by adwait on 2006-10-15
IF you are talking about DNS servers popping up into your resulv.conf, you could just make the file readonly by using
```
sudo chattr +i /etc/resolv.conf
```

---

### Post by handy on 2006-10-16
**Option 3**, of **Post 13** in [this thread]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2"), works beautifuly for me...

---

