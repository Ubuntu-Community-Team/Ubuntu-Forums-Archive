---
title: "Synaptic Error..."
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Papa-san on 2009-04-01
Hi
I was trying to do some updates, and ran into several problems with it. 
I am using 8.04, and hope these issues can be resolved. 

I initially ran 'Update Manager', and there were 15 things it couldn't find. Of those 15, one was reported as 'broken', so I went into Synaptic and used the broken package filter. This is what I got:
```
E: /var/cache/apt/archives/linux-headers-2.6.24-23_2.6.24-23.48_all.deb: failed in buffer_write(fd) (10, ret=-1) 
```It won't let me copy the results from the terminal in Synaptic where all of the details of this epic fail are. I am attaching a screenshot in hopes that someone can read it and help me figure out what to do next...

Update Manager:
It looks like there are 15 files that were returned
"404-Not Found"

---

### Post by zvacet on 2009-04-01
You get a message :"No space left on device."Make some space with this commands

```
sudo apt-get autoremove
```

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

after that 

```
sudo dpkg --configure -a
```

---

### Post by cariboo on 2009-04-01
The first thing to do is to go to SYstem-->Administration-->Software Sources and change to a different server. then open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get update
```

next type:

```
sudo apt-get install -f
```

after the missing dependencies have been installed type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

THe above commands should solve your problem.

Jim

---

### Post by egalvan on 2009-04-01
> **cariboo907 said:**
> 

```
sudo apt-get update && **[COLOR="Red"]sudo apt-get dist-upgrade[/COLOR]**
```

THe above commands should solve your problem.

Jim

Will the above code be consistent with the OP's original question?
The OP stated:
**I was trying to do some updates**

Isn't **[COLOR="Red"]dist-upgrade[/COLOR]** totally different from **update** ?

---

### Post by Papa-san on 2009-04-01
I want to continue using 8.04,
isn't ```
sudo apt-get dist-upgrade
``` going to have me using Jaunty?
I tried that one before, and it left me with more problems right off the bat than I had with Dapper...

EDIT:
I went ahead with all of the recommended commands (except for the last one) and it seems to have corrected most everything. (One of the updates was the w32 codecs, and that one failed, but I'm not too worried about that particular one...)

I guess it didn't take when I tried to resize my root partition a while back...
I'll try that again...
Thanks to all of you!

---

### Post by Papa-san on 2009-04-01
OK... So how do I mark this as 'Solved'. It doesn't show up in 'thread tools' anymore...

---

### Post by drs305 on 2009-04-01
> **Papa-san said:**
> OK... So how do I mark this as 'Solved'. It doesn't show up in 'thread tools' anymore...
I think the 'forum-approved' method is now to attach a solved tag to the thread. 

You can also hit Edit,then Edit again and change Title, but it won't be seen until someone opens the thread. You could also open the thread and change the first word to 'Solved'. Again it won't be shown in the title but if someone hovers over the listing to preview the post they will see 'Solved' in the balloon.

---

