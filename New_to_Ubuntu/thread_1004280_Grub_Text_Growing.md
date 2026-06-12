---
title: "Grub Text Growing?????"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Quarkrad on 2008-12-07
I have install 8.10 and for some weeks had absolutely no problem with it (especially booting up????) - it running like a dream.   I dual boot with winXP and when first installed noticed that for Ubuntu there were two lots of text entries in Grub - something like Ubuntu 8.10, kernel 2.26.xxx and another similar entry underneath with (Recovery Mode). I was not concerned why there were four lines of text but a little curious  (I only have one entry, as expected, to boot to winXP).  This morning on boot up I now have three sets of grub lines re booting Ubuntu - why?   I still boot from the first line and all is fine - is it safe to go into the menu.lst file and delete these other Ubuntu lines? (I assume apart from the (Recovery Mode) line - so I only have two lines in Grub for Ubuntu).

---

### Post by nakama85 on 2008-12-07
I would not delete them but just comment them out by putting the # symbol in front of them

this way it make it easy to add them again if needed.

If you ever have a problem with the new kernels you can add the old ones back and boot into them.

> **Quarkrad said:**
> I have install 8.10 and for some weeks had absolutely no problem with it (especially booting up????) - it running like a dream.   I dual boot with winXP and when first installed noticed that for Ubuntu there were two lots of text entries in Grub - something like Ubuntu 8.10, kernel 2.26.xxx and another similar entry underneath with (Recovery Mode). I was not concerned why there were four lines of text but a little curious  (I only have one entry, as expected, to boot to winXP).  This morning on boot up I now have three sets of grub lines re booting Ubuntu - why?   I still boot from the first line and all is fine - is it safe to go into the menu.lst file and delete these other Ubuntu lines? (I assume apart from the (Recovery Mode) line - so I only have two lines in Grub for Ubuntu).

---

### Post by adult swim on 2008-12-07
whenever you get an update for a new kernel it is going to add a new entry into grub so you can boot from it.  it is usually best to keep your current kernel and the one before it, in case you mess something up majorly you will have a fallback that will boot for sure.  you could edit your menu.lst and delete the entries you dont want or just comment them out.  alternatively you could open synaptic and delete the kernels you are no longer using, make sure and not delete the ones you need/want to keep.

---

### Post by cdtech on 2008-12-07
You wont have any issues. You could even remove the old kernels from synaptic package manager if you feel you need to (to save space). I personally keep an old kernel in case the new one dosen't work, but not listed in the menu list. I can select to edit the grub menu and just manually type it in.

---

### Post by taurus on 2008-12-07
You have two lines for the new kernel (one as in recovery mode), then two more lines for the old kernel (one as in recovery mode), and one  memtest plus your windows entry.  Is that what you see on the screen from GRUB menu?

---

### Post by nakama85 on 2008-12-07
> **adult swim said:**
> you dont want or just comment them out.
 why not?....just curious

---

### Post by adult swim on 2008-12-07
im not sure i understand your question.  i was saying that he could either delete or comment out entries he didnt want showing up.

---

### Post by nakama85 on 2008-12-07
> **adult swim said:**
> im not sure i understand your question.  i was saying that he could either delete or comment out entries he didnt want showing up.

Sorry just miss read. I thought I read you don't want to comment them out..lol 3.36am my time. I guess it's time for bed

---

### Post by Quarkrad on 2008-12-07
Thank you all - new to Linux/Ubuntu - your replies make sense.  Out of interest, how much space is saved deleting a kernel?   I tend to try and keep HD to minimum (all those MS updates????) is it worth deleting old versions or is it so small this is not a relevant question.  Perhaps I can answer my own question as there have not been, what appears to be, any lengthy downloads/updates so perhaps the 'old' kernels are small.   I guess, at the moment, I will leave them and just edit out the grub entries.

---

### Post by twiz86 on 2008-12-07
roughly 75-100mb unpacked i beleive. not very much, but then again i have like 12 kernels installed so thats a good chunk of change.

---

