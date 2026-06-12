---
title: "How can I get Ubuntu 10.04 to recognize ALL of my RAM?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Nickjpost on 2010-12-01
I have seen a thread about this in the forum and the suggestion was to install linux-686-smp, however another post stated that that was no longer supported and when I tried to find the package, I found that it is indeed no longer supported. What can I do so that Ubuntu will utilize all of my RAM? Currently running a Toshiba Satellite L25 with intel Celeron single core and 1.5G of RAM (Ubuntu only recognizes 800MB or so).

---

### Post by NightwishFan on 2010-12-01
I believe the rest of your ram may be in use because of an integrated graphics card. The limit for RAM on the standard kernel is actually 3gb for 32-bit. Just to be sure, post the output of:
```
free -m
```

Also, it would not hurt to check around in your bios for ram/graphics related settings

---

### Post by Nickjpost on 2010-12-01
Wow, I have installed 1.5G in my computer, but in bios it reads that there is only 894MB. I must have mistaken my Mobo's Ram limit apparently as I thought it was good for up to 2G. *sigh* Slow system it is.....thanks for your help!

---

### Post by Utkarsh Ray on 2010-12-01
#2 is correct.

The maximum amount of memory in 32-bit system is limited to 4GB and even all of it isn't available due to physical addressing limitations. My 4GB was detected as 3.1GB in Vista (x86) and 7(x86) and 2.98GB in XP(x86) on Intel Core2Quad (x64) Intel DG41RQ1 (it shows 1804MB video memory which I doubt). While 7(x64) showed it to be 3.96GB. I'm a novice to Unix-type systems so I haven't found how much memory Ubuntu(x86) detects.

---

### Post by TNT1 on 2010-12-01
> **Utkarsh Ray said:**
>  I'm a novice to Unix-type systems so I haven't found how much memory Ubuntu(x86) detects.

If you use the PAE kernel, your 4Gb will show up as ~3.8GiB.

---

### Post by migs73 on 2010-12-01
+1 to that. It is what I use (and get 3.8GB with 4GB of RAM), the PAE kernel actually allows you to use it all if you have it(and more - upto 64GB i think).

---

### Post by NightwishFan on 2010-12-01
You can only address so much per process though.

---

### Post by TNT1 on 2010-12-01
> **NightwishFan said:**
> You can only address so much per process though.


Physical Address Extension?:D

---

### Post by NightwishFan on 2010-12-01
Im sorry? I do not quite understand the question.

---

### Post by Utkarsh Ray on 2010-12-01
Thanks for the information. That shows Linux uses resources better than Windows. Its significantly faster than Virtual PC or Wubi when I installed it as dual boot.

---

### Post by migs73 on 2010-12-02
> **NightwishFan said:**
> You can only address so much per process though.

As the processes you can use will be limited to 32bit then the RAM usage limitation comes from them. 
PAE does allow you to use multiple processes, with greater RAM than the standard 32bit kernel (handy for VM's in particular).

---

### Post by NightwishFan on 2010-12-02
I know this. I was just curious why it was challenged.

---

### Post by migs73 on 2010-12-02
> **NightwishFan said:**
> I know this. I was just curious why it was challenged.

I was just adding some meat to the bones of your statement, hopefully for clarity because I didn't understand the challenging either!

---

