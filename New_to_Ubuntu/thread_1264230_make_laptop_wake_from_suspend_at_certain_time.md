---
title: "make laptop wake from suspend at certain time?"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-09-11
i would like to set a timer to make ubuntu wake from suspend at certain time and then use alarm clock package to wake me up is there a quick simple way to make this happen?

---

### Post by unutbu on 2009-09-11
Open a terminal (Applications>Accessories>Terminal)
and type
```

sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
```


Then suspend the machine. If the above command works, your machine should wake itself up in 5 minutes.

You can read more about it here: [http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually_2](http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually_2)

---

