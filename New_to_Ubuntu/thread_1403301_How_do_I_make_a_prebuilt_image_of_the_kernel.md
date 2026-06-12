---
title: "How do I make a prebuilt image of the kernel?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Vignesh S on 2010-02-10
Alright, here we go. I want to make my own kernel version of the 2.6.21-17 kernel. The reason is because I can use a prebuilt kernel image for [Android-x86]("http://www.android-x86.org") and after having downloaded their source tree, I can compile a custom version of Google Android that has a kernel that actually recognises my wifi card and the ethernet (the 2.6.31-17 kernel already has the latter, it's the former I want to add).

So how do I rip apart the kernel, add the RTL8192SE driver to it and compile it again into a prebuilt image that I can base the compiled android-x86 upon :)?

---

### Post by cariboo on 2010-02-11
Have a look [here]("https://help.ubuntu.com/community/Kernel/Compile"), it should probably help you out.

---

