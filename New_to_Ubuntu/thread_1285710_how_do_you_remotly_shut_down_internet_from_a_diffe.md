---
title: "how do you remotly shut down internet from a different pc?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by guitarr7 on 2009-10-08
how do you remotely hack into a computer and quit the internet ( or any other application ) on one computer from another ??:P

---

### Post by nhasian on 2009-10-08
its not really a hack, but if you enable ssh on the remote pc, then you can log in remotely and use:

```
sudo killall [program]
``` 

or

```
sudo modprobe -r [wifi_driver]
```

---

### Post by guitarr7 on 2009-10-08
sweet .. ty

---

### Post by carnagex420x on 2009-10-08
top or ps will give you a list of running programs and their pids. To kill a specific one: ```
kill [pid]
``` or ```
killall [program]
```
```
sudo ifconfig [interface] down
``` Will down internet access.

---

### Post by guitarr7 on 2009-10-08
kl..
do you know how to find out the password of someones user..

---

### Post by carnagex420x on 2009-10-08
There are security tools you can use to recover passwords from a Linux box but you need to have physical access to the PC. If you are the admin you should own the root user and don't need the password of the user logged in.
Also if you are trying to "hack" someone this isn't the place to be taught.

---

### Post by anewguy on 2009-10-08
> **carnagex420x said:**
> 
Also if you are trying to "hack" someone this isn't the place to be taught.

Exactly.  I don't think people here normally provide ANY information on these types of requests.  When it is apparent that the OP is trying to find out how to disrupt someone else, even if we think it is a kid who thinks this is "fun", NO information should be provided.

I think our standard reply is something along the lines of:

"We don't support such activity".

Thanks for letting the OP know not to post such things here!

Dave :)

---

### Post by theDaveTheRave on 2009-10-08
> **guitarr7 said:**
> kl..
do you know how to find out the password of someones user..

as carnagex420x said
> If you are the admin you should own the root user and don't need the password of the user logged in.
Also if you are trying to "hack" someone this isn't the place to be taught.

My major security worry is my chip and pin credit card. If some lowlife clones my card, with just 9999 attempts they will get my PIN number (and 9999 attempts is just a few microseconds away with modern pc's).

but here really isn't the place to discuss these things (and are just the ramblins of a mad person on a coffee break)....


and response to the OP

> **guitarr7 said:**
> how do you remotely hack into a computer and quit the internet ( or any other application ) on one computer from another ??:P

I wish I could find a way to "hack" into my desktop, as the monitor on it has died, and being a cheap skate I can't be bothered to get a replacement!

I did set up SSH on it many moons ago, but never used it, as I didn't need to.

As a more direct response to the issue for the OP I often log into a remote server via SSH (not hard to set up).

I can the tell the pc to perform a complete reboot if I desire
```

sudo shutdown -r now

```

(change < now > to a time and it will shut down after that many seconds)

I am guessing that I can tell the pc how long to wait before it reboots too, but I haven't investigated that one yet.


David

---

### Post by 3rdalbum on 2009-10-08
Thread reported - there's nothing about the message that implies that the OP has permission to enter this machine.

---

