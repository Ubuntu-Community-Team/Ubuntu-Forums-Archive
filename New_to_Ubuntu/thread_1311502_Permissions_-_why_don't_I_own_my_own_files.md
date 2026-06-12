---
title: "Permissions - why don't I own my own files?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by polytropos on 2009-11-02
I just did a fresh install of Koala.  I can't alter any of the files in my root directory, because, according to the computer, I am not the owner.  What has happened?

I should add this: I partitioned my computer with a '/' mount point, a swap space, and then a massive '/var' space.  The last of these is for file storage.  If there is a better way to partition - I have no doubt that there is - please tell me as well.

---

### Post by NoaHall on 2009-11-02
You aren't the owner. Root is. The files in root are the system files, need to run the operating system. Stay inside your /home/

---

### Post by liquidbee on 2009-11-02
```
/ - root
/home - private temporary files
/data - music, pictures, backups and whatnot ( stuff that you don't want to loose )
swap

```

This is how I do it - if you loose the ownership of /data, chown it :)

---

### Post by lisati on 2009-11-02
> **NoaHall said:**
> You aren't the owner. Root is. The files in root are the system files, need to run the operating system. Stay inside your /home/

+1: A small slip of the finger or click in the wrong place can have nasty side effects. Ever noticed that some Windows systems "hide" files and folders when you navigate to places like C:\ when using Windows Explorer.

---

### Post by ovroniil on 2009-11-02
Yes, dear! you are not the owner of those files. The real owner is the Root! "Root" is just like an "Administrator" in windows. So when you login as a the Root then you can modify the files. This is actually one kind security of Ubuntu that prevents the user from any kind of disaster. So that the user can't accidentally delete any system files.

But as an user you have the permission to do anything in your 'area' and that is '/home'. Yes home is your area. It's like the "My Documents" in Windows. You can store or delete any files here. 

While installing Ubuntu I always made three partitions: 1. '/' 2. '/home' 3. 'swap'. In '/var' mainly logs, databases, etc are stored. 

Now if you want to get access in root then type the following code. **But be sure about what you are doing!**
```

sudo nautilus /
```

UPDATE:[B]
** The above code has some disadvantages. The explanation is underneath. **[/B]

---

### Post by ZankerH on 2009-11-02
You probably don't need a separate partition for /var, unless you plan on running a server. You should just copy your stuff over to your /home directory and change the ownership to yourself, giving yourself read and write access to /var probably isn't the best idea.

---

### Post by aysiu on 2009-11-02
```
gksudo nautilus
``` is the way to go if you want to make graphical changes to system files (user files are in /home/*username*... anything outside that directory is a system file).

If you prefer the terminal, use ```
sudo -i
``` Do **not** use *sudo nautilus*, and definitely don't use *sudo -s*

---

### Post by ovroniil on 2009-11-02
> **aysiu said:**
>  Do **not** use *sudo nautilus*, and definitely don't use *sudo -s*

Is there any specific reason for that??

---

### Post by aysiu on 2009-11-02
> **ovroniil said:**
> Is there any specific reason for that??
Yes. If you launch a graphical application with *sudo* (as opposed to *gksudo* or *kdesu*) or if you use *sudo -s* to get a persistent root prompt, you are launching the application or command with **root privileges** but still using the **user environment**, which can lead to accidental change in ownership of user files to root, which can lead to some applications not functioning properly or some user settings not sticking.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ovroniil on 2009-11-02
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")@[[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")

Thanx for the info, I did not know that. So for the caution, I've altered my previous post by putting "SUDO" instead of "sudo".

---

### Post by NoaHall on 2009-11-02
> **ovroniil said:**
> [[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")@[[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")

Thanx for the info, I did not know that. So for the caution, I've altered my previous post by putting "SUDO" instead of "sudo".

Why not replace it with gksudo anyway?

---

### Post by Je Et on 2009-11-02
> Why not replace it with gksudo anyway?


This didn't work when I was trying to change /dev/input/js0

PEACE:)

Je Et

---

### Post by ovroniil on 2009-11-02
> **NoaHall said:**
> Why not replace it with gksudo anyway?

So that people will know why [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") has said so! ;)

---

### Post by liquidbee on 2009-11-02
> **ovroniil said:**
> So that people will know why [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") has said so! ;)

He didn't said anything about the difference between lowercase and uppercase commands.

---

### Post by ovroniil on 2009-11-02
[quote=liquidbee]He didn't said anything about the difference between lowercase and uppercase commands.[/quote]

He mentioned about the difference between using **sudo** and **gksudo**. So to prevent the people to run the command with **sudo**, I altered that one into capital letters. I could make it **gksudo**, but in that case people will miss the point and chronicles why [COLOR=Black]on earth** aysiu**[/COLOR] mentioned about **gksudo**.

---

### Post by cariboo on 2009-11-02
The only time you would use sudo to run a graphical program, is if you start it from a terminal. Other wise use gksu or gksudo.

---

### Post by Zoot7 on 2009-11-02
Just to add, here's a nice article explaining file permissions and ownership.
**[http://www.linuxforums.org/security/file_permissions.html]("http://www.linuxforums.org/security/file_permissions.html")**

---

### Post by aysiu on 2009-11-02
> **cariboo907 said:**
> The only time you would use sudo to run a graphical program, is if you start it from a terminal. Other wise use gksu or gksudo.
Even then I would use *gksudo* or *kdesu*.

If you want to be able to close the terminal afterwards, you can use the *&* sign at the end: ```
gksudo nautilus &
```

---

### Post by polytropos on 2009-11-02
Thanks for all of the feedback.  So, suppose I set my system up like this:

/
/home
/swap
/data

A few questions:

1.  Which are primary partitions, and which are logical?

2.  What size should each be?

I got myself into this jam because earlier today I set up Koala and, though I allocated 20 G to '/' and 10 G to '/home', both (I think) as primary partitions, quickly maxed out my space.

I'm planning at this point to run a fresh install--just looking for the best way to set things up.

Thanks again!

---

### Post by Merk42 on 2009-11-02
I don't see the need of a separate /home and /data.  I mean if /data is music/movies/documents, there are folders in /home for that

I have / around 20GB (but only used about half)
I have swap around 2GB
The rest is /home

---

### Post by liquidbee on 2009-11-03
> **polytropos said:**
> Thanks for all of the feedback. So, suppose I set my system up like this:
 
/
/home
/swap
/data
 
A few questions:
 
1. Which are primary partitions, and which are logical?
 
2. What size should each be?
 
I got myself into this jam because earlier today I set up Koala and, though I allocated 20 G to '/' and 10 G to '/home', both (I think) as primary partitions, quickly maxed out my space.
 
I'm planning at this point to run a fresh install--just looking for the best way to set things up.
 
Thanks again!
 
/ and /home - primary
swap and everything else you may add - logical
 
Don't forget that /data ( my example ) is just a mount point - you can change it to something more intiuitive :)

---

### Post by oldos2er on 2009-11-03
> **polytropos said:**
> Thanks for all of the feedback.  So, suppose I set my system up like this:

/
/home
/swap
/data

A few questions:

1.  Which are primary partitions, and which are logical?


 They can all be logical, if you prefer.

---

