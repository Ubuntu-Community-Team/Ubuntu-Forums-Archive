---
title: "Pause while booting"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by zcacogp on 2010-05-26
Chaps, 

I have recently installed 10.04 on my desktop machine. And very fine it is too - I am very happy with it! 

One minor niggle tho'. When I boot the machine up, there is a pause in the boot-up sequence. Of around 15 seconds. The sequence goes like this: 

- Machine boots, GRUB is displayed, I choose Ubuntu
- Login screen appears. I choose my account, and type in password
- 'Light' screen is displayed, login tune is played
- **Approx 15 second pause, 'Light' screen is displayed**
- Account appears, with background and panels

Nothing seems to happen during the pause (as far as I can tell), and it doesn't happen on either of the other 10.04 machines I use. 

Are there any diagnostics I can run to see what is happening during this time period, and if there is anything I can do about it? 

It's not major problem, but I'd quite like to have as quick a boot-up as possible!

Thanks, an advance, for any help. 


Oli.

---

### Post by cariboo on 2010-05-26
Are you running an encrypted home directory?

---

### Post by zcacogp on 2010-05-26
Not that I am aware of. 


Oli.

---

### Post by Anjrew on 2010-06-16
any new information on this bug?

the OP has described my exact same problem.  i do not have an encrypted home directory, and in previous versions of ubuntu i have had no similar problems.

I've seen a few other threads talking about this problem too and none have a solution...

---

### Post by migs73 on 2010-06-16
Check to see if your bios thinks you have a floppy drive (assuming you don't of course) and disable it in the bios. None of the posts I've seen regarding this seem to know why it helps but it seems to!!?!

---

### Post by philinux on 2010-06-16
> **migs73 said:**
> Check to see if your bios thinks you have a floppy drive (assuming you don't of course) and disable it in the bios. None of the posts I've seen regarding this seem to know why it helps but it seems to!!?!

See the general help forum sticky. Although a fix has now been released.

---

### Post by migs73 on 2010-06-16
Phil

I think I should just copy your post onto the bottom of mine as we just seem to be on the same threads today!!!! Or may you are omnipresent on all threads? I am beginning to think it is the latter :p.
I think I'll check your excellent sticky first before posting the second or third hand info I end up peddling ):P

---

### Post by zcacogp on 2010-06-16
Hi, 

Thanks for the floppy disabling suggestion; I'll try it. 

I'll have a look at the sticky as well. Thanks for the suggestion. 


Oli.

---

### Post by Anjrew on 2010-06-16
> **migs73 said:**
> Check to see if your bios thinks you have a floppy drive (assuming you don't of course) and disable it in the bios. None of the posts I've seen regarding this seem to know why it helps but it seems to!!?!

HEY that did it!  Yeah never mattered before, but things change.  Thanks a ton for the help.

---

### Post by zcacogp on 2010-06-19
> **migs73 said:**
> Check to see if your bios thinks you have a floppy drive (assuming you don't of course) and disable it in the bios. None of the posts I've seen regarding this seem to know why it helps but it seems to!!?!Ding! Improved things here no end as well. Thanks very much Migs. 

(As an aside, it only held things up on the first log-in. If you were to log out and in again without rebooting then it logged in much more quickly.) 

Happy to mark this thread as solved. Thanks chaps. 


Oli.

---

