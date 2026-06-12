---
title: "Help with 'mv'"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by jinba.ittai on 2010-12-29
If you havent already guessed, this is the startup file for conky. I am trying to get it in the home folder.



EDIT: Dont worry about the mv command, i just realized it wasnt supposed to go into the /home folder but into the user home folder /home/(username)


But now i have a problem, when i move files, it takes forever for them to transfer to the destination (only in the gui). 

For example, i move conky start file into home folder, and although it shows up in the home folder under hidden files, it still is present on my desktop and i cannot delete it!

---

### Post by audiomick on 2010-12-29
I suspect that you can't erase the file because of something to do with permissions.

If you are sure that the file is really copied to where you need it, and working properly, you could try erasing it from the desktop by starting nautilus with root privileges.

to do this:
```
gksu nautilus
```
in the terminal. You will be asked for you password. Type your login password and then enter. You will not see what you are typing.

Be careful using nautilus in this way. It will erase system files without asking for confirmation if you tell it to.


Another way, if you are happy with the terminal, might be
```
sudo rm /path/to/file
```

I would suggest looking at
```
man rm
```
before you do this, as rm in combination with sudo is potentially fatal to your system if you get it wrong. Pay particular attention to what the option -r and the option * mean.

---

### Post by jinba.ittai on 2010-12-29
I tried 'rm' and other commands. It kept telling me this file was no longer in that destination. But it showed in the Desktop Gui. 




After reboot this morning, everything is fine. So ill go ahead and mark as solved.

---

