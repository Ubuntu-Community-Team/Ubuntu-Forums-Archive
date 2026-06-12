---
title: "SSH &amp; Gui remote access."
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by lawentzel on 2008-02-20
Here is a strange one.  I had this working yesterday.  Now it suddenly doesn't want to work.

I have SSH setup on my home system.  I have my router configured to do port forwarding to that computer.  I can log in to my computer using PUTTY.  All of that is working fine.

I am now getting an error message on logging into my home computer which reads:

```
/usr/bin/X11/xauth:  error in locking authority file /home/lee/.Xauthority
```

I have XMing installed on my work computer.  Yesterday I could type "sol" as and example and the Solitary game would pop up using the combination of PUTTY and XMing.  Today it doesn't work.  The two things that changed was, I rebooted both computers, and I shut off Remote desktop on my home computer seeing as VNC it isn't nearly as secure as SSH.

Any suggestions?  Thanks.

---

### Post by lawentzel on 2008-02-20
Solved this.  The setting in PUTTY had somehow gotten changed or messed up.  After verifying both SSH tunneling and X11 forwarding was setup, it suddenly worked.  So... Life is good.

---

