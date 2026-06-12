---
title: "apache,zimbra,and nagios in one server"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by dark_musicianus on 2011-06-09
Hello every body,

i just install the server with 3 services,

apache zimbra and nagios

apache and zimbra work well, i install apache in port 80 and zimbra in port https

and the last i installed the nagios,, everything run well. But suddenly, I can not log via ssh,and also via tty, i don't know why it happen,, is apache + zimbra + nagios can not installed in one server, or maybe it error because another reason, thx 4 help

---

### Post by webofunni on 2011-06-09
Yes, you can install the services. I dont think they will make any changes in tty. are you able to see anything in logs ?

```

tail -f /var/log/syslog

```

---

### Post by dark_musicianus on 2011-06-10
thx 4 the answer i'll try next time if the error come again,, but when that error came ,i can not login with tty and ssh,how can I use that command to know the log? thx be4

---

### Post by webofunni on 2011-06-10
Is this an intermittent issue ? Then get the logs, when you will be able to login.

---

### Post by dark_musicianus on 2011-06-10
no, that's not intermittent problem,, i really can not login,, i try to wait a moment, hope that i can log in to the server, but it just wasting the time. Now i have reinstalled the server,, but i need to know why that's happen,, and why i can not log with ssh and tty,, but if the services can be installed,, it sounds good for me, may be the error is because the wrong installation proccess

---

