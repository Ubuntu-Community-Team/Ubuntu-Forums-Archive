---
title: "Running a command at start up"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Igniteflow on 2009-08-12
Hi all,
I've just reinstalled Ubuntu and I can't seem to find how to run a command from startup every time I boot up.  I want to run the following command:

sudo hdparm -B255 /dev/sda

Could someone please tell me how to do this, I've completely forgotten:oops:

---

### Post by credobyte on 2009-08-12
```
System / Preferences / Startup applications

```

---

### Post by WRDN on 2009-08-12
There are a couple of options. The easiest is to go to System > Preferences > Sessions and adding the Startup Program (this application is called gnome-session-properties).
You could also add the command to /etc/rc.local, which runs at the end of the boot process.

---

### Post by bacardiandwatermelon on 2009-08-12
I think once I had issues running sudo commands, I hate to put them in a script and run the script at startup... Don't know if that still applies...

---

### Post by Buuntu on 2009-08-12
Yes, you can't run sudo commands in System > Preferences > Startup Applications.  If you add the command (without the sudo in front) to /etc/rc.local it should work though.

---

### Post by Igniteflow on 2009-08-12
Thanks Buuntu, that's exactly what I was after

---

