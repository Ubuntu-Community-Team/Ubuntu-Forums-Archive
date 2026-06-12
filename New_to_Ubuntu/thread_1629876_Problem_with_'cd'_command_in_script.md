---
title: "Problem with 'cd' command in script"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by NeverHide on 2010-11-24
I'm new with scripts,we just starting creating some basic scripts at my University on a Linux course.I keep the files that i use for that course in a certain folder and so every time i want to do something in the terminal i have to cd all the way to that folder.So i figured i'd make a script to do that for me to save time.So this is what i wrote in that script
```

cd /home/neverhide/Desktop/TEI/leitourgika/ergasthrio

```
I saved it on the home folder and made it executable.
When i execute it nothing happens,i just get a new command line...
I tried both relative(./leitourgika) and full path (/home/leitourgika) to no resault

---

### Post by DaithiF on 2010-11-24
Hi,
you don't want a script, you want an alias instead.

put something like this in your .bashrc
```
alias cds='cd /home/neverhide/Desktop/TEI/leitourgika/ergasthrio'
```

the explanation: a script executes in a new child process.  in that process you do indeed cd to the directory you want, but that process them immediately exits, and one of the rules of shell scripting is that a child process cannot affect the environment of its parent ... the current working directory is a part of the environment, and any cd commands in a child process won't change the cwd of the parent.

with an alias you are simply establishing an abbreviation for a command which executes within your current environment.

hope that makes sense

---

### Post by Verbeck on 2010-11-24
try replacing this with your script. it'll open a terminal in the directory specified
[I]
gnome-terminal --working-directory='/home/neverhide/Desktop/TEI/leitourgika/ergasthrio'[/I]

---

### Post by matt_symes on 2010-11-24
Hi

Run your script like this (from the terminal)

. ./script_name

That is dot space dot slash script_name

or use an absolute path.

. /path/to/script_name

DaithiF has a good description of why ./script_name is not working.

Kind regards

---

### Post by NeverHide on 2010-11-24
Thank you all for the fast responses :D

Just a couple of questions though:
DaithiF,the alias command works but when u close the terminal the alias is erased and the next time u want to use it you have to assign the command to the alias all over again.Tried it in the script to see if it'll work but the script doesn't work then.Is there another way to use the alias command so it'll stay there after you close the terminal?

matt_symes,executing the script using the . ./script_name works perfectly :D but could you please tell me what that dot before the path changes so it runs?you know to expand my knowledge :smile:

Thanks again everyone :D :D

---

### Post by matt_symes on 2010-11-24
Hi

> **NeverHide said:**
> Thank you all for the fast responses :D

Just a couple of questions though:
DaithiF,the alias command works but when u close the terminal the alias is erased and the next time u want to use it you have to assign the command to the alias all over again.Tried it in the script to see if it'll work but the script doesn't work then.Is there another way to use the alias command so it'll stay there after you close the terminal?

matt_symes,executing the script using the . ./script_name works perfectly :D but could you please tell me what that dot before the path changes so it runs?you know to expand my knowledge :smile:

Thanks again everyone :D :D

To answer your first question, you need to put the alias into the ~/.bashrc file and make sure the file is executable using chmod +x .bashrc

It will then be persistent.

To answer you second question, it runs the script as source. Ie. in the parent shell and does not create a child shell for it.

Kind regards

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by DaithiF on 2010-11-24
> **NeverHide said:**
> 
DaithiF,the alias command works but when u close the terminal the alias is erased and the next time u want to use it you have to assign the command to the alias all over again.Tried it in the script to see if it'll work but the script doesn't work then.Is there another way to use the alias command so it'll stay there after you close the terminal?


yes -- see the part in bold:

> 
[B]put something like this in your .bashrc
[/B]```

alias cds='cd /home/neverhide/Desktop/TEI/leitourgika/ergasthrio'

```


---

### Post by DaithiF on 2010-11-24
> **NeverHide said:**
> 
DaithiF,the alias command works but when u close the terminal the alias  is erased and the next time u want to use it you have to assign the  command to the alias all over again.Tried it in the script to see if  it'll work but the script doesn't work then.Is there another way to use  the alias command so it'll stay there after you close the terminal?


yes -- see the part in bold:

> 
[B]put something like this in your .bashrc
[/B]```

alias cds='cd /home/neverhide/Desktop/TEI/leitourgika/ergasthrio'

```


---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by DaithiF on 2010-11-24
> **NeverHide said:**
> 
DaithiF,the alias command works but when u close the terminal the alias is erased and the next time u want to use it you have to assign the command to the alias all over again.Tried it in the script to see if it'll work but the script doesn't work then.Is there another way to use the alias command so it'll stay there after you close the terminal?


yes -- see the part in bold:

[B]put something like this in your .bashrc
[/B]```

alias cds='cd /home/neverhide/Desktop/TEI/leitourgika/ergasthrio'

```

---

### Post by DaithiF on 2010-11-24
Edit: removed duplicate of previous post (forum hung on first submit)

---

### Post by matt_symes on 2010-11-24
duplicate

---

### Post by matt_symes on 2010-11-24
Wow.

Forums database went *hic*?

---

