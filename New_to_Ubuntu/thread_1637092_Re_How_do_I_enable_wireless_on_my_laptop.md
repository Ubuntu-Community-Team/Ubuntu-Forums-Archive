---
title: "Re: How do I enable wireless on my laptop?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by xavierkang on 2010-12-04
Before asking question,i let you all know my laptop spec first.
Compaq V3839TU
Wireless Broadcom 43XX
Ubuntu 10.10

Question is i dont know how to enable wireless.My laptop got a switch button to trun on/off for bluetooth and wireless.I turn it off before,after that turn on.The bluetooth and wireless no function already(meaning disabled or turned off).I have go to  screen upper right hand side click bluetooth to turn on.But wireless I dont know how to turn it on.Can anyone teach me by using terminal ?

---

### Post by Spyderkid on 2010-12-04
can you run 

lsusb

in a terminal please nd post the stuff that comes out.

---

### Post by idi0tf0wl on 2010-12-04
Are you saying your wireless was working before and is no longer?

In any case, reference this thread: [http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

It was of help to me.

---

### Post by xavierkang on 2010-12-04
My problem is top of the right hand side on screen got wired and wireless network icon. And the wireless view that is wireless is disabled,but i check to my wireless driver side,it view that the wireless driver is activated. So how to solve this problem

---

### Post by idi0tf0wl on 2010-12-04
Again, please reference this thread:

[http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

I have a feeling that that's what's gonna do it for you. If you're having a hard time understanding the English or something (but please not out of laziness), post back and I'll dash out the commands you should be looking for. Seriously. This is probably the solution to your problem.

---

### Post by Penguin=) on 2010-12-04
Easy way to solve is to do exactly this:


go to System-->Preffrences-->then find network connections.

When it opens go to the wireless tab, and find auto (The name of your router), then click on it  and select edit, then at the top make sure connect automaticly is ticked, then turn it off and on again (or in your case, just turn it on), restart your computer and there you go!!!

hope this helps you!

---

### Post by xavierkang on 2010-12-04
Finally I done it.By using command.However thx to you all.
 
```
sudo rfkill unblock all
```

---

### Post by idi0tf0wl on 2010-12-04
Congratulations!

Please mark your solved threads as [SOLVED]

---

