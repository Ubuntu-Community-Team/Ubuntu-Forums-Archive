---
title: "combine hard drives-an easy way?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by derryt on 2010-04-25
Hi all,my current hd is nearly full-about 3 gb left spare!

I found an old hd that works fine and mounts ok to be used,but is there any way i can get ubuntu to read them as 1 large hd rather than seperate? Im not the most texhnically minded so if theres an easy solution i'll give it a go,if not i shall just carry on as is for now!

Thanks in advance,

Derry

---

### Post by Temposs on 2010-04-25
They are separate devices, so no, there's no way to read them as one large hdd.

---

### Post by zekopeko on 2010-04-25
> **Temposs said:**
> They are separate devices, so no, there's no way to read them as one large hdd.

That's not true.

1. I *think* that you could use this: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

   But you would probably have to format your drive. 

2. Another far simpler option is to add the extra disk to fstab and mount it inside your home directory. You could use any name for the directory.

3. Another option is to use something like unionfs with number 2: [http://en.wikipedia.org/wiki/UnionFS](http://en.wikipedia.org/wiki/UnionFS)

Disclaimer. I haven't tried any of that.

---

### Post by Temposs on 2010-04-25
I stand corrected. I suppose you could still say there's no **easy** way to do this, for a non-technically minded user.

---

### Post by zekopeko on 2010-04-25
> **Temposs said:**
> I stand corrected. I suppose you could still say there's no **easy** way to do this, for a non-technically minded user.

Not true again :P

[https://launchpad.net/nautilus-easy-unionfs](https://launchpad.net/nautilus-easy-unionfs)

---

### Post by Temposs on 2010-04-25
Reverse socratic method ftw >_>

---

