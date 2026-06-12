---
title: "Ubuntu Trashcan for beginners"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by cbride on 2009-03-11
As a new Ubuntu user, I'm posting because I have a problem with Nautilus and the Trashcan Applet.

Currently I am running the basic Hardy Heron 8.04 install that came with my Dell Mini 9.  Because the system is limited in storage space, I have been strictly managing my file space.

A few weeks ago, I downloaded and compiled the source code for Zdoom v2.2.0.  I ran the program for a few days and got tired of it.  In an attempt to regain some lost filespace, I deleted the source files and the compiled program using Nautilus.  All was fine and dandy, until I went to empty the trash can.

Apparently, Nautilus "deleted" some files with root-only access to the trashcan.  When emptying the trash, all of the files with user access were deleted, however the few files with root-only access remain.

When attempting to delete the root-only files, I am prompted with a window that states:  

"Error while deleting.
There was an error while deleting a.o
>Show more details
Error removing file: Permission Denied
XCancel  Skip All  Skip

OK.  So I have a few questions.

Is there a definitive resource that explains how the trashcan and Nautilus operate when deleting files?

Many forum posts about the trashcan reference a hidden ".Trash" file or folder located in the /home/*username*/  directory.  I've attempted to find the file or directory using both nautilus and the terminal with no luck.  There are a great deal of hidden files in the /home/*username*/ folder, but none named anything like .Trash .

If a .Trash file does not exist, where are the files being stored?

In an attempt to delete the files using superuser permissions, I've run

gk sudo nautilus /home/*username*/

in an attempt to find the files.  They don't appear when I do this.  Nor does nautilus allow me to access ANY trash folder (for either root or the standard user.

Does anyone know what is going on?  Am I just misunderstanding the file system and how Nautilus and the trashcan work together?

Any help would be appreciated.

---

### Post by blueridgedog on 2009-03-11
To find the files:

```
sudo find / -name .Trash
```

Then to delete them:

```
gksudo nautilus
```

Then to see hidden files Ctrl + H

Navigate to the location shown with the find command and delete as you see fit.

As far as an explanation....perhaps another forum user has one.

---

### Post by kanikilu on 2009-03-11
I believe the folder you are looking for is ~/.local/share/Trash/

Press CTRL+H in Nautilus to show hidden files if you don't see your "dot" files and directories (e.g. .local).

You can either go to the commandline and do ```
sudo rm -rf /home/username/.local/share/Trash/*
``` to delete them, or start a root file browser with ```
gksudo nautilus
``` and browse to the above path.

// Edit - obviously use due diligence whenever using *sudo rm -rf*. Bad things happen if you mistype a path.

---

### Post by blueridgedog on 2009-03-11
Kanikilu, as a rule I agree with your command line mojo, but I think the generally accepted rule on the forum is to try and talk users through solutions without the rm -rf command given that it can backfire.  

You can use gksudo nautilus then Ctrl + H to go and delete the files in ~/.local/share/Trash and not have to resort to rm -rf.

---

### Post by kanikilu on 2009-03-11
> **blueridgedog said:**
> Kanikilu, as a rule I agree with your command line mojo, but I think the generally accepted rule on the forum is to try and talk users through solutions without the rm -rf command given that it can backfire.  

You can use gksudo nautilus then Ctrl + H to go and delete the files in ~/.local/share/Trash and not have to resort to rm -rf.

Yeah, sorry - as soon as I posted that I realized it might not be the safest thing to suggest and edited. 

From a forum-op. perspective I can see why they don't want people to suggest potentially dangerous commands.

To the OP, try the GUI method first. Although there's nothing that says deleting from a root-owned nautilus window can't do just about as much damage as the CLI method, so still be sure you know what you are deleting before doing so.

---

### Post by blackstripes on 2009-03-11
What is the difference between 'rm' and 'rm -rf'? Isn't 'rm' the dos equivalent of 'del'?

---

