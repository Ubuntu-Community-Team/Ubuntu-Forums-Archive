---
title: "Failing to login as root"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by gemm on 2009-05-10
Hi,

I want to login as root on ubuntu, however, when I type 'su' and I type my passwords and and press 'enter', I receive the following error message:

su: Authentication failure

I am typing my password, which I use for my account (user name). When I want to install something via Synaptic Package Manager, I use this same password and it works. Why do I get this message here? 

If I write 'sudo <some_command>', I am prompted for a password, I type it, but it also fails.

Actually, the reason to want to login as root is that I want to see where ubuntu installs my programs. I have installed Java via the package manager, however, I don't know where it is installed. I need it, because I have to tell Eclipse where to find Java (and which Java to use). Is there another way to check this?

---

### Post by overdrank on 2009-05-10
> **gemm said:**
> Hi,

I want to login as root on ubuntu, however, when I type 'su' and I type my passwords and and press 'enter', I receive the following error message:

su: Authentication failure

I am typing my password, which I use for my account (user name). When I want to install something via Synaptic Package Manager, I use this same password and it works. Why do I get this message here? 

If I write 'sudo <some_command>', I am prompted for a password, I type it, but it also fails.

Hi and welcome, this link may help. [RootSudo]("https://help.ubuntu.com/community/RootSudo")
Also the [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by CatKiller on 2009-05-10
> **gemm said:**
> Actually, the reason to want to login as root is that I want to see where ubuntu installs my programs. I have installed Java via the package manager, however, I don't know where it is installed. I need it, because I have to tell Eclipse where to find Java (and which Java to use). Is there another way to check this?

You can see which files a package has installed in Synaptic. Find the package that you've installed and select Package -> Properties -> Installed Files. The executable might be in /bin, /sbin, /usr/bin or some other place (probably with a bin in the name, for binary).

You can also see which file gets run for a given command with **which <command>**. For example, which firefox gives /usr/bin/firefox, telling me that the executable for Firefox is kept in /usr/bin.

---

### Post by kukibird1 on 2009-05-10
> **gemm said:**
> Hi,

I want to login as root on ubuntu, however, when I type 'su' and I type my passwords and and press 'enter', I receive the following error message:

su: Authentication failure

I am typing my password, which I use for my account (user name). When I want to install something via Synaptic Package Manager, I use this same password and it works. Why do I get this message here? 

If I write 'sudo <some_command>', I am prompted for a password, I type it, but it also fails.

Actually, the reason to want to login as root is that I want to see where ubuntu installs my programs. I have installed Java via the package manager, however, I don't know where it is installed. I need it, because I have to tell Eclipse where to find Java (and which Java to use). Is there another way to check this?

In a terminal type dpkg -L name of program. Here is an example 

dpkg -L sun-java6-jre 

You can also pipe the output into a pager or to a file.

dpkg -L sun-java6-jre > install  or whatever name you give the file  


dpkg -L | pager   this will let you scroll through a very long listing 

type man dpkg in a terminal for more info.

---

