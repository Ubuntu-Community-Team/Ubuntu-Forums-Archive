---
title: "Build Essential For Wireless Connection"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by rclowery on 2010-03-23
Hi There,

I'm new to Ubuntu - or at least the command line interface and I am having some problems.

I'd like to install a Realtek wireless Linux driver on my laptop running Ubuntu 9.10 64-bit, but I am unable to build headers in the kernel because I lack a package called build-essential, therefore I can't properly follow the rest of the steps necessary to install the driver.

When I try to install several packages that build-essential depends on I get stuck. I can't seem to install g++-4.4_4.4.1-4ubuntu8_amd64.deb without first installing libstdc++6-4.4-dev_4.4.1-4ubuntu8_amd64.deb. The problem is that libstdc++ tells me it needs the same g++ package I just mentioned to install. Therefore I can't get any further because both of them seem to depend on each other for installation!

Does anyone have any idea how to address this issue? I may be overlooking something, which is entirely possible considering that I've never done anything like this before.

I'd appreciate any help you can offer.

---

### Post by mkvnmtr on 2010-03-23
You do lnot say how you are trying to install. Normally I go to the synaptic package manager and search for build-essentials and it handels all or the other packages for me. I assume that the software center does the same but have never used it. I like synaptic.

---

### Post by rclowery on 2010-03-23
mkvnmtr,

Thank you for your reply.

I'm unable to install using Synaptic - perhaps because the packages all end in .deb?

I also have no Internet access on the computer I am trying to fix, so please bear that in mind if you have any other advice. Also, if you need any output from the terminal, please let me know. 

Its a bit frustrating at this point. All I want to do is get my wireless up and running, but I need to install these packages first before I can follow the instructions. 

Thanks again for your help.

RC

---

### Post by lkraemer on 2010-03-23
Try this:
[http://keryxproject.org/](http://keryxproject.org/)

You only need an Internet connection and a USB Memory Stick to download
what you need, then take it to the computer that doesn't have an Internet
connection and install.

SIU to the Rescue!
(Southern Illinois University)



Also..........
Sys>admin<software sources and check box for add CD.
Another way is to type in terminal

```

gksudo gedit /etc/apt/sources.list

```
and remove # sign from cd-rom line(it is on top of the file). Save file.
Put your Ubuntu disc in drive and go to the synaptic and install build-essential.
Yes,you have that package on disc.

lkraemer

---

### Post by rclowery on 2010-03-23
Thank you friends,

I found an excellent piece of advice in this forum where a person was having the same issue:

[http://ubuntuforums.org/showthread.php?t=1083081](http://ubuntuforums.org/showthread.php?t=1083081)

I used: sudo dpkg -i *.deb

This installed all the packages at once without any problems with circular dependencies.

Hopefully now I'll be able to get my wireless up and running.

Cameron

---

