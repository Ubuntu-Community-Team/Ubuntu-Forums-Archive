---
title: "wont wake from suspend/hibernate"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by blacque on 2011-03-26
i have another problem on top of brightness problems. my netbook wont wake after i suspend it or hibernate it. only solution is to reboot it. someone help. please take me step by step as i know nothing about programming..im a noob:(

---

### Post by foutes on 2011-03-26
Need info on netbook.

Make

Model

Graphics chip

Etc

Withou the above no one has any idea where to begin.

---

### Post by blacque on 2011-03-26
> **foutes said:**
> Need info on netbook.

Make

Model

Graphics chip

Etc

Withou the above no one has any idea where to begin.



running ubuntu 10.10
kernel 2.6.35-28-generic
atom n450
have no idea what graphics card but its a samsung n150

thanks for responding

---

### Post by CaKiwi on 2011-03-26
Did you install inside Windows (using Wubu)? If so, I don't think suspend/hibernate works.

---

### Post by samacaster on 2011-03-26
What amount of swap space are you using?

---

### Post by blacque on 2011-03-27
> **CaKiwi said:**
> Did you install inside Windows (using Wubu)? If so, I don't think suspend/hibernate works.
i am not using wubu as far as i know. its just ubuntu. it came with win7 starter and i deleted that when it was sluggish...

---

### Post by blacque on 2011-03-27
> **samacaster said:**
> What amount of swap space are you using?
i dont know all i know is that the hard drive is i60 gigs and i have 1gig ram...

---

### Post by foutes on 2011-03-27
In order for hibernate to work you need a swap partition at least double the amount of physical memory.

Even then,for example. 

You can run into a bug in ATI graphics drivers.

Formatting the HD to EXT4 has always resulted in my laptops/netbooks not hibernating,I use EXT3. 

Some laptop/netbooks just do not work with hibernate.



I would add a 2gig partition and that might solve problem.

---

### Post by blacque on 2011-03-28
> **foutes said:**
> In order for hibernate to work you need a swap partition at least double the amount of physical memory.
 
Even then,for example. 
 
You can run into a bug in ATI graphics drivers.
 
Formatting the HD to EXT4 has always resulted in my laptops/netbooks not hibernating,I use EXT3. 
 
Some laptop/netbooks just do not work with hibernate.
 
 
 
I would add a 2gig partition and that might solve problem.
 
 
to partition, would i need to reinstall ubuntu?what is EXT4/3 
please be patient as i have no knowledge when it comes to fiddling with these tech toys

---

### Post by khelben1979 on 2011-03-30
Information about [EXT3]("http://en.wikipedia.org/wiki/Ext3") and [EXT4]("http://en.wikipedia.org/wiki/EXT4") - Wikipedia.

I'm uncertain about the previous poster stating that this issue would be because of EXT4. Do you have any sources for that? I would guess that newer releases of Ubuntu would not have any serious issues with the EXT4 filesystem, any comments on that?

---

