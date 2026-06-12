---
title: "ubuntu cd upgrade won't boot"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by becca2010 on 2010-11-26
i burned the 10.10 ubuntu cd and installed,it said sucess install but needs to restart, restarted but it wont move past the main sreen that just has ubuntu on it?

---

### Post by madjr on 2010-11-26
i suppose with the live disk everything went fine, so thats weird

what is your computer model and graphics card?

did you install now a new partition?

---

### Post by becca2010 on 2010-11-26
ha computer modal unknown ,its a shell with many different parts,and yes i did a full partition ,graphic card is good,i was running hardy 8.04 before the ungrade ,i'm using the install disk now to be able to get online to fine answers ,i've tryed three time to erase hard drive and do a complete new install from disk but all with the same result,it dose tell me i have an error so that might be the problem

---

### Post by sikander3786 on 2010-11-26
> it wont move past the main sreen that just has ubuntu on it?

Can you please press Esc at that screen and produce the text here, if you can see it.

Another workaround is to put in the "nomodeset" parameter in the Grub line.

Press and hold down Shift key at Bios screen. Grub menu should pop up. Highlighting the first entry, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Can you see the desktop now?

---

### Post by zipteye on 2010-11-26
Take the disc out.
Power down the computer by holding down the power button.
Wait about 20 seconds.
Power computer back on.

---

