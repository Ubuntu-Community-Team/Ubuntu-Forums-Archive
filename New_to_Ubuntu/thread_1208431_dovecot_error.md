---
title: "dovecot error"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by scarlett88 on 2009-07-09
hi 
i am facing a problem setting up the maildir in the dovecot.conf file.
when i name the maildir as

mail_location = maildir:~/var/mail/MailDir

i am getting the following error..

..desidoc@desidoc-desktop:~$ /etc/init.d/dovecot restart
 * Restarting IMAP/POP3 mail server dovecot                                     start-stop-daemon: open pidfile /var/run/dovecot/master.pid: Permission denied (Permission denied)
                                                                         [fail]
desidoc@desidoc-desktop:~$ 


please help me out.. :(
what should be the maildir and mbox addresses..
what is the difference..?

:confused:  i am so confused.....

---

### Post by scarlett88 on 2009-07-10
Please help me.. :icon_frown:
 its so irritating

---

### Post by ainsworth_t on 2009-07-10
> ..desidoc@desidoc-desktop:~$ /etc/init.d/dovecot restart
* Restarting IMAP/POP3 mail server dovecot start-stop-daemon: open pidfile /var/run/dovecot/master.pid: Permission denied (Permission denied)
[fail]

If you're not logged in as root, try running it with sudo:

```
sudo /etc/init.d/dovecot restart
```

---

### Post by scarlett88 on 2009-07-10
hi :)
thanks :)
it worked that way.. :)
can you please tell me some source to study the mail server establishment and working..
some tutorial which tells how to do it step by step.
its so confusing..
i tried reading from ubuntu server guide but could not understand it. :(

how the mails are stored using maildir and mbox...

---

### Post by ainsworth_t on 2009-07-10
I was going to suggest the Ubuntu Server Guide but if you don't get much from it you might also want to check out the Ubuntu Community Documentation ([https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)) along with HowtoForge ([http://www.howtoforge.com/howtos/email](http://www.howtoforge.com/howtos/email))

---

