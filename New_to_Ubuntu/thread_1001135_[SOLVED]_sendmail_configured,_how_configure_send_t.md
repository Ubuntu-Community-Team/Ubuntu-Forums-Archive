---
title: "[SOLVED] sendmail configured, how configure send to address of cron job outputs?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by tnek on 2008-12-03
man cron says:
>        cron  then  wakes up every minute, examining all stored crontabs, checking each
       command to see if it should be run in the current minute.  When executing  com&#8208;
       mands,  any  output is mailed to the owner of the crontab (or to the user named
       in the MAILTO environment variable in the crontab, if such exists).  The  chil&#8208;
       dren  copies  of cron running these processes have their name coerced to upper&#8208;
       case, as will be seen in the syslog and ps output.
I have configured ssmtp to emulate sendmail and I'm able to send mails using ```
sendmail <some-address>
```I'm wondering about this part of the above man quote:
> any  output is mailed to the owner of the crontab (or to the user named in the MAILTO environment variable in the crontab, if such exists).
How will the system know where to send the mail? I am the owner of the crontab but I can't recollecting having entered an e-mail address when creating my user account. I need help checking if the correct information is there and if not configure it. All help greatly appreciated!

---

### Post by linux_tech on 2008-12-03
In addition to LOGNAME, HOME, and SHELL, cron will look at MAILTO if
it has cause to send mail 

Put MAILTO=username in the top part of your crontab file

```
crontab -e
```
To send email to [email]admin@domainname.com[/email], enter:
```
MAILTO=admin@domainname.com
```

---

### Post by tnek on 2008-12-04
Ah! :-)

And if I would not fill in MAILTO it would try to send to [FONT=Courier New]<myAccountName>@<myComputersDnsName>[/FONT]? Which would not work as my computername is rat.farm and that address would be [email]kent@rat.farm[/email] which isn't available outside my LAN.

In other words I'll have to fill in MAILTO for each account which uses cron, or there will be no valid mail recipient.

---

