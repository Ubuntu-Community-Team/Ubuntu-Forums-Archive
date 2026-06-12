---
title: "Synaptic Package Manager"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by k-boy on 2010-08-06
***new user of Ubuntu...can anyone tell where can i find  files that are downloaded using synaptic package manager???***

---

### Post by chopinhauer on 2010-08-06
> **k-boy said:**
> ***new user of Ubuntu...can anyone tell where can i find  files that are downloaded using synaptic package manager???***
[U]
[/var/cache/apt/archive/](file:///var/cache/apt/archive/)[/U], but are you sure you don't want to use Synaptic to also install the packages?

---

### Post by kellemes on 2010-08-07
> **k-boy said:**
> ***new user of Ubuntu...can anyone tell where can i find  files that are downloaded using synaptic package manager???***

Depends on the file..
But as said.. normally you use Synaptic to install software so you don't need to know where they are located, you just need to run it.

---

### Post by rburkartjo on 2010-08-07
k dont know if this is what you are looking for but if you open the ubuntu software center there is an option that shows you all the software you have installed on your system

---

### Post by beew on 2010-08-07
> k dont know if this is what you are looking for but if you open the  ubuntu software center there is an option that shows you all the  software you have installed on your system
I think Ubuntu Software center only shows those which have a launcher in the drop down menus, which means most of them are missing if they don't create a launcher. In  other words, you can find them in the drop down menu anyway if Ubuntu Software center lists them at all.

If you know specifically what you are looking for, say, a utility called bchunk, you go to the terminal and type 

```
$ which bchunk 
``` If the package is installed it will tell you where it is. If it is not then it does nothing.

But what if you don't know the exact name? I think there must be some kind of smart search using the command line but I don't know how. In these situations I would go to synaptic, find the program's entry and then click 'properties' and it will tell you where it is installed along with other information.

I use synaptic exclusively  and find Ubuntu Softeware Center pretty useless. I have actually gotten rid of it in one of my Ubuntu installations (I have 3,  two installed in external hard disks) and so far there is no ill effect. I prefer synaptic over the command lines. The command line is fast and efficient if you know already what you want and what the name of the program is. But synaptic gives you a catalogue with descriptions to browse through if you don't have very specific idea.

---

### Post by beew on 2010-08-07
kellemes

> But as said.. normally you use Synaptic to install software so you don't  need to know where they are located, you just need to run it.Well that is not very satisfactory, is it? :)

 Besides, you do need to know where they are installed sometimes say if you need to make a launcher or choose a program in some "open with" boxes when it is not listed by default.

---

### Post by Achilles124 on 2010-08-07
usr/bin is the place to look for programs installed.

---

### Post by k-boy on 2010-08-08
Thank you guys for your reply.I just wanted to know where it saves nothing rather i needed it for.

---

### Post by QLee on 2010-08-08
> **k-boy said:**
> Thank you guys for your reply.I just wanted to know where it saves nothing rather i needed it for.

The answer to your question as you stated it was given in post 2 by chopinhauer. That's where the package files downloaded by Synaptic go.

However it's pretty clear you're actually asking where the files related to the application installed by the package manager are located. You can see the locations of files unpacked by the package manager for specific programs by checking the "properties" in Synaptic. Select (highlight) the package you are interested in and select properties from the menu, a property sheet will open and then select the installed files tab to see a list of the locations of installed files for that application.

The "which" command (as posted by beew) gives you the location of the command to start the program that you would need in order to create  a launcher.

---

