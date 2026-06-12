---
title: "Can't change directory"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by jhargis1012 on 2011-01-26
Hello. I'm trying to navigate to a directory in the Terminal, and here is what's happening:

jhargis1012@jhargis1012-laptop:~$ cd .wine
[email]jhargis1012@jhargis1012-laptop:~/.wine[/email]$ cd drive_c
[email]jhargis1012@jhargis1012-laptop:~/.wine[/email]/drive_c$ ls
Program Files  windows
[email]jhargis1012@jhargis1012-laptop:~/.wine[/email]/drive_c$ cd program files
bash: cd: program: No such file or directory
[email]jhargis1012@jhargis1012-laptop:~/.wine[/email]/drive_c$ 

Why won't it let me pull up the Program Files folder? I'm trying to get to a Wine game I have installed so I can use the Terminal to run it in windowed mode rather than fullscreen.

Thanks.

---

### Post by mikewhatever on 2011-01-26
Bash shell is case sensitive, try this instead:
```
cd Program\ Files
```

---

### Post by jhargis1012 on 2011-01-26
Wow, thanks, that worked! So, why the backslash there? Does that tell the terminal there's a space between the words?

---

### Post by garyed on 2011-01-26
Another way to do it is to use double quotes:
```
cd "Program Files"
```
You can also partially type ```
cd Progra
``` and then hit the tab key & it will finish the typing for you if nothing else begins with whatever you already typed.

---

### Post by Rushyang on 2011-01-27
Well, that is called "Escape Sequence in bash". 

When you type..
$ cd Program Files

It will only search for a directory called "Program" in your current working directory. (which is not exist) and after space all will be ignored as you can't change 2 directories using single "cd".

To indicate that space is within your given name, you have to tell that - that space is in your directory name. That's why we use \.

Else, you can use directly .. 
$ cd 'Program File'

Or you can often use "tab-completion" feature in terminal when you don't want to write the whole name..

For example,
type ...
$ cd Pr   
and then press TAB key on your keyboard, it will search all directories starting with the word "Pr" in your current working directory.

---

### Post by jhargis1012 on 2011-01-27
Thank you, everyone. That is helpful.

---

