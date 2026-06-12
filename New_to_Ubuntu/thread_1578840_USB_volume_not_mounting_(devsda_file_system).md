---
title: "USB volume not mounting (/dev/sda file system?)"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Vinnie V on 2010-09-21
I am using 8.10 (Ibex). I found a USB drive that I have used previously for storing video and music. When I plug it in, I get the following error message, "Cannot Mount Volume. The volume 'CENTON USB' uses the /dev/sda file system which is not supported by your system." I do not remember formatting it with this file system.

How can I reformat the USB drive so that it will mount properly?

Thank you.

---

### Post by sikander3786 on 2010-09-21
If it hasn't got any valuable data, unmount it and then use gparted to format accordingly. If gparted isn't installed, install it by

```

sudo apt-get install gparted

```

You are using quite an old version of Ubuntu i.e, 8.10. 10.04 is out and 10.10 scheduled to be released in October. Try to upgrade or reinstall to a supported version if possible.

---

### Post by Vinnie V on 2010-10-31
OK, so I verified that the version that I am using is not causing the problem. I have other USB drives that mount fine. I installed gparted, and using that changed the formatting. It is now formatted with fat32, which my other drives that work are using. It will still not work on my machine. 
The error message still says "The volume 'SPORT' uses the /dev/sda file system which is not supported by your system." 
In addition, I now get an error message that says "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

The drive does not have any data on it, so I am open to anything to get it to work.

Any suggestions?

Thank you.

---

### Post by tajiknomi on 2010-10-31
[SIZE=2]*I didn't get your problem,but i will suggest you to install **Mount-manager*** From software center...and then mount your USB via Mount-manager(its GUI) [/SIZE]

---

### Post by sikander3786 on 2010-10-31
> **Vinnie V said:**
> OK, so I verified that the version that I am using is not causing the problem. I have other USB drives that mount fine. I installed gparted, and using that changed the formatting. It is now formatted with fat32, which my other drives that work are using. It will still not work on my machine. 
The error message still says "The volume 'SPORT' uses the /dev/sda file system which is not supported by your system." 
In addition, I now get an error message that says "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

The drive does not have any data on it, so I am open to anything to get it to work.

Any suggestions?

Thank you.
Simply did you try the same USB stick with some other PC/OS? I mean are you sure the drive itself is in good state?

---

### Post by Vinnie V on 2010-10-31
> **sikander3786 said:**
> Simply did you try the same USB stick with some other PC/OS? I mean are you sure the drive itself is in good state?

It works with other PC, and OS. I haven't been able to try it on my other Linux PC (vid card burned out), but it works with Win 7, and Mac OSX.

---

