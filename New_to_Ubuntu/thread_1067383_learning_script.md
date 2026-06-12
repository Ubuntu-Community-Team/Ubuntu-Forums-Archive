---
title: "learning script"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by cliffm on 2009-02-11
Can not locate .back_profile trying to learn about scripting and this is one of the files specified to modify. gedit says its empty. Find can not locate it, as user or root.
Thanks for the help in advance

---

### Post by nmccrina on 2009-02-11
Hi. Did you mean .bash_profile? 

If so, Ubuntu uses .bashrc instead to set environment variables, etc.

---

### Post by jemate18 on 2009-02-11
find / -name "*bash_profile*" -> but ubuntu uses bashrc

find / -name "*bashrc*" -> finds all occurences

---

### Post by hyperyoda on 2009-02-11
> **cliffm said:**
> Can not locate .back_profile trying to learn about scripting and this is one of the files specified to modify. gedit says its empty. Find can not locate it, as user or root.
Thanks for the help in advance

Hi,

I assume you meant that you want to find the file ".bash_profile", this file and ".bashrc" should be located in your $HOME directory. For example if you are user 'joe' look for it in /home/joe by typing:
$ ls -a

This will show all files.

The locate command should also be able to find it. First update the locate database:
$ updatedb

Then type this:
$ locate .bash_profile

And find should also tell you where it is:
$ sudo find / -name ".bash_profile" -print

These guides should help you learn BASH scripting:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html")
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/") 

Zach

---

### Post by cliffm on 2009-02-11
Thanks for the help. I did mean bash not back.This link [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) did not mention bashrc. I will contune on my way.
Thanks again

---

