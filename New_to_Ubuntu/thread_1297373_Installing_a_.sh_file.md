---
title: "Installing a .sh file"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-10-21
I realize this is something that has been addressed in previous threads, but I found the instructions too confusing to get anything worthwhile out of them, except that I should make sure that the file has executable permissions, which I've done.

When I double click the file, to make it run, I get several options. "Run" "Run in Terminal" and "Display". Run in Terminal causes the terminal to open briefly then close before I have a chance to read what it says. "Display" gives me the simple error message "unable to run the application" and the option to expand details. There are three sets of details, all of which are extremely long and I am unable to copy and paste them for some reason. I will type them out manually if you ask me to. "Run" makes...nothing happen whatsoever. The box just closes, my computer makes no "thinking noises" and that's it.

If this is not complete information just tell me what else I need to supply and I will. I'm new to Ubuntu, so I don't always know exactly what essential information is.

---

### Post by nwadams on 2009-10-21
a .sh file is a bash script. So run it from the terminal by using 

```
cd ~/path/to/.sh/file 
```

then

```

./file.sh

```

when you run the script by hitting run in terminal what it does is it runs in a terminal and then closes the terminal window when the script finishes. So double click on it and hit display and then you will see the commands in the script to see what it actually does.

you can post the content of the script here if you don't understand it. 

regards

nwadams

---

### Post by rahrahmah on 2009-10-21
I tried substituting the filename for file, putting the filename before .sh and just leaving the script unchanged and every time it told me there was "no such file or directory". are there other things I should be changing? Because it's clearly right there on the desktop.

---

### Post by SkyNet2029 on 2009-10-21
you need to be in the working directory that the script is in.
 
then
 
```
$sh ./name_of_script_file
```
 
that should do it

---

### Post by wojox on 2009-10-21
You may need to change permissions:

```
chmod 777 /path/some_linux_installation.sh
```

---

### Post by rahrahmah on 2009-10-22
all of those still say no such directory or file. I'm changing the indicated place to say the filename. Should I be changing "path" to like "myname/home/desktop" or something?

---

### Post by nwadams on 2009-10-22
yes, if it is on the desktop you have to change the path to the desktop. the defualt directory is your home directory.

---

### Post by OpenGuard on 2009-10-22
```
cd $HOME/Desktop
sudo chmod +x file.sh
./file.sh

```

** Replace file.sh with what you have there ( file name ).

---

### Post by The Cog on 2009-10-22
> **rahrahmah said:**
> all of those still say no such directory or file. I'm changing the indicated place to say the filename. Should I be changing "path" to like "myname/home/desktop" or something?

No, it would be /home/yourname/Desktop. When you start a command prompt, just type: **cd Desktop** and that will change you to your desktop. Then make the file executable: **chmod +x filename** and then run it: **./filename**

---

### Post by 3rdalbum on 2009-10-22
Easiest way to do it:

Drag the file into a terminal (it fills in the file path for you). Bring the terminal window to the foreground and hit Enter to run the command.

If the shell script is an installer, it probably need to be run as root, which requires that you run:

```
sudo -i
```

first. You might also need to make the file executable by root.

---

