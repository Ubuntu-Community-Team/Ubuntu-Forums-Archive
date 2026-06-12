---
title: "How Do I Remove Files from opt?"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by T C on 2010-08-02
I ran "install.sh" for a program and it put two new subfolders in my /opt folder. Now I've decided I don't want that program on my computer. How do I remove the subfolders it created?

-TC

---

### Post by Drenriza on 2010-08-02
what is the program called?

---

### Post by orethrius on 2010-08-02
**[COLOR="Red"]!!!CAUTION!!![/COLOR] Sudo can be an INCREDIBLY dangerous command.  Use EXTREME care to follow ONLY the instructions listed below.  Your files can be deleted, or worse, if you are not careful.  YOU HAVE BEEN WARNED. [COLOR="Red"]!!!CAUTION!!![/COLOR]**

Okay, now that that's out of the way, assuming you know which folders were added, you would simply open a Run dialog (Alt+F2), type:
```
gksudo 'nautilus /opt'
```
press enter, then enter your root password.

From there, you have privs to remove ANY FOLDER on your system, hence the BOLD, RED caution notice above.

If you don't know which folders were modified, simply order them by List View and check the Date Modified fields.  Again, be VERY CAREFUL doing any of this.

Once you're done, click the icon of a pair of keys on your panel (right-click on pre-10.04 systems), and select "Drop elevated priviliges".

That should do the trick! :)

---

### Post by mrout on 2010-08-02
**[COLOR="Red"]Warning: Root (sudo) is extremely dangerous, and when used wrongly it can completely destroy your computer.[/COLOR]**

It's fairly simple, to delete the folder run at your command prompt:

replace subfolder1 and subfolder2 with the folders your want to delete

```
$ sudo rmdir /opt/subfolder1
$ sudo rmdir /opt/subfolder2
```
They will need to be empty. To do this run first:

```
$ sudo rm -R /opt/subfolder1/*
$ sudo rm -R /opt/subfolder2/*
```
**[COLOR="#ff0000"]Be VERY careful when combining sudo and rm (for remove), as some of the most dangerous commands are some of the most simple.[/COLOR]**

---

### Post by T C on 2010-08-02
Thanks for the replies.

I actually knew about sudo and rmdir; I just didn't know that was the right thing to do.

For me, the most confusing thing about Linux is not figuring out how to do things, but figuring out the right way to do things. The GUI offers several ways to install and uninstall programs, so it is not obvious to a beginner that removing folders manually with sudo and rmdir is the correct way to uninstall a program from opt.

Drenriza, the program in this case is Second Life.


-TC

---

### Post by MrPok on 2010-08-04
> **T C said:**
> .. For me, the most confusing thing about Linux is not figuring out how to do things, but figuring out the right way to do things. The GUI offers several ways to install and uninstall programs, so it is not obvious to a beginner that removing folders manually with sudo and rmdir is the correct way to uninstall a program from opt.

Drenriza, the program in this case is Second Life.

I agree with T C that it is sometimes unclear how to add/remove some application *manually* that is, without the software-center/synaptic/apt/.deb-files/etc. 

I came across this post while searching how (and if) to remove an install of **Eclipse** (an old version 3.4.2, instead of the 3.5.2 that is available now) from /opt . I must have installed it there myself over a year ago, but back then I was a bit overwhelmed :o with the Linux experience, so I couldn't trace back how I had it installed. 

Anyhow, I guess that just removing the /opt/eclipse directory is enough to erase any traces of the old version ..so I can start using the (already installed) new Eclipse version? 
Re-importing the workspace..

If not, let me know pls. (sorry if this appears a topic hijack :) )

Kind regards,
Paul

---

