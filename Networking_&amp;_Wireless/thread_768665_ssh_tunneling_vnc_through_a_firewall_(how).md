---
title: "ssh tunneling vnc through a firewall (how?)"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by tamman2000 on 2008-04-26
I posted this yesterday, under a different subject...  But only 8 people looked at it, so I guess I must have had a bad subject on the post, I am trying to be more descriptive this time...

I have a Kubuntu box at work (lets call it desk.work.com) and a Ubuntu laptop at home (lets call it lap.home.org) and a mac laptop at home too (mac.home.org). Between my desk.work.com and the outside world is login.work.com (a red hat box which does firewall duty on which I don't have sudo).

I usually don't have to do much work via ssh because I have almost everything I use regularly on at least one of my laptops, but I have recently taken on some new modeling tasks that involve software that can only be used on desk.work.com because of licensing...

I will be telecommuting for a week soon, and I would like to be able to use vnc as I have heard it is much faster than ssh -X.

Right now to run a X app on desk, displayed at lap or mac I
ssh -X login.work.com, and then from login I ssh -X desk.work.com.

Can I do something similar with vnc?

Thanks,
Tamman2000

---

### Post by Monicker on 2008-04-26
My response to a similar thread might help.

[http://ubuntuforums.org/showthread.php?t=768341]("http://ubuntuforums.org/showthread.php?t=768341")

---

### Post by tamman2000 on 2008-04-26
Thanks, 

so would I 

ssh -C -L 5901:localhost:5901 login.work.com

and then from login

ssh -C -L 5901:localhost:5901 desk.work.com

and then on lap.home.org

vncviewer localhost:0

Is that how I would handle the extra hop?

(please forgive my novice status when it comes to ssh tunneling...)

Thanks,
Tamman2000

---

### Post by Monicker on 2008-04-26
Should be able to simplify that a bit. From lap.home.org:

```
ssh -C 5901:desk.work.com:5901 username@login.work.com
```

The -C is for compression, and optional.  You might try with and without to see if there is performance difference.


If vnc is using port 5901 then you would do:

```
vncviewer localhost:1
```

..from your home machine.


5900 = :0
5901 = :1

and so forth.....

---

