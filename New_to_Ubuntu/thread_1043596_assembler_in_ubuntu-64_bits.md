---
title: "assembler in ubuntu-64 bits"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by qvyang on 2009-01-18
i am learning assembly language in uni and i'm confused about all these assembly language terms.
what's the difference between x86, IA32 and gas?

i compiled my c program into assembly language in my ubuntu terminal, however i realized that all the code it generated are different from what i am using in uni. for example: the frame/base pointer register is %rbp instead of %ebp and movq instead of movl since it is 64-bit! is there any way that i can simulate a x86 or IA32 in my terminal? thanks!

---

### Post by snova on 2009-01-18
x86 and IA32 are two different architectures. From what I recall, they are also very different.

GAS is an assembler, the GNU ASsembler. It's also sometimes the name of the syntax that it uses (AT&T syntax).

---

### Post by shifty_powers on 2009-01-18
> **snova said:**
> x86 and IA32 are two different architectures. From what I recall, they are also very different.

GAS is an assembler, the GNU ASsembler. It's also sometimes the name of the syntax that it uses (AT&T syntax).

erm, sorry?

> IA-32 (Intel Architecture, 32-bit), often generically called x86 or x86-32, is the instruction set architecture of Intel's most commercially successful microprocessors. It is a 32-bit extension, first implemented in the Intel 80386, of the earlier 16-bit Intel 8086, 80186 and 80286 processors and the common denominator for all subsequent x86 designs. This architecture defines the instruction set for the family of microprocessors installed in the vast majority of personal computers in the world.

(from good old wikipedia...)

---

### Post by snova on 2009-01-18
> **shifty_powers said:**
> erm, sorry?

Ah, oops, I was thinking of [IA-64]("http://en.wikipedia.org/wiki/IA-64").

> Itanium's architecture differs dramatically from the x86 architectures (and the x86-64 extensions) used in other Intel processors.

Edit: And, come to think of it, that doesn't say much about the instruction set, either.

---

### Post by qvyang on 2009-02-14
Thanks guys! I get it now.

---

