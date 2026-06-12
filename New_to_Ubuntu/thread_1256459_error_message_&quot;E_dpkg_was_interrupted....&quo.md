---
title: "error message &quot;E: dpkg was interrupted....&quot;"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by magicsparklefish on 2009-09-02
I keep getting the following message when I try to install updates, use synaptic package manager and other things....
"E: kpdg interrupted. you must manually run 'kpdg --configure -a' to correct the problem.
E:_cache->open()failed, please report."

I haven't got a clue what this means, how I came to have it or what to do!!!!

---

### Post by Bachstelze on 2009-09-02
> **magicsparklefish said:**
> you must manually run 'kpdg --configure -a' to correct the problem.

[...]

I haven't got a clue what this means, how I came to have it or what to do!!!!

Seems clear enought to me. By the ways, it's "dpkg", and since you have to run it as root, it must be run with sudo, hence:

```
sudo dpkg --configure -a
```

---

### Post by NoaHall on 2009-09-02
kpdg? you mean dpkg? anyway, run the command it gives you, and can you post the result from "cat /etc/apt/sources.list"

---

### Post by magicsparklefish on 2009-09-02
sorry dpkg.....   thing is I have no idea how to run a command, what root or sudo means! (we are talking dumb blonde/brunette computer illterate absolute beginner here!)

---

### Post by NoaHall on 2009-09-02
Oh, okay, go to "Applications -> Accessories -> Terminal" and then type the commands

---

### Post by magicsparklefish on 2009-09-05
Thankyou! I now have access to the magic window!   Unfortunately after entering the command my machine went into a catatonic state for 24hrs until I gave up and turned it off....   It seems that in my case the disk drive is on its last legs so not a lot can be done (I'm told)!  Thanks for taking the time to reply.

---

### Post by Bachstelze on 2009-09-05
> **magicsparklefish said:**
> Thankyou! I now have access to the magic window!   Unfortunately after entering the command my machine went into a catatonic state for 24hrs until I gave up and turned it off...

It was probably just waiting for you to enter your password. ;)

---

