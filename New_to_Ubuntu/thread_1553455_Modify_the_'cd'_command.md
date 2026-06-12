---
title: "Modify the 'cd' command?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by RoyalPie717 on 2010-08-15
Whenever a use the cd command on bash, I tend to use the ls command, and I'm getting tired of doing it. Is there a way to change the cd command so that it can print out files and dir of the directory I just changed?

---

### Post by CharlesA on 2010-08-15
You could try using alias, but I don't know how that would work with the cd command, since it is usually used for single commands (e.g., ls -l).

---

### Post by Rushyang on 2010-08-15
Actually I don't quite understand why you want to list out all files by modification date from **"cd"** command. 

1) if you want to list all directories and files by modification date, there's command...

> ls -t

If you want to see modification date as well..

>  ls -lt 

2) Now, If you want to list out "ls -lt" by default when you type just "ls" or any other command which is not already in default command, like your name or something..

Then one thing is you can create an alias at the end of your $HOME/.bashrc file.

> 
alias your_prefered_command_here='ls -lt'


I hope that will help you out.

---

### Post by Elfy on 2010-08-15
Maybe create a script to do it - somehow you need to get cd to ask for input before it runs ls

or get used to running ls in the command  

cd foo && ls

---

### Post by Vaphell on 2010-08-15
you can create a script my_cd.sh that does:
```

#!/bin/sh

cd $1
ls -la
```

an put it in one of the locations that are listed in
```
echo $PATH
```
next step would be to edit .bashrc file in your home dir. Find alias section
if you do
```
alias cd='my_cd.sh'
```
it should work
i think that when you type some string in, alias does the replacement and then the command is parsed and executed so in reality cd you type in is my_cd.sh in reality

edit: i suggested putting the script in some system dir, but it can work perfectly fine with a local script
lets say you have a dir my_scripts and your my_cd.sh is located there
```
alias cd='~/my_scripts/my_cd.sh'
```
i actually tested this version and it works. This is probably more elegant because you really shouldn't pollute system dirs with the stuff for your personal use.

edit2: i lied, it doesn't work, there is a problem to solve. cd in script doesn't cause the context of terminal to change. You get the list of stuff in destination dir but the terminal stays in place.

[http://stackoverflow.com/questions/874452/change-current-directory-from-a-script](http://stackoverflow.com/questions/874452/change-current-directory-from-a-script)

**solution:**
script my_cd.sh
```

#!/bin/sh

function my_cd()
{
  cd $1
  ls
}

```

added lines to .bashrc:
```

. ~/my_scripts/my_cd.sh
alias cd='my_cd'

```

---

### Post by geirha on 2010-08-15
I'd just make a function to put in ~/.bashrc
```

cdl() {
  cd "$@" && ls
}

```
Once you've saved that in ~/.bashrc, open a new terminal and use cdl as you would use cd: ```
cdl ~/Desktop
```

---

### Post by Vaphell on 2010-08-15
your version is more compact than mine but there is no reason not to mask your cdl with an alias. Well, it's up to the user.

damn, shell can do a lot nifty things :)

---

### Post by geirha on 2010-08-15
It's not an alias, it's a function. One could of course also call the function cd.
```
cd() {
  builtin cd "$@" && ls
}

```
Notice that the command inside the function now changed to "builtin cd" instead of just "cd", because running just "cd" would call the function itself, which would give infinite recursion.

That also means, that if you want to do a cd without the ls, you have to either unset the cd function or prepend "builtin" before it.
```
~/testdir$ type cd
cd is a function
cd () 
{ 
    builtin cd "$@" && ls --color=auto
}
~/testdir$ cd ~/testdir
file1  file2
~/testdir$ builtin cd ~/testdir
~/testdir$ unset cd
~/testdir$ type cd
cd is a shell builtin
~/testdir$ cd ~/testdir
~/testdir$ 

```

---

### Post by Vaphell on 2010-08-15
not that i get what you mean ;-) i understand the difference between an alias and a function (i think)

i meant slapping alias cd='cdl' on top of that what you suggest
user types **cd somedir** and shell silently substitutes cd with cdl and runs **cdl somedir** - doesn't it work that way?

---

### Post by geirha on 2010-08-15
If that alias is set **after** the cdl function is set, that'll work. If it's done in the opposite order, you get infinite recursion. I recommend using the cd function above rather than a function + an alias.

---

### Post by Vaphell on 2010-08-15
ok, thanks for explanation :)

---

### Post by RoyalPie717 on 2010-08-17
> **geirha said:**
> It's not an alias, it's a function. One could of course also call the function cd.
```
cd() {
  builtin cd "$@" && ls
}

```Notice that the command inside the function now changed to "builtin cd" instead of just "cd", because running just "cd" would call the function itself, which would give infinite recursion.

That also means, that if you want to do a cd without the ls, you have to either unset the cd function or prepend "builtin" before it.
```
~/testdir$ type cd
cd is a function
cd () 
{ 
    builtin cd "$@" && ls --color=auto
}
~/testdir$ cd ~/testdir
file1  file2
~/testdir$ builtin cd ~/testdir
~/testdir$ unset cd
~/testdir$ type cd
cd is a shell builtin
~/testdir$ cd ~/testdir
~/testdir$ 

```
This worked with me, thank you.

---

### Post by DaithiF on 2010-08-17
just to add that an equivalent way of calling the builtin command but with less typing is to prefix it with a '\'
so 
```
builtin cd
\cd

```
are equivalent

---

