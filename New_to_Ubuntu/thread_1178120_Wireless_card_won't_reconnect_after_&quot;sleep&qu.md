---
title: "Wireless card won't reconnect after &quot;sleep&quot;"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by pcb2x on 2009-06-04
Hi;

I've posted this problem several times under "Network" but I'm getting no responses.  Hoping for at least a hint here.

I'm running Ubuntu 9.04 using Gnome
.
When I awaken the computer from "sleep" my wireless card (D-Link WUA 1340) does not automatically connect. However when I boot the computer no problem - it connects with no problem.

To get the card to connect I have to unplug it and then plug it back in. It's a bit of a hassle (considering the computer's kind of hidden under my desk).

Does anyone have any suggestions?

I'm pretty new to Linux but I'm not bad at following suggestions and directions.

Thanks in advance.
Perry.

---

### Post by nandemonai on 2009-06-04
You could always try this in terminal after a resume:

```
sudo /etc/init.d/networking restart
```

---

### Post by chrisod on 2009-06-04
I had a similar problem with 8.10 and found that if I put the computer to sleep via the command line it woke without issue. If I used to GUI to sleep - it frequently crashed on wake. Might be worth trying in your case too. IIRC the command was
```

sudo /etc/acpi/sleep.sh
```

---

### Post by tlaurent on 2010-12-19
I had the same problem and followed the steps given here ([http://www.twentyways.com/2010/11/19/fixing-wireless-issues-with-asus-eeepc-1000he-running-ubuntu-10-10/]("http://www.twentyways.com/2010/11/19...-ubuntu-10-10/")) and that solved it.
For information, I'm running Ubuntu 10.10 on eeePC 901.

---

