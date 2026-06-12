---
title: "Can't install anything. says there's other installers when there isn't"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by esotericguy on 2008-12-28
I've got Ubuntu 8.10 running with the modified eee pc kernel on my (obviously) eee pc 1000ha. It's installed via Wubi. Now that the intro is out of the way.

I'm trying to install Opera, themes, etc., but it won't let me. It will allow installations from the add/remove... but not from downloaded debs.

This is the message i get:
[[IMG]http://img114.imageshack.us/img114/6729/screenshotjd7.th.png[/IMG]](http://img114.imageshack.us/my.php?image=screenshotjd7.png)



so what's the verdict/advice?

---

### Post by gettinoriginal on 2008-12-28
Are you sure you do not have synaptic or terminal open ??

---

### Post by Michael.Godawski on 2008-12-28
hi,

make sure no other installing application or update application is running. 
So close the Synaptics, Add/remove, the terminal, update manager and what not.

Now open only one of them. Ubuntu does not allow to mix the installation processes.

---

### Post by mkvnmtr on 2008-12-28
If a notice says you have other installers open then you have other installers open. Either "add/remove" or "Synaptic package manager". You will have to close it before you can install with another method. You said you want to install a deb. Have you read a tutorial about what is necessary to install that type of files?

---

### Post by esotericguy on 2008-12-28
> **Michael.Godawski said:**
> hi,

make sure no other installing application or update application is running. 
So close the Synaptics, Add/remove, the terminal, update manager and what not.

Now open only one of them. Ubuntu does not allow to mix the installation processes.

absolutely nothing is open. I even went so far as to restart and the first thing i did was to try to install Opera. The same message popped up. I've checked the systemld be causing this? monitor, and from what i could tell synaptic nor any other updates are happening.

anything esle that causing this?

---

### Post by cariboo on 2008-12-28
You may have a leftover lock file in either /var/apt/lists, /var/lib/dpkg or /var/cache/apt/archives.

Jim

---

### Post by esotericguy on 2008-12-28
> **cariboo907 said:**
> You may have a leftover lock file in either /var/apt/lists, /var/lib/dpkg or /var/cache/apt/archives.

Jim

I have no idea what this implies. Any more info?

---

### Post by Michael.Godawski on 2008-12-28
Indeed weird.

What does the ```
top
``` command say?

---

### Post by baruch60610 on 2008-12-28
You might want to try using 'ps' to see what's running.  There may be some script that you don't know about that starts an installer.

The syntax is:

```
 ps aux
```As for finding the (possible) offending program, you might try to grep for 'synaptic', 'apt', or whatever else there may be.  That syntax would be:

```
 ps aux | grep -i synaptic
```I generally use the -i option to tell grep to ignore case.  Otherwise it might miss 'Synaptic', because it has a capital letter.

Note that if you use this syntax, you'll always get at least one hit - that's the query you're running.  Grep will detect its own process and list it.

---

### Post by esotericguy on 2008-12-28
> **Michael.Godawski said:**
> Indeed weird.

What does the ```
top
``` command say?


[[IMG]http://img374.imageshack.us/img374/1381/screenshot1rk2.png[/IMG]](http://img374.imageshack.us/my.php?image=screenshot1rk2.png)
[[IMG]http://img374.imageshack.us/img374/screenshot1rk2.png/1/w1024.png[/IMG]](http://g.imageshack.us/img374/screenshot1rk2.png/1/)

---

### Post by gettinoriginal on 2008-12-28
according to top, gnome terminal is running, kill it.

---

### Post by baruch60610 on 2008-12-28
A lock file is a special file that signals to other programs that a certain program is running.  So if you had synaptic running, it would create a lock file.  If you tried to run some other package manager, that other program would check to see if there is a lock file.  If there is, it will give an error message and end.

It could happen that if one package manager ended abruptly, it didn't have a chance to clean up after itself.  In that case, it may not have been able to remove the lock file.  Any other package manager would see that lock file and print out their error message.

I think there's a lock file created in /var/lib/dpkg, but I'm not sure what its name is.  Probably something like 'lock'.

---

### Post by esotericguy on 2008-12-28
> **gettinoriginal said:**
> according to top, gnome terminal is running, kill it.

gnome terminal was running ofcourse, how else could i have gotten that info? other than that everything should be right

---

### Post by esotericguy on 2008-12-28
> **baruch60610 said:**
> 

I think there's a lock file created in /var/lib/dpkg, but I'm not sure what its name is.  Probably something like 'lock'.


it's there alright, but i cannot delete it. when i check the permissions, it says i'm not the owner.

---

### Post by arubislander on 2008-12-28
Try deleting it with:
```
sudo rm /var/lib/dpkg/lock
```
when asked for a password, type your own (the one you used for logging in.)

---

### Post by esotericguy on 2008-12-28
> **arubislander said:**
> Try deleting it with:
```
sudo rm /var/lib/dpkg/lock
```
when asked for a password, type your own (the one you used for logging in.)

I do that and it does delete it, i checked. but when i try to install opera again the same message occurs and the lock file becomes created again.

:(

---

### Post by arubislander on 2008-12-29
> **cariboo907 said:**
> You may have a leftover lock file in either /var/apt/lists, /var/lib/dpkg or /var/cache/apt/archives.

Jim

Did you also look in the other locations Jim mentioned? I myself do not have a /var/apt/lists, but the other two do exist and have lock files if for instance Synaptic is running.

---

