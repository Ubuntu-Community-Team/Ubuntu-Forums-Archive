---
title: "sudo and crontab"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-15
Hi Ubuntu Community:

My user crontab executes scripts, which when finished, [COLOR="Red"]**I want to shutdown my machine and save electricity.**[/COLOR]

So, I want to shutdown my system using 

[COLOR="red"]sudo shutdown -h "now"[/COLOR]

in my crontab, also.

However, this command requires the user password to run. 

[COLOR="Blue"]**How do I add the password to the**[/COLOR] [COLOR="Red"]sudo shutdown -h "now"[/COLOR] [COLOR="blue"]**command?**[/COLOR]

Thanks!
Phil Smith
Duluth, GA

---

### Post by Paqman on 2010-08-15
Just run it as a normal root cron job.

---

### Post by gmargo on 2010-08-15
You could edit the "sudo" permissions (using **visudo(1)**) to allow you to run /sbin/shutdown without a password.  I think the line would be:

```

     phil = NOPASSWD: /sbin/shutdown

```

---

