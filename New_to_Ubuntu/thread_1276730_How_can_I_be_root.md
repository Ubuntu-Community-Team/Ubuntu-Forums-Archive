---
title: "How can I be root ?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Drakkor on 2009-09-27
I've set a unix (root?) password,but don't know how to login as root !
Thanks

---

### Post by doas777 on 2009-09-27
I'm not quite sure what your saying about the password, but, in ubuntu, by default, you cannot login as root itself, but there are easy ways to elevate your access within your own shell. this is done for security reasons, and is a great way to balence running as a limited user and still being able to perform administrative tasks.


check out this doc: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

if you want to run a terminal as root, just open a term, and enter:
```
sudo -i
``` and enter your own users password. all subsequent commands will be run as root.

if you want to run a graphical app as root, hit Alt + F2, and enter 
```
gksu <applicationname>
```if you want to browse the file system in nautilus, hit Alt + F2 and enter 
```
gksu nautilus
```you can create launchers (shortcuts) that contain any of the commands above, that you can put on your desktop, panel, or menus.

If your still not convinced that you can do everything you wan to do,  you will have to ask a search engine on how to enable the root account. the forum CoC asks us not to provide that information or links to it.

good luck

---

### Post by LewRockwell on 2009-09-27
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

.

---

### Post by bigboy_pdb on 2009-09-27
My response is essentially the same as doas777's response. I typed it between when his was posted and the question was asked so I'll post mine as confirmation about his response.

For GUI programs that require root access a dialog will pop up asking for your root password.

In the terminal, to execute a program as root you write "sudo" before the command. For example, to list hardware as root you'd use "sudo lshw".

To force a GUI program to run as root you can use "gksudo". For example, to run nautilus (the GNOME file browser as root), you'd use "gksudo nautilus".

Once you've run a program using sudo/gksudo, there's a period of time where you won't be prompted to enter a password when running another program using sudo/gksudo.

It's not safe to run programs as root when you don't need to do so. The majority of problems in Windows occur because people login as Administrator (or install programs as Administrator). When I ran Windows, I never had problems with malware because I almost always logged in as a limited user.

If you're going to be running a number of commands as root in a terminal, you can use "sudo su" to open a shell as root (in a terminal).

In Ubuntu, it isn't possible to log in as root by default. There's probably a way that you can modify your system so it can be done, but any security conscious user will recommend against it.

---

### Post by aysiu on 2009-09-27
This post has been answered.

Frankly, there's no need to set a root password.

For more details, read [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

