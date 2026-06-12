---
title: "Can't setup time"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by aloprot on 2010-03-02
I can't setup my clock on ubuntu, I right click it, preferences, time setings, it asks me for my password but then it brings me back to general/locations/weather window and nothing happens. I'm using 9,10-64 bit version. What can I do in this situation?

---

### Post by Arijit_Kundu on 2010-03-02
go upto time settings, **change the time first, then click set system time**.

---

### Post by aloprot on 2010-03-02
It worked but how can I update my time with a timeserver, like you did in Windows to have the correct time?

---

### Post by Arijit_Kundu on 2010-03-02
this may help
[https://help.ubuntu.com/7.04/server/C/NTP.html]("https://help.ubuntu.com/7.04/server/C/NTP.html")

---

### Post by aloprot on 2010-03-02
Thanks very much, I will try and see if it works and update this thread. 

Regards, aloprot.

---

### Post by aloprot on 2010-03-02
But is there a way to thick an option to automaticly update my time in gnome? I don't want to start doing a cron file and so on. I heard that there is an option to automaticly do this. How do I  enable ntp on my system? I searched on preferences in the clock but no luck.

---

### Post by Arijit_Kundu on 2010-03-02
go to system> administration> time and date
unlock this (click on the icon of a key), then change configuration to keep syncronized

---

### Post by aloprot on 2010-03-02
I did it, and this will syncronize all the time my time with the servers without me having to write a cron file to check every day the time right?

Thank you very much!

---

