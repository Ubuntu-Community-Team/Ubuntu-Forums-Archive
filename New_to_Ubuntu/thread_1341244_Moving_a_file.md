---
title: "Moving a file"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by dmakshay2002 on 2009-11-29
Hello ppl.
 Im new to ubuntu and learning it. So say that u have a file in your desktop. Lets say it is learn ubuntu and also u've another folder called LEARN. so all i wanted to do is move the learn ubuntu file from the desktop to the folder LEARN. so in the terminal i gave the command mv learn ubuntu LEARN. it should've moved right? but its not it gave an error. I know tat u cant use spaces in between a file name but how to access it in ur terminal? pls help guys.
Thanks in advance...

---

### Post by Redmage913 on 2009-11-29
Forgive me, but can't you use Nautilus, Ubuntu's file manager, to move the file where you need? Or are you trying to learn how to use the terminal to move a file?

---

### Post by Virtual Liberty on 2009-11-29
Use quotes.

```
mv ./file.rar "/home/user/learn moving files/"
```

---

### Post by scorp123 on 2009-11-29
If there are spaces in a file name you can either use quotation marks, e.g.
```
mv "My Folder Here" /path/to/target/
```

... or you can ***"escape"*** the spaces. That's Unix-language for saying ***"tell the shell to ignore the space"***. The backslash **\** character is used for this. So this command works the same like the one above, except we *"escape"* the spaces:
```
mv My\ Folder\ Here /path/to/target/
```

---

### Post by NoaHall on 2009-11-29
Can you post the full commands to the files? As in, /home/user/Desktop/file

---

### Post by halitech on 2009-11-29
if the file and the folder are both on the desktop, then it should be
```
mv learn\ ubuntu LEARN
```
you can use a \ at the end of each word if there are spaces or put " " around it as well. Remember, *nix is case sensative so ubuntu learn and Ubuntu Learn are not the same thing.

---

### Post by conehead77 on 2009-11-29
You can use spaces if you put a slash before the space
```
mv /home/user/Desktop/learn\ ubuntu /home/user/somefolder
```
Another trick you will need often when working on the command line: use TAB a lot. It auto-completes filenames and commands for you

---

### Post by t0p on 2009-11-29
Okay, couple of things here:

For a start, bash (the terminal) doesn't like spaces in file names.  You need to escape the space by using the '\' symbol.  So a file called 'learn ubuntu' must be called, in the terminal, 'learn\ ubuntu'.

To move that file from Desktop to a directory ("folder") called LEARN, use the following command:

```

mv learn\ ubuntu LEARN/learn\ ubuntu
```

A simpler example (involving no spaces): to move a file called 'file' from the Desktop to the Documents folder:

```
mv Desktop/file Documents/file
```

If you don't understand, please post back.

> **Redmage913 said:**
> Forgive me, but can't you use Nautilus, Ubuntu's file manager, to move the file where you need? Or are you trying to learn how to use the terminal to move a file?

Not exactly the most helpful of replies...

---

### Post by scorp123 on 2009-11-29
> **halitech said:**
>  Remember, *nix is case sensative so ubuntu learn and Ubuntu Learn are not the same thing. +1 !!

Case matters. "Ubuntu LEARN", "Ubuntu learn" and "Ubuntu Learn" are NOT the same folders.

---

### Post by The Cog on 2009-11-29
You can escape spaces with backspaces as in **learn\ ubuntu** or easier on the eye is to use quotes as in **"learn ubuntu"**. Anything on the desktop is in your Desktop folder, like /home/dmakshay/Desktop so that file you are trying to copy is probably **"/home/dmakshay/Desktop/learn ubuntu"**. You can normally shorten your home directory to ~ so this should also be the same file: "~/Desktop/learn ubuntu" or ~/learn\ ubuntu.

---

### Post by dmakshay2002 on 2009-11-30
got it guys.. thanks a lot.. :D

---

