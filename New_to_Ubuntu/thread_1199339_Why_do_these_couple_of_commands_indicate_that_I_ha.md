---
title: "Why do these couple of commands indicate that I have three users?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by adamogardner on 2009-06-28
I'm trying some commands out and it seems they indicate that there are three user instances running concomitantly.  Can you explain what these mean, or if there is something to correct?  Thankyou

---

### Post by lloyd_b on 2009-06-28
> **adamogardner said:**
> I'm trying some commands out and it seems they indicate that there are three user instances running concomitantly.  Can you explain what these mean, or if there is something to correct?  Thankyou

Could you possibly tell us what commands you're trying out, and exactly what it's telling you?  You aren't giving us enough information to understand why you think it's telling you that there are 3 users...

Lloyd B.

---

### Post by adamogardner on 2009-06-28
Is there an award for being stupid?  If not one should be named after me.

adamogardner@CRONUS:~$ uptime
 22:06:04 up 15 min,  3 users,  load average: 0.89, 0.79, 0.66
adamogardner@CRONUS:~$ w
 22:06:12 up 16 min,  3 users,  load average: 0.76, 0.77, 0.65
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
adamogar tty7     :0               21:51    0.00s 45.53s  0.14s x-session-manag
adamogar pts/0    :0.0             21:51   14:28m  0.12s  0.12s bash
adamogar pts/1    :0.0             22:05    0.00s  0.12s  0.00s w
adamogardner@CRONUS:~$ 


this should clear things up a bit.  Sorry

---

### Post by jerome1232 on 2009-06-28
Because you have two terminals open, each one is a new "login" from the same user.

---

### Post by adamogardner on 2009-06-28
thanks

---

