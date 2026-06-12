---
title: "No wifi"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by dannyb7878 on 2014-02-21
Hi, 

I just install Ubuntu 13.10 on my computer, and my wifi doesn't work at all. It says that the wifi is disabled by hardware switch and on the rfkill command it shows that it's hard blocked: 

```
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

I've searched a lot about the issue as it seems quite popular and i've tried different soultion yet none of them worked. 

Thanks.

---

### Post by varunendra on 2014-02-21
Welcome to the forums dannyb7878 !

> **dannyb7878 said:**
> 
```
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
....
6: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
```

I've searched a lot about the issue as it seems quite popular and i've tried different soultion yet none of them worked. 

Thanks.

Have you tried this one yet - [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558) ??
I'm pretty sure not, so please try the suggestion, and let us have your feedback.

---

### Post by dannyb7878 on 2014-02-23
Thank you it fixed the problem.

---

### Post by varunendra on 2014-02-23
Glad it did. Please consider adding yourself to the Affected users list on the bug report page, if you haven't already. :)

---

