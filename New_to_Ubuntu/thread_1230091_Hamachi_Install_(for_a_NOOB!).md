---
title: "Hamachi Install (for a NOOB!)"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by NiGHtsBeta09 on 2009-08-03
Hello.  I'm brand new to Ubuntu.  I'm a Windows-experienced person.  Can anyone tell me how to install Hamachi on Ubuntu, please?  I've tried the guides, but I always get stuck at one point or another.  My Firefox isn't working on my XP, and I don't want to have to switch OSs for internet surfing and Hamachi/GoogleTalk!  It gets annoying.

Any help will be greatly appreciated!  Thanks!  ^^

---

### Post by Bradtek on 2009-08-03
Have you at least read the README file inside the 
hamachi-0.9.9.9-20-lnx.tar.gz       ?

---

### Post by NiGHtsBeta09 on 2009-08-06
Yes, but as I stated, I am completely new to the works of Ubuntu.  I have no idea what to do.  I tried the "make install" as it said, but it gave an error, so I think I'm going wrong.  ON THE FIRST STEP!  ><

I really need help....  T^T

---

### Post by pedro3005 on 2009-08-06
First you open up the terminal, then you run 'cd nameofdirectory', nameofdirectory being the directory where hamachi was extracted. Then './configure', when it is done 'make' and finally 'make install'. That is the standard compiling procedure and should work :)

---

### Post by justrivers on 2009-08-11
I'm having issues with Hamachi as well.  The Make File and the tuncfg work fine but whenever I run 'hamachi-init' the terminal prompt immediately follows up with 'killed' so I cannot start the process.  I've tried running it as stated above and as 'sudo hamachi-init', both respond killed.

System log shows this:
 Pid: 3530, comm: hamachi-init Tainted: G  

I can provide the full log detail if needed.

help...

---

### Post by 3rdalbum on 2009-08-11
> **NiGHtsBeta09 said:**
> Yes, but as I stated, I am completely new to the works of Ubuntu.  I have no idea what to do.  I tried the "make install" as it said, but it gave an error, so I think I'm going wrong.  ON THE FIRST STEP!  ><

I really need help....  T^T

What error message does it give? Do you have the build-essential package installed?

Telling us "It gave me an error" without telling us the error message is like taking your car to the mechanics and saying "There's something wrong with my car, how much will it cost to fix it?". The mechanic is not going to know what's wrong without personally driving the car around.

---

