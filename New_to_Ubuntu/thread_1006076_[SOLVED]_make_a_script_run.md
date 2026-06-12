---
title: "[SOLVED] make a script run"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by egalvan on 2008-12-08
I'm experimenting with GRUB, so I decided to try  a script to automate the edit process.

I placed the following inside a text file:


```
#!/bin/bash
gksu gedit /boot/grub/menu.lst
```

closed it, then changed the properties to make it 'executable',

then saved it to the desktop.

when I double-click, it pops up in a text editor.

So what step(s) did I miss?

(I'm self-taught in all this)

P.S.
this is a screen-shot of the 'properties' for the file.

---

### Post by adult swim on 2008-12-08
you need to open a terminal and cd to the directory that the file is in 
```
cd /home/ernest/Desktop
``` and then run ```
sudo chmod +x edit_grub
```

or you can just right click the file choose properties and then on the permissions tab mark the make file executable box.
EDIT: woops i didnt see you had already tried to make it executable via properties

---

### Post by Kareeser on 2008-12-08
Hm.. you say you've changed the properties to make it executable, but that's a permissions thing...

Can you post an output of the permissions?

```

cd ~/Desktop
ls -l ./edit_grub

```

---

### Post by Vunutus on 2008-12-08
I'd try right clicking it on the desktop and seeing if there are any "execute" contect menu items. If not, the easiest thing to do is to execute it from the command line.

If it's executable, you should just be able to type "/boot/grub/menu.lst" at the terminal, or "./menu.lst" from the /boot/grub directory. 

Also, you might need to be root in order to manipulate grub scripts, but I'm not very experienced so I'm likely wrong. If none of the above works I'd try adding sudo before the commands.

---

### Post by egalvan on 2008-12-09
> **Kareeser said:**
> Hm.. you say you've changed the properties to make it executable, but that's a permissions thing...

Can you post an output of the permissions?

```

cd ~/Desktop
ls -l ./edit_grub

```

```
ernest@gx280:~/Desktop$ ls -l ./edit_grub
-rwxr-xr-x 1 ernest ernest 43 2008-12-04 07:00 ./edit_grub

```

---

### Post by Kareeser on 2008-12-09
You mean to say you waited 3 days before coming here to find help? ;)

Try running the script in the terminal, it should work...

```

./edit_grub

```

If not, post the error message, and we'll see why.

Unless I'm wrong, your permissions look okay.

---

### Post by egalvan on 2008-12-09
OK, just a few more words, to make sure everything is clear...

I pasted BOTH lines into the file... 
I though they were both needed?

```

#!/bin/bash
gksu gedit /boot/grub/menu.lst
```

the above two lines are all in the file...

second, this script was to automate the OPENING of the GRUB file
*menu.lst*. (I'm lazy).

I admit to knowing about batch files from DOS days.

I read a little about script files.

---

### Post by egalvan on 2008-12-09
> **Kareeser said:**
> You mean to say you waited 3 days before coming here to find help? ;)

Try running the script in the terminal, it should work...

```

./edit_grub

```

If not, post the error message, and we'll see why.

Unless I'm wrong, your permissions look okay.

OK, don't know where you got "three days".,.. :)

I've been hammering at this for at least a week. Google, you know.
I like to learn. Mistakes are interesting.

But back to the issue...

yes, typing './edit_grub'  in the terminal works...
but it kinda defeats a bit of the original purpose,,,
which is to simply double-click the file on the desktop, and have the editor come up in 'root' mode, with the menu.lst file open for changes...

or is this not possible?

Will a script open a terminal from the desktop?

---

### Post by kaibob on 2008-12-09
Check the Nautilus "Executable Text Files" preference setting (see thumbnail). The run-executable-text-files option should be selected.

---

### Post by egalvan on 2008-12-09
> **kaibob said:**
> Check the Nautilus "Executable Text Files" preference setting (see thumbnail). The run-executable-text-files option should be selected.

OK, I forgot about that setting... I had set it as "open" so that I would not accidentally run scripts...

So, are all scripts just "executable text files"?

