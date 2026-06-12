---
title: "How can you know if source code has been stolen?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Poga on 2010-03-20
I have very limited programming experience, so I ask this without much background in regard to programming itself.  I do have, however, a significant interest in FOSS and, consequently, the accompanying licenses and laws.

I read from time to time about various lawsuits in the free software community, often about some person or company that has taken source code from an open-source project and then illegally incorporated it into their own proprietary software.  However, I am always left wondering how people can tell if particular source code has actually been used.

For example, Company X is writing a program that randomly draws squares, circles, and triangles.  They've finished the coding for the squares and triangles, but haven't yet gotten to the part for the circles.  Then they notice that an open-source project, called Omazing, already exists, which has code that will randomly draw circles.  Despite the terms of the open-source license, Company X decides to use Omazing's code in its own program.  Company X later distributes and sells the resulting shape-drawing program as its own.

Yet given that Company X's program is proprietary, and the source code is never released, how would anyone ever know if they used Omazing's code?

---

### Post by mikewhatever on 2010-03-21
Well, according to GPL, Company X has the right to use the open code in their proprietary program, in fact, that's the idea of open source, 'The code is free to use for anyone.'. You can't really steal the code that's freely available for anyone to take and use, can you.

---

### Post by achase79 on 2010-03-21
Yea, GPL basically just says you can use this but if you make changes (to the used source code) you have to post them to the GPL project.

---

### Post by sailthesea on 2010-03-21
Omazing would know, and they would rightly kick up a stink about it it!:)

---

### Post by Poga on 2010-03-21
I still don't understand how Omazing (or any other party) would know that their code had actually been used.  Company X used their code, incorporated it into their own program, and never credited or told anyone else about their use of Omazing's work (nor did they share the source code).

So, if others cannot see the source code in Company X's resulting program, how do they even know that Omazing's code was used in the first place?  The binaries that were distributed would not share the same strings of 1's and 0's (or could easily be made to not share the same 1's and 0's), correct?

How does Omazing, or anyone else, ever know about what Company X has done?  Is there any way to check?

---

### Post by derekeverett on 2010-03-21
I'm no expert here, but I think it would pretty much come down to someone connected with the project ratting out the others.

There could be a number of reasons for doing that, disgruntled employees/partners/associates etc. probably being high on that list.

Secrets are hard to keep. Especially juicy ones and big ones. Most software projects require a group of people so keeping information restricted would be difficult.

---

### Post by Poga on 2010-03-21
Just to clarify, I should mention that I am thinking of a copyleft license, like the GPL, which requires the resulting source code to be shared.

However, if a company uses someone else's GPL'ed code, yet does not acknowledge that they used it, and does not make the resulting source code of the program they used it in publicly available, how can anyone else ever know that the 'theft' ever took place?

---

### Post by mikewhatever on 2010-03-21
I suppose such a company could get away with it for a while. Why don't you ask real experts instead.;)

