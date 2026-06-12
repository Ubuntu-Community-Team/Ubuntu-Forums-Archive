---
title: "Grub Loader"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-05-13
How do I put XP at the top?

---

### Post by MarcusA on 2009-05-13
I'd guess get startup manager from Add/remove programs, then go to system - administration - startupmanager and change default operating system.

---

### Post by Ericyzfr1 on 2009-05-13
Edit your menu.lst file. You can give a priority number starting with "0".

---

### Post by stretch427 on 2009-05-13
Type in terminal
```
 sudo nano /etc/grub.conf
```
and at the top of that you'll see

```
default         0
```

all you have to do is change the "0" to whichever boot option XP is. It's probably the last one in the boot order. And simply change the value to "3" or whatever yours is. 

then save and exit and when you restart you should have XP set as default.

Cheers!

---

### Post by kakashi_12 on 2009-05-14
That command didn't work. It just created a new file. I even tried it under root. And I couldn't find a startup manager. Do I download it somewhere?

---

### Post by NHArticleTen on 2009-05-14
sudo gedit /grub/menu.lst


then you can shuffle the grub to your personal preferences

---

### Post by hobo14 on 2009-05-14
> **MarcusA said:**
> I'd guess get startup manager from Add/remove programs, then go to system - administration - startupmanager and change default operating system.
Pretty sure that doesn't work.

Edit /boot/grub/menu.lst and shift it higher up in the file.

---

### Post by maybeway36 on 2009-05-14
Run: gksu gedit /boot/grub/menu.lst
Take the XP entry/block that begins with something like "title Microsoft Windows XP" and is about 4 or 5 lines, and move it up right above the line reading ### BEGIN AUTOMAGIC KERNELS LIST.

---

### Post by kakashi_12 on 2009-05-14
nvm, i finally got it. my classmate helped me out.
i had to su through the terminal first.
then i just changed the default number to line 6.
ubuntu was updated once, so my lines of choices are...
 
ubuntu (the most recent)
ubuntu recovery mode
ubuntu (the first unupdated one)
ubuntu recovery mode
ubuntu memory test
other operating systems
windows xp home
 
I'de like to just get rid of that dumb line that says other os's. can i delete it without it messing up my system?
 
My only next question is that if I go to update ubuntu again and there is another choice at the boot loader, does that mean i'll have to edit the menu.lst to be number 7 or 8 next, and every time I update it?

---

### Post by kakashi_12 on 2009-05-14
Actually, technically i didn't put xp at the top. i just made it the default. it is the default highlighted one.

---

### Post by Niniel on 2009-05-14
Yes, the next time there's a kernel update and another pair of kernel/recovery mode entries is added, the numbers will be wrong, unless you uninstall your oldest kernel right away.

---

### Post by stretch427 on 2009-05-14
sorry for the bad command, I didn't check it. I should have,  my bad.
Glad you got it working though.

---

