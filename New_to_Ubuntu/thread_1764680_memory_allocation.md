---
title: "memory allocation"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by MK-MK on 2011-05-22
hello. I am looking for help on how to get more ram allocated to a program. I looked through many fora and haven t found anything.
I use a statistical package through Wine. When I request (in the statistical program) 2 Go of RAM, it says the "OS refuses to provide memory". However, I have >6 Go free. Is there a restriction to wine's memory allocation? 

I have the new 11.04 ubuntu version on 64 bit computer. I think I didn't have that issue with my old computer (I was limited only by the actual RAM). I also checked this with several version of the statistical software and the memory issue stays. 

any help or hint more than welcome!
MK

---

### Post by 3rdalbum on 2011-05-22
I'm not an expert on Wine, so there might be a way around this.

Wine is kind of like an emulator for Windows, and more specifically 32-bit Windows (because most Windows programs are 32-bit). If you have 4 GiB of RAM, Windows itself grabs the last 2 GiB for itself and leaves only 2 GiB for everything else. As you're probably aware, 4 GiB is the maximum amount of addressable RAM in 32-bit operating systems.

So, the OS (Wine) refuses to provide more than 2 GiB of RAM to a running program, because that's what Windows would do.

There might be a way to override this in Wine, and this is just my theory on how Wine works. I definitely know that 32-bit Windows behaves in this manner. Perhaps obtaining a 64-bit version of your statistical program might cause Wine to work like 64-bit Windows?

---

### Post by MK-MK on 2011-05-23
Thanks for the response. Actually, from what I understand, Wine is [not yet ready to run 64 bits]("http://wiki.winehq.org/Wine64ForPackagers") applications.. (or at least for beginners..) so I ll have to stay with the 32 bits version of the program.
I don't know how to let my program get more ram. I know that on some windows XP server, I can request 5 Go. But here, through wine, I am limited to 1.3 Go... and it's frustrating, because my old computer could do better! (1.5) 
Maybe I can expand the virtual memory? Any other ideas/hint very welcome... There must be a setting I am unaware of.. 
MK

---

### Post by wildmanne39 on 2011-05-23
> **MK-MK said:**
> hello. I am looking for help on how to get more ram allocated to a program. I looked through many fora and haven t found anything.
I use a statistical package through Wine. When I request (in the statistical program) 2 Go of RAM, it says the "OS refuses to provide memory". However, I have >6 Go free. Is there a restriction to wine's memory allocation? 

I have the new 11.04 ubuntu version on 64 bit computer. I think I didn't have that issue with my old computer (I was limited only by the actual RAM). I also checked this with several version of the statistical software and the memory issue stays. 

any help or hint more than welcome!
MKHi, I never been able to do much with wine, so I run virtualbox with windows in side of it and you can give it as much memory  as you want.

---

### Post by MK-MK on 2011-06-02
just a follow up: I did the virtual box and it worked. From my readings, I came to the conclusion that the current version of wine is for 32 bits programs, and that the 64 bit version is still at experimental stage (and I won't experiment myself, as I don't feel confident in ubuntu,, so far).
I will try again when the 64 bit wine version for 64 bit windows application will be stable, and let you know.

---

### Post by wildmanne39 on 2011-06-02
> **MK-MK said:**
> just a follow up: I did the virtual box and it worked. From my readings, I came to the conclusion that the current version of wine is for 32 bits programs, and that the 64 bit version is still at experimental stage (and I won't experiment myself, as I don't feel confident in ubuntu,, so far).
I will try again when the 64 bit wine version for 64 bit windows application will be stable, and let you know.
Hi, I am glad you installed virtualbox and was able to do what you wanted that way. if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

