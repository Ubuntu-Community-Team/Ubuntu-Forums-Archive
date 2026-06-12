---
title: "Wake Up U!"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-05-28
how can i wake up my Ubuntu OS for example at 12.40?
is there any function doing this?

i know that to shutdown i need to do:  sudo shutdown 12:40 -P

so? ;)

PS: sorry for my bad english)

---

### Post by halitech on 2009-05-28
hit the power button? *shrug* 

seriously though, are you trying to find if there is a way to have the system turn on at a certain time after being powered down? If so, I don't believe there is as the system isn't running so can't run commands to turn it on.

---

### Post by tanjir on 2009-05-28
You want cronjob if you want to do anything at any given time. Type "crontab -e" it will show you current cron jobs. Anyway, detailed information is available here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by m_duck on 2009-05-28
For that you would probably need to find an option in your BIOS to automatically switch the PC on at a certain time.

---

### Post by ssdt on 2009-05-28
You will have to update your bios with this information to make this possible, there is no other way than that.

---

### Post by lavinog on 2009-05-28
You can set it in bios if it isn't going to change.

There is a way to set this in linux, but I have to look it up.

In the meantime, you can also use another computer to wake it up using wakeonlan

---

### Post by lavinog on 2009-05-28
here is a link that explains how to do it, but I haven't tried it yet.
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
make sure you follow the **Using /sys/class/rtc/rtc0/wakealarm** sections and not the **/proc/acpi/alarm** ones

---

