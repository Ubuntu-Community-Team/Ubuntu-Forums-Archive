---
title: "Installing ksh on ubuntu 11.04(natty)"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Rocky007 on 2011-08-14
I would like to install ksh in my ubuntu 11.04(core 2 duo machine). When i did a search for ksh to be installed on ubuntu I got a link for ksh from package.ubuntu.com but they are only available for i386 and amd64. When i gave uname -m it says i686. uname -r gave 2.6.38-10-generic.

Could some one please help me choose the right ksh to be installed in i686 machine to mimic the unix os?
and please help me understand what does 2.6.38-10-generic mean?

---

### Post by kimda on 2011-08-14
> **Rocky007 said:**
> I would like to install ksh in my ubuntu 11.04(core 2 duo machine). When i did a search for ksh to be installed on ubuntu I got a link for ksh from package.ubuntu.com but they are only available for i386 and amd64. When i gave uname -m it says i686. uname -r gave 2.6.38-10-generic.

Could some one please help me choose the right ksh to be installed in i686 machine to mimic the unix os?
and please help me understand what does 2.6.38-10-generic mean?

sudo apt-get install ksh 

This will install ksh on your system.
2.6.38-10-generic is the kernel which is installed on your system.

You might want to change you shell in ksh because bash is standard. With the command chsh you can change your shell. Or you can just use it temporary by entering ksh at the prompt.

---

### Post by AlphaLexman on 2011-08-14
You would install the 'i386' version... your 'i686' version is just a faster 32-bit version. You don't have a 64-bit processor according to the 'uname' output.

---

### Post by oldos2er on 2011-08-14
Intel Core 2 Duo is 64-bit; 'uname -m' tells the bitness of the current kernel, not the processor.

---

### Post by Rocky007 on 2011-08-15
Thanks for your reply guyz. I installed ksh using sudo apt-get install ksh as suggested. It automatically installed i386 version.

---

### Post by oldos2er on 2011-08-15
Can you please mark the thread as 'Solved' (under Thread Tools)? Thanks.

---

