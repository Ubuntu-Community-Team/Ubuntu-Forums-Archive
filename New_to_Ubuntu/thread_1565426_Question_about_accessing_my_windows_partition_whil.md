---
title: "Question about accessing my windows partition while running ubuntu."
date: 2010-08-31
forum: New to Ubuntu
---

### Post by archer7282 on 2010-08-31
Hello all,  

I new to the Ubuntu world but have converted 2 laptops in my household to Ubuntu and enjoy using them in my home network (cable modem connected to wrt54g2 router, which is hard wired to my main desktop computer)

I want to be able to dual boot my main destop computer with ubuntu and windows 7.

I do however have some concerns,  I greatly appreciate any help pointing me in the right direction etc

I use this main computer to wirelessly share files with 2 other computer and a media player in my home network.  All the files that I am currently sharing are obviously stored on my windows partition.

so my question is, once I dual boot this computer will my other computers, and most importantly will my media player still be able to access my windows partion in order to play the media stored there?


Thanks much for any help you can offer.

---

### Post by Thryn on 2010-08-31
I believe the answer is yes. I can see my Windows 7 (ntfs format) partitions fine from Ubuntu. At one time I had a bunch of music stored in a Windows partition and I could play it just fine. However, Windows will not see your Ubuntu partition(s) due to lack of support for the relevant formats (ext3 or ext4 I think).

---

### Post by tom.swartz07 on 2010-08-31
> **Thryn said:**
> I believe the answer is yes. I can see my Windows 7 (ntfs format) partitions fine from Ubuntu. At one time I had a bunch of music stored in a Windows partition and I could play it just fine. However, Windows will not see your Ubuntu partition(s) due to lack of support for the relevant formats (ext3 or ext4 I think).

Correct.
You could access Windows files as much as you want, but unless you do some major modifications to Windows, you wont be able to read Ubuntu files. 

Current Ubuntu installations (which you likely have) use the EXT4 filesystem, if you are so inclined to try and get Windows support for it.

Hope this helps!
Cheers!

---

