---
title: "Newly installed RAM"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by logik6 on 2009-10-29
Hello,

I have just installed a 4GB RAM on my Lenovo Ideapad Y530 on 32-bit processor. BIOS shows that the installed RAM is 4GB but still Ubuntu does not recognize so much RAM. It just shows 2.4GB instead (I am running Windows 7 on virtual box in parallel and that is the reason why I went for the upgrade). Is there any way that Ubuntu can claim the unclaimed RAM without reinstallation?

Thanks.

---

### Post by MrKlean on 2009-10-29
Go here...worked for me ; )

[http://www.webupd8.org/2009/10/use-more-than-3gb-of-ram-in-ubuntu.html](http://www.webupd8.org/2009/10/use-more-than-3gb-of-ram-in-ubuntu.html)

---

### Post by logik6 on 2009-10-30
Worked!!! Thank you

---

### Post by egalvan on 2009-10-30
> **MrKlean said:**
> Go here...worked for me ; )

[http://www.webupd8.org/2009/10/use-more-than-3gb-of-ram-in-ubuntu.html](http://www.webupd8.org/2009/10/use-more-than-3gb-of-ram-in-ubuntu.html)

"We don't think you need a 32-bit kernel, so you won't get it"

One more small step in Ubuntu's march towards becoming Microsoft-II.

Sadder and sadder.

Linux is supposed to be about choices.

---

### Post by mcduck on 2009-10-30
> **egalvan said:**
> "We don't think you need a 32-bit kernel, so you won't get it"

One more small step in Ubuntu's march towards becoming Microsoft-II.

Sadder and sadder.

Linux is supposed to be about choices.

I suppose you didn't quite understand the linked post. Not to mention that you probably didn't even try to find and read the original article from where the short quote in that page was taken.

There is a 32-bit kernel, and now there's also 32-bit-kernel with PAE enabled. Everything you could do with the 32-bit server kernel you can do with the 32-bit PAE kernel. In addition that kernel works better for desktop users who need 32-bit kernel and more than 4GB of RAM. So what's the problem?

Instead of getting less choices we actually now have same amount of choices as before, but they were slightly adjusted to work better for both desktop *and* those servers that might still have 32-bit hardware.

edit: Here's the full quote for you:
> 
Note that the i386-server flavour is being dropped. I can think of no good reason to continue to support a 32 bit server. The 32 bit -generic kernel ought to suffice for those headless implementations that have used the -server flavour in the past, such as home gateways. **All of the -server unique settings can be made at runtime to a -generic{-pae} kernel**, the most important of which are I/O and process scheduler settings.
[https://wiki.ubuntu.com/KernelTeam/Specs/KarmicKernelFlavours]("https://wiki.ubuntu.com/KernelTeam/Specs/KarmicKernelFlavours")

---

### Post by egalvan on 2009-11-03
> **mcduck said:**
> I suppose you didn't quite understand the linked post.
Not to mention that you probably didn't even try to find and read the original article from where the short quote in that page was taken.


I can plead guilty to not quite understanding the linked post,
(the tone of the quote reminded me strongly of Microsoft-think..)

**_BUT_**

Yes, I found the original article, and read almost all of it (90%).
I do take the time to read as much as possible.
Don't always understand, but I try.


So automatic updates to the kernel will also automatically update the "run-time" options?
Or will there be hoops to jump through?

---

