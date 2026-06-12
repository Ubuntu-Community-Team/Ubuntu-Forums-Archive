---
title: "^64 bit pros and cons"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by KG4UJD on 2011-03-26
I'm building my first system and I'm tring to deiced on my operating system what are the pros and cons of 64 bit ubuntu?

---

### Post by Dark_Stang on 2011-03-26
In a brief post...

Pros -
 - Handles more than 4GB of RAM
 - Handles multiple processors and multiple cores better than 32 bit
 - Won't freak out in the year 2038
 - Overall increased performance

Cons - 
 - Some software still isn't 64 bit

---

### Post by KG4UJD on 2011-03-26
Im not a computer savvy person but I have to ask whats going to happen in 2032??

---

### Post by Dark_Stang on 2011-03-26
> **KG4UJD said:**
> Im not a computer savvy person but I have to ask whats going to happen in 2032??

Sorry, I made a typo. 2038, not 2032.
> Year 2038 problem
Main article: Year 2038 problem
The original Unix timestamp (time_t) stores a date and time as a 32-bit integer representing the number of seconds since January 1, 1970. During and after 2038, this number will exceed 32 bits, causing the Year 2038 problem (also known as Unix Millennium bug, or Y2K38). To solve this problem, many systems and languages have switched to a 64-bit timestamp, or supplied alternatives which are 64-bit.
- Wikipedia

---

### Post by oldos2er on 2011-03-27
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Cracklepop on 2011-03-27
64 bit is faster thanks to more, and longer registers(although probably not enough for you to notice unless you do a lot of CPU intensive stuff).
64 bit allows you to access 4+GB of RAM without having to use PAE (an extra lookup to access memory, which harms performance)

It's crazy to restrict 64 bit hardware by using a 32 bit OS.

Although there may still be a few programs lagging behind and not offering a 64 bit version, it isn't something to worry about: 64 bit Ubuntu can run 32 bit programs.

---

### Post by aaaaalex on 2011-03-27
I agree with that. Have been reluctant to switch to 64 bit OS i made the 'leap' with Lucid and am currently running Maverick. 

So far i have not found any reason not to use 64 bit.

> **oldos2er said:**
> [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

When reading that please keep in mind that its already ancient - sure the general gist of it remains true but as it says in the post:

> One thing to remember when choosing 64bit or 32bit is that not only is the Linux Kernel progressing the distro of your choice will forever be progressing, as well, and issues that some might of had using one software architecture may not be there in later versions.

---

### Post by 3rdalbum on 2011-03-27
Another interesting thing to note is that Ubuntu 32-bit is compiled to the lowest common denominator; that is, it's not optimised for the later instruction set extensions that modern CPUs come with. You can theoretically run Ubuntu 32-bit on a 386 CPU.

The 64-bit edition is optimised using settings that are appropriate for every 64-bit CPU, and using new features that are available in all 64-bit CPUs but not in every 32-bit CPU.

---

### Post by SoFl W on 2011-03-27
> **KG4UJD said:**
> Im not a computer savvy person but I have to ask whats going to happen in 2032??

You better find out, it is only 27 years away!

---

### Post by Dark_Stang on 2011-03-28
> **3rdalbum said:**
> Another interesting thing to note is that Ubuntu 32-bit is compiled to the lowest common denominator; that is, it's not optimised for the later instruction set extensions that modern CPUs come with. You can theoretically run Ubuntu 32-bit on a 386 CPU.

The 64-bit edition is optimised using settings that are appropriate for every 64-bit CPU, and using new features that are available in all 64-bit CPUs but not in every 32-bit CPU.
I *think* it is 586 or higher, but that is still far from optimized for modern processors.

---

### Post by picman1 on 2011-04-01
2038... just like the year 2000 was going to ruin all PCs. 
Why do people make such nonsense up?

Hey, if you believe such things then don't worry about 2038. Nostradamus predicts the end of the world in 2012.

---

### Post by Jedcurtis on 2011-04-01
When I first installed Ubuntu, I inadvertently installed the 32 bit version.  All was fine for about an hour when I noticed what i did.  After a quick reinstall to the 64 bit version I think my system increased in speed by quite a bit.  I've also found that every piece of software I need is available to me in the 64 bit variant.  I also have 8 gb of really fast ram in my laptop and it definitely makes a huge difference performance wise.
I'll never revert back to the 32 bit architecture.  Like going from a CRAY back to a commodore 64! (IMHO)...

Jed

---

### Post by ikt on 2011-04-01
> **picman1 said:**
> 2038... just like the year 2000 was going to ruin all PCs. 
Why do people make such nonsense up?

huh?

You've compared something that is going to happen, to a sensationalised newspaper headline.

2038 WILL affect computers running 32 bit software.
2000 DID affect computers running outdated software, but hundreds of millions of dollars was spent fixing the problem so the PCs that were effected didn't fall over.

"y2k bug is going to cause planes to fall out of the sky and all PCs" was a newspaper headline, and the reason 'people make such nonsense up' is to sell fear and newspapers to people who don't know what's going on, and as you can see, it works.

---

