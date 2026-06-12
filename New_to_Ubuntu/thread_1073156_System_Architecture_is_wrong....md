---
title: "System Architecture is wrong..."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by djstormx on 2009-02-18
I recently installed Ubuntu on my system and am using its dual boot feature.  I've been trying to install Shockwave on my system, but for some reason the installer/downloader keeps giving me an error saying "package architecture (i386) does not match system (amd64)".  Now, I know that the CPU (an Intel Core2Quad Q9400) supports a 64bit environment, but why is Ubuntu saying my system architecture is amd64?

---

### Post by fooman on 2009-02-18
> **djstormx said:**
>   Now, I know that the CPU (an Intel Core2Quad Q9400) supports a 64bit environment, but why is Ubuntu saying my system architecture is amd64?

because you have installed the 64bit version of ubuntu.  it is recognized as "amd64" because amd was the first to come up with 64bit processors and thus they coined the phrase so to speak....it does not mean that ubuntu thinks you have an amd cpu.  it uses that name for 64bit installations with both amd and intel 64bit processors.

i know i didn't explain it very well,  but i hope that helps.

---

### Post by ashwinhgtx on 2009-02-18
Isn't Shockwave a Windows only software? Are you trying to install it through wine? I'm not sure if wine supports 64bit yet.

---

### Post by mcduck on 2009-02-18
> **ashwinhgtx said:**
> Isn't Shockwave a Windows only software? Are you trying to install it through wine? I'm not sure if wine supports 64bit yet.

Yes, it is. I suppose the OP is actually taking about Flash (AKA "Shockwave Flash").

But anyway, sounds like you have installed 64-bit version of Ubuntu and are now trying to install 32-bit version of Flash. Just like fooman suggested.

(the architecture for 64-bit processors is called "amd64" because AMD was the one who made the standard. Intel often calls their own amd64-compatible processors as "EM64T" simply because they hate the fact AMD beat them this time and developed the standard before they were able to do it. :D)

---

### Post by sdennie on 2009-02-18
> **mcduck said:**
> 
(the architecture for 64-bit processors is called "amd64" because AMD was the one who made the standard. Intel often calls their own amd64-compatible processors as "EM64T" simply because they hate the fact AMD beat them this time and developed the standard before they were able to do it. :D)

Actually, it's not that AMD beat them, it's that AMD had a more desirable 64bit (AMD64) architecture than Intels 64bit architecture (IA-64) because it was backward compatible with the existing 32bit architecture.  When no one wanted IA-64, Intel begrudgingly went to AMD64.

But, I digress...  ;)

---

### Post by 3rdalbum on 2009-02-18
Why not use the 64-bit Flash that's available from [www.adobe.com?](www.adobe.com?)

---

