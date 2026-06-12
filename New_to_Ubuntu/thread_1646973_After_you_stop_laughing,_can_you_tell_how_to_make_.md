---
title: "After you stop laughing, can you tell how to make a program to launch an application?"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-12-16
Hello:

I downloaded Freeplane - mind mapping software.

It unzipped into a sub-folder in Downloads.

To launch it, I am to navigate to its folder from within a terminal and then do: sh freeplane.sh

This works.

What I would like to do is to be able to launch it from a menu, say the Office menu under the 'Applications' main menu.

Can this be done? If so, how?

Also, should I move the Freeplane folder to a more apt folder rather than leave it in Downloads?

Thanks,

---

### Post by TeoBigusGeekus on 2010-12-16
Move the folder to your /home partition.
Right click the menus>Edit menus.
Go to Office and click new for the right side of the window.
Name the launcher whatever you want, choose an icon for it if you wish and give as command
```
sh ~/foldername/freeplane.sh
```
...and you're done.

EDIT:
Why should we laugh?

---

### Post by Robert.Thompson on 2010-12-16
> **TeoBigusGeekus said:**
> Move the folder to your /home partition.
Right click the menus>Edit menus.
Go to Office and click new for the right side of the window.
Name the launcher whatever you want, choose an icon for it if you wish and give as command
```
sh ~/foldername/freeplane.sh
```
...and you're done.

EDIT:
Why should we laugh?

I could only get it to work with the following command:

          sh /home/rob/freeplane/freeplane.sh

Why would it not work with:

          sh ~/freeplane/freeplane.sh
                     or
          sh ~/rob/freeplane/freeplane.sh

???:confused:

Thanks,

---

### Post by bodhi.zazen on 2010-12-16
> **Robert.Thompson said:**
> I could only get it to work with the following command:

          sh /home/rob/freeplane/freeplane.sh

Why would it not work with:

          sh ~/freeplane/freeplane.sh
                     or
          sh ~/rob/freeplane/freeplane.sh

???:confused:

Thanks,

sh does not know where ~ is =)

Take a look at environmental variables.

In general, and IMO, it is best to use the full path in menu entries and scripts, rather then ~ , ./ , ../..

You can look at this:

[http://www.codecoffee.com/tipsforlinux/articles/030.html](http://www.codecoffee.com/tipsforlinux/articles/030.html)

---

### Post by TeoBigusGeekus on 2010-12-16
Oh yeah... I've encountered this before... It must be a bash thing.
EDIT:
Alright bodhi.

---

### Post by bodhi.zazen on 2010-12-16
> **TeoBigusGeekus said:**
> Oh yeah... I've encountered this before... It must be a bash thing.
EDIT:
Alright bodhi.

I thought you might have a better idea =)

Mine is just a guess, without an error message, or downloading and looking at the source, it is hard to know.

Not to state the obvious, but a well behaved script has a she-bang at the top

!#/bin/bash or #!/bin/sh

If not, you can call the script with 

bash /path/to/file
sh /path/to/file
perl /path/to/file

calling bash, sh, and perl to interpret the file if you wish.

---

### Post by TeoBigusGeekus on 2010-12-16
> **bodhi.zazen said:**
> I thought you might have a better idea =)

Mine is just a guess, without an error message, or downloading and looking at the source, it is hard to know.

Not to state the obvious, but a well behaved script has a she-bang at the top

!#/bin/bash or #!/bin/sh

If not, you can call the script with 

bash /path/to/file
sh /path/to/file
perl /path/to/file

calling bash, sh, and perl to interpret the file if you wish.

I have no idea for the cause of this, cause if you
```
sh ~/myscript.sh
```
from terminal everything will run normally.
By the way, sh is just a symbolic link to bash (at least in arch):

---

### Post by bodhi.zazen on 2010-12-16
> **TeoBigusGeekus said:**
> I have no idea for the cause of this, cause if you
```
sh ~/myscript.sh
```
from terminal everything will run normally.
By the way, sh is just a symbolic link to bash (at least in arch):

Aye, it varies by distro. In Ubuntu sh is linked to dash.

And mine was just a guess, as you point out, I am probably wrong on that.

---

### Post by NertSkull on 2010-12-16
What I do, is right click on the desktop and click make launcher.

Then fill in the important stuff (sepcifically the command to run) then save it.

Then I move it off the desktop to a folder (just to keep the desktop clean).

Then you can drag the launcher into the panel or menus.

Super easy, always has worked for me.

---

