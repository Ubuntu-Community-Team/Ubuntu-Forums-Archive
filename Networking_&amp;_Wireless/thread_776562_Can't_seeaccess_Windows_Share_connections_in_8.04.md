---
title: "Can't see/access Windows Share connections in 8.04"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by pronihil on 2008-04-30
Before I upgraded to 8.04, I had been connected to my school's various network servers (by using the Places -> Connect to Server menu item). After I upgraded, they disappeared. I thought maybe it was just a part of the installation, and tried to connect to them again using the Windows Share option as I had done before. 

Long story short, instead of being able to connect to the windows servers, I'd get a "No application is registered as handling this file" error. If I tried again, I'd get a "Location is already mounted" error, but I'm obviously not mounted.

Please help! Being able to access those servers will make my life much easier as a student.

---

### Post by MaindotC on 2008-04-30
There's a problem accessing password-protected shares.  You should be able to access the server that houses the shared folders, but the minute you access your own folder it should say one of your error messages or the one I get which is: 

```

Error: Failed to mount Windows share
Please select another viewer and try again.

```

A thread is started here [http://ubuntuforums.org/showthread.php?t=775199](http://ubuntuforums.org/showthread.php?t=775199) and the issue is also being handled by launchpad at [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072).  I'm watching those threads just as much as you are :(

In the meantime what I do - I know this is a gross workaround but - I have a Fedora 8 lab computer on the campus network that has no problem accessing the shares so I vnc into that and then access my shares from there.  If I need them on my laptop I use sftp to download them to my laptop drive.

I hope Sebastian Bacher of launchpad can advise how to fix this...

---

### Post by pronihil on 2008-05-03
Thanks for the information. I feel a bit sheepish now about starting this thread when others are already working on fixing it. Ahh well. :)

---

### Post by MaindotC on 2008-05-03
Np - at least twice a day a new thread goes up stating they're having problems so I'm making it my personal mission to inform everyone :)

---

