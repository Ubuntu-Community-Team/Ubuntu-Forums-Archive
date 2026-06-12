---
title: "internet rate"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by jtmedin on 2009-10-30
How does one find the current rate of the internet connection? TIA

---

### Post by bkratz on 2009-10-30
> **jtmedin said:**
> How does one find the current rate of the internet connection? TIA

If you are referring to your connection rate go to 

[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by jtmedin on 2009-10-31
No i was thinking of something like windows status. I showes the packet count in real time so you get an idea of the data flow.

---

### Post by XCan on 2009-10-31
You can have a look in the system-monitor for the bw you are currently using under the "Resources tab". If you want the packet rate you can see it in vnstat by typing ```
 vnstat -l 
```

---

### Post by t0p on 2009-10-31
**System > Administration > System Monitor > Resources**

---

### Post by Viva on 2009-11-02
Install the [netspeed]("apt:netspeed") applet and add it to the gnome-panel.

---

