---
title: "dump /var/log/messages into html"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by esquilomorto on 2009-09-21
Hi,

I'm new to ubuntu and would like to know if it's posssible to dump the content of /var/log/messages to a html file in the /var/www/logvpn/index.html.

thanks in advance

---

### Post by hailtothethief on 2009-09-23
I don't know of a clean way of doing it, but the following command will surround all of them with <H3> tags, append them to /var/www/logvpn/index.html **AND** delete the message log:

```
cat /var/log/messages | sed -e "s/\(.*\)/<h3>\1<\/h3>/" >> /var/www/logvpn/index.html; cat /dev/null > /var/log/messages
```

I would use a .css file to format them to make them pretty. This is called a **sed** command, info can be found here: [http://www.grymoire.com/Unix/Sed.html]("http://www.grymoire.com/Unix/Sed.html")

You'll probably want to run that in the form of a cron command, info can be found here: [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by robert_pectol on 2009-09-23
You should probably leave off the, "; cat /dev/null > /var/log/messages" at the end and **NOT** delete the system log file.  It's just not good practice and shows little foresight.  Parse and copy the system logs to your heart's content but leave the logs themselves intact.

Robert

---

### Post by esquilomorto on 2009-09-23
First of all thanks for replying, i was testing using > and tee but it give a very bad way of visualizing the info.

I keep in my both suggestion, once more thanks.

---

