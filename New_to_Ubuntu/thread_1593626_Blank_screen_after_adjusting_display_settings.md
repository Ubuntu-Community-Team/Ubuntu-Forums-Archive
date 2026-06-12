---
title: "Blank screen after adjusting display settings"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by radiosgalore on 2010-10-11
Well...! 

I never thought i'd take the plunge and ditch Windows but i'm glad i did. Spent quite some time messing with programs and settings and yes it had to happen eventually...


I was in the Display settings trying to clear a compositing error Docky threw up and must have set things too high cuz all i got was a blank screen  with the thinnest of lines at the top. So... i needed input a command line and a friend told me to enter sudo rm etc/X11/xorg.conf which i did not knowing what it was or why. terminal then said the file or directory didnt exist despite me seeing it as I booted from CD and running live. couldnt edit or delete it from there either. Now i'm stumped and no so little about command lines i have no clue how to sort this without a format. ok essay over i'll wrap up with a final word. HELP!!

---

### Post by celticbhoy on 2010-10-11
Have you tried booting into recovery & reconfiguring packages?

---

### Post by radiosgalore on 2010-10-11
> **celticbhoy said:**
> Have you tried booting into recovery & reconfiguring packages?

nope. not even sure how to. your talking to a total novice here i feel like i'm having to re learn how to use a computer

---

### Post by celticbhoy on 2010-10-11
When you switch the PC on, after the bios info grub you will eather get a message saying press 'ESC' for menu, or grub menu will load.
If you get 'ESC' then press the esc button funny enough.

when you see the menu you will have at least two options, choosed the second from top

when the recovery menu loads, there will be an option to reconfigure or fix packages select that first.

thenh select normal boot

---

### Post by radiosgalore on 2010-10-11
OK after considerable fussing got it to work. somehow booted into a low res version and manualy adjusted things. serves me right for messing around i guess

---

