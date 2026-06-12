---
title: "rootdev check"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by ziegegeist on 2009-02-01
Hi folks,

I am unable to boot Ubuntu on my computer. I'm using version 8.10 with a dual boot for Vista. I installed some updates the last time I signed on. When I try to start Ubuntu, it runs through the bar moving back and forth, then the bar fills up. After that, it goes through several things that end in [OK]. Then, I get something roughly like...

rootdev has been started 26 times without a check 

check forced

From there I have a prompt, but I have no idea what to type. 

Any help would be deeply appreciated.

---

### Post by ziegegeist on 2009-02-01
Fixed.

---

### Post by zabien1970 on 2009-02-01
rootdev being checked is a normal process ubuntu does, after every 26 times mounting the hard drive it checks for errors, let it run, the curser is to allow you to hit esc to skip it this time

Edit: See ya got it while I was typing

---

### Post by egalvan on 2009-02-02
> **ziegegeist said:**
> Fixed.

Comne on, don't leave us guessing...

Did you do something that fixed it?

Was it just a waiting game?

HOW was this fixed?

---

### Post by Iwanthelp on 2009-02-07
How did you fix it? I have the exact same problem except 24 mounts.

---

### Post by Iwanthelp on 2009-02-08
So, how'd you fix it?

---

### Post by ziegegeist on 2009-02-10
Sorry to take so long to get back to you. All I did was run it in whatever the Ubuntu equivalent of safe mode is, and from there I honestly don't remember. I am brand spanking new to Linux, and I find that I stumble into and out of problems without ever really understanding what happened. Sorry I couldn't be of more help.

---

### Post by ziegegeist on 2009-02-10
The way zabien1970 described it, is pretty much how it went, as best as I can remember it. I guess I didn't have to start it in safe mode; that's just something I did. Patience is the key, I think.

Many thanks, Zabien!

---

### Post by Iwanthelp on 2009-02-10
Mine also booted into a maintenance shell though, do you know how to run it from theere? Our problem really is we don't know the command, so my brother says "What should we type"?

---

### Post by cariboo on 2009-02-10
I would suggest booting from the LiveCD and once at the desktop open an Applications-->Accessories-->Terminal and type:

```
sudo fsck -a /dev/sdxy
```

Where /dev/sdxy is the partition that needs checking.

Jim

---

### Post by Iwanthelp on 2009-02-11
If you're talking to me, then: There is no partition, go see my new thread in this same forum. Also, I can't boot from live CD 'cause we don't know how to make this computer boot from CD.(HP A305W.)

---

