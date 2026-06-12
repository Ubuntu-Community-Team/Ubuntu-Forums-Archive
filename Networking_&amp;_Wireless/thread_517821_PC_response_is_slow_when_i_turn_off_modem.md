---
title: "PC response is slow when i turn off modem"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by pravinba on 2007-08-05
Hi,

I am using dual-boot system with XP & Feisty. The PC seems to work fine when it is connected to the internet. But when i turn off my modem, the system response is very slow. 

For eg.,  

1. It takes a longtime to access any files on the hard drive.
2. Have to wait for the menu to pop-up after clicking "Applications"

I feel that a process is running which constantly depends on the internet. Unable to find out the exact reason. Can anyone suggest something for this problem? 


Thanks,
Pravin

---

### Post by noob12 on 2007-08-05
When you turn off your modem does shutting down networking help?
```

sudo /etc/init.d/networking stop

```

---

### Post by bobdole211 on 2007-08-09
I, too, have this same problem.  It works perfectly on my AMD 4800, 2 gigs of ram, nvidia 8600 gt while on the internet.

I tried disabling the network card from within the desktop environment but that didn't seem to have any effect.  I will try stopping it as you suggest.

Also, if this doesn't work, what other information might be helpful to troubleshoot this?  When I open up the XFCE task manager nothing seems to be taking up large %'s of CPU/memory.

Thanks!

---

### Post by bobdole211 on 2007-08-10
Hey, that fixed the problem!

Any way to automate that so I don't have to control alt f6 each time I turn on the computer vs. waiting a 
whole minute for the desktop to appear and opening up a terminal?

Thanks!

---

### Post by mips on 2007-08-10
Do you have a loopback interface configured ???
If you do add it to the hosts file with your boxes name as the FIRST entry.

---

### Post by bobdole211 on 2007-08-14
Can you please give me an example?  I'm not super familiar with Linux quite yet.

I do have the local interface there, the 127.0.0.1, but can you show me an example as to how that would look?

Thanks!

---

### Post by pravinba on 2007-10-14
Thanks noob12...  :)

The solution that you gave worked right...

Tension's Gone !!!!

---

