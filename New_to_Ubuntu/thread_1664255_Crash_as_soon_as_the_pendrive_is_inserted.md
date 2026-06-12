---
title: "Crash as soon as the pendrive is inserted"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by mp87 on 2011-01-10
Hi everybody,

this is my first post here, I hope not to do too many mistakes.
My problem is that as soon as I insert my pendrive (Kingston Data Traveler 101 G2), the system completely locks up and I'm unable even to move the cursor, so that the only solution is to shut down the laptop (Dell XPS 15).
Initially I thought that the problem could be related to a script that allowed to mount iso images simply right clicking on them and choosing on the menu the appropriate voice, therefore I removed it; but the problem still persists.
Do you have any suggestions? Please do ask me questions, I'm a totally newbie to linux systems.

Mattia

---

### Post by soapytheclown on 2011-01-10
Can you boot and operate with the pendrive inserted from cold?

If that doesnt work, the only thing I can suggest is this, honestly its not a perfect solution but this is the best I can suggest:

open a terminal and type in:
```
gedit /var/log/kern.log
```

go down to the bottom and note whats the last thing there. 

plug your drive in a let your system lock up.

As soon as it does hold:

```
Ctrl+Alt+SysReq
```

and type in the word 

```
reisub
```

That should turn your machine off in the safest possible way. Then take your drive out and boot your machine back up. Go back to that original file and see if those logs provide anything useful. (or post them here hopefully one of us can pick up whats going on)

---

### Post by corncob on 2011-01-11
> **mp87 said:**
> Hi everybody,

this is my first post here, I hope not to do too many mistakes.
My problem is that as soon as I insert my pendrive (Kingston Data Traveler 101 G2), the system completely locks up and I'm unable even to move the cursor, so that the only solution is to shut down the laptop (Dell XPS 15).
Initially I thought that the problem could be related to a script that allowed to mount iso images simply right clicking on them and choosing on the menu the appropriate voice, therefore I removed it; but the problem still persists.
Do you have any suggestions? Please do ask me questions, I'm a totally newbie to linux systems.

Mattia

I'd check out the pen drive first thing.  Does it work in another computer?

---

### Post by mp87 on 2011-01-11
> **soapytheclown said:**
> Can you boot and operate with the pendrive inserted from cold?

Unfortunately not. It seems like the system is trying to load the pendrive, but is unable to do it. I think that because two days ago I inserted the pendrive and the system recognized it, without crashing. Then I removed and reinserted it, but Ubuntu locked up.

I cannot even follow your procedure, since now I cannot access normally to Ubuntu (just the recovery mode works) :(

> **corncob said:**
> I'd check out the pen drive first thing.  Does it work in another computer?

Well, I tried it on different computers with Windows XP and it always worked properly. Up until few days ago it worked finely also with my Ubuntu.

---