### Post by kanikilu on 2009-03-11
> **blackstripes said:**
> What is the difference between 'rm' and 'rm -rf'? Isn't 'rm' the dos equivalent of 'del'? ```
man rm
``` Don't use those options if you don't know what they do.

---

### Post by blackstripes on 2009-03-11
> **kanikilu said:**
> ```
man rm
``` Don't use those options if you don't know what they do.

I haven't said that I am using them.  I understand that rm is the remove command, I'm just not sure if the -rf portion is what makes it particularly "dangerous".

---

### Post by kanikilu on 2009-03-11
> **blackstripes said:**
> I haven't said that I am using them.  I understand that rm is the remove command, I'm just not sure if the -rf portion is what makes it particularly "dangerous". Sorry I didn't mean to imply that you were - only that if "you" (the generic you, not *you* personally) don't know what a command (or in this case option) does, look it up and find out. That's why the man pages are there. If you read the manual and still don't understand why it's potentially dangerous, PM me.

---

### Post by Eisenwinter on 2009-03-11
> **blackstripes said:**
> I haven't said that I am using them.  I understand that rm is the remove command, I'm just not sure if the -rf portion is what makes it particularly "dangerous".
The "-rf" part of the "rm -rf <file/directory>" is an option switch.

The **"r"** switch means **recrusive removal**, this means it'll also remove any subfolders and "subfiles". 
The **"f"** switch means **force**, the command will be executed, **despite any protests by the system**.

People say rm -rf is dangerous. Well, it's not. 

As long as you know where everything is on your machine.

---

### Post by blackstripes on 2009-03-11
> **Eisenwinter said:**
> The "-rf" part of the "rm -rf <file/directory>" is an option switch.

The **"r"** switch means **recrusive removal**, this means it'll also remove any subfolders and "subfiles". 
The **"f"** switch means **force**, the command will be executed, **despite any protests by the system**.

People say rm -rf is dangerous. Well, it's not. 

As long as you know where everything is on your machine.

Thanks!

---

### Post by blueridgedog on 2009-03-11
> **Eisenwinter said:**
> 

People say rm -rf is dangerous. Well, it's not. 

As long as you know where everything is on your machine.

I agree and I use it all the time (as a Unix admin it is part of life).  My only suggestion was to build a trail of support where we show ways to get the job done without rm -rf so that we fit our advice in with the goals and objectives of the forum.  The command is a tool and any tool used correctly is a great thing.

---

### Post by cbride on 2009-03-11
Ok.  I was able to find the trash folder.  Apparently (for my install of Ubuntu) the Nautilus maintained trash is found in ~/.local/share/Trash

Was Nautilus's storage location for trash changed in the last few months????  Most of the information I could find directed me to a folder ~/.Trash    which didn't exist.

Either way.  For Nautilus v2.22.3 under Ubuntu 8.04 on my Dell Mini 9, the files within the Nautilus "Trash" or "Trashcan" are located under /home/*username*/.local/share/Trash  or better represented as ~/.local/share/Trash  .


Thanks for everyone's help.

---

### Post by kanikilu on 2009-03-11
> **cbride said:**
> Ok.  I was able to find the trash folder.  Apparently (for my install of Ubuntu) the Nautilus maintained trash is found in ~/.local/share/Trash

Was Nautilus's storage location for trash changed in the last few months????  Most of the information I could find directed me to a folder ~/.Trash    which didn't exist.

Either way.  For Nautilus v2.22.3 under Ubuntu 8.04 on my Dell Mini 9, the files within the Nautilus "Trash" or "Trashcan" are located under /home/*username*/.local/share/Trash  or better represented as ~/.local/share/Trash  .


Thanks for everyone's help.

That's where the trash is for everyone - my first post pointed to that path...

---

### Post by presence1960 on 2009-03-11
To evade this in the future : If you feel confident enough that you won't delete any important files you can open your file browser, go to edit, preferences and then to the behavior tab. At the bottom is Trash. Tick the box "Include a Delete command that bypasses Trash".

A delete command will be added to the context menu. But be warned it bypasses Trash. Once it is deleted it is gone.

---

### Post by jerome1232 on 2009-03-11
On another note if you delete files in a root nautilus session, they just get moved to the root users trash located at /root/.local/share/Trash/. 

So if your deleting files in nautilus while running it as root you know where to look.

---

