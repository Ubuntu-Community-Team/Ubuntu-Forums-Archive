---
title: "Dual booting Vista and Ubuntu with wubi, and running Crossover"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by cocodave on 2008-12-17
Hello. I am a new user to ubuntu, dual booting from windows with wubi. Ubuntu is now firmly by OS of choice.

Is it possible to use the crossover software on ubuntu to run software i have already installed on my windows. 

I ask because I am keen to run microsoft office on my ubuntu since I have paid for it, and as all my university work is using docx features. Furthermore, i have run out of licenses for my software so i cannot install it again.

Thankyou

---

### Post by rlunger on 2008-12-17
> **cocodave said:**
> Hello. I am a new user to ubuntu, dual booting from windows with wubi. Ubuntu is now firmly by OS of choice.

Is it possible to use the crossover software on ubuntu to run software i have already installed on my windows. 

I ask because I am keen to run microsoft office on my ubuntu since I have paid for it, and as all my university work is using docx features. Furthermore, i have run out of licenses for my software so i cannot install it again.

Thankyou

Yes, this is possible.  I don't know if WINE will work with the newest version of office (you mentioned docx formats), but Codeweavers has a customized version of WINE just for Office called CrossoverOffice.  You might want to give this a try.

---

### Post by theozzlives on 2008-12-17
Open Office Writer saves in Word format, I think the other Open Office apps are compatible with MS Office.

---

### Post by cocodave on 2008-12-17
To be more specific, i have many many pages of equations written in office 2007 form which i would like to remain editable. This is why I require office 2007.

So crossover gives the option to install from a CD or another source. I tried installing from my winword.exe file on my windows files (accessible through /host) but this failed as it wasnt an installation file. If it is possible, how do i use crossover to run my windows programmes without installing them seperately on ubuntu.

---

### Post by eriqjaffe on 2008-12-17
> **cocodave said:**
> If it is possible, how do i use crossover to run my windows programmes without installing them seperately on ubuntu.I don't think that's possible, especially since most Windows applications write to the registry when they're installed and need to be able to read those entries at runtime.

---

