---
title: "vsftpd"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by vanhornd on 2009-12-23
Hello Ubuntu users and admirers,

When I make a change in /etc/vsftpd.conf, I would like the vsftpd process to refresh using my new changes.  All I have discovered so far is to reboot my Ubuntu machine which is very clunky!  I'm sure there is an easier way . . .

---

### Post by Geoff918 on 2009-12-23
> **vanhornd said:**
> Hello Ubuntu users and admirers,

When I make a change in /etc/vsftpd.conf, I would like the vsftpd process to refresh using my new changes.  All I have discovered so far is to reboot my Ubuntu machine which is very clunky!  I'm sure there is an easier way . . .

One of two things ought to work:

sudo /etc/init.d/vsftp restart (or maybe vsftpd restart)

or in more recent disto releases the following may work

sudo service vsftp restart (or again vsftpd whatever the case may be for this service)

Remember, Linux is built for servers originally. A restart is almost never necessary unless there's a kernel change. And, that won't be there for long as something called ksplice has come out that prevents even that from needing a restart. It will probably be a few years before we're ready to trust it, though. :)

I hope this helps.

---

### Post by wojox on 2009-12-23
```
sudo /etc/init.d/vsftpd restart
```

---

### Post by swoody on 2009-12-23
Have you tried restarting the vsftpd daemon itself? Try:
```
sudo /etc/init.d/vsftpd stop
```
```
sudo /etc/init.d/vsftpd start
```

I'm not familiar with it, but there may also be a 'restart' or 'reset' option you could try.

Let us know if that works out :)

---

### Post by wojox on 2009-12-23
> **Geoff918 said:**
> 
sudo service vsftp restart


Ah yes, if your using the Desktop that should work for Karmic.

---

### Post by vanhornd on 2009-12-23
This worked absolutely flawlessly!  Thank you all who replied.  All of the variant replies probably would work as well; this reply had the added bonus of teaching me where the startup file is located.  

I am totally amazed that I had so many useful replies in less than ten minutes!  The Ubuntu community is so helpful it boggles my mind . . .

Happy holidays to all of you!

---

