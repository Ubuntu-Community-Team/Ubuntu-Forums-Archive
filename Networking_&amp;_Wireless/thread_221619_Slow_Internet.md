---
title: "Slow Internet?"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by khoda on 2006-07-23
Hey,

Finally got Ubuntu up and running. The internet works but its VERY slow. My ethernet port is integrated in my mobo (Asus a8n5x). 

Can anyone think of what the problem is? I searched little for drivers but with the slow internet it's pain-staking. 

Any ideas?

---

### Post by wieman01 on 2006-07-24
You need to disable "ipv6" in the kernel as well as in Firefox (if this is your default browser). Simply follow this thread, post addressing similar problems and presenting solutions:

[http://www.ubuntuforums.org/showthread.php?t=218733]("http://www.ubuntuforums.org/showthread.php?t=218733")

---

### Post by khoda on 2006-07-24
I did this and when the text editor opened the alias file it was blank...

Also: I am plugged in, not wireless.

---

### Post by wieman01 on 2006-07-24
> **khoda said:**
> I did this and when the text editor opened the alias file it was blank...

Also: I am plugged in, not wireless.

I anwered you in the other thread. Check it out.

---

### Post by khoda on 2006-07-25
That didn't do it...

---

### Post by khoda on 2006-07-27
Does it mean anything if it's only slow when it's connecting.

For instance, once I'm connected to IRC (after a long wait) the messages dont lag or anything. Same with gaim. 

Could this be a firewall issue? If so, how would I fix it?

---

### Post by tty01 on 2006-07-27
i had the same issue a few days ago.  turns out ubuntu is picking up one of my internal ips as a dns nameserver for some odd reason.  once deleted problems went away.  cat your /etc/resolv.conf  and check if there is any internal addresses in that file.

---

### Post by khoda on 2006-07-27
so I checked the file, but all the severs are correct.

Then, instead of going to google.com I went to google's IP and it was MUCH faster. So something's wrong in the hostname to IP conversion. 

I have DHCP enabled, I believe if that makes any difference.

Any ideas?

---

