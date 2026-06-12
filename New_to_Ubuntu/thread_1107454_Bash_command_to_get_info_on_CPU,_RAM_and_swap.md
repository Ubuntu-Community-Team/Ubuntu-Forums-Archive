---
title: "Bash command to get info on CPU, RAM and swap"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-26
Hi,
I was wondering which bash commands can tell: 
how many CPUs, 
how many cores of each CPU, 
how big are the RAM, 
how big is the swap?
Thanks a lot!

---

### Post by yeats on 2009-03-26
You only need one command:

```
top
```

You'll see all that your looking for.  "1" (the number one) toggles the processor core information.

---

### Post by mrjohnston on 2009-03-26
I would recommend htop, basically the same as top, but much easier to read and navigate so its a lot easier on the eyes and brain.  Its in the repos, but you will need to install it.  Should meet all your needs (and then some).

---

### Post by flylehe on 2009-03-26
Thanks!

chrissharp123:
For the processor core information, what do you mean by "'1' (the number one)"? Here is what top gives:
> top - 20:11:48 up 101 days,  6:37, 149 users,  load average: 3.02, 3.24, 3.35
Tasks: 330 total,   3 running, 326 sleeping,   1 stopped,   0 zombie
Cpu(s): 25.0% us,  0.2% sy, 12.5% ni, 62.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:  32958132k total, 28091720k used,  4866412k free,   393168k buffers
Swap: 32764556k total, 11450952k used, 21313604k free,  7618344k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
...................

---

### Post by x33a on 2009-03-26
press 1 after opening top, and you'll see what he means :)

---

### Post by mikko.rantalainen on 2012-09-14
> **flylehe said:**
> 
how many CPUs, 


```
cat /proc/cpuinfo | grep "physical id" | sort -u | wc -l
```

> 
how many cores of each CPU, 


I guess it's possible to have different core count per socket. This will output multiple core counts if some sockets have different core count:
```
cat /proc/cpuinfo | grep "siblings" | sort -u | cut -d: -f2
```

> 
how big are the RAM, 


```
grep MemTotal /proc/meminfo
```

> 
how big is the swap?


```
grep SwapTotal /proc/meminfo
```

---

