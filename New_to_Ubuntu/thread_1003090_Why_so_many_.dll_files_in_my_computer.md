---
title: "Why so many .dll files in my computer?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-05
Hi

I thought that dll files were Microsoft dynamic linked library files. I moved to Ubuntu to escape MS. 

Does linuX use .dll files in its OS? If not why should I have lots of .dll files on my system?

I have virus checked the files and they are not viruses according to clamav.

---

### Post by damis648 on 2008-12-05
Exactly where are you finding them? Linux doesn't use them.

---

### Post by OutOfReach on 2008-12-05
Where are these .dlls? I have a feeling that they are used by a program not Linux.

---

### Post by ibutho on 2008-12-05
> **damis648 said:**
> Exactly where are you finding them? Linux doesn't use them.

Some programs do. I have noticed dlls in mono based programs.

---

### Post by bwallum on 2008-12-05
Here's some. How do I get a search to be reported to a text document?

---

### Post by OutOfReach on 2008-12-05
I am almost positive that those are meant (and used) for mono-based programs. (C#)

---

### Post by bwallum on 2008-12-05
Thats a relief, I thought Ubuntu had sold out to MS! (I'll go and wash my mouth out now and pray for forgiveness for a week)

---

### Post by directhex on 2008-12-06
> **OutOfReach said:**
> I am almost positive that those are meant (and used) for mono-based programs. (C#)

Correct. "dll" and "exe" are the standard extensions for CLI libraries and apps, so we re-use those extensions on Free Software CLI stacks like Mono or DotGNU Portable.NET, for better interop with Windows users (i.e. MS.NET)

Anything dll or exe in /usr/lib/cli or /usr/lib/mono is a cross-platform piece of free software code - despite the file extension

---

