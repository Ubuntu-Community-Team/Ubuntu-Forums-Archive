---
title: "Want to specifically disable on one user account but not on others on Ubuntu 16.04"
date: 2016-06-17
forum: Networking &amp; Wireless
---

### Post by paul266 on 2016-06-17
I'm hoping this is the right place to ask this question.  Various searches led me to all kinds of cool info, but not what I am specifically trying to do.  I'm new to Ubuntu, but not to linux in general
I have a computer that is going to be available to everyone in the household to play music and videos in the basement.  I have a gigabyte wifi/bluetooth card installed.  I want the normal user accounts to be able to use bluetooth connections, but NOT the wifi connection to the internet.  I want the wifi to work for the admin account ONLY.  Can anyone let me know how to set these permissions, or point me to an appropriate thread?  Thanks in advance!:D

---

### Post by xen3 on 2016-06-18
My post here seemed incorrect, it didn't actually work because it blocked more than I wanted.

But see [http://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html](http://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html). You can block wifi access for a single user using:

```
sudo iptables -A OUTPUT -o wlp2s0 -m owner --uid-owner <username> -j DROP
```

---

### Post by steeldriver on 2016-06-18
Probably the "right" way to do it is via policykit - but good luck finding any usable documentation for that

---

### Post by TheFu on 2016-06-18
The easiest way is to disable the built-in wifi and setup a $10 USB wifi dongle. Then just keep the wifi dongle with you.  For added protection (not really, but enough for kids and Mom), setup the router to block all other MACs so if the kids or Mom buy or borrow another USB wifi stick, it won't connect.

If there's an ethernet port, be certain to disable that as well.

This is also a good way to control kids internet access on a desktop at home. Take the dongle away, when they aren't supposed to use the internet.

---

### Post by xen3 on 2016-06-18
By the way:

> **xen3 said:**
> iptables -A OUTPUT -o wlan0 -m owner --uid-owner root -j ACCEPT
iptables -A OUTPUT -o wlan0 -j DROP

You would need to set those rules to run at startup, for instance in /etc/rc.local

Regards, and good luck.

---

### Post by paul266 on 2016-06-18
Thanks to all, but I think some of the answers here may be a bit beyond me, I'm missing a starting point  (I think I'm rustier than I thought).  Anyway.  I have found something that does WHAT I want, but I'm having trouble making it do it when I want.  I can use  ***sudo ifconfig wlp2s0 down***  to kill the network, but I want it to happen when the computer starts up.  I have been trying to get it to work from /etc/rc.local, but it doesn't seem to be working

---

### Post by TheFu on 2016-06-18
Try:
**/sbin/ifconfig wlp2s0 down**

No need for sudo. Just need the full path and the correct device.  You can also use **rfkill**. That can be enough to confuse many more people, but I don't know if it works on 16.04 or not.

---

### Post by paul266 on 2016-06-18
that path name in rc.local?  the ifconfig command does not work without "sudo" when put in the terminal.

---

### Post by xen3 on 2016-06-19
> **paul266 said:**
> Thanks to all, but I think some of the answers here may be a bit beyond me, I'm missing a starting point (I think I'm rustier than I thought). Anyway. I have found something that does WHAT I want, but I'm having trouble making it do it when I want. I can use ***sudo ifconfig wlp2s0 down*** to kill the network, but I want it to happen when the computer starts up. I have been trying to get it to work from /etc/rc.local, but it doesn't seem to be working


If your wlan device is **wlp2s0 **then the following will instantly kill wifi for a **single user** only:

```
sudo iptables -A OUTPUT -o wlp2s0 -m owner --uid-owner <username> -j DROP
```

**Iptables** is the Linux **firewall**. So you are adding a rule to the **firewall**.

This rule blocks **outgoing traffic** for that single user.

You would replace <username> with the user you want (don't use < > in it).


Alternatively it is also possible to block all users that have a certain **group**. If you set someone's primary group to "users":

```
sudo usermod <username> -g users
```

And then add the following:

```
sudo iptables -A OUTPUT -o wlp2s0 -m owner --gid-owner users -j DROP
```

Then you will have (for this session) blocked all users of group "users" from having wifi access.


Therefore if you did that for every user, and then added:

```
/sbin/iptables -A OUTPUT -o wlp2s0 -m owner --gid-owner users -j DROP
```

to rc.local, then on **startup** this would take effect and block all of those users from having wifi access with that single rule.


Alternatively, of course, if you have 3 users, say **john**, **adam** and **eve**, then you can also do:

```
sudo iptables -A OUTPUT -o wlp2s0 -m owner --uid-owner john -j DROP
sudo iptables -A OUTPUT -o wlp2s0 -m owner --uid-owner adam -j DROP
sudo iptables -A OUTPUT -o wlp2s0 -m owner --uid-owner eve -j DROP
```

Just give it a try. It will work instantly.

The reason for not needing "sudo" in /etc/rc.local, is because rc.local is already executed with **root** privileges.

If you want to clear the changes you have made (reset it to the previous situation), use:

```
sudo iptables -F OUTPUT
```

Good luck. It's really easy, you just need to execute those commands and it will work. Guaranteed. It's absolutely the preferable solution for your case because you won't need to do anything else, ever.

---

