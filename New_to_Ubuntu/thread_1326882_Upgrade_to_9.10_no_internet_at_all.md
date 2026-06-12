---
title: "Upgrade to 9.10 no internet at all"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-11-14
I have a Dell Mini9 that was happily running 9.04 until I decided to upgrade to 9.10 a while ago. After upgrading, I was unable to connect to the internet, wired or wireless. The network manager shows there are no wired networks. Ping says network is unavailable. As far as I can tell it looks as if it doesn't even know there is a wired network.

Any ideas on how to fix this?

BTW I know the wireless shouldn't work out the box as it needs a restricted driver, but wired should.

Thanks,
JR

---

### Post by Jon Monreal on 2009-11-14
Do you have 9.10 or 9.10 netbook remix? I recall seeing something about problems with 9.10 remix on the Mini 9.

EDIT: It appears that this is a problem.  [This webpage]("http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html") appears to have information on how to fix it (just scroll down to #5). If you need additional help with this, please feel free to post.

---

### Post by Commander_Bob on 2009-11-15
I am using regular 9.10.

That website has info for installing the **wireless** driver. The first step is > - First connect to the internet via a wired connection My wired connection does not work at all.

---

### Post by k3lt01 on 2009-11-15
Follow the instructions in [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") link. Then let us know how you go.

---

### Post by Commander_Bob on 2009-11-19
Just tried it, nothing, still no connection. Do you think re-downloading and installing might fix it? It's been probably a month since I installed, so maybe it has changed.

EDIT: I though I should also mention that ifconfig only gives 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by Commander_Bob on 2009-11-25
Anyone? Still having this problem.

---

### Post by Sealbhach on 2009-11-25
> **Commander_Bob said:**
> Anyone? Still having this problem.

Did you try a reinstall with the latest build? Ethernet should work out of the box. You can get the latest build here: [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

It seems there was a problem with the wireless: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

.

---

### Post by Commander_Bob on 2009-11-25
I downloaded it off the main page 5 days ago. I'm downloading the link you sent, and I'll try NBR.

I also tried installing the wireless drivers from a USB drive but that still didn't work. After a reboot they became un-activated.

---

### Post by Sealbhach on 2009-11-25
> **Commander_Bob said:**
> I downloaded it off the main page 5 days ago. I'm downloading the link you sent, and I'll try NBR.

I also tried installing the wireless drivers from a USB drive but that still didn't work. After a reboot they became un-activated.

Well, if it doesn't work, the sensible thing would be to go back to 9.04. You won't be missing all that much in 9.10.

.

---

### Post by Commander_Bob on 2009-11-26
Looks like a down-grade for me. :(

---

### Post by mikewhatever on 2009-11-26
I think your issue is rather simply and is easily fixable.
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Obviously, using OpenDNS, as suggested in post #4, has nothing to do with the issue.

---

### Post by VertexPusher on 2009-11-26
This is not necessarily a driver issue. When I upgraded from 9.04 to 9.10, the DSL connection in Network Manager (using PPPoE) stopped working too. I could restore the connection using the old-fashioned pppoeconf tool, but peer DNS still didn't work until I made /etc/resolv.conf a symbolic link to /etc/ppp/resolv.conf.

---

### Post by Commander_Bob on 2009-11-26
Would you mind explaining this in a bit more detail?

@mikewhatever: I read that link way before I posted. If you read the first post, my wired internet doesn't work, so I can't install drivers for the wireless card. I even tried installing the driver via a USB drive and it still did not work.

EDIT: I just booted up 9.04 on a flash drive and the wireless worked out of the box, however my wired still doesn't. Maybe my netbook is broken :( .

---

### Post by Commander_Bob on 2009-12-30
I think I've fixed the problem. I'm on vacation and only have WiFi (I'm using Dell's version on Ubuntu) so I can't check.

It looks like the LAN controller was disabled in the BIOS. I don't think I did it, but I may have disabled it a while back. Once I get home I'll see if it works and then upgrade to 9.10 and get away from Dell's garbage version.

---

