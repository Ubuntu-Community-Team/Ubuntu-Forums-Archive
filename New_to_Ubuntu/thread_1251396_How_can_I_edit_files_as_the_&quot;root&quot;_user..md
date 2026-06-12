---
title: "How can I edit files as the &quot;root&quot; user...?"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by raicho on 2009-08-27
I recently made the switch to Xubuntu thanks to some great guidance from various members on the board here, and it's been fantastic for my day-to-day use.

However every now and then I need to tinker with things but am simply unable to.  I've created the user account "ryan" during setup, but I can't do anything with it.

For instance I'm currently trying to follow the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=764576](http://ubuntuforums.org/showthread.php?t=764576)

However I can't change any file permissions because I evidently don't have permission, nor can I edit any files outside of my home folder.

Can anyone tell me how I can get access?  How can I be the root user whilst logged in with my account?

Thanks.

---

### Post by credobyte on 2009-08-27
```
sudo <command>

```

Tough, you need to be in the list of sudoers.

---

### Post by braete on 2009-08-27
open a terminal, type sudo gedit(or any editor you like) and then type the path to the file or drag it onto the terminal window, hit enter, type ur pass when prompted(no worry if it doesnt give you any visual hint), hit again enter, then enjoy the power of the root !

---

### Post by Zill on 2009-08-27
> **raicho said:**
> ...However I can't change any file permissions because I evidently don't have permission, nor can I edit any files outside of my home folder.

Can anyone tell me how I can get access?  How can I be the root user whilst logged in with my account?...
Welcome to the forums.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

This is an faq.  Google is your friend!

---

### Post by Iowan on 2009-08-27
[Here]("http://www.psychocats.net/ubuntu/fixsudo") is another that may be of interest.

---

### Post by tuxxy on 2009-08-27
> **credobyte said:**
> ```
sudo <command>

```Tough, you need to be in the list of sudoers.

I think for the GUI it should be gksudo;

```
gksudo gedit <filename>
```

You can also edit files from within the terminal with vim for example.

```
sudo vim <filename>
```

---

### Post by Grifulkin on 2009-08-27
> **tuxxy said:**
> I think for the GUI it should be gksudo;

```
gksudo gedit <filename>
```

You can also edit files from within the terminal with vim for example.

```
sudo vim <filename>
```

Vim is way to complicated for someone new to linux.  Also I've been around for a year and still have no clue how to use it.  I would suggest nano instead, very easy.  I'm just thinking from the point of view of someone just starting out, vim is too complicated at the beginning.

```
sudo nano <filename>
```

---

### Post by bterminalx on 2009-08-27
Another cheap trick to use is setting a password for the root user 

```
sudo passwd root
```then to login to root you type

```
su
```

---

### Post by Grifulkin on 2009-08-28
> **bterminalx said:**
> <snip>

I don't think you should tell them how to change the root password, I don't even think you are allowed to do that on the forums.

If he really wants to become root in the terminal, ```
sudo -i
``` is a perfectly good code or ```
sudo /bin/bash
```

---

### Post by credobyte on 2009-08-28
> **tuxxy said:**
> I think for the GUI it should be gksudo;

```
gksudo gedit <filename>
```You can also edit files from within the terminal with vim for example.

```
sudo vim <filename>
```

Actually, I've never used gksudo for gedit. Yes, you'll need to configure it twice ( 2 config files ), but .. who cares ? If I need to spend 40 seconds on configuring it, why to bother with gksudo, gksu and other *weird* commands ? :)

---

### Post by kerry_s on 2009-08-28
in xfce4, i use a custom action:

**gksudo gnome-open %f**

check directory, text & other.

you can then right click the folder or file to open as root.

---

