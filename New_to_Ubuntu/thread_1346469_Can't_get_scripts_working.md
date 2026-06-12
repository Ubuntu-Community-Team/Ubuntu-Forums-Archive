---
title: "Can't get scripts working"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Daemonmonkey on 2009-12-05
Hello!

I'm a relatively new user... I'm not totally unfamiliar with *nix but my knowledge is quite rusty, but I'm trying to learn... 

I'm having a problem getting scripts to work, even the simplest one, like this one: > #!/bin/sh
echo "test"

I have also **CHMOD 777** to be sure, **ls -l** gives -rwxrwxrwx

Running **sh** from terminal works, I get the $-prompt and when I enter a for-loop it executes w/o problem.

using **sh < script** (whereas script is the file with commands) works.
I'm running 9.10 under VMWare player 3.0.0

---

### Post by Bachstelze on 2009-12-05
If you have saved your script as [font=monospace]hello.sh[/font], you run it with

```
./hello.sh
```

---

### Post by conehead77 on 2009-12-05
How exactly do you want to run the script? If sh script.sh works it's all fine i think. ./script should also work. Just script won't work.

---

### Post by Daemonmonkey on 2009-12-05
Ahh thanks both Bachstelze and conehead77! 

I was probably stuck with the MS-DOS thinking, where you don't need the leading path reference.

By the way, is there any way to circumvent this behaiviour?

---

### Post by slakkie on 2009-12-05
yes, although I don't advise it:

export PATH=$PATH:.

Now you can run your script as run_script, instead of ./run_script.

---

### Post by Bachstelze on 2009-12-05
> **Daemonmonkey said:**
> 
By the way, is there any way to circumvent this behaiviour?

Yes, but it is not recommended, as it creates a big security risk. See for example [this post]("http://www.linuxforums.org/forum/misc/27942-linux-doesnt-automatically-add-current-directory-path.html#5") for details.

---

### Post by Daemonmonkey on 2009-12-05
Ah, yes. Now I remember... As I hinted in the beginning, I learnt some *nix for appr. 25 years...

We made then some "nasty" scripts, like logging out the user when he typed ls och another of the common shell commands... 

Thanks for reminding me...

---

