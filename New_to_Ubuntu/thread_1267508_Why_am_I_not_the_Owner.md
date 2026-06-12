---
title: "Why am I not the Owner??"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Marlowe221 on 2009-09-15
Why is it that all the files, folders, etc, say I'm not the owner?? I am the only user... What gives and how do I fix it???

---

### Post by Khanton on 2009-09-15
Ubuntu uses the root account to create the files used to make the OS run. As for changing this I am not sure.

---

### Post by steveneddy on 2009-09-15
Ah - but you are.

Since you are the administrator of that machine, you ARE root.

System critical files and folders are owned by root so you don't bork something by fiddling around where you don't belong.

You can

```
gksudo nautilus
```to open a "privileged" file browser.

When you see commands on the forums or the internet that start with

**sudo** or **gksudo** - they are refering to 

**S**uper **U**ser - which in essence is you.

It is done this way to protect you and your system if it is ever compromised (or the cat steps on the keyboard)

those links in my sig will teach you that and more about your system.

Please don't hesitate to post your questions.

Here's a link that may explain it further so that you may understand:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Marlowe221 on 2009-09-15
Well I get the whole stopping me from self-destructing thing. But I'm apparently not even the owner of a game I downloaded and installed 5 minutes ago..... I'm supposed to add some files to the game but I can't do it

---

### Post by halitech on 2009-09-15
where did you install the game to and did you use sudo to install it?

---

### Post by k33bz on 2009-09-15
> **Marlowe221 said:**
> Well I get the whole stopping me from self-destructing thing. But I'm apparently not even the owner of a game I downloaded and installed 5 minutes ago..... I'm supposed to add some files to the game but I can't do it

```
chown username.username path/to/file
```

---

### Post by misfitpierce on 2009-09-15
It more than likely added the files to a root directory where you need root access to add the files... Open a terminal and do this...
[quote="TERMINAL"]gksu nautilus[/quote]
Then navigate to the place and paste into directory in root nautilus and it'll work.

---

### Post by Bölvaður on 2009-09-15
> **Marlowe221 said:**
> Why is it that all the files, folders, etc, say I'm not the owner??
Which files exactly?
If 100% all files are owned by someone else, then we might have a problem. But that kind of problem should never arise unless if you deleted the user that owned those files (which probably did not happen).


The reason it says you are not the owner is because you aren't the owner. They where created under a different user named **root**.

> **Marlowe221 said:**
> I am the only user...

Yes and no.
You are 2 users at the same time. One which is you, and the other one that is root (think of it as the system admin account...).

> **Marlowe221 said:**
> 
What gives and how do I fix it???
Log in as root. But be careful, programs that are allowed to run under the user root have absolute power.
If you want to run the file browser as root press Alt+F2 and type```
gksu nautilus
```
*nautilus* is the file manager and *gksu* is the graphical user switcher (hence the name).

You can run any program you want as root just by typing gksu and then the correct program name.

---

### Post by Bölvaður on 2009-09-15
> **Marlowe221 said:**
> But I'm apparently not even the owner of a game I downloaded and installed 5 minutes ago..... I'm supposed to add some files to the game but I can't do it


Perhaps we can help you out with that.
What game did you download?
How exactly did you install it? (many different ways)
What are you suppose to change/add?.. and where

---

### Post by Marlowe221 on 2009-09-15
I'm trying to install new songs into frets on fire

---

### Post by steveneddy on 2009-09-15
> **Marlowe221 said:**
> Well I get the whole stopping me from self-destructing thing. But I'm apparently not even the owner of a game I downloaded and installed 5 minutes ago..... I'm supposed to add some files to the game but I can't do it

Ah - now the actual reason for the thread.

Just follow the instruction I gave you

and follow the path to the folder.

But there may be an easier way. Is the game telling you to put files somewhere?

What are the files and where do they go?

Post the instruction the game is asking you to perform.

We can accomplish a lot faster by utilizing the terminal.

---

### Post by k33bz on 2009-09-15
> **Marlowe221 said:**
> I'm trying to install new songs into frets on fire

Did you download and install or did you get it from the  synaptic manager?

---

### Post by Bölvaður on 2009-09-15
> **k33bz said:**
> Did you download and install or did you get it from the  synaptic manager?

it doesnt matter as the files he is supposed to place will always be owned by the user, that is, placed in his home folder.

look at the top panel, Places &#8594; Home Folder
Press Ctrl+H (to see hidden files)
look for .fretsonfire and then inside that directory click songs
there is where you are supposed to place your songs :)

---

