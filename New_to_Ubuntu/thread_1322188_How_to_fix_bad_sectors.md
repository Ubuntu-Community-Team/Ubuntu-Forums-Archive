---
title: "How to fix bad sectors?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-10
im running a 106gb Samsung HM160HI, and ive just found out today that she has bad sectors. Now, although its only one, i still wanna fix it, just to keep the old girl purring. so how do i fix this "sector"

---

### Post by juancarlospaco on 2009-11-10
Buy a new disk.
Bad sector is already stored on badsectors file to avoid using it.

---

### Post by jnorthr on 2009-11-10
have used the 'dd' command a few times and you might be able to get it to re-initialise the bad sector. see here: [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by JamesParnell on 2009-11-10
ooh ok thanks, i think that sector might be the reason why i've lost 20gb of my HDD.

---

### Post by coffeecat on 2009-11-10
How did you find the bad sector? How old is the drive?

With the sophistication of modern disc drives' firmware, there have probably already been several bad sectors detected and remapped without you knowing about it.

I agree with juancarlosparco. If that was my drive, I would copy any valuable data off pronto and discard it. My data and time is more valuable than a disc drive.

---

### Post by JamesParnell on 2009-11-10
i found it through Palimpset Utility in 9.10 and the drive is only a month of two old, maybe the failure of my old install is the reason why its messed up...is there any way to actually fix the sector?? i cant afford a new drive and "DD" command i am not familiar with, so i would need some help using it

---

### Post by coffeecat on 2009-11-10
Ah - Palimpsest.

Two comments. I take back everything I said - temporarily. :wink: There have been reports on the forum of Palimpsest reporting daft data and false alarms with some makes of drives. You might want to do a forum search to get the overall picture. If you post the detailed data under "More Information" someone with more knowledge than I could cast an eye over it and tell you if it makes sense.

On the other hand - I read somewhere that Google published some interesting data on their experience of drive failures. The picture was that some would fail in the first month (fairly heavy usage), but those that survived would mostly last five years or more. So - it's not inconceivable for a new-ish drive to fail.

Sorry I can't be of more help.

---

### Post by QIII on 2009-11-10
Just a few more cents worth...

Sometimes rough handling of the disk while handling/installing it may cause the heads to bounce on the platters.  

Best case is that there is damage to one spot on the drive.

Worst case is the possibility that the head will start to drag on the platter.  That means big trouble, as you might well imagine.

If you really have a bad sector and it is caused by physical damage, the likelihood that further damage will occur is high.

Save everything OFTEN.

Use a tool to check the disk for defects often.  Not sure I can recommend Palimpsest as that tool.

If you see more bad sectors starting to appear, back everything up and go straight to BestBuy or Fry's.

---

