---
title: "SMART query"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by sazan on 2009-04-28
Hi
I was running "smartctl -d ata -a /dev/sdb" command to get a long output.

Somewhere in the document i  found this ...


```

Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

```


I am not able to figure out what the last sentence *** "" It "wraps" after 49.710 days. ""*** means. I had run the same command for multiple disks and this sentence seems to be a standard for all devices. and I am looking for to what it really means.

---

### Post by sazan on 2009-04-28
bump..!!!

---

### Post by Peter09 on 2009-04-28
Seems to suggest that after 49 days the timer goes back to 000

---

### Post by sazan on 2009-04-28
thank you, that sounds very valid.

---

### Post by unutbu on 2009-04-28
If you search the man page of smartctl for the word "wraps" you will find
> 
Note: this time stamp wraps after 2^32 milliseconds,
or 49 days 17 hours 2 minutes and 47.296 seconds.

and it can be confirmed that indeed 2^32 milliseconds roughly equals 49.710 days.

So apparently, Powered_Up_Time is measured in milliseconds and stored in a 32-bit variable. When the real Powered_Up_Time becomes greater than 2^32 milliseconds, the value gets cut down or "wrapped" to a number between 0 and 2^32.

---

### Post by sazan on 2009-04-28
> **unutbu said:**
> If you search the man page of smartctl for the word "wraps" you will find


and it can be confirmed that indeed 2^32 milliseconds roughly equals 49.710 days.

So apparently, Powered_Up_Time is measured in milliseconds and stored in a 32-bit variable. When the real Powered_Up_Time becomes greater than 2^32 milliseconds, the value gets cut down or "wrapped" to a number between 0 and 2^32.



Thanks a lot, this was exactly what i was looking for, didn't look into manual for 'wrap', great idea.. thanks

---

