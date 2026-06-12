---
title: "a program is still running"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by guidenhelp on 2009-09-30
I am using Ubuntu 9.04, since i have download it, it work fine with my broadband but recently i have upload it by manager and then after it didn't connect with my broadband. previously when i just switch on my DSL modem it start. I run "sudo pppoeconf" and I got message that another software using my pppoe. now when i shut down or restart ubuntu i got message that "A program is still running" and it says that is unknown program. is anybody have face same problem in Ubuntu 9.04. I am looking for solution for this as I can't connect with my broadband. I am new in Linux world and in Ubuntu.

---

### Post by mikewhatever on 2009-09-30
Can you clarify the following phrase:
> but recently i have upload it by manager
What exactly have you done?

---

### Post by wildman4god on 2009-09-30
Open system monitor, goto the processes tabs and find the process the os is compaining about and end it.

---

### Post by guidenhelp on 2009-09-30
i have update by update manager and when i looked my programs there was connection manager application too. since i saw that i got this unknown program still running error when i log off and it not allow me to connect broadband as "sudo pppoeconf" say "some other program using pppoe"

---

### Post by cariboo on 2009-09-30
If you try to run pppoeconf, make sure pppoe isn't running. Check and see if pppoe is started on boot by typing in a terminal:

```
ps ax | grep pppoe
```

if it is kill the process by typing:

```
sudo kill <pid>
```

where <pid> is the procees id number to the left of the listing you got when you ran the first command.

---

### Post by Excedio on 2009-09-30
> **cariboo907 said:**
> if it is kill the process by typing:
 
```
sudo kill <pid>
```
 
where <pid> is the procees id number to the left of the listing you got when you ran the first command.
 
Would
```
sudo pkill pppoeconf
```
work as well?

---

