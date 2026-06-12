---
title: "SUDO incident reporting"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-25
I am the administrator of a family laptop (mostly managed remotely from my laptop or desktop via SSH/VNC). How can I actually be notified when a user not in the sudoers file tries to become root? I know it seems silly, but I'm a very strict administrator ;).

---

### Post by collinp on 2010-07-25
I believe that such notifications are sent in an email message to the superuser (root). So, you would have to set up a mail system of some kind to receive those notifications.

---

### Post by yetiman64 on 2010-07-25
> **collinp said:**
> I believe that such notifications are sent in an email message to the superuser (root). So, you would have to set up a mail system of some kind to receive those notifications.

+1

or

to check manually from terminal,

```
cat /var/log/auth.log | grep "user NOT in sudoers"
``` such a code on my install outputs after a deliberate sudo attempt from a non admin account

> Jul 25 16:10:58 <my localhostname> sudo:    testuser : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/testuser ; USER=root ; COMMAND=/usr/bin/apt-get updateFrom this I can see my "testuser" account was used in an attempt to run the command "sudo apt-get update" from a non admin account. Also <my localhostname> is just being used here to censor my machine name on the forums, the actual hostname is outputted in terminal.

---

### Post by patchwork on 2010-07-25
You can add the mail_badpass parameter to your /etc/sudoers.

With this, you can either use the default root mail account (accessible through the command ```
sudo mail
```) or specify another account.

```
man sudoers
```

---

### Post by waynerod on 2011-08-06
Yeah, the var/log is the place.

On a lighter note, check this out:
[http://imgs.xkcd.com/comics/incident.png](http://imgs.xkcd.com/comics/incident.png) :popcorn:

---

### Post by domino1241 on 2012-11-25
According to [http://stackoverflow.com/questions/13546933/where-are-sudo-incidents-reported](http://stackoverflow.com/questions/13546933/where-are-sudo-incidents-reported), the log is kept in

```
/var/spool/mail/<USERNAME>
```

so you can set up emails to your mail account when that file is updated.

---

### Post by overdrank on 2012-11-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

