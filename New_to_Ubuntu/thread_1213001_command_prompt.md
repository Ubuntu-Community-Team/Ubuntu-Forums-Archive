---
title: "command prompt"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by carrarin on 2009-07-14
How do i change the command prompt from 
ubuntu@ubuntu:~$ 

to something cooler like

coolbuntu@ubuntu:~$ .

---

### Post by Cheesemill on 2009-07-14
You need to edit your ~/.bashrc file, see the following link for detailed instructions.

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

---

### Post by Lampi on 2009-07-14
please search this forums for customize BASH prompt - I remember a great tutorial about tweaking your bash prompt. Haven't bookmarked it though, there are several here in the forum archvie

---

### Post by prshah on 2009-07-14
You can change your prompt by setting the environment variable PS1. For example```
export PS1='coolbuntu@ubuntu \W:'
``` will give you a prompt of ```
coolbuntu@ubuntu ~:
```. The "\W" is replaced with the current working directory.

There are a number of settings you can use, including background/foreground colors, etc.
For a further example, I use```
${debian_chroot:+($debian_chroot)}\[\033[0;32m\]\d \[\033[0;34m\]\t \[\033[0;0m\]\W:\$
``` This gives me a prompt as```
[color=green]Tue Jul 14[/color] [color=blue]21:32:28[/color] ~:$
```

The parts that follow a "\" are called escape sequences and are fully explained in the link given above in the post by Cheesemill.

---

### Post by carrarin on 2009-07-14
thanks, that helps :-)

---

### Post by Paddy Landau on 2009-07-14
You can use '\e' instead of '\033'. So the previous example could read
```
${debian_chroot:+($debian_chroot)}\[\e[0;32m\]\d \[\e[0;34m\]\t \[\e[0;0m\]\W:\$
```('e' stands for 'escape', and 033 is the code that the computer receives -- or used to -- when you press the "Esc" button.)

---

