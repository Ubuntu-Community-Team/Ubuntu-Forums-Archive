---
title: "Problems with using the terminal to run programs"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by MrMittens on 2011-07-11
Hello, this is probably the least complicated problem of all complicated problems, but being a beginner with ubuntu, I cannot solve it.

Being lazy as I am, I make aliases for almost everything I have to do more than once. i.e. Update, change to a often-used directory, etc. Well, I am attempting to make an alias to run a program that isn't in the current directory.

It looks like this:

alias alias_name="./Documents/scripts/program_name.exe" (By the way, it's a window's program that does work and is marked as executable. I have ran it in the terminal when in the same directory.

When I run this command, it states that there is no such file or directory. I have checked that path many times, and in fact have had troubles with this in the past; however this is my first posting on the matter.

Any help would be appreciated.

Thanks,

MM

---

### Post by nothingspecial on 2011-07-11
Try it with the full path or put your scripts directory in your $PATH

---

### Post by dethorpe on 2011-07-11
What directory are you in when you try to use the alias? The . makes the path relative to current directory so would only work if you are in your home dir. if you want it to work from anywhere use ~ to indicate your home eor use the full path e.g.:
 
```
 
alias alias_name="~/Documents/scripts/program_name.exe"
 
OR 
 
alias alias_name="/home/username/Documents/scripts/program_name.exe" 

```
 
As the previous poster says the better option may be to but your scripts directory in your PATH then can run the program without any path so don't really need an alias. Any other program/script you put in there will then also run.
 
 
e.g. in the .bashrc file add the line below to add the directory to your path:
 
```
 
export PATH=$PATH:"~/Documents/scripts"

```
 
Then can just run it directly from the command line:
 
```
 
$ program_name.exe

```
 
Hope that helps

---

### Post by MrMittens on 2011-07-12
Thank you to the both of you, I followed your advice, and it works. (: 

Plus, I learned something new about linux.

Once again, thank you.

MM

---

