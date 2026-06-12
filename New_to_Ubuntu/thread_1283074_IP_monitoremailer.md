---
title: "IP monitor/emailer?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by MarkX on 2009-10-05
Hello folks!
I need a prog, preferably with GUI, which emails my dynamic IP to my email every time it changes (so I can access my security cams, for example or use remote desktop). There are numerous such IP mailer progs for windows but is there an equivalent one for Ubuntu please?

(No, I don't want to use dyndns. It closes free accounts if they are not used for a month and I don't want/need to rely on some other company!)

---

### Post by MarkX on 2009-10-06
Anyone, please?

---

### Post by Sarmacid on 2009-10-06
I have no knowledge of a program like that existing, but a way to do it would be setting up a mail server and having a cron job to email you your address every hour/day or so.

**EDIT**
Now that I think about it, should probably be a lot easier if you make a script to check your ip every minute and mail you if it changes using evolution. Not sure if evolution will support this but I guess it will after installing the evolution cli package.

---

### Post by MarkX on 2009-10-06
> **Sarmacid said:**
> I have no knowledge of a program like that existing, but a way to do it would be setting up a mail server and having a cron job to email you your address every hour/day or so.

There are loads of progs for windows which automatically email you the latest dynamic IP from your remote computer. 

Surely there must be one for Linux? I can't believe there isn't one in Linux, it's incredibly useful. 
Such a feature should be incorporated into all manner of applications as standard.
It saves lots of wonga not having to pay for a fixed IP or relying on dyndns.

---

### Post by MarkX on 2009-10-06
> **Sarmacid said:**
> I have no knowledge of a program like that existing, but a way to do it would be setting up a mail server and having a cron job to email you your address every hour/day or so.

**EDIT**
Now that I think about it, should probably be a lot easier if you make a script to check your ip every minute and mail you if it changes using evolution. Not sure if evolution will support this but I guess it will after installing the evolution cli package.

Sadly, I wouldn't know where to start, but thanks!
 
It just needs a little GUI which says:

Email IP to: 
1)...........
2)...........

X  on change
X  every: ...day/s, ..hours, ..minutes

The IP could be displayed in the email subject title so it doesn't even have to be opened and can be copied and pasted.
Like this:  

New home IP- [http://123.123.123.123](http://123.123.123.123)

That little feature could be integrated into various apps including email programs like Thunderbird or whatever.

---

### Post by Sarmacid on 2009-10-06
Well, in case you ever get around to make the thing yourself this will be useful

This script will create an email and put it in your outbox in evolution. It will be sent next time evolution does send & recieve
```
#!/bin/bash
date '+From <email address> %a %b %e %T %Y' > /tmp/autoemail
echo "Subject: Auto_Create_Email" >> /tmp/autoemail
echo "From: A_User <email address hidden>" >> /tmp/autoemail
echo "To: <email address hidden>, <email address hidden>" >> /tmp/autoemail
echo "">> /tmp/autoemail
echo "This message was autocreated" >> /tmp/autoemail
echo "2nd Line" >> /tmp/autoemail
echo "">> /tmp/autoemail
cat /tmp/autoemail >> /home/user/.evolution/mail/local/Outbox
exit 0
```

To get your ip in the subject just replace the line for
```
echo "Subject: `ifconfig eth0| grep Mask | cut -d: -f2|awk '{ print $1}'`"
```

And to automate this whole process just use crontab.

---

### Post by MarkX on 2009-10-09
Many thanks but I just found a very good IP mailer which excellent GUI that works in windows and Linux:

[http://www.ip-monitor.com.ar/download.php](http://www.ip-monitor.com.ar/download.php)

[https://sourceforge.net/projects/ipmonitor/files/](https://sourceforge.net/projects/ipmonitor/files/)

---

