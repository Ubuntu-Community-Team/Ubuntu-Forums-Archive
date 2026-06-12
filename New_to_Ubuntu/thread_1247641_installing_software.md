---
title: "installing software"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by il pepe on 2009-08-23
i installed software, not from the adding/removing software, nor from the synaptic kit.
From cd.
I installed it under my personal map: /home/user/map

The stupid thing is, the software works, as i started it once the installation was finished (that was an option);
Now i'm trying to search for a start point, to restart the software, and i don't seem to find it...
Were are those thinks placed? so i can add it to my desktop or menu's and stuff...

---

### Post by MelDJ on 2009-08-23
u can type in terminal sudo yourprogram to run it

---

### Post by Capitalism on 2009-08-23
System > Preferences > Main Menu
Click 'New Item' and name it.
In the Command textbox, just type in the name of the program or the package that you installed. :)

---

### Post by il pepe on 2009-08-23
the sudo program doesn't work, so neither does the add new item thing as it is based on the same.
Tried both before :-S
I need soemthing like the .exe in windows...

---

### Post by MelDJ on 2009-08-23
whats the program you installed?

---

### Post by Bölvaður on 2009-08-23
let's begin from the beginning.
what type of installation was this from the cd?

binary installer (it will look the same as in windows as exe is a binary installer)
and scripts

.deb , a installation package (it will most likely create menu items)

a directory with all files included, just need to copy it to your computer and run it.

source code, did you compile from source?


if you used binary installer, did you run it as root or your own user (if you dont know tell me how you installed it... did you double click a file? what file? did you write something in the terminal?)

---

### Post by il pepe on 2009-08-23
installed it mounting a iso file in the /media/ map.
Then double clicked a install file which started automatically the installing procedure.
Then further i had to choose a place where to install, and i chose /home/user/map.
at the end of the installing procedure, i was asked if i wanted to start the software, i chose yes, so i'm pretty sure software is installed correctly.

If i look back at this, i guess it was a binary install, because it was very similar to a windows install.
i didn't have to give a command or sudo thing, so i suppose i installed it as software under my own user...

the software is Matlab 2009a...

---

### Post by Bölvaður on 2009-08-23
oh yeah matlab doesnt make menu items.

but it isn't much trouble doing that your self.

if matlab places some of it's files into your ~/bin  (~ means /home/username/)
then move those files into correct place. by opening the terminal and...

```
cd ~/bin
sudo mv * /usr/bin
```

and then right click the application menu, select Edit Menus
Click Education and then New item.

Type: Application
Name : Matlab
command: matlab  (it should be the same as the file that was in your ~/bin but now has been moved to be accessable through just typing the name of the file)

---

### Post by il pepe on 2009-08-24
still nothing. I'm going to try a reinstall...

---

### Post by il pepe on 2009-08-24
> **Bölvaður said:**
> oh yeah matlab doesnt make menu items.

but it isn't much trouble doing that your self.

if matlab places some of it's files into your ~/bin  (~ means /home/username/)
then move those files into correct place. by opening the terminal and...

```
cd ~/bin
sudo mv * /usr/bin
```and then right click the application menu, select Edit Menus
Click Education and then New item.

Type: Application
Name : Matlab
command: matlab  (it should be the same as the file that was in your ~/bin but now has been moved to be accessable through just typing the name of the file)
the first bin, is suppose, is the bin which is part of matlab? so under the MATLAB installiation map?
And the files in there have to be copiied to the usr/bin? And that is supposed to do the trick? did i understand that correct?

---

### Post by tarps87 on 2009-08-24
They would be the ones in the bin folder of the matlab install, you only need to copy them if you want to be able to run it by just typing in the commands name. Even so I would make a link rather that moving the file
```
sudo ln -s *pathToMablab*/bin/*matlabLauncher* /usr/share/bin
```

---

### Post by il pepe on 2009-08-24
> **tarps87 said:**
> They would be the ones in the bin folder of the matlab install, you only need to copy them if you want to be able to run it by just typing in the commands name. Even so I would make a link rather that moving the file
```
sudo ln -s *pathToMablab*/bin/*matlabLauncher* /usr/share/bin
```
that did the trick, at least almost. I was getting the splash screen, but that i disappeared.
I read that problem somewhere else, and the trick was to add -desktop in the command line.
Thanks for the help!

---

