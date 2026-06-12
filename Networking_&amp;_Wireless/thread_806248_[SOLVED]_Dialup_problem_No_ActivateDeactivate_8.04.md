---
title: "[SOLVED] Dialup problem: No Activate/Deactivate 8.04 Live"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by JAYCEE1 on 2008-05-24
I'm not new to Linux. I am trying out the Live CD Hardy on my IBM Thinkpad T23 that is currently running Fedora 5. I am able to connect with dialup using Fedora. 

Problem is when I put in the Hardy Live CD for a test drive, I do not get the activate or deactivate button on System>Admin>Network. I put in the phone #, DNS, TTYS1, etc. 

What am I doing wrong?

Thanks!

---

### Post by JAYCEE1 on 2008-05-25
I've seen others on here with the same problem: no activate deactivate. I just cannot find a resolution.

Anybody know how to fix this?

Thanks!

---

### Post by JAYCEE1 on 2008-05-25
OK, I think I solved my own problem. I ran

```

sudo pppconfig

```

entered root password and went through the steps. I had to use static DNS addresses (both primary and secondary) to get the connection to stay alive.

I also ran 

```

sudo gedit /etc/ppp/peers/provider

```

and put in my user ID (from ISP) and modem location. For those who don't know, run the command and edit the items that do not have a pound sign/hash mark (#) next to them and then save.

It works now but the transfer rate seems pretty slow. I'll mark as resolved.

---

