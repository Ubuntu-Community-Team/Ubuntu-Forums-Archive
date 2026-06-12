---
title: "Need help running script"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-07-17
So when I try to type a few of the commands I've seen on the forum into the Terminal, it comes up with a password line, but when I type anything, nothing shows up. Also, when I hit ctrl+alt+f2 and it comes up with login where I type my user name and then it does the same thing with the password. I type, nothing shows up. Am I suppose to hit something else while I'm typing or something? I'm thoroughly confused.

---

### Post by ubudog on 2009-07-17
> **GodlySoup said:**
> So when I try to type a few of the commands I've seen on the forum into the Terminal, it comes up with a password line, but when I type anything, nothing shows up. Also, when I hit ctrl+alt+f2 and it comes up with login where I type my user name and then it does the same thing with the password. I type, nothing shows up. Am I suppose to hit something else while I'm typing or something? I'm thoroughly confused.

That's normal.  It's supposed to do that.

---

### Post by Superkoop on 2009-07-17
When you type the phrase 'sudo' you are invoking Super User Privileges, this means that you have write access to important system files. Normal users do not have write access to these files, to protect from unauthorized damage done to your operating system.

---

### Post by GodlySoup on 2009-07-17
Well, if that's normal, what am I doing wrong? I type in the password correctly...

---

### Post by lisati on 2009-07-17
> **GodlySoup said:**
> Well, if that's normal, what am I doing wrong? I type in the password correctly...

I looked at the screenshot. It's not a password problem: it says "Command not found". Are you in the correct directory?

---

### Post by sisco311 on 2009-07-17
> **GodlySoup said:**
> Well, if that's normal, what am I doing wrong? I type in the password correctly...

autogen.sh is not in your current working directory. 

you can list the files with the *ls* command and change the directory with *cd*. For more info: [uhelp]community/UsingTheTerminal[/uhelp]

---

### Post by CatKiller on 2009-07-17
> **sisco311 said:**
> autogen.sh is not in your current working directory. 

... or it is, but it isn't executable.

---

### Post by sisco311 on 2009-07-17
> **CatKiller said:**
> ... or it is, but it isn't executable.

in that case bash throws a *Permission denied* error.

so please believe me, it's not in the dir. :)

---

### Post by GodlySoup on 2009-07-17
Okay, well I'm trying to run it from a folder on my desktop... I'm trying to install a game and, because I no nothing of adding applications onto Ubuntu, I looked it up here and I was trying to run installation from the terminal as one of the threads suggested.

---

### Post by sisco311 on 2009-07-17
> **GodlySoup said:**
> Okay, well I'm trying to run it from a folder on my desktop... I'm trying to install a game and, because I no nothing of adding applications onto Ubuntu, I looked it up here and I was trying to run installation from the terminal as one of the threads suggested.

```
cd ~/Desktop/nameofthegame
sudo ./autogen.sh
```

when you type the path to the dir use tab auto complete.
type the first few letters, then hit Tab.

---

### Post by ~sHyLoCk~ on 2009-07-17
Ok first of all ```
sudo ./autogen.sh
``` will never work no matter which directory you go to since sudo doesn't understand what ./autogen.sh is!

Go to the directory where ./autogen.sh is, then type in ```
sudo chmod +x autogen.sh
```

Now simply execute it as ```
./autogen.sh
```

---

