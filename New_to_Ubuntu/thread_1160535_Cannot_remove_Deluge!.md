---
title: "Cannot remove Deluge!"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by mubarak on 2009-05-15
[SIZE=3]Hi,

I've installed UNR and its running beautifully! Then I decided to install Deluge. Now, I cannot remove it. I've googled it but got nothing.

I've also tried to remove it via Terminal but it says it doesn't exist on the system. Please help! :cry:

[/SIZE]

---

### Post by radiocognition on 2009-05-15
Hi

Let me see if I got this right.  You have tried to remove Deluge from add remove and it still remains.  Try this then:

1) Can you still start Deluge when you click on the icon? (probably yes) if so, open a terminal and input this
```
sudo aptitude remove deluge
```
if the terminal spits out some kind of error message, post it here so I can tell you what's happening.

2) if you cannot start Deluge from the menu, it may be already uninstalled (and the icon was left behind on accident).  Try to start the program from the command line by typing
```
deluge
```
if nothing happens, try
```
which deluge
```
And if that returns nothing, then Deluge has been removed from your system and you can manually remove the launch icon.

---

### Post by mubarak on 2009-05-15
[SIZE=3]Hey radiocognition!

I've done what you posted but it didn't work. This is what I got.

mubarak@mubarak-laptop:~$ sudo aptitude remove deluge
[sudo] password for mubarak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 69 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

After typing, **deluge**, this is what I got.
mubarak@mubarak-laptop:~$ deluge
bash: /usr/bin/deluge: /usr/bin/python2.5: bad interpreter: No such file or directory

After typing, **which deluge**.
[/SIZE][SIZE=3]mubarak@mubarak-laptop:~$ which deluge
/usr/bin/deluge[/SIZE]
[SIZE=3]
The program never worked in the first place. I'm using ktorrent now, and its working pretty nice. I don't know why deluge is causing so much trouble :\
[/SIZE]

---

### Post by lovinglinux on 2009-05-15
To uninstall Deluge run this:

```
sudo apt-get purge [color=#FF0000]deluge-torrent[/color]
```

I'm not sure what is the problem, but I think Deluge is currently associated with Python 2.5 in your system instead of Python 2.6, which comes installed with Jaunty. I would not recommend installing Python 2.5, because it increased the CPU usage a lot on my system. But maybe someone could tell how to use Deluge with Python 2.6 as it should.

---

### Post by mubarak on 2009-05-15
[SIZE=3]YEAAH!!! Thanks loads lovinglinux! You're awesome! :D[/SIZE]

---

### Post by lovinglinux on 2009-05-15
> **mubarak said:**
> [SIZE=3]YEAAH!!! Thanks loads lovinglinux! You're awesome! :D[/SIZE]

:) You are welcome.

---

### Post by radiocognition on 2009-05-15
Be sure to mark this thread as closed, what that last command did was remove the residual config files.  Do you know if the maintainers of the Deluge package are aware of this issue?

---

### Post by mubarak on 2009-05-16
How do I do that? Sorry, it is my first time to use a forum.

---

### Post by kpkeerthi on 2009-05-16
Click on **Thread Tools** above your first post.

---

### Post by lovinglinux on 2009-05-16
> **radiocognition said:**
> what that last command did was remove the residual config files.

No. The last command removed deluge itself and the configuration files, because the correct command is *[color=#33CC00]deluge-torrent[/color]*, not [color=#FF0000]*deluge*[/color].

> **radiocognition said:**
> Be sure to mark this thread as closed

> **kpkeerthi said:**
> Click on **Thread Tools** above your first post.

I must be missing something. As far as I know, a thread can only be closed by a moderator. It could be marked as "Solved", but this feature has been disabled a couple of months ago.

---

### Post by Paddy Landau on 2009-05-16
> **lovinglinux said:**
> I must be missing something. As far as I know, a thread can only be closed by a moderator. It could be marked as "Solved", but this feature has been disabled a couple of months ago.
Correct. Instead, edit your very first post in the thread, and add [Solved] to the start of the title. So, the title will read, "[Sovled] Cannot remove Deluge!"

---

