---
title: "What are Daemons?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by ooobooontooo on 2008-12-24
Hi,

So I've been wondering about this. What exactly are daemons? How are they different from other processes? Thanks in advance.

---

### Post by damis648 on 2008-12-24
[URL="http://en.wikipedia.org/wiki/Daemon_%28computer_software%29"]http://en.wikipedia.org/wiki/Daemon_(computer_software)
[/URL] 
Basically, they are processes that usually run in the background to manage something, like a printer, networking, etc.

---

### Post by ooobooontooo on 2008-12-24
So basically it's the computer's job to start init and that pretty much takes care of the rest of the daemons? Why didn't they just choose to have one process that waits in line to be woken up? For memory reasons? But daemons always take up more memory. Why is that true?...Sorry for all the questions.

EDIT: Also, why do programs come in pairs as daemons and separate processes if the daemons are going to be bigger (memory-wise) anyway?

---

### Post by handydan918 on 2008-12-25
> **ooobooontooo said:**
> So basically it's the computer's job to start init and that pretty much takes care of the rest of the daemons? Why didn't they just choose to have one process that waits in line to be woken up? For memory reasons? But daemons always take up more memory. Why is that true?...Sorry for all the questions.

EDIT: Also, why do programs come in pairs as daemons and separate processes if the daemons are going to be bigger (memory-wise) anyway?

The power of the Linux kernel is that it is configurable. Most Linux systems in the world are probably not running desktops, but servers. It would not be very practical to try to set up a "one-size-fits-all" distribution that loaded every possible client, server, etc. The security issues would be ...well, a lot like Windows...
 By it's nature, almost everything in Linux is based on a client/server relationship, and this generally requires two pieces of software.

---

### Post by ooobooontooo on 2008-12-28
Excellent. Thanks, this actually really helped me in my network programming training.

---

### Post by handydan918 on 2008-12-29
> **ooobooontooo said:**
> Excellent. Thanks, this actually really helped me in my network programming training.

Damn! Tricked into helping with homework again!!

:D

---

### Post by ooobooontooo on 2008-12-30
Haha. Actually not really. I was just looking at the client server model and figured out the connection between ftp and ftpd with the help of your explanation. Also, I'm not being forced to do network training. So rest assured. You're not aiding some lazy student who's too lazy to do his homework. You're aiding a lazy person who's trying to learn about Ubuntu.:D Thanks a lot for your help.

---

