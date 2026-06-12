---
title: "So frustrated: can't change directory in termanls"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Shiseiji on 2011-07-23
I know just enough to be frustrated. I am trying to change directories so I can unpack an image to create a boot micro SD

terminal shows ron@ron-Linux~$

DIR lists my directories including "Nook".

cd /Nook returns "No such file or directory.

Installed Krusader.

Krusader shows /home/ron

cd/home/ron/Nook returns "No such file or directory.

What obvious to a dedicated user is this noob missing?

TIA

Ron

---

### Post by malspa on 2011-07-23
> **Shiseiji said:**
> 
DIR lists my directories including "Nook".

Do you mean **ls**?

> **Shiseiji said:**
> cd /Nook returns "No such file or directory.

Try **cd Nook**.

> **Shiseiji said:**
>  cd/home/ron/Nook returns "No such file or directory.

Try putting a space after "cd": **cd /home/ron/Nook**

---

### Post by centaurusa on 2011-07-23
> **Shiseiji said:**
> cd /Nook returns "No such file or directory.


Try cd \Nook or cd Nook

---

### Post by realzippy on 2011-07-23
1. Linux is case-sensitive.
   "DIR" won't show anything.Btw,use "ls" instead of "dir"....
2. If "dir" shows "Nook",you had to type:

   ```
cd Nook
``` 
    to access the folder.  

3. Paste the original outputs from your terminal,so we can find typos.

---

### Post by thefasterblueone on 2011-07-23
when going to "cd /Nook" use [COLOR="Red"]~[/COLOR]. Example: ```
cd ~/Nook
```


cd/home/ron/Nook   needs a space between cd and /  { cd /home/ron/Nook }

---

### Post by coffeecat on 2011-07-23
> **Shiseiji said:**
> cd /Nook returns "No such file or directory.


"cd /Nook" is looking for a folder called Nook in the root of the filesystem. The commands others have given you will get you to the Nook sub-directory of your home folder when you are in your home folder in the terminal.

---

### Post by Shiseiji on 2011-07-23
ron@ron-Linux:~$ cd ~/Nook

Did it! 

To all who provided help: Thanks!

I couldn't get copy/paste to work, who knows.  It was about then my frustration meter started to peg out. Did this time. Duh, habit [crtl] c [ctrl] v dosen't cut it.

Sorry about the confusion with case, I knew to use lower then didn't type it in correctly. My bad when case is important. Thanks for the patience. So now I have a "sudo dd if=nookhoney04.img of=/dev/sdd1 bs=1M" = "password for ron"

I don't remember setting two passwords, but the one I use for Unbutu updates isn't correct . . .

---

### Post by centaurusa on 2011-07-23
> **Shiseiji said:**
> 

I couldn't get copy/paste to work, who knows.  It was about then my frustration meter started to peg out. Did this time. Duh, habit [crtl] c [ctrl] v dosen't cut it.



Try[FONT=Times New Roman, serif][SIZE=3][/SIZE][/FONT] Ctrl-Shift-V

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

