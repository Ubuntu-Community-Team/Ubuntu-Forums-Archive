---
title: "Ram ?"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by nynoah on 2009-07-15
I am running 64 bit Ubuntu 9.04

I have 4 gigs of ram installed but my compture only sees 3.1 gig.

Why is that?  Is there something wrong?  I would rather it sees 4 as it should.

If this makes a difference, I am on a Dell 620 lap top with normal Intel graphics card (sucks I know)

---

### Post by NightwishFan on 2009-07-15
Does the intel card suck up the rest of your RAM? Possibly but unlikely. Perhaps check around your bios for some settings releated to the RAM. Perhaps somone else can help you better, I have never even seen a computer with more than 3gb of ram, let alone used.

---

### Post by markharding557 on 2009-07-15
very common issue mine only sees 1.9 out of 2.0?

---

### Post by NightwishFan on 2009-07-15
My Nvidia card takes mine from 1024mb to about 881. If your card uses in the range of 500+mb that might be why. Please note that if it is not integrated then it will not use normal system RAM. Otherwise I think it is a bios issue.

---

### Post by nynoah on 2009-07-15
Its not that my computer is using all the ram.  But it can not see it.  I would be fine if I had 2.0 and only saw 1.9, but this is a lost of nearly 1 gig.  Also given the fact that a 32bit system can only see 3, it makes me question what is going on.

I will poke through BIOS to see if there is some setting in there.

---

### Post by Phlex_de on 2009-07-15
I just checked my ram with 'free' and it only displays 3897 MB total.
I've got a dedicated graphics card but it's under 4096 MB, too. Not as much as your are missing but if your card is integrated it might add up to something similar.

(4 GB of ram, ubuntu 9.04)

---

### Post by philcamlin on 2009-07-15
yeah thats normal

mine sees 1.45 of 1.5GB:popcorn:

---

### Post by theozzlives on 2009-07-15
This troubles me because I have 4 GB RAM coming in the mail for my Dell Inspiron 1525. I know I'm gonna have to go 64 bit, but I want my lappy's RAM to be recognized.

---

### Post by handydan918 on 2009-07-15
> **theozzlives said:**
> This troubles me because I have 4 GB RAM coming in the mail for my Dell Inspiron 1525. I know I'm gonna have to go 64 bit, but I want my lappy's RAM to be recognized.

Don't be troubled. 32 bit Linux can be made to support up to 64 gigs...
[See?]("http://packages.debian.org/sid/linux-image-2.6.30-1-686-bigmem")

---

### Post by 3rdalbum on 2009-07-15
It sounds to me like a BIOS setting that is restricting the amount of recognised RAM.

---

### Post by lavinog on 2009-07-16
Since you have a laptop, I would think that your video card is using some of that memory. I don't know about .9G though.

Some motherboards have a bios option called memory remapping. See if you have it, if so change the setting and see if it makes a difference.
This was a common problem with ATI users when hardy was out, but I think was fixed by updated video drivers.

---

### Post by CompizDoDo on 2009-07-16
it could be that a program is using the ram and not showing you that but you do know that your always using your ram to its extent know matter how much it sais you have

---

