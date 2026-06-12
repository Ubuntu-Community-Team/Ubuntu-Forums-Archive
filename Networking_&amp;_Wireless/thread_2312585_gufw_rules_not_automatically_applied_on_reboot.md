---
title: "gufw rules not automatically applied on reboot"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by cannondale0815 on 2016-02-05
I have been using gufw for a while now to open up a specific port for owncloud. Unfortunately, on each reboot, the port opening doesn't appear to stick, so I have to start gufw, toggle the switch to off and then back to on, before the port is open.

How can I have the rules automatically applied upon each start?

Thanks
-J

---

### Post by sammiev on 2016-02-05
Hi,

Have you tried this yet?

```
sudo ufw enable
```

```
sudo ufw status verbose
```

---

### Post by cannondale0815 on 2016-02-05
Yes, in fact I did. And I should have mentioned that. Ufw is enabled, and it does claim it's running when checking the status upon reboot. It also shows that my rules are set properly. Yet the port still isn't open until I disable then enable it (which I usually do via gufw, but I suppose the same could be done with ufw on the command line).

---

### Post by sammiev on 2016-02-05
Hi,

After you do a fresh boot try.

```
sudo ufw status
```

and do you see any rules you added?

Post them here so people can better understand what's happening.

---

### Post by cannondale0815 on 2016-02-12
I apologize for the late response. I just restarted my Ubuntu server, and, as usual, OwnCloud wasn't accessible from the outside (it's running on port 9000). The ufw status read as follows:

```

Status: active


To                         Action      From
--                         ------      ----
32400:32443/tcp            ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
137,138/udp                ALLOW       Anywhere
139,445/tcp                ALLOW       Anywhere
4242                       ALLOW       Anywhere
80,443,9000/tcp            ALLOW       Anywhere
32400:32443/tcp (v6)       ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
137,138/udp (v6)           ALLOW       Anywhere (v6)
139,445/tcp (v6)           ALLOW       Anywhere (v6)
4242 (v6)                  ALLOW       Anywhere (v6)
80,443,9000/tcp (v6)       ALLOW       Anywhere (v6)

```

I then did a sudo ufw disable, followed by sudo ufw enable, and the status is unchanged after, but (!) OwnCloud is now accessible:

```
To                         Action      From
--                         ------      ----
32400:32443/tcp            ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
137,138/udp                ALLOW       Anywhere
139,445/tcp                ALLOW       Anywhere
4242                       ALLOW       Anywhere
80,443,9000/tcp            ALLOW       Anywhere
32400:32443/tcp (v6)       ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
137,138/udp (v6)           ALLOW       Anywhere (v6)
139,445/tcp (v6)           ALLOW       Anywhere (v6)
4242 (v6)                  ALLOW       Anywhere (v6)
80,443,9000/tcp (v6)       ALLOW       Anywhere (v6)

```

What gives? :)

---

### Post by sammiev on 2016-02-12
You have me on that one.

---

### Post by cannondale0815 on 2016-03-05
Anyone else able to lend me a helping hand in resolving this issue?

---

### Post by cannondale0815 on 2016-03-16
Anyone? Anyone? Bueller.... Bueller....

Is there another forum where I might have a better chance at getting help?

---

### Post by cannondale0815 on 2017-03-15
Responding to my own post from a while back, I solved my issue by adding the below line into the root crontab:

@reboot /usr/sbin/ufw reload

This line essentially forces a reload of ufw upon every reboot. And it works for me.

---

