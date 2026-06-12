---
title: "WINRAR part 2 problem"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by ALSY7 on 2010-08-08
Hi Guys 
       ive got a 2 part winrar,i got the password and when i extract part 1 it gets to 98% and asks for part 2 and goes to clipboard and then cancels.part 2 has extracted but part 1 says the same error message.any ideas?
:p
Thanks&Regards

---

### Post by dwbsr on 2010-08-08
> **ALSY7 said:**
> Hi Guys 
       ive got a 2 part winrar,i got the password and when i extract part 1 it gets to 98% and asks for part 2 and goes to clipboard and then cancels.part 2 has extracted but part 1 says the same error message.any ideas?
:p
Thanks&Regards
Sounds like winrar can't find part 2, make a folder on your desktop put both .rar files into the folder and try to extract again.

---

### Post by ALSY7 on 2010-08-08
Thanks for the reply.
Yes tried that and rebooted,got same error message at 98%.
It did create the new folder but i had to cancel and the folder was empty.Regards

---

### Post by gandaran on 2010-08-08
what rar package do you have installed? the unrar-free? try installing unrar, rar and p7zip-full

---

### Post by ALSY7 on 2010-08-08
ive got the standard Ms WinRar.I couldnt get unrar to install.
It lets me unpack part2 of the rar,its strange ive never had a problem like this before.

---

### Post by ikt on 2010-08-08
> **ALSY7 said:**
> ive got the standard Ms WinRar.I couldnt get unrar to install.
It lets me unpack part2 of the rar,its strange ive never had a problem like this before.

try getting the .rar files again, sounds corrupt.

---

### Post by ALSY7 on 2010-08-08
yes i got another version of it which had just 1 part and it worked fine,so like you say corrupt file.thanks for your help,you put me on the good road.regards AL:popcorn:

---

### Post by gandaran on 2010-08-08
> **ALSY7 said:**
> ive got the standard Ms WinRar.I couldnt get unrar to install.
It lets me unpack part2 of the rar,its strange ive never had a problem like this before.
what happens if you run
```
sudo apt-get install unrar
```
theres no need to run windows applications, rar files work just as good with native programs
for creating rar files install rar.

---

