---
title: "ubuntu 64 bit"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by cap10Ibraim on 2010-03-20
I am just wondering does ubuntu 64 bit work on intel 64 bit , beacuase when  i press download the file name is ubuntu 9.10 - desktop - amd64 ?

---

### Post by _h_ on 2010-03-20
Yes it does.

---

### Post by cap10Ibraim on 2010-03-20
thx i'am sick of dual boot 
windows 7 64bit and ubuntu 32bit now i'm downloading the ubuntu 64 bit to enjoy it as my only os

---

### Post by djchandler on 2010-03-20
> **cap10Ibraim said:**
> I am just wondering does ubuntu 64 bit work on intel 64 bit , beacuase when  i press download the file name is ubuntu 9.10 - desktop - amd64 ?

It's called AMD64 because AMD developed the technology of co-existent 64-bit and 32-bit instruction sets on the same CPU, and it was actually first called x86-64. This has been cross-licensed to Intel, which then renamed it to EM64T (not compatible with Itanium or IA-64). If your Intel CPU supports 64-bit instructions (Prescott P4 and newer), then it is compatible.

AMD later introduced the name AMD64 for marketing purposes; Intel introduced its Intel 64 naming soon thereafter. Microsoft uses the vendor-neutral term x64.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by cascade9 on 2010-03-20
> **djchandler said:**
> It's called AMD64 because AMD developed the technology of co-existent 64-bit and 32-bit instruction sets on the same CPU, and it was actually first called x86-64. This has been cross-licensed to Intel, which then renamed it to EM64T (not compatible with Itanium or IA-64). If your Intel CPU supports 64-bit instructions (Prescott P4 and newer), then it is compatible.

I didnt know that AMD called is x86-64 before they came up with AMD64 (I would like to see a link for that if possible). 

Not all the presscotts supported x86-64- just some of them.  

> 
**[Prescott]("http://en.wikipedia.org/wiki/Pentium_4#Prescott") (90 nm)**

 
[LIST]
[*]All models support: *[MMX]("http://en.wikipedia.org/wiki/MMX_%28instruction_set%29"), [SSE]("http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions"), [SSE2]("http://en.wikipedia.org/wiki/SSE2"), [SSE3]("http://en.wikipedia.org/wiki/SSE3")*
[*]*[Intel 64]("http://en.wikipedia.org/wiki/Intel_64")*: supported by 5x6, 511, and 519K
[*]*XD bit (an [NX bit]("http://en.wikipedia.org/wiki/NX_bit") implementation)*: supported by 5x5J, 519J, and all [Intel 64]("http://en.wikipedia.org/wiki/Intel_64")-compatible models
[/LIST]
**[Prescott]("http://en.wikipedia.org/wiki/Pentium_4#Prescott") (90 nm)**

 
[LIST]
[*]All models support: *[MMX]("http://en.wikipedia.org/wiki/MMX_%28instruction_set%29"), [SSE]("http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions"), [SSE2]("http://en.wikipedia.org/wiki/SSE2"), [SSE3]("http://en.wikipedia.org/wiki/SSE3"), [Hyper-Threading]("http://en.wikipedia.org/wiki/Hyper-Threading")*
[*]*[Intel 64]("http://en.wikipedia.org/wiki/Intel_64")*: supported by F-series, 5x1, 517, 524
[*]*XD bit (an [NX bit]("http://en.wikipedia.org/wiki/NX_bit") implementation)*: supported by 5x0J, 5x1, 517, 524
[*]Model SL7E4 has an unattached fan heatsink.
[/LIST]


[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)


> Originally, two Prescott lines were released: the E-series, with an 800 MHz FSB and [Hyper-Threading]("http://en.wikipedia.org/wiki/Hyper-Threading") support, and the low-end A-series, with a 533 MHz FSB and Hyper-Threading disabled. Intel eventually added [XD Bit]("http://en.wikipedia.org/wiki/XD_Bit") (eXecute Disable) and [Intel 64]("http://en.wikipedia.org/wiki/Intel_64") functionality to Prescott.

[http://en.wikipedia.org/wiki/Pentium_4#Prescott](http://en.wikipedia.org/wiki/Pentium_4#Prescott)

The Core Solo/Duos, released well after the prescotts, were 32bit only as were a lot of the atoms.

---

### Post by srs5694 on 2010-03-20
My memory is that the name "AMD64" predates "x86-64," although I'm not positive of that. I am 100% positive that "AMD64" was in use before Intel introduced their first x86-64 CPU. I wrote [an early piece on AMD64 and Linux](http://www.linux-mag.com/id/1699) for Linux Magazine back in 2004, before the first Intel x86-64 chips hit the stores, and the article uses both terms, with an emphasis on "AMD64" because that seemed more prevalent to me at the time. FWIW, I still use the computer described in that article, although it's no longer my main desktop system.

---

### Post by djchandler on 2010-03-21
> **cascade9 said:**
> I didnt know that AMD called is x86-64 before they came up with AMD64 (I would like to see a link for that if possible).

[http://www.amd.com/us-en/Corporate/VirtualPressRoom/0,,51_104_543_552~715,00.html]("http://www.amd.com/us-en/Corporate/VirtualPressRoom/0,,51_104_543_552%7E715,00.html")
[http://www.stanford.edu/class/ee380/Abstracts/O00927.html](http://www.stanford.edu/class/ee380/Abstracts/O00927.html)

> The Core Solo/Duos, released well after the prescotts, were 32bit only as were a lot of the atoms.I see I was guilty of negligence in terms of saying Prescott and subsequent were 64-bit compatible. And apparently the first EM64T extensions on Intel CPUs weren't entirely AMD64 compatible either. I'm certainly happy that those differences have been settled.

What else would you expect from an AMD fan that hasn't bought a new Intel chip since the 80486DX2-66?

Although I've had my hands on plenty of used Intel chips, it's only been by chance (which I agree is huge). Balancing that is our local recycling center ([KC Surplus Exchange]("http://www.surplusexchange.org/")) treats Intel chips as special while all but giving away AMD systems when they come in. Free beats any price.

---

### Post by cascade9 on 2010-03-21
Thanks for that, I was under the impression (like srs5694) that AMD64 was used 1st. Probably by the time that they were being released, the marketing department had gone 'ohh, a chance to give intel another kick', but the original technically specifications sure look like x84-64. Which for the engineers might well have had more clout than 'AMD64', that could very well have been an non x86 compatable, AMD version of itanium/IA-64. 

As far as the presscott thing goes.....I admit to being a hardware monkey. I've had the whole 'presscotts are 64 bit' discussion professionally, and I tend to remember hardware parts/numbers/capabilities really well. 

 I'm in a similar boat.....and to be honest I've never bought a new retail Intel CPU (I've bought a couple 2nd hand). Had a lot of intel systems over the years, everything from old 286s onward. Also, the same thing happens with the local recycling centres, I've picked up a freebie or two from hem because 'AMD are junk' LOL. One of those systems is still running 5 years later with no problems. :D

---

