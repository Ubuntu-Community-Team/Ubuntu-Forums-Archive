---
title: "linux for dummies"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by GrumpyOldGoat on 2011-09-08
Which version would be the best to have on hand for the 'dummy' questions that seem to pop up on irregular occasions?

In the last 2 years quite a few have slapped me, so I learned to work around them, but the problems are still there and finding answers are not always easy by the time I search through thousands of posts with a related subject title.

I am using Ubuntu 11.04, upgraded fro 9.04 with a boot issue with GRUB that tells me to just use this command line to boot normally, that gives me an error on login......

Thanks for any help,
Drew

---

### Post by donkyhotay on 2011-09-08
are you asking what book you should buy? Personally I wouldn't recommend buying a book for "dummy" type questions. Those change all the time and the books quickly become obsolete. Google is your best option for dummy type questions. I generally only use actual reference books for networking stuff where I can't get online to ask the question and generally it's more of an advanced problem.

//edit: BTW, if you post what kind of problem you're having with GRUB there is a good chance someone here might know the answer.

---

### Post by ubudog on 2011-09-08
Are you talking about the "* for Dummies" series of books?

Also, do you have Windows installed (dual-boot)?

Upgrading to 11.04 from previous versions has presented problems to many people.  I recommend doing a clean install, backing up all your stuff to an external hard drive, or flash drive, then copying it back into the new install.

The command I use to backup my stuff is:
```
rsync -av --progress /home/michael /media/externalhd/
```

That'll create a directory on the hard drive called michael, with all the contents of your home directory in it.  If you have other users on the computer, and want to backup their stuff, do this:

```
rsync -av --progress /home /media/externalhd/
```

Hope that helps, let us know if you have any questions!  :-)

---

### Post by ubudog on 2011-09-08
> **donkyhotay said:**
> are you asking what book you should buy? Personally I wouldn't recommend buying a book for "dummy" type questions. Those change all the time and the books quickly become obsolete. Google is your best option for dummy type questions. I generally only use actual reference books for networking stuff where I can't get online to ask the question and generally it's more of an advanced problem.

//edit: BTW, if you post what kind of problem you're having with GRUB there is a good chance someone here might know the answer.

+1

Google is your best friend for stuff like that.

---

### Post by GrumpyOldGoat on 2011-09-08
Sometimes a hard copy is the best, easiest and most convenient way.

Both google and Ubuntu Forums are good sources... IF you have reliable internet access.

Thanks for your suggestions, every bit helps.
Drew

---

### Post by GrumpyOldGoat on 2011-09-08
I had windoze vista 64 bit home premium on this computer that was slowly dying.
ms support took little notice of my issues telling me that I just needed to do another 'update' even though it was the 'updates' that retrograded the usability and functionality of my computer.
I installed Ubuntu (8 I think)as a backup OS.  2 days later windoze stopped recognizing the keyboard on bootup.

ms 'non-support' kept telling me to type in various commands and I kept telling them to toddle their little butts on over to show me how that's done when their software ignores the keyboard.
It's still there and still dead... nobody showed up.

I think I am going to do a reformat and new install of Ubuntu and install windoze as a 'virtual drive' OS for those times when it's really needed (as if that will ever happen again).

Thanks for the instructions on backing up everything!

Drew

---

