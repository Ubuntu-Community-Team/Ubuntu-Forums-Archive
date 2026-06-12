---
title: "SIOCSIFFLAGS: Operation not permitted"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by maor2 on 2014-02-15
Hello,
I'm trying to use the command :
```
ifconfig wlan0 up
```
And I'm getting this error:
```
SIOCSIFFLAGS: Operation not permitted
```
There is any way to fix it?
thanks

---

### Post by The Cog on 2014-02-15
With privileged commands like that, you need to put the word "sudo" in front. This will ask you to repeat your password before running the command as root (the super-user).
```
sudo ifconfig wlan0 up
```

---

### Post by maor2 on 2014-02-15
> **The Cog said:**
> With privileged commands like that, you need to put the word "sudo" in front. This will ask you to repeat your password before running the command as root (the super-user).
```
sudo ifconfig wlan0 up
```

Thanks for your quick reply, but it's still not working.
The same error :icon_frown:

---

### Post by The Cog on 2014-02-16
I don't know what to try beyond that. Can you post the output of these commands:
```
lspci -v
ifconfig -a
iwconfig
```
and I'll move the thread to the networking forum where you are more likely to get the attention you need.

---

### Post by maor2 on 2014-02-16
> **The Cog said:**
> I don't know what to try beyond that. Can you post the output of these commands:
```
lspci -v
ifconfig -a
iwconfig
```
and I'll move the thread to the networking forum where you are more likely to get the attention you need.
You can see here my pasted commands
[http://pastebin.com/u/Maor_](http://pastebin.com/u/Maor_)

---

