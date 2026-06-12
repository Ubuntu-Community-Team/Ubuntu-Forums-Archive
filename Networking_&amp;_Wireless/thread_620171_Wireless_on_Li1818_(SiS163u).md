---
title: "Wireless on Li1818 (SiS163u)"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by ArieM on 2007-11-22
Bought a Li 18181 recently and made it dual boot. In Vista Wireless
functions properly. In Ubuntu Linux 7.10 I installed the SiS163.INF with
ndiswrapper. Devicemanager reports diver installed. But I don't see the
wireless network. in the Networkmanager. Can you help me.

---

### Post by scopo on 2007-12-17
I am having exactly the same problem, can anyone help ?

---

### Post by DerMika on 2007-12-18
I have the same problem. Managed to solve it by following some commands from this thread: [http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy](http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy)

```
sudo modprobe ndiswrapper
```
```

sudo vim /etc/modules

add "ndiswrapper" on a new line at the end of the file
```

this makes it load on boot.



But what i haven't managed to solve, is actually making the connection. Once out of 30 times i'm able to connect, but mostly it fails. Also, when booting, the connection is not made. I have to disable wireless and try again and again until i manage to make a connection. If i have a lucky day, this works...

Are the drivers that buggy?

---

### Post by TheGreatSage on 2007-12-20
[QUOTE=DerMika;3972666]I have the same problem. Managed to solve it by following some commands from this thread: [http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy](http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy)

```
sudo modprobe ndiswrapper
```
[CODE]
sudo vim /etc/modules

**When I get to this point and try to type ndswrapper I get an error " E35: No previous regular expression.**

What am I doing wrong?

---

