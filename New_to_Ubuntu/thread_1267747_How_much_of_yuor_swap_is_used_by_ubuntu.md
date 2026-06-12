---
title: "How much of yuor swap is used by ubuntu"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by sumeshgupta on 2009-09-16
I have 2GB RAM and have created 1.5GB swap partition. However my conky has never shown swap being used. RAM usage fluctuates with  each program I run. Swap is always 0/1.5GB. Why is it therefore necessary to create a swap partition? or is conky showing wrong figures?

---

### Post by Mike_IronFist on 2009-09-16
> **sumeshgupta said:**
> I have 2GB RAM and have created 1.5GB swap partition. However my conky has never shown swap being used. RAM usage fluctuates with with each program I work with. Swap is always 0/1.5GB. Why is it therefore necessary to create a swap partition? or is conky showing wrong figures?

Whenever a computer running Ubuntu hibernates, it saves all the data it has in RAM to the swap partition.

In addition, Swap does other cool stuff. It allows your computer to run faster because it will allocate little bits of itself to processes that Ubuntu needs to run, and it also allows you to use up more than your system's RAM, since it can operate as virtual memory.

And if that doesn't sound all that intriguing, remember that it's still needed for hibernating, so it's worth having around.

---

### Post by pmlxuser on 2009-09-16
the figures are right. in the ages where RAM was so small the essence of a swap was very big nowadays the essence of Swap is very minimal and you have observed its almost never used. But may be sometimes you will use it. usually swap is used when RAM is Full, swaping running programs with idle to utilise the limited resource of RAm , but with 2GB of RAM and normal computer use it is enough not to require a swapping process.

---

### Post by misfitpierce on 2009-09-16
Well until you use up most of your ram, atleast 80% of it you wont see your SWAP go anywhere... Its ram written on harddrive which is slower but there in case of emergencies.

I only got a GIG of ram but most I ever seen used up was like 1% of 2.9GB when I had tons of stuff open using a ton of ram... Atm its 0.1% of 2.9GB. I had a bunch of stuff open earlier though like a billion tabs in firefox and video editor with LMMS music maker and some photo editing going on and so on.

---

### Post by kixome on 2009-09-16
0% of 1.7gig

---

### Post by ausgado on 2009-09-16
try reading the following item on Debian [http://www.debian.org/releases/stable/ia64/apcs03.html.en](http://www.debian.org/releases/stable/ia64/apcs03.html.en) this may help as Debian is the base OS for Ubuntu. Hope this helps.

---

### Post by sunchiqua on 2009-09-16
10-200Mb / 1024Mb ( depends on what I do .. video transcoding takes a lot more than that ).

---

### Post by earthpigg on 2009-09-16
> How much of yuor swap is used by ubuntu

none, i dont have one :D

---

### Post by slakkie on 2009-09-16
0% atm of 502 Mb

---

### Post by TenPlus1 on 2009-09-16
same here, no swap needed...

---

### Post by tomBorgia on 2009-09-16
Just had to expand mine to 3GB... I was maxing out 1GB doing day to day stuff (it's an old computer only 1GB RAM). So there [-(

---

### Post by Perfect Storm on 2009-09-16
I have 4GB RAM and I made a 2GB of swap. The reason I did that is because I like to heavy stuff like image editing, video editing and audio editing. If you're do stuff like that, it's highly recommended to set a big swap (or a lot of RAM).

But normally when I gaming/listening music/web etc. It don't get used.

---

### Post by NightwishFan on 2009-09-16
Here is a good link:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


I would always have a swap, just in case. It is also needed for hibernation. Sometimes when I run GIMP using an SVG or a game, my swap gets used.

---

### Post by del_diablo on 2009-09-16
The requirements for hibernation is a bit more than the amount of RAM you got.
I would not recommend having it as a file at all, windows does with that it freely scales upwards that and we all see how much it suffers from fragmentation.

---

### Post by wojox on 2009-09-16
1.5 G, Swap gets used on heavy flash pages.

---

