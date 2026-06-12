---
title: "ubuntu 10.10 system halt"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by donny.davis on 2011-03-26
im using ubuntu 10.10
whenever i try to shutdown
the shutdown screen appears with the dots running
with the msg

ASKING ALL PROGRAMS TO TERMINATE..
SYSTEM WILL HALT NOW......[OK]
DEACTIVATING SWAP......[OK]
UNMOUNTING LOCAL FILESYSTEM.....[OK] 
UNMOUNTING WEAK FILESYSTEM....[OK]
SYSTEM HALT........

but the system won't poweroff
what to do?????

---

### Post by jtarin on 2011-03-26
[Try this suggestion.]("http://www.understated.co.uk/2004/automatic-shutdown-in-ubuntu/")Report back.

---

### Post by sriramrangan on 2011-03-26
Just try: 
```
sudo shutdown now
```

---

### Post by jtarin on 2011-03-26
> **sriramrangan said:**
> Just try: 
```
sudo shutdown now
```
Good suggestion for a manual shutdown but he might possibly be looking for a automatic way....possibly.

---

### Post by donny.davis on 2011-03-26
i wrote it in /etc/modules
but of no use

---

### Post by donny.davis on 2011-03-26
sudo shutdown now

its giving me recovery mode 
and again hangs

also if i use the shutdown button
it displays a message box saying
"close all programs running"
but there r no programs running in the background...
i even disconnect Autoetho and close docky

---

### Post by jtarin on 2011-03-26
Try the command ```
sudo init 0
```if it shuts down properly restart then try to shut down normally.

---

### Post by donny.davis on 2011-03-26
> **jtarin said:**
> Try the command ```
sudo init 0
```if it shuts down properly restart then try to shut down normally.

it didnt work

---

### Post by donny.davis on 2011-03-27
hey ppl should i format my root and install ubuntu again...
reply fast....... 
there is nothing important if i format my root becoz i installed it just a week b4

i need ur suggestions

---

### Post by fabricator4 on 2011-03-27
> **donny.davis said:**
> hey ppl should i format my root and install ubuntu again...
reply fast....... 
there is nothing important if i format my root becoz i installed it just a week b4

i need ur suggestions

A common thread in people reporting this problem is a device conflict.  It can be a wireless lan card, a tuner card, or anything else.  A way to test it is to remove drivers/support for the device (or the device itself) and see if the problems persists. Have a look at [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/721706").

If it didn't happen on the liveCD for example, and didn't happen on a new install but did after support for some device was added, then that would be a clue.

If you were going to reinstall I'd suggest trying 10.04 LTS.  Installing 10.10 again will probably just do the same thing.  Actually 10.04 may do the same thing, but at least you'd be adding more data to describe the circumstances of the problem.

Chris

---

### Post by donny.davis on 2011-04-05
hey ppl i made a .iso file of my Ubuntu cd
and used it in the virtual box in my friend's computer
and it gave the same error(mentioned earlier) while shutting down the virtual machine...

so it may be the problem of the CD... i hope im right..
what u'll feel...

and thankx for ur support and suggestion

---

### Post by Dutch70 on 2011-04-05
You can check the cd for defects...
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by donny.davis on 2011-04-06
Thank you
:)

---

### Post by Dutch70 on 2011-04-06
Your welcome

I'm guessing that was the problem since you've marked the thread solved.

Enjoy!!!

---

