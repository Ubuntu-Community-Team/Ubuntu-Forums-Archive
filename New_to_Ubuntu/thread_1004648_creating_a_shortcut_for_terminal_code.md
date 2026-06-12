---
title: "creating a shortcut for terminal code?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-12-07
I would like to make a shortcut for AssaultCube ( a game)

Currently to get it to work i have to do the following commands -

```
mckenzie@mckenzie-ubuntu:~$ cd /home/mckenzie/AC
mckenzie@mckenzie-ubuntu:~/AC$ sudo sh ./assaultcube.sh
 
```

how can i get a shortcut to do this for me? or is it a matter of writing some code [if so - a little help]?

cheers

---

### Post by lovelyvik293 on 2008-12-07
Hai man you can write a shell script for your code.

---

### Post by phantomjoker on 2008-12-07
ok, how would I go about doing that?

All i know about shell script is it always starts with a # - i think!

---

### Post by lovelyvik293 on 2008-12-07
Just make a file and put 
```
sudo sh /home/mckenzie/AC/assaultcube.sh 
```
in that file and put this file in the /bin folder.With applying the execute permissions.
Or you can add the path of your game to the PATH variable.So that it can be used as a command.

---

### Post by bp1509 on 2008-12-07
d

---

### Post by DirtDawg on 2008-12-07
You don't need a shell code, you just need to set up aliases. Make a backup of your .bashrc file in your home folder(just in case), then open it with your favorite text editor:
```
cp ~/.bashrc ~/.bashrc.DEFAULT
gedit ~/.bashrc
```
Right around line 68, you'll see a section that looks like this:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
Uncomment the lower area so it looks like this:
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```
Ta-daa, now you can build aliases! You can see some examples just below the section mentioned. Uncomment any of those you might like. Then you can make your own and simply add them to the list. In your case, it might be something like:
```
alias assault="/home/mckenzie/AC/assaultcube.sh"
```
Then you can run Assault Cube by typing the word 'assault' into your terminal (Note you should *not* run Assault Cube as root!). Now any time you need an alias, simply add it to your .basrc file, or you can create a new file in your home folder called '.bash_aliases' and store them there.

---

### Post by snova on 2008-12-07
Referring to the above suggestions by DirtDawg, it is '.bashrc', not '.basrc'. However, that still requires a terminal. It should be simple to create a short script for the icon.

Put this in a file somewhere, and give it executable permissions:

[PHP]
#!/bin/bash
cd /home/mckenzie/AC
sudo sh ./assaultcube.sh
[/PHP]

I don't know whether the 'assaultcube.sh' has to be run in its installation directory, or whether it correctly compensates for symbolic links, so this is probably the safest route.

Then create the icon as normal. For "command" or "executable" or whatever it is, put the full path to the file you just created.

Also, why sudo? You shouldn't run it as root.

---

### Post by mgmiller on 2008-12-07
To add a launcher to your Applications drop down in the top panel, Right click Applications and select "Edit Menus".

On the left side,  Click "Games" to high lite it.
On the right side, click "New Item"
Leave Type as Application
Name:  Assault Cube  (or whatever you want it to say)
Command:  sudo sh ./ /home/mckenzie/AC/assaultcube.sh
Comment: whatever you would like it to say when you mouse over the entry in the menu system.

If you want to change the icon, just click on it the big icon on the left side and pick something you like.

Click ok and that should do it.
When you click on the game, it will ask you for your password and then should run.

I am also curious why it needs sudo to run.

---

### Post by snova on 2008-12-07
That brings to mind another idea- when creating a launcher, it should give you the option of specifying the working directory. Fill this in with the location. Then, for the executable, use './assaultcube.sh' (if that does not work, use an absolute path).

But, do you know that it is necessary to run the program in its directory? If not, just fill in the path to the script.

---

### Post by phantomjoker on 2008-12-08
um well it needs sudo because if i run it without - the graphics are all line'y - as in just lines of colour (cant see anything) so cant exit, so have to restart - why would that be?

---

### Post by phantomjoker on 2008-12-08
> **snova said:**
> Referring to the above suggestions by DirtDawg, it is '.bashrc', not '.basrc'. However, that still requires a terminal. It should be simple to create a short script for the icon.

Put this in a file somewhere, and give it executable permissions:

[PHP]
#!/bin/bash
cd /home/mckenzie/AC
sudo sh ./assaultcube.sh
[/PHP]

I don't know whether the 'assaultcube.sh' has to be run in its installation directory, or whether it correctly compensates for symbolic links, so this is probably the safest route.

Then create the icon as normal. For "command" or "executable" or whatever it is, put the full path to the file you just created.

Also, why sudo? You shouldn't run it as root.
Ok, i created the text document

but what .****** do i need to put at the end to make it a command... sorry for the basic questions

---

### Post by snova on 2008-12-08
The convention is .sh, but it doesn't matter. Linux doesn't care, you could use ".beans" and it wouldn't make a difference.

---

