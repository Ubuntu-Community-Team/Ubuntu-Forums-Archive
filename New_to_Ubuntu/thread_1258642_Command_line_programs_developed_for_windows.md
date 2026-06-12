---
title: "Command line programs developed for windows"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by whatifwe on 2009-09-05
I am a Windows based software engineer with over 40 years of experience.   My Linux experience is using the now obsolete Linspire operating system and is quite limited.

My specialty is the development of error-free software in strict compliance with the principles of ISO-9001,  I have over the years developed a number of command line open-source tools that can be downloaded from my website free of charge.  Both Windows and Linspire version are available.

Unfortunately the loss of Linspire has crippled my ability to maintain my Linux versions.  I have already attempted to rebuild these programs and have found that a major redevelopment effort might be necessary.  I am quite sure that my inexperience with Linux is creating most of my difficulties.

I have heard from various sources that it may be possible to interface a Windows program with a Linux operating system.   These are command-line programs that access the operating system (display, keyboard, files) with the stream system routines (fopen, etc).  Memory is allocated by the calloc routine. Other than fetching time and date, there is no other usage of the operating system.   

Is there an interface that can permit this windows based program to be used in this Linux environment?  If so, I could quickly update my web-site and these programs would again be available to the Linux community.

---

### Post by cmcanulty on 2009-09-05
Wine might work

---

### Post by wojox on 2009-09-05
Or dosemu

[http://dosemu.sourceforge.net/](http://dosemu.sourceforge.net/)

---

