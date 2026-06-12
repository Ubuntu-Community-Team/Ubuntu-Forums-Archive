---
title: "What Exactly Does Swap Memory Do?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-02-01
I seem to remember reading that swap memory is vital to any linux system functioning well.

I've got a swap partition of about 2.5GB, but whenever I've looked at System Monitor, it has never shown it as being any more than 2% used.

Which makes me ask the question here as to what swap memory is meant to do? And how does it improve linux's performance?

---

### Post by audiomick on 2010-02-01
Hi Roger.
look here
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by mcduck on 2010-02-01
It doesn't increase performance, it allows the system to work when it has less RAM than what your running applications need. Your computer's processor can only work with data it gets from RAM, but when there's not enough RAM available some data from meory can be moved to swap partition on your hard drive to free more RAM for the current task. Then when that data is needed again something else has to be moved to swap instead, and the data read back to memory. Considering that accesssing data from the hard drive takes thousands of times longer (I'm not even exaggerating!) than accessing data from RAM takes, your processor will spend most of it's time waiting for data to move from swap to RAM and everything you are doing will become slow. Swapping is not something you'd like to happen. :P

Still, Swap is also used when you hibernate the machine. All data from RAM is written to swap partition and the computer is powered down. When you boot the data is read back from swap to RAM and the system can continue from where it was left. For this purpose you should have at least as much swap space as you are using RAM, but to be safe you'd better have at least as much swap as your system's total RAM.

(Linux kernel also uses little swapping as part of memory management, when it's not sure if some cached data could be dropped it might move it to swap for a while, and then drop it if it wasn't needed. Ths is why you often see just a little bit of swap use even ewhen you have plenty of free RAM available).

If you don't want to hibernate the machine, and you have plenty of RAM available, you don't usually need any swap partition and having one will not increase performance in any way. On the other hand hard drives are usually large enough that using a gigabyte or two for swap partition might be a good idea just in case you'd some day need it.. ;)

---

### Post by Roger Allott on 2010-02-01
Thanks for the answers.

If swap is needed for hibernating a linux machine, what does Windows use when it hibernates (or sleeps)?

---

### Post by mcduck on 2010-02-01
> **Roger Allott said:**
> Thanks for the answers.

If swap is needed for hibernating a linux machine, what does Windows use when it hibernates (or sleeps)?

Windows writes the memory data into a hidden file located in your C: drive ("hiberfil.sys" on WinXP).

Suspending (or sleeping) doesn't power off the machine completely, RAM stays powered so there's no need to store that data anywhere else.

---

### Post by muteXe on 2010-02-01
To successfully hibernate and restore your ubuntu after a hibernate, not only do you require swap you also require something known as a "fekking miracle" :)

---

### Post by audiomick on 2010-02-02
> **muteXe said:**
> To successfully hibernate and restore your ubuntu after a hibernate, not only do you require swap you also require something known as a "fekking miracle" :)

Is that what is wrong with mine? Hmmm... best go out and buy one of those then....;)

---

### Post by lotharmat on 2010-02-02
> **audiomick said:**
> Is that what is wrong with mine? Hmmm... best go out and buy one of those then....;)


Apparently "Best Buy" deal in miracles!

---

### Post by audiomick on 2010-02-02
> **lotharmat said:**
> Apparently "Best Buy" deal in miracles!

Oh, good! Do they have branches in Germany?;)

---

### Post by lotharmat on 2010-02-02
> **audiomick said:**
> Oh, good! Do they have branches in Germany?;)

No - German efficiency would not allow them to trade!!:D

---

### Post by bolucpap on 2010-02-02
Whenever I hear the words "German Efficiency", I think "trust me to get the hard one".

---

### Post by audiomick on 2010-02-02
> **bolucpap said:**
> Whenever I hear the words "German Efficiency", I think "trust me to get the hard one".

sometimes I think that is just a synonym for "over engineered"...;)

---

### Post by cascade9 on 2010-02-02
> **mcduck said:**
> Windows writes the memory data into a hidden file located in your C: drive ("hiberfil.sys" on WinXP).

Suspending (or sleeping) doesn't power off the machine completely, RAM stays powered so there's no need to store that data anywhere else.

This is one of the things about windows that I always get annoyed at. Easy enough to move your swapfile to another partition with windows (which I always do, its a good idea for various reasons), but moving hyberfil.sys is impossible...as far as I know anyway.

---

