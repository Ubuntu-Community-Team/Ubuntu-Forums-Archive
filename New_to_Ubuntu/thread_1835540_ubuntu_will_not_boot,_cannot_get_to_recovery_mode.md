---
title: "ubuntu will not boot, cannot get to recovery mode"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by stevebobby on 2011-08-29
After installing a few packages last night and possibly doing something wrong to a bash file (? I am new to linux), my Ubuntu will not boot. I can't even do the 'esc' into recovery as I get a brief Intel message, a brief Ubuntu logo and then only the purple screen. Hitting esc at any of these points will not work. 

I have access to another computer. I am thinking I can get Ubuntu onto a USB and try to boot with that? Is that a good idea? If so, how exactly should I do this?

thanks a bunch!

---

### Post by snip3r8 on 2011-08-29
What packages did you install?

---

### Post by HarrisonNapper on 2011-08-29
It depends on the file modified really. I think a good thing to do would be to Ctrl-Alt-F1 when you get to the purple screen to get to a terminal (let us know if you can't do that). Login, then type "dmesg |less" and then "G" (note the capital) to jump down to the end. "j" and "k" for moving up and down. Look for any errors (things with exclamation points usually) and look them up online.

Do you remember which file you edited? If you can get to a terminal, we can probably give you the commands to re-edit it back to an unedited state :)

Cheers.

---

### Post by stevebobby on 2011-08-29
Thanks for responding to my post.
I am trying to install samtools which has several dependencies including zlib, libncurses5-dev and a few others that were listed on the installation guide (although it was hardly a guide). I used the sudo apt-get command for most of these, but the only one I think I may have messed with is the zlib where I typed make clean and make after it was already installed...
As for the bash file (the one in my home directory), I was trying to add the samtools directory to my shell's PATH, but I may have done that incorrectly?

---

### Post by stevebobby on 2011-08-29
ctrl-alt-F1 worked and I logged on, now I see command line.
following your instructions, a long list comes up. Navigating up through it I cannot see any errors. The last line says unknown key ffd1 pressed? That could be me... I will look more carefully for errors...

> **HarrisonNapper said:**
> It depends on the file modified really. I think a good thing to do would be to Ctrl-Alt-F1 when you get to the purple screen to get to a terminal (let us know if you can't do that). Login, then type "dmesg |less" and then "G" (note the capital) to jump down to the end. "j" and "k" for moving up and down. Look for any errors (things with exclamation points usually) and look them up online.

Do you remember which file you edited? If you can get to a terminal, we can probably give you the commands to re-edit it back to an unedited state :)

Cheers.

---

### Post by ajgreeny on 2011-08-29
For future reference, it is not Esc you press to get you to the grub menu and recovery mode any more.  Since grub2 appeared you need to press shift when booting to get the menu.

Nevermind, you got to a desktop, albeit a command line, by using Ctrl+Alt+F1, so you can still probably sort out things from there once you remember what file you edited.

---

### Post by HarrisonNapper on 2011-08-29
If you aren't sure what file you edited, hit the up arrow until you get to a line for editing a file IF you edited from command line. You can also do "less ~/.bash_history" and look through that ("G" to get to the bottom of it--no pun intended).

If you're not comfortable with terminal, try out shift for grub rescue mode. Rescue mode has a number of goodies.

---

### Post by stevebobby on 2011-08-30
> **HarrisonNapper said:**
> If you aren't sure what file you edited, hit the up arrow until you get to a line for editing a file IF you edited from command line. You can also do "less ~/.bash_history" and look through that ("G" to get to the bottom of it--no pun intended).

If you're not comfortable with terminal, try out shift for grub rescue mode. Rescue mode has a number of goodies.

Thanks HarrisonNapper, this is helpful. I can see all the commands I did to screw this thing up in the first place. How do I exit this list from less ~/.bash_history?

I got it - q

---

### Post by stevebobby on 2011-08-30
I need to edit my bash file that i changed to add a directory to my path. This file is in my home directory but it is hidden (doesnt show with ls command). I forget the exact name of the file, so how do I list hidden file names?

google is a wonder, sorry for the newbie questions.

ls -a did it.

---

### Post by ajgreeny on 2011-08-30
> **stevebobby said:**
> I need to edit my bash file that i changed to add a directory to my path. This file is in my home directory but it is hidden (doesnt show with ls command). I forget the exact name of the file, so how do I list hidden file names?

google is a wonder, sorry for the newbie questions.

ls -a did it.
Don't worry about it.  You're learning fast, and you will probably not forget those things in a hurry.

---

