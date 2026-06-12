---
title: "noob question"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by DAWARIS1 on 2009-07-26
when following "how to's" for example [http://ubuntuforums.org/showthread.php?t=870001&highlight=turn+sound+support](http://ubuntuforums.org/showthread.php?t=870001&highlight=turn+sound+support) when it says 
sudo apt-get install build-essential linux-headers-`uname -r`
what does the 'uname -r' stand for, do u have to put something else there in its place?

---

### Post by Sub101 on 2009-07-26
If you were to type uname -r on the terminal you would get the number of your kernel.

So all that is doing is telling the apt-get the name of the kernel you want to "build-essential".

---

### Post by ubername on 2009-07-26
> **DAWARIS1 said:**
> when following "how to's" for example [http://ubuntuforums.org/showthread.php?t=870001&highlight=turn+sound+support](http://ubuntuforums.org/showthread.php?t=870001&highlight=turn+sound+support) when it says 
sudo apt-get install build-essential linux-headers-`uname -r`
what does the 'uname -r' stand for, do u have to put something else there in its place?

I don't know what they stand for but I'm sure a quick ggogle would explain. However it is worth noting that the ` character is a 'back tick' (top left of UK keyboard) rather than a 'single quote' (bottom rightish of UK keyboard)  - if you don't cut and paste of course.

---

### Post by Liolikas on 2009-07-26
uname -r is command which shows your Linux kernel version. Try it out. ;)
So command you posted means install same kernel headers version as kernel siple as that. It should work without edition just copy paste.

---

### Post by AndyCee on 2009-07-26
Actually a good question.

Short answer - type it in exactly and it is a valid command, backticks and all:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Long answer:
Backticks (`) nest commands. If you type
```
uname -r
```
into a terminal, it will tell you the kernel version of your operating system. I get "2.6.28-13-generic". So the expanded command would be:
```
sudo apt-get install build-essential linux-headers-2.6.28-13-generic
```. Putting `uname-r` in the command means it will work for any kernel version.

Does that make sense?

---

### Post by DAWARIS1 on 2009-07-26
Awesome! Thanks for the answers, i realised what i was doin wrong, i wasn't using the back tick (`) when typing it in i was using (') if u catch my drift! just like Ubername was saying, lol.

---

