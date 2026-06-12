---
title: "Changed my prompt!"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by adamogardner on 2009-05-30
I just learned a cool trick to get my terminal prompt to display date, time, and working directory.  I had to change a shell variable called PS1.  You can see in my brief history the command I used and the instant results I achieved.  


adamogardner@CRONUS:~$ PS1='\d, \t \w'
Sat May 30, 18:52:33 ~cd ..
Sat May 30, 18:53:06 /homecd ..
Sat May 30, 18:53:10 /ls
bin    etc

---

### Post by adamogardner on 2009-05-30
But when I open another terminal it is the default prompt again.  How can I make the change more permanent?

---

### Post by sisco311 on 2009-05-30
append the ~/.bashrc file with:
```
PS1='\d, \t \w'
```

---

### Post by kk0sse54 on 2009-05-30
> **adamogardner said:**
> But when I open another terminal it is the default prompt again.  How can I make the change more permanent?

Edit your ~/.bashrc or perhaps ~/.zshrc is you use zsh instead of bash.

---

### Post by fslezak on 2009-05-30
I have the same problem, EXECPT it is with "ls". I always set the color to "always". When I run "ls" it still is black and white. Any help?

---

### Post by asmoore82 on 2009-05-30
> **fslezak said:**
> I have the same problem, EXECPT it is with "ls". I always set the color to "always". When I run "ls" it still is black and white. Any help?

append this line to your ~/.bashrc
```
alias ls='ls --color=always'
```

---

### Post by adamogardner on 2009-05-30
> **sisco311 said:**
> append the ~/.bashrc file with:
```
export PS1='\d, \t \w'
```

Thanks,  just exactly what do I do?  Do I add that line or do I comment out the two existing lines and replace it with that?  

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

---

### Post by asmoore82 on 2009-05-31
I would set mine immediately after these 2 lines:
```
# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

it should _not_ be exported to the environment; as demonstrated here:
```
**[COLOR="Lime"]asmoore@ubuntu-lenovo:[COLOR="Blue"]~[/COLOR]$[/COLOR]** sh
$ [COLOR="Red"]#<<not fancy, but functional[/COLOR]
$ exit
**[COLOR="Lime"]asmoore@ubuntu-lenovo:[COLOR="Blue"]~[/COLOR]$[/COLOR]** export PS1
**[COLOR="Lime"]asmoore@ubuntu-lenovo:[COLOR="Blue"]~[/COLOR]$[/COLOR]** sh
\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]$ [COLOR="Red"]#<<YiKES[/COLOR]
```

---

### Post by andrew.46 on 2009-05-31
Hi adamogardner,

If you run:

```
man bash
```

and search for 'PROMPTING' you will see *all* of the possibilities :-).

Andrew

---

### Post by Gen2ly on 2009-05-31
Mine's based on Gentoo's.  I've taken out username since I'm the only one using this machine and just use the machines name as I ssh into others:

```
# Regular User:
PS1="\[\033[01;32m\]"@emach"\[\033[01;34m\] \w \$\[\033[00m\] "

# Root:
PS1="\[\033[01;31m\]"@emach"\[\033[01;34m\] \w \$\[\033[00m\] "
```
[img]http://www.archive.org/download/ArchPs1/root-user.png[/img]

---

### Post by andrew.46 on 2009-05-31
Hi Dirk,

> **Dirk.R.Gently said:**
> 

```
# Regular User:
PS1="\[\033[01;32m\]"@emach"\[\033[01;34m\] \w \$\[\033[00m\] "

# Root:
PS1="\[\033[01;31m\]"@emach"\[\033[01;34m\] \w \$\[\033[00m\] "
```
[img]http://www.archive.org/download/ArchPs1/root-user.png[/img]

But the account you call 'Root' must not really be root (as in the image) because the setting '\$' gives '#' for the root prompt:

```

 \$     if the effective UID is 0, a #, otherwise a $

```

or is this an odd effect of sudo rather than su?

Andrew

---

### Post by Gen2ly on 2009-06-01
Good catch, dere.  Hadn't seen that before.  Yep, you caught my typo.  Using a $ instead of a # isn't all that much of a problem here since the output iscolored.  Of course, it would make a difference if there was no username entered.

Ooop, my bad scratch everything i just said.  :)  Yeah i know to what you are-referring but in this case you have to leave it as I posted. the # and $ delimiters are for basic-cases.

---

### Post by fslezak on 2009-06-07
What is the ~/.bashrc file and how do you access it? Just another question, where do I put the code alias ls='ls --color=always"?

---

### Post by snova on 2009-06-07
> **fslezak said:**
> What is the ~/.bashrc file and how do you access it? Just another question, where do I put the code alias ls='ls --color=always"?

A file named ".bashrc" in your home directory (~) that Bash runs automatically when you open a new terminal. Files beginning with a . are hidden, so press Ctrl-H in Nautilus to see it.

It goes anywhere in the file.

---

### Post by mtrpoland on 2009-06-13
Hi,
I have a tiny problem that is related to the main topic.
I have created a user called 'tom'.
My default bash prompt is set using .bashrc file at terminal startup.
I have copied the same .bashrc to 'tom's home directory in order to provide "him" the same prompt features.
When I use su command nothing (the prompt) happens:
```

mike@laptop:~/ $su tom
Password:
$

```How to get:
```

mike@laptop:~/ $su tom
Password:
tom@laptop:/home/mike/ $

```?

If I use su with --preserve-enviroment I receive my desired effect but cd takes me to mike's home directory!!!
:-)

Mike

---

### Post by Cheesemill on 2009-06-13
If you really want to customise your prompt, check this out:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

Cheesemill

---

### Post by fslezak on 2009-08-15
How do you put in the username and Computer Name?

---

### Post by fslezak on 2009-08-15
There is _[COLOR="Red"]no[/COLOR]_ bashrc. Do I need to create one?

---

### Post by Gen2ly on 2009-08-15
You, can check this page fslezak:

[http://wiki.archlinux.org/index.php/Color_Bash_Prompt](http://wiki.archlinux.org/index.php/Color_Bash_Prompt)

Good place to begin.

---

### Post by andrew.46 on 2009-08-15
Hi fslezak,

> **fslezak said:**
> There is _[COLOR="Red"]no[/COLOR]_ bashrc. Do I need to create one?

I suspect you have forgotten the dot at the beginning of the filename. It is a hidden file *$HOME/**[COLOR="Red"].[/COLOR]**bashrc* and can be opened with any text editor and then edited with caution.

Andrew

---

### Post by fslezak on 2009-08-17
I put in the dot and the file is NOT in Nautilus.

---

### Post by fslezak on 2012-06-10
Never mind, I found it (with my anti-noobishness)!

---

