---
title: "Networking (sort of) died"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by lenmorgan on 2010-07-03
I'm not truly a beginner since I've been using Linux since the 0.99.xxx kernel but I'm fairly new to Ubuntu.  

I HAD a working server system that I use at my house and everything was fine.  I run an SSH server and a Postgres database on it.  Something happened (or I did something to it that I can't remember) and now I don't have any ability to communicate with it at all from my Windows box.

All of my server daemons are running and I can use them locally on the machine.  What's odd (to me anyway) is that if I ping from my windows box, I get the four lines from the windows box saying "host unreachable" but when it's done, it says "4 packets received, 0 packets lost".

I'm thinking this is a very simple problem since ALL of the networking has gone away and it ALL used to work.  Any ideas on where to start?

Thanks!

len

---

### Post by Virigoth on 2010-07-03
> **lenmorgan said:**
> I'm not truly a beginner since I've been using Linux since the 0.99.xxx kernel but I'm fairly new to Ubuntu.  

I HAD a working server system that I use at my house and everything was fine.  I run an SSH server and a Postgres database on it.  Something happened (or I did something to it that I can't remember) and now I don't have any ability to communicate with it at all from my Windows box.

All of my server daemons are running and I can use them locally on the machine.  What's odd (to me anyway) is that if I ping from my windows box, I get the four lines from the windows box saying "host unreachable" but when it's done, it says "4 packets received, 0 packets lost".

I'm thinking this is a very simple problem since ALL of the networking has gone away and it ALL used to work.  Any ideas on where to start?

Thanks!

len

Did you accidently enable iptables or modify your existing tables?

---

### Post by lenmorgan on 2010-07-03
Well, now I feel stupid!  iptables WAS on but after executing:

service iptables stop

I'm still having the same problem.  Is there something else that could have been turned on?

len

---

