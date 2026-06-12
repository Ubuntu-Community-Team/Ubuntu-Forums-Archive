---
title: "Running a VB prog with mono"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by HellionDBZ on 2009-08-30
OK so I installed wine and found out it won't run my VB prog. So I installed mono after doing some research and still it won't run. I'm trying mono --aot <filename> and it doesn't work. Also I tried mono --config <filename> still nothing. So I tried to open it with the acctual app and see if I could do it that way and it won't open the file, I get a invalid PE file soooo any idea's how to convert/compile this to run?

---

### Post by Liolikas on 2009-08-30
Install MS visual studio in wine.
Or if you have source you maybe can try to compile it with [http://www.realsoftware.com/](http://www.realsoftware.com/)
Basically VB is worst option from popular ones for coding multi-platform things.

Learn Python :P I run same Python soft on windows linux and nokia n series phone.

---

### Post by directhex on 2009-08-30
> **HellionDBZ said:**
> OK so I installed wine and found out it won't run my VB prog. So I installed mono after doing some research and still it won't run. I'm trying mono --aot <filename> and it doesn't work. Also I tried mono --config <filename> still nothing. So I tried to open it with the acctual app and see if I could do it that way and it won't open the file, I get a invalid PE file soooo any idea's how to convert/compile this to run?

Um, what on EARTH are you trying those commands for? They're pretty much the opposite of what you want.

Firstly, do you have [libmono-microsoft-visualbasic8.0-cil](apt:libmono-microsoft-visualbasic8.0-cil) installed? It's the core assembly that all VB.NET apps use. Next, what *actualy* error do you get from a simple "mono foo.exe"? Actual messages are *vital* to debugging problems.

---

