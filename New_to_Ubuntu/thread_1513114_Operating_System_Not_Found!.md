---
title: "Operating System Not Found!"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-06-19
I have a Dell Mini 9 netbook. I was using the previous version of Ubuntu with no problems until suddenly everything shut down on me while I was surfing the web. When I rebooted, it said that my operating system was not found!

I am using a live Ubuntu USB right now. Do I have to reinstall Ubuntu? What's going on? Is all my data gone? What can I do to fix this?

---

### Post by k3lt01 on 2010-06-19
How many times have you tried to reboot? I'm just thinking it may be a one off event that isn't anything to be concerned about.

My desktop does it occasionally but another reboot and everything is fine.

---

### Post by cariboo on 2010-06-19
I sounds like you may have had a hard drive failure. Try opening a terminal and typing:

```
sudo fsck -a /dev/sda1
```

Substitute your device label for the command above.

---

### Post by greenleaves123 on 2010-06-19
I get this:

fsck 1.41.3 (12-Oct-2008)
ubuntu@ubuntu:~$ 

I tried rebooting 3 times and it still said OS not found.

---

### Post by k3lt01 on 2010-06-19
Does Nautilus show your hard drive in Places? I'm assuming your using regular Ubuntu, I don't now what UNR looks like but I'm working on it being similar.

---

### Post by greenleaves123 on 2010-06-19
OK, I just called Dell technical support and I'm still under warranty. They're going to fix the hardware. 

What could cause HD failure? Is it because it is a solid state drive and has been rewritten too many times? That doesn't make sense though. I've only had my netbook for less than 2 years.

---

### Post by greenleaves123 on 2010-06-19
At the blue screen before startup, it said 0 MB hard drive.

---

