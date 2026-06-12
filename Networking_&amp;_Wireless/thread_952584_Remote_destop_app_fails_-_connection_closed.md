---
title: "Remote destop app fails - connection closed"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by ookooboontoo on 2008-10-19
Hi all,

I have two Ubuntu Hardy machines though one has additional kde and xfce desktops installed but I have been working in GNOME.

I set up in System>preferences>remote desktop to view one of the pcs. When I go to the other computer through remote desktop viewer, I can find the computer to remote into but when I do, it returns```
Connection to host adrian-laptop was closed.
```

I have tried playing with other port numbers, tried it the other way round and checked in case it was wireless playing up.

This is on a local network through a DG834 NETGEAR ADSL Router.

It seems my experiences are similar to this [http://ubuntuforums.org/showthread.php?t=856413]("http://ubuntuforums.org/showthread.php?t=856413") but I have always got connection closed. I tried with the IP instead of the hostname but still no joy.

Has anyone any ideas?

Thanks

---

### Post by risu_vk on 2008-10-19
try using vnc

---

### Post by bo_n_tulsa on 2008-10-19
My situation may be different from yours, but for some reason when I get the "closed" message, I open up a terminal and ping the remote machine I'm trying to connect to.
After I do this, the remote desktop software immediately connects.

---

### Post by ookooboontoo on 2008-10-19
> **risu_vk said:**
> try using vnc

Thanks,

I tried that, with both java and tightvnc and still no joy. 
in java I put in vncviewer adrian-desktop:3
and get
java.net.UnknownHostException: adrian-desktop

I put in vncviewer 192.168.0.3:3
and get
java.net.ConnectException: Connection refused

not quite sure which password tightvnc wanted me to put in but all trys failed.

---

### Post by ookooboontoo on 2008-10-19
> **bo_n_tulsa said:**
> My situation may be different from yours, but for some reason when I get the "closed" message, I open up a terminal and ping the remote machine I'm trying to connect to.
After I do this, the remote desktop software immediately connects.

Thanks, tried it but did not seem to work :(

did you ping it once or kept pinging?

---

### Post by ookooboontoo on 2008-10-19
I find the out put from remote desktop viewer is 
Connection to host "adrian-desktop.local:5901" was closed.
Does that look right?

---

### Post by bo_n_tulsa on 2008-10-19
> **ookooboontoo said:**
> Thanks, tried it but did not seem to work :(

did you ping it once or kept pinging?

When I enter this into terminal:
ping ipaddresshere

I just let it sit there and ping my work machines IP until the viewer connects.  Usually about 10-15 pings.
Don't know why it works for me though.  Maybe it's "poking" my work computer awake.  don't know.

---

### Post by ookooboontoo on 2008-10-19
Thanks for the idea I will try it tomorrow.

A

---

### Post by risu_vk on 2008-10-20
seems like a connection issue similar to firwall/nat block . When i used to get this kind of issues i used to try a smal http server like webfs([http://linux.bytesex.org/misc/webfs.html](http://linux.bytesex.org/misc/webfs.html)) and try to access the [http://ipadress](http://ipadress) . If its working then the problem is specific to remote desktop.Also can try [http://127.0.0.1](http://127.0.0.1) to check whether loopback is working. Best wishes

---

### Post by ookooboontoo on 2008-10-20
> **bo_n_tulsa said:**
> When I enter this into terminal:
ping ipaddresshere

I just let it sit there and ping my work machines IP until the viewer connects.  Usually about 10-15 pings.
Don't know why it works for me though.  Maybe it's "poking" my work computer awake.  don't know.
I tried this in several ways but sadly to no avail.

> **risu_vk said:**
> seems like a connection issue similar to firwall/nat block . When i used to get this kind of issues i used to try a smal http server like webfs([http://linux.bytesex.org/misc/webfs.html](http://linux.bytesex.org/misc/webfs.html)) and try to access the [http://ipadress](http://ipadress) . If its working then the problem is specific to remote desktop.Also can try [http://127.0.0.1](http://127.0.0.1) to check whether loopback is working. Best wishes
Thank you for this idea, I wonder if it is the router I am using. I think I will try first to hook it up to an independent hub to see if it will work itself out. This is going to bug me until fixed, I will need to see if I can RD a a Windows PC. I used to be able to on my old netgear router.

Thank you for your continued thoughts on this.

A

---

