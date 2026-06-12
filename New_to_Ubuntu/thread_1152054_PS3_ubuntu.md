---
title: "PS3 ubuntu"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Ambly on 2009-05-07
Im really new on linux, about one month. Tried YLD 5 and YLD 6 before ubuntu 8.10 ppc 64b. And im really happy with this distro. I will upgrade to 9.4 in the future, after i solve the partition problem.

 Im using a 320gb HD on PS3 (instead of the original 40gb). 
 My question is how to do a diferent partition, cause im using just 10gb for ubuntu and about 310gb for ps3 OS. I would like to use something like 250gb for ubuntu and 70gb for ps3 but i cant find how to do that.

 Can you please post a "how to", send me a link or explan me how :confused:

 Thanks!
(hope thats understandable, my first language isnt english)

---

### Post by Hospadar on 2009-05-07
easiest way is to use "gparted"
if you boot off of a livecd (after a clean shutdown), do Alt-F2, then type "gksu gparted" you'll be able to graphically edit/resize/make/delete whatever partitions the way you want

---

### Post by Ambly on 2009-05-07
> **Hospadar said:**
> easiest way is to use "gparted"
if you boot off of a livecd (after a clean shutdown), do Alt-F2, then type "gksu gparted" you'll be able to graphically edit/resize/make/delete whatever partitions the way you want
 
 Hum! gparted!?
 
I will search about that. To get more information.
Thank you very much for you tip.

---

### Post by durand on 2009-05-07
> **Hospadar said:**
> easiest way is to use "gparted"
if you boot off of a livecd (after a clean shutdown), do Alt-F2, then type "gksu gparted" you'll be able to graphically edit/resize/make/delete whatever partitions the way you want

No, I dont think you can do that on the ps3. You need to use the PS3 XMB to reformat the hard drive. I'm not sure if it will wipe your data though.

Please tell me if that worked, I want to try to install linux on my ps3 again. Thanks.

---

### Post by Ambly on 2009-05-08
Im not sure but gparted will take DAYS, at leat that what happen to a guy here in these forum, after 3 days he quit waiting (look for thread =  gparted is to slooooww).

Any sugestions that doesnt mean gparted or "reformat and reinstall"???


Ps: Consider that im talking about ps3 processor not a normal pc.

---

### Post by durand on 2009-05-08
> **Ambly said:**
> Im not sure but gparted will take DAYS, at leat that what happen to a guy here in these forum, after 3 days he quit waiting (look for thread =  gparted is to slooooww).

Any sugestions that doesnt mean gparted or "reformat and reinstall"???


Ps: Consider that im talking about ps3 processor not a normal pc.

Gparted is not slow, it just doesn't support PS3's partition stuff. The only way to do this is to use the XMB unless something changed since the last time I used PS3 linux.

---

### Post by wizard10000 on 2009-05-08
XMB will allow you to repartition the other way too - 10gb for the PS3 and the remainder of the drive for Ubuntu.

---

### Post by Ambly on 2009-05-08
> **wizard10000 said:**
> XMB will allow you to repartition the other way too - 10gb for the PS3 and the remainder of the drive for Ubuntu.

Well that obvious!!!
I know that i can choose either way, 10 for other OS or 10 for PS3 OS, but that is pointless.
Since i got a 320gb HD, 10gb is to small either way.


My question is how (if possible) to do a diferent size partition? 



It must be possible, i will keep searching.
Please post some helpful opinions.

Thank you..

---

### Post by patchido on 2009-05-09
what if you take out the HDD from PS3 and use gparted from a computer? that would be fast and you could configue it as you wish

---

### Post by durand on 2009-05-09
> **patchido said:**
> what if you take out the HDD from PS3 and use gparted from a computer? that would be fast and you could configue it as you wish

That sounds like a good idea. Sorry, I didn't know that the ps3 could only partition fixed sizes.

---

### Post by durand on 2009-05-09
BTW, have you tried posting this on the psubuntu forums?

[http://psubuntu.com/](http://psubuntu.com/)

---

### Post by Ambly on 2009-05-09
> **durand said:**
> BTW, have you tried posting this on the psubuntu forums?

[http://psubuntu.com/](http://psubuntu.com/)

 No i didnt. Im realy unexperient.

 By the way, that idea to put the HDD on a computer maybe good, im not sure that will work cause ps3 is the primary OS and it may reformat (when it gets back into ps3)and use all space as default, all for ps3 OS (then i need to use the xmb to do a partition to use another OS). 
 But for now i cant try that because i just have a laptop (just if i buy a HDD external box).

 I will search on psubuntu and if i dont find what im searching for then i will post.

 Thank you again for you help!:)

---

### Post by Ambly on 2009-05-12
Ok i quit, for now. Ive search and post on psubuntu and it looks that its impossible, at least for now.

I just change the way it was (reformat and install (lol)), now 10gb for ps3 and 310 for ubuntu 9.4, and im using external 40gb for ps3.

 If things change please post!!!

ps.I thing that sony have to update the ps3 firmware, to change the defualt format.

---

### Post by MontelEdwards on 2009-05-12
Im sorry, I really cant help you... but does anyone know what filesystem the PS3 is? i was thinking vfat or something. idk

---

### Post by bigfatgooglefat on 2009-07-17
> **MontelEdwards said:**
> Im sorry, I really cant help you... but does anyone know what filesystem the PS3 is? i was thinking vfat or something. idk

The PS3 uses an encrypted vfat 32 filesystem (because it has a 4GB file size limit). the encryption makes it impossible to edit the partitions with a normal computer.  The linux partition runs inside that encrypted area, most likely on a virtual filesystem created by the ps3's hypervisor. That's what i've been able to conclude based on what i know anyway... in other words, you're at the hands of Sony for what size you can have.;)

---

