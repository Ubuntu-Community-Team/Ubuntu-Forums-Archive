---
title: "those this mean i have a 64bit system"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by cameronedwards on 2009-10-29
I had a 32bit version of windows on this computer but since installing ubuntu i think i that i actually have a 64 bit system.

---

### Post by Teber on 2009-10-29
looks that way. try booting a 64 bits live cd. it that works you'll know you got a 64 bits cpu.

---

### Post by Treepwood on 2009-10-29
It means your system hardware is capable of running 64bit OS.

---

### Post by Joeb454 on 2009-10-29
The CPU is a 64 bit *capable* CPU, however you have a 32 bit system installed currently (the platform shows i686, which is 32 bit).

If your platform said x86_64, you would be running a 64 bit system :)

---

### Post by SkyNet2029 on 2009-10-29
This just means your cpu can run 64 bit. Its showing a dual core cpu with 64 bit extensions enabled. So you should be able to run 64 bit ubuntu. The i686 kernel is a modified 32 bit processor for celerons and up or athlons and up. 
Just a thought though, you should defineltely give the 64 bit ubuntu a shot as it would greatly improve performance.
The answer to your question:
You have a cpu capable of 64 bit operations but are running a 32 bit OS on it.

---

### Post by Scunnered on 2009-10-29
How does one ascertain which version is loaded on to the system.

I believe that I should be able to run a 64 bit version but am unsure which version I have.

---

### Post by philinux on 2009-10-29
Apps>access>terminal

```
uname -a
```

Linux philcb-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 **x86_64** GNU/Linux

---

### Post by Scunnered on 2009-10-29
**philinux**

Many thanks for your reply.

My system is listed as i686 so if I read your post right I should be using x86_64?

I will leave things to bed down with the server before I do anything now.  An initial look at things just showed the 32bit download at the moment.  

I like so far what I see so I can be patient.

Again thanks vm

---

### Post by realzippy on 2009-10-29
If this:

Intel Dual Core T2390 1.86Ghz; Intel GMA x 3100 graphics, Atheros AR242x802.11 a/b/g. 1GB RAM

is your system,the T2390 is a 64 bit CPU.

---

### Post by cameronedwards on 2009-10-30
> **SkyNet2029 said:**
> 
Just a thought though, you should defineltely give the 64 bit ubuntu a shot as it would greatly improve performance.
 You have a cpu capable of 64 bit operations but are running a 32 bit OS on it.
thanks but i spend so much time modifying ubuntu that i'm not sure if i want to do it all again. also i lack the equipment necessary to backup my stuff (i lose things easily).

---

### Post by philinux on 2009-10-30
If it ain't broke why fix it. ;)

---

### Post by Matt__ on 2009-10-30
> **SkyNet2029 said:**
> 
Just a thought though, you should defineltely give the 64 bit ubuntu a shot as it would greatly improve performance.

That is a completely unqualified statement Sky. Your claimed performance would rely on many other hardware factors such as installed RAM, particularly as memory addressing is doubled in size.
64bit also has some other bugbears, like flash and java often being a pain to set up. I have both 64 and 32 Ubuntu 9.04 on my laptop for comparison and apart from spending longer getting everything working in 64bit there is no performance difference.
(everyday use..burning dvds/browsing/music/games)

In my opinion...IF IT AINT BROKE DONT TRY TO FIX IT :P

---

