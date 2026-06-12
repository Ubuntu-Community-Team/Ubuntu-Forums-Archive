---
title: "Problems with .bash_profile"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by MG&amp;TL on 2011-07-11
Am in the process of learning the terminal, and the basics of scripting, however have come up against a problem.

Performing some alias tweaks to save me some time for common tasks in the terminal requires me to edit .bash_profile, which is under /home/.myusername. However, if I open it in gedit, e.g. *sudo gedit .bash_profile* it opens a blank gedit document. It can't seriously be telling me there is nothing in there?

Any help, especially from terminal gurus, is much appreciated :D

---

### Post by nothingspecial on 2011-07-11
1. You don't have a .bash_profile by default so it will be empty.

2. Don't edit stuff in your $HOME with sudo

3. If you do want to open gedit as root use gksudo not sudo

4. You may wan't to consider putting all your aliases in ~/.bash_aliases, which you will also have to create.

Any questions, post back :D

---

### Post by fdrake on 2011-07-11
> **MG&TL said:**
> Am in the process of learning the terminal, and the basics of scripting, however have come up against a problem.

Performing some alias tweaks to save me some time for common tasks in the terminal requires me to edit .bash_profile, which is under /home/.myusername. However, if I open it in gedit, e.g. *sudo gedit .bash_profile* it opens a blank gedit document. It can't seriously be telling me there is nothing in there?

Any help, especially from terminal gurus, is much appreciated :D

did u try :

```
gedit ~/.bashrc
```?

---

### Post by AlphaLexman on 2011-07-11
> **MG&TL said:**
> Performing some alias tweaks to save me some time for common tasks in the terminal requires me to edit .bash_profile, which is under /home/.myusername. However, if I open it in gedit, e.g. *sudo gedit .bash_profile* it opens a blank gedit document. It can't seriously be telling me there is nothing in there?
Actually ~/.bash_profile is **NOT** the best place to put your personal aliases...

Better in ~/.bashrc

...and even better in ~/.bash_aliases if you have the following code in your ~/.bashrc
```
if [ -r ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by MG&amp;TL on 2011-07-11
Ok, lots of questions with 'newbie' stamped ALL over them now...

If there is no text file with bash source code in it, how does bash run in the first place? And how do I 'create' something that logically has always been there, but I can't see it? I realise bash_profile is useless for aliases now, but I'm curious to see what the code looks like.

So a separate directory is better for personal tweaks, just create a new text file, call it .bash_aliases. How do I create a .something_hidden_behind_a_dot file in gedit?

bashrc works, and it has the bash_alias clause, too.

---

### Post by nothingspecial on 2011-07-11
Just type 

```
gedit .bash_aliases
```

Fill it with aliases.
When you save it, it will be created. 

Then type

```
. ~/.bashrc
```

so that bash will read your .bashrc (and .bash_aliases).

---

### Post by AlphaLexman on 2011-07-11
> **MG&TL said:**
> Ok, lots of questions with 'newbie' stamped ALL over them now...

If there is no text file with bash source code in it, how does bash run in the first place? And how do I 'create' something that logically has always been there, but I can't see it? I realise bash_profile is useless for aliases now, but I'm curious to see what the code looks like.

So a separate directory is better for personal tweaks, just create a new text file, call it .bash_aliases. How do I create a .something_hidden_behind_a_dot file in gedit?

bashrc works, and it has the bash_alias clause, too.
Bash reads these files:

[LIST=1]
[*]/etc/profile executed automatically at login, first.
[*]The first file found from this list: ~/.bash_profile, ~/.bash_login, ~/.profile
[*]~/.bashrc is read by every shell after the login files.
[/LIST]

---

### Post by alquery on 2011-07-11
> **MG&TL said:**
> Ok, lots of questions with 'newbie' stamped ALL over them now...

If there is no text file with bash source code in it, how does bash run in the first place? And how do I 'create' something that logically has always been there, but I can't see it? I realise bash_profile is useless for aliases now, but I'm curious to see what the code looks like.

So a separate directory is better for personal tweaks, just create a new text file, call it .bash_aliases. How do I create a .something_hidden_behind_a_dot file in gedit?

bashrc works, and it has the bash_alias clause, too.

If you're looking for the source code of the program "bash" itself, it won't be in any files. The files like .bashrc and .bash_aliases just let you define aliases and functions that you can run *using* bash.

---

### Post by MG&amp;TL on 2011-07-12
Ok, thanks people, another newbie sent on his way! :D

---

