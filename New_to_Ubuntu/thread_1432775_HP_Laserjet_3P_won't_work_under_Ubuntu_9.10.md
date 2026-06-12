---
title: "HP Laserjet 3P won't work under Ubuntu 9.10"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Paul G Coleman on 2010-03-18
I installed Ubuntu 9.10 yesterday and all was fine. I then added my HP Laserjet 3P printer on LPT1 which seemed to be fine. However, when I try and print from Open Office the two lights on the printer come on but nothing happens. I've tried the different driver options but it makes no difference? I know the printer is okay because I've got a dual boot machine with Windows XP and it works fine under that. Has anybody else had this problem and knows of a solution?
 
Thanks, Paul.

---

### Post by yeats on 2010-03-18
> I've tried the different driver options but it makes no difference?

Which driver options have you tried?  Is there an option that matches your printer model?  HP is pretty well supported in Linux...

---

### Post by arochester on 2010-03-18
Have you checked the Paper Size? It is a while since I had an HP Laser but I seem to remember that it defaulted to US Legal. I used A4 paper and had to change it, otherwise the lights flashed because there was no US Legal size paper available...

---

### Post by Paul G Coleman on 2010-03-18
Re drivers - I selected the first (recommended) one in the list and when that didn't work I tried a couple of others but I can't remember exactly which ones.
 
Re paper size - It was definitely set to A4.
 
If HP are well supported then I'll play around a bit more. I just didn't want to waste my time if the 3P is not supported, it is, after all, nearly 20 years old!!
 
Thanks, Paul.

---

### Post by yeats on 2010-03-18
Thought:

Create a plain text file.  At the terminal:

```
gedit
```

Then type some stuff, save it as "test.txt".  Then (also from the terminal):

```
lp test.txt
```

If it prints, you know the printer is working and that arochester's idea is probably a clue to the solution.

---

### Post by Paul G Coleman on 2010-03-18
Yep, sounds like a plan. I'll do that tonight and post back the result.
 
Cheers, Paul.

---

### Post by Paul G Coleman on 2010-03-18
Well I double checked the page format and it is A4, which is correct. I created a text file and tried to print it from within terminal as suggested but exactly the same thing happened... the printer went from having one light on to two as though it was going to print and then... nothing. Looking in the print queue it says it's 'processing'

I know for sure it's not the hardware as it works under XP.

Paul.

---

### Post by yeats on 2010-03-18
Is the printer giving you any error codes?

---

### Post by PRC09 on 2010-03-18
I think you could also try the driver for the 2P as it is similar or the original Laserjet II and see if either will work...

---

### Post by Paul G Coleman on 2010-03-19
Thanks for the suggestions...

Re error codes - no it says [COLOR=Red]'00 READY A4'[/COLOR] on the display as it always has done when it's ready to print.

Re 2P driver - I just tried that and it was exactly the same.

This is really irritating :mad: 

I'd love to be able to ditch XP altogether but can't if I'm unable to print anything.

Cheers, Paul.

---

### Post by Paul G Coleman on 2010-03-21
I solved this by buying a more up to date printer. I bought a Samsung colour laser which was also a pain to get working but now seems okay :D

The colour laser cost me half of what the mono one cost back in 1992. I guess that's progress for you.

Paul.

---

