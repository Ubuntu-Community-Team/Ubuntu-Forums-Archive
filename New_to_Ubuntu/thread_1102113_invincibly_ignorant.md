---
title: "invincibly ignorant"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by hippocrat on 2009-03-21
New to ubuntu and looking for help.

I need to use terminal but when I visit I find a command line already there which reads 'andrew@andrew-laptop:~$'

I'm sure this is a dumb question - but can I delete this without screwing something up?

I have a penchant for doing this and am rather old [71]

Thanks for help

hippocrat

---

### Post by Bachstelze on 2009-03-21
This is the command prompt, it is how the system tells you it's waiting for your command while at the same time giving you some information about your environment (your current username, the hostname of the machine and the current directory).

Just type your command and press enter, the prompt is not part of it:

```
firas@itsuki ~ % echo "hello"
hello
itsuki ~ # echo "hello"
hello
root@animedesu:~# echo "hello"
hello

```

As you can see, the prompt has no influence over what a command does.

---

### Post by D1ZZ4ZZT3R on 2009-03-21
> **hippocrat said:**
> New to ubuntu and looking for help.

I need to use terminal but when I visit I find a command line already there which reads 'andrew@andrew-laptop:~$'


hippocrat

we all have that (as far as i'm aware) and is perfectly normal. andrew@andrew-laptop is just, basically, you or, more spcifically, you@yourhomefolder. it's after the ~$ where you enter your commands. for instance, open your terminal and type in (without brackets) "ls -l" and press enter. this will show you everything in your home folder, aka 'andrew'. now, type in (without brackets once again) "cd Desktop" and press enter. if your system is the same as mine, you should now see that you are in your Desktop folder. once again, type "ls -l" and you will see a list of everything on your Desktop. 

remember, it's usually case sensitive. 

i hope this helps a bit. i'm new to it myself but, i figured i could help a little :p

---

### Post by paydaydaddy on 2009-03-21
What you are seeing is merely the identity of the user and the machine/partition/directory you are on. For example, when I open a terminal I get the display: dragon@smaug:~$. I simply enter commands after the dragon@smaug:~$ display. If the problem is that you don't recognize 'andrew@andrew-laptop:~$', then that is a different kettle of fish to fry and you should post back here with a more in depth explanation of your problem.

---

### Post by hyper_ch on 2009-03-21
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by ivanvajar on 2009-03-21
This is your prompt first section tells what user is logged on and after @ sign is the name of computer.

---

### Post by hippocrat on 2009-03-23
many thanx from hippocrat to all who generously supplied me with info about the line in terminal - still wrestling with ubuntu - but hey I keeps the old synapses flashing - at my age a good thing

---

### Post by Xiong Chiamiov on 2009-03-23
BTW, your prompt is controlled by the PS1 environment variable; you can see what it looks like with
```

echo $PS1

```
As you can tell, you probably don't want to mess with it, as the syntax is rather annoying to deal with.  If you'd like something else (for instance, the time, or different colors), ask here and someone will likely be able to fix you up.

---

