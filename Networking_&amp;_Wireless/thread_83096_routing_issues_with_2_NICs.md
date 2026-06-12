---
title: "routing issues with 2 NICs"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by bb002 on 2005-10-27
I'm assuming that is the issue. I have two NICs in newly built server. I've given both cards static ips and everything works until i have both active at the same time.

eth0 -- private IP 192.168.150.6
eth1 -- Public IP   10.10.10.10 <- I know it's private but lets play pretend.

I want everything to default to the public card unless the destination ips are "192.168.149.255/255.255.255.0", "192.168.148.255/255.255.255.0", and "192.168.152.255/255.255.252.0". When ever a destination ip is private i want the next hop as the private gateway 192.168.150.1

As you can see, I know what I need to do but I can't figure out what configuration tool I need. I thought it would have been part of Ubuntu's Network GUI tool but I didn't see it. If that is indeed where I need to do this what's the name of that tab so I can fry my eyes for their blindness.

[edit]
This maybe a double post but I got taken to [http://ubuntuforums.org/newthread.php](http://ubuntuforums.org/newthread.php) after i clicked post. I didn't see my topic so i reposted. Mod, you can delete either of the threads since i managed to use the browser back button to copy my text.

---

### Post by adwait on 2005-10-28
Try the command
```
route
```

Read the man pages to figure out to everything

---

### Post by bb002 on 2005-11-26
I used the route command to fix the routes but the fix is not permenant.

The server went down roughly Thursday night sometime. Dunno how it happened but the power cord came unplugged from the PSU. The server came back up ok Friday morning when I noticed it was off but the routes were once again back to the old bad ones and i had to redo them again. After experementing a bit restarting the server would revert the routes. I endd up creating a shell script to automactically correct the routes.

Now I need to know how to add it to the boot process after the init of the two NIC.

---

