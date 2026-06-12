---
title: "Is there a Driver for this?"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Rsonic on 2011-07-28
Hello I recentley switched from Windows to Ubuntu (11.04) on my Acer aspire 3002LC. Now my problem is that there seems to be no specific Driver for my graphic card (SiS M760G). I have been googleing around but the only thing i found so far is a try of an aftercoded driver of a user, who doesn't seem to be very engaged to finish it (quits becaus of missing help) and the binary driver that Ubuntu is using as Default definitly doesn't get the performance out of my Graphic card. I wanted to know if there is any solution , because this topic seems to be a pretty outdated one.
Many Thanks if you could giv me advice ^^.

Rsonic

---

### Post by ~!geek!~ on 2011-07-28
Did you try to let 'additional driver' application identify the card you are using. If not, open additional driver application using: 
strike window key once to get dash-> start typing addi... -> use mouse to select additional drivers -> if you see the driver available select and activate it by downloading the driver.

---

### Post by Rsonic on 2011-07-28
Tried it but theres no driver . The problem is Known but the manufracturer has no intention to make one so there isnt one ... sadly.

---

### Post by Rsonic on 2011-07-30
*PUSH* isn't there anyone capable of helping me?

---

### Post by linuxman94 on 2011-07-30
Hate to break it to yah, but it's not gonna work.  SiS IGPs are just poorly supported and there are no drivers for them.

---

### Post by Rsonic on 2011-07-30
oh thats not good.... isnt there any alternative or sonething like an acalleration program?

---

### Post by Dlambert on 2011-07-30
Install the latest mesa libs? or freeglut3, just a suggestion

---

### Post by gordintoronto on 2011-07-30
It's a basic, cheap video adapter, which provides basic functions. You can't expect much more from a six-year-old, low-end laptop.

---

### Post by Rsonic on 2011-07-31
My point is just that i've seen the peformance on windows XP and expected it here to be at least the same to provide...

---

### Post by Paqman on 2011-07-31
> **Rsonic said:**
> My point is just that i've seen the peformance on windows XP and expected it here to be at least the same to provide...

Unfortunately not. Some of the more obscure cards aren't well supported. This is one of them. If Windows is giving you better performance then that's the OS to use if you want 3D graphics.

---

### Post by Rsonic on 2011-07-31
Okay, but that sure won't let me run that Windows Sh*t.

---

### Post by Dlambert on 2011-08-14
Seriously, you may need freeglut3 installed, i had to do it on my GM45 before any OpenGL application would run.

---

