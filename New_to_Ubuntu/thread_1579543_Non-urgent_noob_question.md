---
title: "Non-urgent noob question"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by juil on 2010-09-22
I would just like to know what's taking all the memory????
I'm only running chromium, terminal and gedit...

---

### Post by formaldehyde_spoon on 2010-09-22
It's caching files or programs you have used/will use, to improve performance.

---

### Post by juil on 2010-09-22
Is this a constant process because it's been going on for a while now...

---

### Post by SmokeyThePanda on 2010-09-22
O.o I've never seen that. It shows you only using like..10% of your memory, yet you're nearly using all of it.

---

### Post by formaldehyde_spoon on 2010-09-22
> **juil said:**
> Is this a constant process because it's been going on for a while now...

Yes.  See here for an explanation: [http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

Run ''free -m'' in a terminal and look at the -/+ buffers/cache line if you want to know how much you're currently using.

---

### Post by juil on 2010-09-22
So, we had a power outage this morning and my computer experienced a hard reset... -_-

Anyway here is the result of 'free -m'
As you can see the swap memory is hardly being used...or should i say not being used at all.
Is there something to be said about the allocation of memory?

---

### Post by migs73 on 2010-09-22
Try the code

 ```
top
```

This gives you a look at all your processes and the system usage. From this you should be able to see what is eating your RAM.

---

### Post by juil on 2010-09-23
Ok, this is weird. It's not matching up as you can see in the screenshot, unless i setup conky config wrong. Here is the MEM line from conky file:

```
MEM $alignc $mem / $memmax $alignr $memperc%
$membar
```

EDIT: I think it's right because i just ran sysmonitor from screenlets and it's showing RAM 59%....
Is this a bug??

---

### Post by Rubi1200 on 2010-09-23
You are also running Compiz; that can also cause problems sometimes.

---

