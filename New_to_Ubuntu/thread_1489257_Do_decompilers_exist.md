---
title: "Do decompilers exist?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-20
I mean if they did then wouldn't the Wine people be able to decompile windows so that they could get it to work better? I know that they're doing it just by using libs and other techniques, but it makes it difficult to get it to work perfectly without having access to the source code.

---

### Post by Zyrtec on 2010-05-20
Decompilers do exist, but they're not exactly feasible. Reverse engineering is very frowned upon in most cases, and a lot of compilers obfuscate their programs.

---

### Post by tgalati4 on 2010-05-20
First rule of decompilers:   Don't talk about decompilers.

Second rule of decompilers:  Don't talk about decompilers.

---

### Post by Legendary_Bibo on 2010-05-20
Oh apparently there are some that work extremely well. They can get the entire code besides the comments exactly as the author wrote them. That is scary, but I thought most people who write programs for linux always provide the source code anyways.

---

### Post by srs5694 on 2010-05-20
In terms of the specific issue of decompiling Windows to help with WINE development, there are also legal issues. Specifically, if you decompile Windows and then use the decompiled code in WINE, you've just opened yourself and the WINE project up to a lawsuit from Microsoft. Even if you don't cut-and-paste the code directly, but use the decompiled code in a less direct way, there's the potential for accusations of copyright infringement.

I've heard of cases where this sort of thing is done, but it's usually handled in a "clean room" manner, in which one team does the decompiling and documents what they find (documenting APIs that are undocumented by the original vendor, for instance), and another team re-implements the individual functions or APIs based solely on the first team's documentation, without seeing the actual decompiled code. This was done to reverse engineer some early PC BIOSes, IIRC. AFAIK, the WINE developers don't use this technique (or any sort of disassembly of Windows code); however, my knowledge of how the WINE developers work is quite limited.

---

### Post by QIII on 2010-05-20
If someone like a WINE developer decompiled my code (which is obfuscated, so it would be difficult, but not impossible), I'd have their boney little backsides in court for violating my copyrights and intellectual property rights so quick their heads would spin.

It's not like WINE is unknown.  They're not going to just do it.  It would be too easy to see that they had done it.

A s**t-eating grin and a plea for forgiveness would not stop them from paying for it.

---

### Post by lisati on 2010-05-20
I haven't looked at recent offerings, but suspect that a making decompiler that exactly matches the original source code line by line (not counting comments) would be a non-trivial task, particularly when there's code obfuscation and different possible optimizations to figure in. Even the disassemblers I've looked at often require a little help. 

Having said this, I am aware that reverse engineering tools do exist, and that legal complications can arise.

---

### Post by -humanaut- on 2010-05-20
I would imagine if the WINE project started decompiling and reverse-engineering Microsoft's code they'd be shutdown fairly quick if there pockets aren't extremely deep.

---

### Post by Legendary_Bibo on 2010-05-21
What if a third neutral party were to do it, rewrite the code so it does the same thing, but in a different way (the same way many others such as myself got away with plagiarism in highschool...just reword everything), and disclose the code over to the Wine development team. Unethical yes, but it would help with avoiding legal repercussions. I wouldn't be able to do this, but I mean if the Wine people could get their hands on the code in some legal manner, it would really cause a leap in the development. Apparently the Win 7 source code was leaked because it could be found with the installation of Win 7.

---

