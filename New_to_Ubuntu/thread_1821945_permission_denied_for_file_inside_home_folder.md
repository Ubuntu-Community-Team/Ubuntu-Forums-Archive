---
title: "permission denied for file inside home folder"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by imortalninja161 on 2011-08-09
hay guys i was strolling along in the terminal today and copied a folder from my hard drive that was fine now 
The folder i want to open this there "tafe cert4"

> ninjalo161@ninjalo161-Aspire-5742:/home$ ls -a
.  ..  ninjalo161  Tafe cert4then i do this and get this 

> ninjalo161@ninjalo161-Aspire-5742:/home$ cd Tafe\ cert4
bash: cd: Tafe cert4: Permission deniedi also tried 

> ninjalo161@ninjalo161-Aspire-5742:/home$ sudo cd Tafe\ cert4
sudo: cd: command not found***UPDATE** 
i looked at the folder in the GUI aswell at i wont let me in the folder it said permission denied maybe it was a but copy or placed in the wrong folder :/ 

This is what i have in result to ls command mmm folder dusent look rite ;/ i dont any thing bout linux file permissions but Tafecert4 dusent have many lol

> 
drwxr-xr-x  4 root       root       4096 2011-08-10 10:46 .
drwxr-xr-x 24 root       root       4096 2011-08-10 10:46 ..
drwxr-xr-x 33 ninjalo161 ninjalo161 4096 2011-08-10 09:41 ninjalo161
drwx------ 10 root       root       4096 2011-08-10 10:27 Tafe cert4


Thanks 
imortalninja161

---

### Post by lmarmisa on 2011-08-09
Try to post the result of this command:

```

ls -al

```

---

### Post by XubuRoxMySox on 2011-08-09
I have a *totally graphical* cheat that I use to move files around to and from "restricted" folders. I discovered it during my flirtation with the lightning-fast LXDE desktop.

Using Software manager or Synaptic, install **PCManFM**. It's LXDE's file manager but for a "lightweight" it packs a punch! Let's say I just downloaded this wicked cool wallpaper and want to add it to my collection.  In PCManFM, I copy files from */home/downloads*, which is "open," to *usr/share/xfce4/backdrops* (where Xubuntu keeps my wallpapers), which is a "permission denied" directory. Heh heh, we'll see about that! 

Click on **Tools -> Open Current Folder as Root**. Enter my password and bingo, a new window opens with a heading, "[COLOR="Blue"]WARNING! You are in Superuser Mode![/COLOR]"

Now I can just drag and drop my stuff between folders effortlessly. 

It's a graphical substitute for "sudo" in the terminal. Works for me!

-Robin

---

### Post by jtarin on 2011-08-10
> then i do this and get this

Quote:
ninjalo161@ninjalo161-Aspire-5742:/home$ cd Tafe\ cert4
bash: cd: Tafe cert4: Permission denied
i also tried

Quote:
ninjalo161@ninjalo161-Aspire-5742:/home$ sudo cd Tafe\ cert4
sudo: cd: command not found 

This is not windows....to descend into a directory it is a forward slash "/".

---

### Post by -kg- on 2011-08-10
> **jtarin said:**
> This is not windows....to descend into a directory it is a forward slash "/".

I don't know about that, jtarin...I tried several experiments, and while it indeed is a forward slash, attempting to use a back slash didn't throw the same error as he's getting.

When I inserted a back slash, it threw a "No such file or directory", not a "cd: command not found".  Of course, it might have something to do with the "sudo" command.  I didn't experiment with that, and I don't know whether sudo can be used with cd, but I don't know why not.

One other way you can access it the GUI way is to launch Nautilus with Super user permissions:

```
gksudo nautilus
```

That way, you should be able to open and navigate the folder.

---

### Post by imortalninja161 on 2011-08-10
yerrrr the / is a result of a earlier executed command so in effect it has not relevents to the syntax of this command 

                             ninjalo161@ninjalo161-Aspire-5742:/home$ #### the command starts at the $ ####### cd Tafe\ cert4
bash: cd: Tafe cert4: Permission denied                      

And no i havent tried the gksudo nautilus yet thank you for the command but i was hoping to resolve the issue in terminal. I am studying linux more specificity redhat as a part of my networking course and our test will all be on using terminal so i am trying to get ustew using terminal to navigate everywhere atm lol.

Is there a way to add some type of view by everyone or full control permission to that folder threw terminal :/

thanks
imortalninja161

---

