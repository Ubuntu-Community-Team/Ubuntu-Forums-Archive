---
title: "General Unix Syntax Question"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by drmccoy on 2010-05-08
Hello there,

i'm fairly new to the unix world and got stuck at installing a package for about 2 hours until i figured out the problem.

For some reason, logging in permanently as root by su root and then simply typing /home/user/Desktop/script.sh returned me a comand not found, which is highly....annoying for an error code.

cd-ing into the folder and typing script.sh would not work either. Freaked me out. Until I found out that lots of people typed .\script.sh ... for whatever reason. Typing this didnt help either.

Opening up a new terminal, cd-ing into the folder, sudo .\script.sh ... AND IT MAGICALLY WORKS...

Ok, I'm not gonna ask why it would only work this way, but I really started to wonder why those scripts would only run if you put a .\ in front of them. Does this have a higher meaning or ...? 

Thanks for your answers :)

---

### Post by mike2357 on 2010-05-08
The backslash in the UNIX world means "interpret the next character literally rather than using its wildcard meaning."  For instance if you type "ls *.txt", UNIX interprets your statement as "list any files that end with .txt", since * is a wildcard" character.  However if you type "ls \*.txt", UNIX interprets your statement as "list any files with the actual name *.txt".

---

### Post by drmccoy on 2010-05-08
That makes sense, doesn't answer my question though. It's not only a backslash, it's .\, looks more like a directory issue. (cd .\ i.e.)
Besides, there's no wildcard in script.sh, so there should be no need for a backslash :P

---

### Post by veraction on 2010-05-08
Your post has ```
.\script.sh
```, but what you want to be doing is ```
./script.sh
```

The "./" tells the shell that you want to execute the file in your current directory. (Some UNIX versions don't require this). I believe it is mainly a security feature: if someone puts a script called "ls" in a directory that deletes everything, you won't accidentally run it.

---

### Post by peculiar penguin on 2010-05-08
./ refers to the current directory.

Unlike Windows, Unix and Unix-like operating systems usually only consider the search path when looking for commands. So if you want to run something in the current directory, and that directory is not part of the search path, you'll have to prefix the command with ./

Not sure what's going on with your backslashes there.

---

### Post by drmccoy on 2010-05-08
Ah, of course i ment to slash, sorry for that. 
Now that does answer my questions, thank you :)

---