And is the first line in my script neccesary?
I see it in scripts I have studied.
Doesn't the opening hash-mark make it a comment?

---

### Post by igknighted on 2008-12-09
> **egalvan said:**
> OK, I forgot about that setting... I had set it as "open" so that I would not accidentally run scripts...

So, are all scripts just "executable text files"?

And is the first line in my script neccesary?
I see it in scripts I have studied.
Doesn't the opening hash-mark make it a comment?

[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

You could always right click on your desktop and select "create launcher", then point to you script.  You could even give it a pretty icon this way...

---

### Post by egalvan on 2008-12-09
> **kaibob said:**
> Check the Nautilus "Executable Text Files" preference setting (see thumbnail). The run-executable-text-files option should be selected.

Bad news...

I changed the setting, and now ALL text files are being executted...

well, they are not opening in a text editor, the way they should be....

so back to the drawing board...

guess I will try that launcher thing.....

---

### Post by mc4man on 2008-12-09
You could just put your script 'as is' in your home dir. and run chmod u+x on it. Then make a desktop launcher, either on the desktop or put in your lower or upper panel.

A double click should open your grub list.
(not sure if you'd need to enter password, atm here don't have to.(maybe a 15 min. thing, there ways around if you do.

---

### Post by egalvan on 2008-12-09
Alright, the launcher works...

double-click,
password is requested,
and text editor opens with menu.lst...

great...


So a fuhrer question...

if I manage to copy this to the /bin directory, will I be able to execute it by typing the file name (edit_grub) in a terminal?

---

### Post by jbrown96 on 2008-12-09
> **egalvan said:**
> Alright, the launcher works...

double-click,
password is requested,
and text editor opens with menu.lst...

great...


So a fuhrer question...

if I manage to copy this to the /bin directory, will I be able to execute it by typing the file name (edit_grub) in a terminal?

Yes, when you type a command without a location, the system automatically searches a few directories. I know that /bin and /usr/bin searched by default, possibly others too. 

I may be misinformed, and this is really my opinion, but I think that you should put it in /usr/bin. /bin is for the GNU CoreUtils stuff. It's the very basic Unix-y stuff. /usr/bin is where most user-level applications reside.

---

### Post by egalvan on 2008-12-09
> **jbrown96 said:**
> Yes, when you type a command without a location, the system searches a few directories. /bin and /usr/bin searched by default, possibly others too.

I think you should put it in **/usr/bin**.
/bin is for the GNU CoreUtils stuff. It's the very basic Unix-y stuff.
/usr/bin is where most user-level applications reside.

OK, sounds good...

but I can't copy it into /usr/bin either...

seems to be a 'permissions' thing...

more studying...

---

### Post by jbrown96 on 2008-12-09
> **egalvan said:**
> OK, sounds good...

but I can't copy it into /usr/bin either...

seems to be a 'permissions' thing...

more studying...

You will need to move it as root. My permissions on /usr/bin are > drwxr-xr-x   2 root root  69632 2008-12-07 23:10 bin
 You will need to copyt it as root since you don't have write permissions to it. After you move it, you should change the ownership and permissions with the following ```
sudo chown root:root /usr/bin/edit_grub && sudo chmod 755 /usr/bin/edit_grub
``` The purpose of these two commands is essential for security. The chown command gives root control of the file. The chmod commands basically removes write permissions from everyone but root, but still allows everyone to execute it. 
By removing write permissions from everyone but root, a hacker or malware won't be able to modify the script to do something like erasing your files or something equally sinister, unless they have your root password, and then the argument is null because they don't need to modify the script to do their evil.

---

### Post by igknighted on 2008-12-09
The best solution would seem to be to create a folder /home/<username>/bin.  You could put all the scripts you create there, and add that folder should be added to your $PATH automatically after a log out/in.  You shouldn't mess around with putting your own scripts in /usr/bin or any of those folders.

The reason would be that there is an order of preference that the system will look through to run a command, and if you accidentally name a script the same as an essential program, but put it in a folder with a higher preference, you could mess up the system.  So unless you need to override a program with your own version, best to keep it in your own folder.

---

