---
title: "Can't find.... anything D:"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by kameil on 2010-10-09
Ok, I feel like this command is too simple to screw up, but here's what I keep getting:
julia@kammy:~$ cd desktop
bash: cd: desktop: No such file or directory

In the same vein, I've been trying to get Alien to work (I use a 32 bit system) and this keeps happening:

julia@kammy:~$ sudo alien -i jdk-6u21-linux-i586-rpm.bin
[sudo] password for julia: 
File "jdk-6u21-linux-i586-rpm.bin" not found.

I just started using Linux (recovering windows user ;) ), and have done a bit of reading up on everything, but it just seems weird that cd desktop is giving me an error. Any ideas?

---

### Post by 23dornot23d on 2010-10-09
Its a CAPITAL    D

Desktop ....

cd Desktop

When looking for files ..... (ls) for list ........ will show you what is in the directory

So you get the filename right .... select the text of the file that you want in the terminal .....  and middle click .... the mouse button

It will copy the filename "selected/highlighted" for you ....... to the command line

---

### Post by BaffledMollusc on 2010-10-09
It's 
```

cd Desktop

```
Linux filenames are all case sensitive :)

---

### Post by vambo on 2010-10-09
cd Desktop

Linux is case sensitive remember!

---

### Post by GabrielYYZ on 2010-10-09
indeed, things in terminal are really picky with their capitalization "cd Desktop" or "cd Downloads" work but "cd desktop" doesn't.

---

### Post by juancarlospaco on 2010-10-09
Aliens dont like .bin

---

### Post by kameil on 2010-10-09
> **juancarlospaco said:**
> Aliens dont like .bin

Oh jeez D: Ok so I have a lot more reading to do. Thank you guys! <3

---

### Post by BaffledMollusc on 2010-10-09
Oh, a couple of other things. To save yourself typing long filenames, you can press TAB to autocomplete. So if you type "cd Des" and press TAB, it will complete the rest without you typing (assuming there's only one directory name that starts with "Des") :)

About the alien command - I think it should work on files that end in .rpm, not .bin, so I'm a bit confused. "bin" files are generally files you run, whereas "alien" converts .rpm packages (used by Linux distributions like Red Hat) into .deb packages (used by distributions like Debian or Ubuntu).

(In case you didn't know, packages are software you can install. Think of them like a self-extracting installer programs you might use on Windows.)

---

### Post by 23dornot23d on 2010-10-09
for a .bin file

give it execute rights .......
chmod u+x filename

to run it .......
./filename

so in your case
[B]chmod u+x jdk-6u21-linux-i586-rpm.bin
./jdk-6u21-linux-i586-rpm.bin[/B]

---

