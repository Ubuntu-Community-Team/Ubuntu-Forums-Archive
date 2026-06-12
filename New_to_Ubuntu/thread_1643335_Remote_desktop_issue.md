---
title: "Remote desktop issue"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by thisisjay on 2010-12-11
I figured out how to use rdesktop to connect to my windows 7 computer and I installed something that makes it possible to connect to my Ubuntu 10.10 computer from Windows, but I cannot see running processes. Its like I'm looking at a different desktop with nothing open. The whole reason that I use remote desktop is to monitor processes on another computer.

---

### Post by diablo75 on 2010-12-11
> **thisisjay said:**
> I figured out how to use rdesktop to connect to my windows 7 computer and I installed something that makes it possible to connect to my Ubuntu 10.10 computer from Windows, but I cannot see running processes. Its like I'm looking at a different desktop with nothing open. The whole reason that I use remote desktop is to monitor processes on another computer.

If I read you right, you're accessing a remote Ubuntu desktop via something like VNC, and you're wanting to display the processes running on the Linux box from your Windows machine.  You can try System > Administration > System Monitor > Processes tab, or open a terminal window and type:

```
sudo top
```

to see processes in a terminal environment.  There are other system monitor programs out there you can try too; check Synaptic Package Manager to see what others are available from the repositories.

---