### Post by coffeecat on 2011-08-10
> **jtarin said:**
> This is not windows....to descend into a directory it is a forward slash "/".

The OP is not using the backslash as a directory separator. They are using it as an escape character because of the space in the folder name, thus:

```
cd Tafe\ cert4
```

That is correct usage. 

@imortalninja161, as far as I can see your problem is straightforward:

[QUOTE=imortalninja161]```
drwxr-xr-x 4 root root 4096 2011-08-10 10:46 .
drwxr-xr-x 24 root root 4096 2011-08-10 10:46 ..
drwxr-xr-x 33 ninjalo161 ninjalo161 4096 2011-08-10 09:41 ninjalo161
[COLOR="Red"]drwx------ 10 root root 4096 2011-08-10 10:27 Tafe cert4 [/COLOR]
```[/quote]

It's not clear from your post how you got that output (what command did you use?), but your "Tafe cert4" is owned by root and only root has rwx permissions. That's why you can't open it. If "Tafe cert4" is in your home folder, do this command.

```
sudo chown -R ninjalo161: Tafe\ cert4
```

The -R option will also change the ownership of any files inside the "Tafe cert4" folder.

**EDIT**: that command assumes you are still "in" your home directory in the terminal - that is, that you haven't cd'd anywhere.(end-edit).

By the way, when posting terminal output, please use [noparse]```

```[/noparse] tags, not quote tags. You lose important formatting with quote tags.

---

### Post by dethorpe on 2011-08-10
>  
drwx------ 10 root root 4096 2011-08-10 10:27 Tafe cert4 

 
Your folder name has a space in it hence the back slash \ to escape it in the command (its not a directory delimiter). 
 
Can also use quotes round the name to avoid confusion e.g cd "Tafe cert4" (Personally i avoid having spaces in directory names as its a pain)
 
The "Tafe cert4" folder is owned by root with no access to anyone else, to change it to be owned by yourself do this:
 
```
 
sudo chown ninjalo161:ninjalo161 "Tafe cert4"

```
 
(This assumes your user is in group ninjalo161, check this with "id" command to see your main group, if its not ninjalo161 then change the second ninjalo161 in the command to the group your actually in)
 
If you want read access to other users, i.e same permission as the ninjalo161 directory, then do this:
 
```
 
chmod 755 "Tafe cert4"

```
 
(don't have to sudo this one as you now own the file after the chown command, but would do if it was still owned by root)
 
Use man to read up on the chown and chmod commands to see what these are doing and other options. You may need the recursive option (-R) if the directory has futher sub-dirs you need to change as well.
 
**EDIT**: lol, simultaneous reply with coffecat, looks like we are saying the same things though :-)

---

### Post by imortalninja161 on 2011-08-10
Sweeeeeettttt got it Thank you all for you help specially dethorp and cofee cat 

Thanks 
imortalninja161

---

### Post by jtarin on 2011-08-10
> **coffeecat said:**
> The OP is not using the backslash as a directory separator. They are using it as an escape character because of the space in the folder name, thus:

```
cd Tafe\ cert4
```

That is correct usage. 

I wasn't so certain of that, but now I see. As stated by another...I avoid spaces in filenames (always have out of old habits) and this didn't come to mind at all. I did catch the permissions thing but thought....one thing at a time. Good you got it solved.

---

### Post by anewguy on 2011-08-10
I'm wondering how the folder got created.  You see, at least up to and including 10.10, there is a default udev rule for "unknown" USB devices such that they are owned by root - thus causing a need to run applications that use the device as su.  Doing so can result in this problem if the application creates a folder.

I ran into this myself with some non-standard USB cameras and the app that accessed them created a folder for that sessions photos.  Since the device was being owned by root, I could run the app via sudo .....  This kept the folder in my directory tree, however since it was su and the device was owned by root the folder was created with root owner, etc..  The way around this was to add a special udev rule where the particular USB manufacturer and product id's so that the devices where rw access to everyone in a group (you could just make it everything to the world as well).

So, do you know how the folder got created within your home tree?

Dave ;)

---

### Post by -kg- on 2011-08-10
I've learned something here, too...two methods to access a directory with a space in the name.  My thanks, as well!  :D

---

### Post by imortalninja161 on 2011-08-11
> So, do you know how the folder got created within your home tree?

A ok yer sounds abit like the problem i had.

I copied that folder from my NTFS portable hard drive

---

### Post by peteremmm on 2013-03-07
Thank you!!!

---

### Post by coffeecat on 2013-03-07
Back to sleep, old thread.

---

