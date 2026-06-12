---
title: "Swap File"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-01-11
When I installed my Ubuntu dual-boot I never set a swap partition. Since I am a bit obsessive-compulsive (not literally), I would like to create a 1GB swap file in my Ubuntu partition (/dev/sda3). Even though 2GB of memory is probably enough, I would like to do this to get the most out of my Ubuntu. What command/commands would I have to run in order to get a 1GB swap file on my /dev/sda3 partition?

---

### Post by yobird42 on 2009-01-11
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

this might help

---

### Post by jimmy the saint on 2009-01-11
A swap partition is typically automatically created.  You may want to check using gparted.

---

### Post by Captain_tux on 2009-01-11
Post the output of **free -t** and we'll go from there...

---

### Post by Martin Marshalek on 2009-01-11
Free -t gives me this:

```
mmarshalek@MTM-laptop:~$ free -t
             total       used       free     shared    buffers     cached
Mem:       1927292     984036     943256          0      48464     470280
-/+ buffers/cache:     465292    1462000
Swap:            0          0          0
Total:     1927292     984036     943256
mmarshalek@MTM-laptop:~$ 
```

That's with Firefox running as well. As for the SwapFAQ, I looked at that but wasn't sure how to modify the code for /dev/sda3 and 1GB. If someone could tell me what code to use that would be great.

---

### Post by Captain_tux on 2009-01-11
Ok, you don't have a swap partition... and of the available RAM, you're using just over half.

Right, so...

Out of curiousity, what are you using the machine for? If it's just for  web browsing, some YouTube, email, chatting, etc., or in other words, nothing critical, IMHO, you don't need to go through the trouble of creating a swap partition.

I realize that's a somewhat controversial statement, but to each their own.

---