[http://gpl-violations.org/](http://gpl-violations.org/)
[http://www.ebb.org/bkuhn/blog/2009/12/06/anatomy-gpl-violation.html](http://www.ebb.org/bkuhn/blog/2009/12/06/anatomy-gpl-violation.html)

You keep using the term 'theft' which isn't quite applicable to GPL'ed code.

---

### Post by anewguy on 2010-03-21
Even more important, I think, is WHY do you want to know in the first place?  If it's your own code you are worried about, then you have the choice of keeping it proprietary or open source (and the freedoms that others have with that code).  If it's not your code, humm........


Dave

---

### Post by ashu. on 2010-03-21
even if its very different in its binary the operation performed by ur code will be the same if u r really the original programer u'll know n there is always a signatures in programing..if 2 programmers code for same logic its implimentation will be different so when u c its greater chance that u may identify but it depends on the function of code.if its a compleate backend code its tough to identify it..this is my personal idea.there may be other ways too but its my frank openion..

---

### Post by yeats on 2010-03-21
> Well, according to GPL, Company X has the right to use the open code in their proprietary program

Actually, to my understanding, this is one of the things the GPL explicitly prohibits.  If a proprietary program incorporates GPL-ed code, it MUST turn around and apply the GPL (or similar enough terms to meet the terms of the GPL).

> in fact, that's the idea of open source, 'The code is free to use for anyone.'. You can't really steal the code that's freely available for anyone to take and use, can you.

Whether the code is 'free to use for anyone' depends entirely on the terms of the OSS license that is applied.  The MIT/X and Apache licenses are extremely permissive in their terms of use.  The GPL (all versions and variants) on the other hand requires that the program be shared under similar terms.

To the OP:  another issue is software patents, which open source licenses (which only cover the source code and not the functionality of the program) do not address.  That's a whole other ball of wax, though (so to speak).

---

### Post by srs5694 on 2010-03-21
> **mikewhatever said:**
> Well, according to GPL, Company X has the right to use the open code in their proprietary program, in fact, that's the idea of open source, 'The code is free to use for anyone.'. You can't really steal the code that's freely available for anyone to take and use, can you.

No, this is incorrect. The GPL explicitly states that anybody who uses GPLed code must release any derived work under the GPL. In the original scenario, the proprietary shape-drawing program counts as a "derived work." There have been lawsuits over this issue. To the best of my knowledge, they've usually (maybe always) been settled out of court or the GPL rights-holder has won. GPL detractors refer to this as the GPL's "viral nature," because it tends to "infect" any code that it touches.

That said, there are other open source licenses, such as the BSD license, that permit a software developer to take the open source code and fold it into a proprietary product. Also, even with the GPL, the original author can do this, or can reach an agreement with a third party to license the code under other terms. Still, the original post specified the GPL and didn't mention any private agreement, so these caveats don't apply to it.

As to the original question, there are ways to tell. There are software analysis tools that can be used to compare two binaries to tell whether they share similar code. At a crude level, one such type of program is known as a disassembler. It takes the binary and turns it into human-readable assembly language. ("Human" in this case being somebody familiar with assembly language, which is pretty arcane by modern programming standards.) Somebody who's familiar with the code in question, and with how different compilers compile it, will likely be able to spot two binaries that derive from the same source code by examining disassembled code. There may be more automatic comparison programs that can help with this, but if so I'm not familiar with them.

There can also be clues in how the program operates. For instance, suppose that circle-drawing code in the original post includes a bug that causes the circles to become ovals when they're drawn near the corners of the screen. If both final products exhibit the same bug, that's a strong clue that they've got the same source code in common. This wouldn't be enough to convict in a court of law, of course, but it's the sort of thing that may tip off an interested person to look more closely at a proprietary program's pedigree.

---

### Post by cascade9 on 2010-03-23
IIRC, Josh Coalson (flac developer) posted somewhere on hydrogenaudio that he had look at the Alac code (apple lossless audio codec) and thought that at least some of it was the same as the flac code. It would be very difficult to do anything about it, as apple has Very deep pockets...and legally your not allowed to view the code so it would be difcult to prove that the code was 'stolen' by apple.

---

### Post by anewguy on 2010-03-24
GASP!!  One of the "big guys" may have stolen code??  :):)

Funny how they can grab the small guys stuff and get away with it, but you can bet that if I wrote something that incorporated part of their code and tried to sell it, they be on my door faster than I can press the enter key.

Dave :)

---

### Post by Poga on 2010-03-25
Thanks for the responses.  I was especially interested to hear about the alluded to software analysis tools and disassemblers (the latter of which I'm only vaguely familiar with).  I'll be curious to see if I ever hear more about them in the future, or if any sort of automated tool is used for concerns related to license compliance.

One of the reasons my original question was of interest to me in the first place was because, as a proponent of free software, I was curious to know how some of these potential obstacles could be dealt with.  When a program has millions of lines of code, it seemed to me like it wouldn't be too difficult for some person to lift code (or pieces of code) from one program for use in another, without being caught.

However, if unlicensed use can be discovered in things as seemingly obscure as model train software (as was recently discussed in some media outlets), perhaps there is hope.  I guess I'll have to wait and see how things progress.

---