### Post by Zill on 2009-08-28
> **credobyte said:**
> Actually, I've never used gksudo for gedit. Yes, you'll need to configure it twice ( 2 config files ), but .. who cares ? If I need to spend 40 seconds on configuring it, why to bother with gksudo, gksu and other *weird* commands ? :)
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by credobyte on 2009-08-28
> **Zill said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **Why is it an issue?**
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way&#8212;using *sudo* for graphical applications and see no adverse side effects. Giving a link to what I've already said is pretty useless ;) I know why we should use gksudo for graphical applications, but as always, there are some exceptions. Especially, you'll never have any issues with Gedit, no matter how you launch it.

---

### Post by aysiu on 2009-08-28
> **credobyte said:**
> Giving a link to what I've already said is pretty useless ;) I know why we should use gksudo for graphical applications, but as always, there are some exceptions. Especially, you'll never have any issues with Gedit, no matter how you launch it.
But it's good to be in the habit of using the correct prefix all the time instead of keeping a separate list of exceptions.

Isn't the OP using Xubuntu?

In that case, it should be ```
gksudo mousepad
``` and not ```
gksudo gedit
```

---

### Post by aysiu on 2009-08-28
> **credobyte said:**
> Giving a link to what I've already said is pretty useless ;) I know why we should use gksudo for graphical applications, but as always, there are some exceptions. Especially, you'll never have any issues with Gedit, no matter how you launch it.
But it's good to be in the habit of using the correct prefix all the time instead of keeping a separate list of exceptions.

Isn't the OP using Xubuntu?

In that case, it should be ```
gksudo mousepad
``` and not ```
gksudo gedit
```

---

### Post by credobyte on 2009-08-28
> **aysiu said:**
> But it's good to be in the habit of using the correct prefix all the time instead of keeping a separate list of exceptions.

Isn't the OP using Xubuntu?

In that case, it should be ```
gksudo mousepad
``` and not ```
gksudo gedit
```

That's the problem .. if it's already a habit ( eg., you do it automatically, without thinking about it ), it takes time to replace it with something new.
More over, almost all tutorials, where you need to edit files, refer to sudo gedit, not gksudo ( since people already do it in that way and it works for them, I don't think that someone will really want to replace it with something else ).

---

### Post by Zill on 2009-08-28
> **aysiu said:**
> But it's good to be in the habit of using the correct prefix all the time instead of keeping a separate list of exceptions.

Isn't the OP using Xubuntu?

In that case, it should be ```
gksudo mousepad
``` and not ```
gksudo gedit
```

+1

The op is apparently a newbie and should, initially at least, use "best practice" to reduce potential problems.

---

### Post by aysiu on 2009-08-28
> **credobyte said:**
> That's the problem .. if it's already a habit ( eg., you do it automatically, without thinking about it ), it takes time to replace it with something new.
More over, almost all tutorials, where you need to edit files, refer to sudo gedit, not gksudo ( since people already do it in that way and it works for them, I don't think that someone will really want to replace it with something else ).
Right. That is the problem.

People need to get into a new habit.

No one would run *sudo firefox* if they hadn't seen *sudo gedit* in the first place.

---

### Post by aysiu on 2009-08-28
> **credobyte said:**
> That's the problem .. if it's already a habit ( eg., you do it automatically, without thinking about it ), it takes time to replace it with something new.
More over, almost all tutorials, where you need to edit files, refer to sudo gedit, not gksudo ( since people already do it in that way and it works for them, I don't think that someone will really want to replace it with something else ).
Right. That is the problem.

People need to get into a new habit.

No one would run *sudo firefox* if they hadn't seen *sudo gedit* in the first place.

---

### Post by Grifulkin on 2009-08-28
> **aysiu said:**
> But it's good to be in the habit of using the correct prefix all the time instead of keeping a separate list of exceptions.

Isn't the OP using Xubuntu?

In that case, it should be ```
gksudo mousepad
``` and not ```
gksudo gedit
```

+2

I was in the habit of using sudo for everything until I read that article on phychocats.  Now I use gksu for graphical applications, it isn't really that hard to "change" your ways.  Sudo for things insdie the terminal, gksu for the ones that aren't it's a good habit for new people to get into and for people who don't do it to start doing it.

---

