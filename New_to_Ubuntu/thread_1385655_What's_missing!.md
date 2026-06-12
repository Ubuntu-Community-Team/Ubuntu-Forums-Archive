---
title: "What's missing?!"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by furoido on 2010-01-19
I updated my Ubuntu and suddenly I can't see videos on many websites (although on some, I can) or have ability to edit my pix on flickr. 
Anyone tell me which program has gone missing and how I can re-install it (please give exact instructions, as I am a real beginner!)
I tried re-installing the flash on one recommendation, but got told it is up-to-date...
Thanks!

---

### Post by fugaki on 2010-01-19
Honestly it sounds like flash.

Installation/reinstallation depends on whether or not you are using 64-bit OS.

You can check by looking in the /usr folder and see if there is a folder called lib64.

---

### Post by furoido on 2010-01-19
Thanks Fugaki.
At the expense of sounding unbelievably dumb, how do I access the /usr folder?! And if there is no lib64, how do I install it?

---

### Post by furoido on 2010-01-19
found /usr folder! All that's in there is avast4workstation...

---

### Post by fugaki on 2010-01-19
well you dont need it if you have a 32 bit os, but it will be there by default if you have a 64 bit one.

you can either click Places->Computer, then filesystem->usr and look there, or you can open terminal and type

cd /usr

ls

and see if lib64 is listed.

---

### Post by furoido on 2010-01-19
OK, was looking in wrong place...no lib64 is not listed...should I try installing it? If so, how?

---

### Post by fugaki on 2010-01-19
No, you do not need it.

Try using this guide, first, and let us know how it turns out.

[http://www.lehsys.com/2009/10/installing-adobe-flash-on-ubuntu-9-10-just-works/](http://www.lehsys.com/2009/10/installing-adobe-flash-on-ubuntu-9-10-just-works/)

---

### Post by furoido on 2010-01-19
I think the problem is that I don't have Adobe Flash Player installed...I've downloaded the programme and extracted it, but how do I actually install it via terminal i.e. what is the exact command I need to type in?!

---

### Post by furoido on 2010-01-19
THANKS Fugaki! That did the trick!!!

---

