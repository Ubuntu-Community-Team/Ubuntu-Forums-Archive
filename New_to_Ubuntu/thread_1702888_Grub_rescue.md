---
title: "Grub rescue"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by KingLex on 2011-03-08
how do i fix grub rescue prompt - i recently just installed 
Ubuntu for like the 100th time and now i get this prompt 
i do have a Live Cd. I have it installed on my 500GB External HDD
i installed it as followed 

8GB to / (root)
2GB for SWAP 
EXT4 for /home/ 

how do i solve the problem ? or what did i do wrong ?

---

### Post by Daveth on 2011-03-08
so what is on the main pc as the operating system? I'm wondering if the live cd wrote grub to the internal hard drive rather than to your external one, though others here may be able to think this through more clearly- grub always gives me a headache!

---

### Post by gordintoronto on 2011-03-08
What problem are you trying to solve? "how do i fix grub rescue prompt" doesn't describe a problem.

---

### Post by KingLex on 2011-03-09
> **gordintoronto said:**
> What problem are you trying to solve? "how do i fix grub rescue prompt" doesn't describe a problem.

when i try to boot from my External Hdd - it says that 
and how its not a issue ? so its a good thing that its doin that ? 
i dont understand

---

### Post by gordintoronto on 2011-03-09
You try to boot from your external drive, and it displays some error message? What error message?

What is installed on the external drive? (For example, it might be Ubuntu Desktop version 10.10...)

---

### Post by KingLex on 2011-03-10
> **gordintoronto said:**
> You try to boot from your external drive, and it displays some error message? What error message?

What is installed on the external drive? (For example, it might be Ubuntu Desktop version 10.10...)

it said ```
error no such devices found 
grub rescue>
```

---

### Post by Rubi1200 on 2011-03-10
As Daveth already pointed out, it is possible GRUB was written to the internal rather than external drive.

Please provide us with more information as gordintoronto has already asked.

Best thing to do is the following:

1. try changing the boot priority in BIOS

2. experiment with the external drive plugged in and out to see what happens when you change the boot device priority in BIOS

3. boot with a LiveCD and post the output of the boot script (instructions in the link at the bottom of my post)

---

