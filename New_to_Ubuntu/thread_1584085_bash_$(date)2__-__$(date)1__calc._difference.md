---
title: "bash: $(date)2  -  $(date)1  calc. difference?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-28
Hello,

In a newbie script bash I would like to calc the difference between two dates. Which method is recommended ? 


thank you !

---

### Post by Apollo87 on 2010-09-28
Hello,

The best way to handle differences between dates, is to convert to date to a unix timestamp, which is the amount of seconds from Jan 1, 1970.  Since you are dealing with seconds, it makes subtracting dates much easier.

The command 'date' in bash will be able to covert a date into a timestamp.  Wikipedia actually has a pretty good rundown on it:

[http://en.wikipedia.org/wiki/Date_%28Unix%29](http://en.wikipedia.org/wiki/Date_%28Unix%29)


Now I'm not going to write the script for you, because you will never learn that way, but a good push in the right direction would be this command:

```
date --date "2010-09-28" +%s
```

This will convert a date format of YYYY-MM-DD into a time stamp.  Turn two dates into timestamps, then subtract those two timestamps.  And viola, you have the difference between those two dates. 

Now, the difference you get will be in seconds, but the conversion to mins, hours, days or whatever format you want should be easy enough.  Hint: theres 86400 seconds in a day.

Good luck
Let me know if you have any more issues with this.

---

