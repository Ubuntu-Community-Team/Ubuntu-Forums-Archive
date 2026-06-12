---
title: "Trying to use MythtvTroubleshooting guide"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by legswilly on 2011-02-21
Hi, I am a noob. I tried to install MythTv on Ubuntu and cant connect to MySql. Can ping the server. So the guide tells me to remove ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf. I tried to use sudo with it, but it tells me I don't have permissions. So I look for how to change permissions and I can't make out how to do this. Could you please give me a link to an explanation of chmod and chown. I would like to change the permissions,so I can do as it says guide. Would it be better to find a book to look it up.
Thank you for replying

---

### Post by aeiah on 2011-02-21
```
sudo chown -R username:group ~/.mythtv/
```

but really, if you cant remote it with sudo then there's something wrong, because root should be able to remove anything.

what is the exact command(s) and output you receive when removing your mythtv config files?

incidentally, have you tried just looking into the mysql problem? maybe the service isnt running, or the port isnt the correct one.

see if its running:
```
sudo netstat -tap | grep mysql

```

see what port it's set to in /etc/mysql/my.cnf and test with ```
telnet localhost 3306
``` or whatever port you have instead of 3306. it'll say connection refused if its blocked.

---

### Post by wizard10000 on 2011-02-21
My guess is a bad mysql password.  Look here -

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

---

