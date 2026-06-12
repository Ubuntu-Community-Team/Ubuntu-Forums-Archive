---
title: "Installation help"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by orrymr on 2011-03-16
Very new to Ubuntu; trying to install ubuntu 10.10 now for the last few hours, so forgive my curtness. Initial problem was Errno 5 I/O error. I tried to remove my RAM, didn't help, tried a whole bunch of stuff, didn't help. If that wasn't enough, there's a new problem now. Something to do with coercing to Unicode - check the attached pic. At my wits end, any advice would be very much appreciated

---

### Post by seawolf167 on 2011-03-16
[Looks like]("https://bugs.launchpad.net/wubi/+bug/441107") it may be to an invalid MD5Sum. I'd suggest re-downloading the ISO file and remounting/reburning it on your computer then reattempting the installation. Ensure that you close any anti-virus software before installing.

---

### Post by orrymr on 2011-03-16
Not sure exactly what that means, but would that explain why the coercion error spontaneously popped up? Because that wasn't where the installation was stuck before, before it was stuck at an Errno 5 input output error

---

### Post by orrymr on 2011-03-16
well, managed to fix the coercion error by just disconnecting from the internet before running the installation. No idea why that should help, but it seems to. The Errno 5 Input Output is still grating my balls. Thanks in advance for any replies

---

### Post by orrymr on 2011-03-16
I've also tried to burn the .iso onto different disks, to check if maybe the disk itself was faulty. I've also tried using daemon tools to install. Is it possible that ubuntu is just incompatible with some hard drives? If so, with which?
Again, thanks in advance

---

### Post by orrymr on 2011-03-16
MD5Sums were different!

---

### Post by seawolf167 on 2011-03-17
> **orrymr said:**
> MD5Sums were different!

So everything is working now? You were able to redownload a non-corrupted version and the errors went away? I know its a little late, but here is a how-to for [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by orrymr on 2011-03-19
Yeah, works fine now, thanks SeaWolf. Purely out of interest's sake here, what does the MD5sum actually do? I understand that it checks the integrity of the file (somehow), but how does it achieve this? Also, why would the file become corrupted?

---

### Post by chrinabuntu on 2011-03-19
Oh good. I guess your balls are better now. ;O)

---

### Post by orrymr on 2011-03-19
In top shape; thanks for your concern :P

---

### Post by chrinabuntu on 2011-03-19
;o)

---

### Post by isparkes on 2011-03-19
> **orrymr said:**
> What does the MD5sum actually do?

MD5 used in MD5sum is really a cryptographic compression function. It takes any amount of input data and "adds it all up" to give an answer that is always the same length, and **exactly** depends on the input. If you change 1 single bit in the input, the MD5 checksum will be different.

The bit that makes MD5sum really useful is that you cannot reasonably change the input in such a way as to give a predictable output (called a "collision"). This means if someone wanted to change the software in such a way as to insert a key logger or phishing daemon or whatever, they don't have a chance of doing it without changing the MD5 sum. With a non cryptograhpic sum, they could engineer it in such a way that they inserted the keylogger, and then some extra random junk until they got the same checksum and you would never know...

---

### Post by orrymr on 2011-03-19
Does that imply that if I change even a single bit of information from the file, that the output would be COMPLETELY different after an md5sum function is run? Also, assuming the file is corrupter, aside from malicious intent, how else could this happen?

---

### Post by isparkes on 2011-03-19
> **orrymr said:**
> Does that imply that if I change even a single bit of information from the file, that the output would be COMPLETELY different after an md5sum function is run? Also, assuming the file is corrupter, aside from malicious intent, how else could this happen?

Yes, usually obviously completely different.

The most common reason for corruption is that the file got truncated during transmission. Nowadays corruption in the transmission is very rare, but is still possible.

If you download again, and get the same MD5sum but different from what you expect, contact the owner of the file. Either they have made a mistake or have been hijacked.

---

### Post by orrymr on 2011-03-19
Cool, thanks for your help. I did download again, and all was fine n dandy :D

---

