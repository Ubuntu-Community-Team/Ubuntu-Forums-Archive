---
title: "command to shutdown 8.10 server"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-15
What is a easy command to tell the server to shutdown? None of my searches have given a clear indication of such command.

---

### Post by albandy on 2008-12-15
sudo shutdown

---

### Post by bumanie on 2008-12-15
Try this> sudo shutdown -h now

---

### Post by s3a on 2008-12-15
What's the difference between those and sudo poweroff?

---

### Post by louistan3 on 2008-12-15
```
sudo halt now
``` works as well i think.

---

### Post by davec64 on 2008-12-15
From: [http://www.oreillynet.com/linux/cmd/cmd.csp?path=p/poweroff]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=p/poweroff")

> poweroff

poweroff [options]

System administration command. Close out filesystems, shut down the system, and power off. Because this command immediately stops all processes, it should be run only in single-user mode. If the system is not in runlevel 0 or 6, poweroff calls shutdown -h, then performs a poweroff.


Hope that helps!

---

### Post by albandy on 2008-12-15
with shutdown you can specify what to do: halt, power off the computer, reboot...
poweroff is like an alias to shutdown -h now
reboot is like shutdown -r now will reboot de computer
but with shutdown you can specify the time, for example:
shutdown -h 60 will poweroff the computer in 60 minutes

---

### Post by BrandonBan6 on 2008-12-15
```
man shutdown
```

Gives a good run down of the shutdown command.

---

### Post by pshootr on 2008-12-15
Thank you for all the replies. I have just been hitting the power button. :-\"

---

