---
title: "Confused about file system and saving programs, pictures, etc."
date: 2009-10-04
forum: New to Ubuntu
---

### Post by Kill-Switch on 2009-10-04
I been doing a search on this but I am unable to find my answer. This isn't just ubuntu specific question, I been hearing about this on other distros and throughout the GNU/Linux community. 

Whenever someone saves a program or software, I see people saying it's a good idea to always save it in usr/local/src. I always saved everything on the default on firefox which is "Downloads." Why is it a good idea to save softwares in usr/local/src?

Also, for pictures and videos, would this go to home/yourname/pictures or home/yourname/videos? Where do the .tar or extra themes for a certain Windows Manager go?

I'm not sure why it's a good idea to keep it like the way it is above, I wanted to know what's the reason behind it and what types of files should go to a certain directory.

I know it doesn't matter but I'm very curious on learning more about GNU/Linux. Thank you for reading.

---

### Post by snowpine on 2009-10-04
Hi there Kill-Switch, good question! :)

/home/yourname is your user folder, and it is the *only* folder you need to use for everyday tasks. You can't make changes outside this folder unless you use the "sudo" command (which you should only use if you know exactly what you're doing). 

In general, when you install new applications you should install them from the Ubuntu repository by using Add/Remove Programs, Synaptic Package Manager, or the command line ('sudo apt-get install firefox" for example). When you use one of these official tools, it automatically extracts and installs the application to the correct folder; you don't need to worry about it.

I would be wary of anyone instructing a new Ubuntu user to mess with anything in the /usr folder. 

To answer your other question, it doesn't matter whether you save a picture in /home/killswitch/pictures or /home/killswitch/videos or whatever... as long as you remember where you put it. ;)

---

### Post by Kill-Switch on 2009-10-04
> **snowpine said:**
> Hi there Kill-Switch, good question! :)

/home/yourname is your user folder, and it is the *only* folder you need to use for everyday tasks. You can't make changes outside this folder unless you use the "sudo" command (which you should only use if you know exactly what you're doing). 

In general, when you install new applications you should install them from the Ubuntu repository by using Add/Remove Programs, Synaptic Package Manager, or the command line ('sudo apt-get install firefox" for example). When you use one of these official tools, it automatically extracts and installs the application to the correct folder; you don't need to worry about it.

I would be wary of anyone instructing a new Ubuntu user to mess with anything in the /usr folder. 

To answer your other question, it doesn't matter whether you save a picture in /home/killswitch/pictures or /home/killswitch/videos or whatever... as long as you remember where you put it. ;)

I see, thank you for the reply. :)

I won't touch it or anything but in the future, I heard there's going to be a time for a user where he/she must compile a program from source if it's not in the repository. I'm curious to know why the instructions on "how to compile from source" implies that those .tar needs to be saved in usr/local/src. This is because I been wanting to dual boot other distros as well along with ubuntu and it seems like those distro doesn't have the certain repository that makes it easier to install.

---

### Post by starcannon on 2009-10-04
Removing my bad information, [please see post 7]("http://ubuntuforums.org/showpost.php?p=8053159&postcount=7") below. On my ubuntu install, /usr/local/src is empty. Anyway, if your interested in whats going on in those places, it is harmless, to list their contents.
```

ls /usr/local

```this command will let you see whats in /usr/local
Alternatively you could point your Nautilus File Browser to /usr/local as well.
[[IMG]http://img9.imageshack.us/img9/1499/usrlocal.th.png[/IMG]]("http://img9.imageshack.us/i/usrlocal.png/")

Don't be afraid to explore, just don't run commands or modify things you don't understand, unless you are wanting to adventure as well as explore :)

---

### Post by Kill-Switch on 2009-10-04
> **starcannon said:**
> If I remember right, when one installs to /usr/local/whatever that makes the application or other thing saved, available globally. On my ubuntu install, /usr/local/src is empty. Anyway, if your interested in whats going on in those places, it is harmless, to list their contents.
```

ls /usr/local

```this command will let you see whats in /usr/local
Alternatively you could point your Nautilus File Browser to /usr/local as well.
[[IMG]http://img9.imageshack.us/img9/1499/usrlocal.th.png[/IMG]]("http://img9.imageshack.us/i/usrlocal.png/")

Don't be afraid to explore, just don't run commands or modify things you don't understand, unless you are wanting to adventure as well as explore :)

Thank you very much. I wanted to learn more about GNU/Linux, it's becoming a hobby so I'm very curious about these things. Searching for these things doesn't come up with these types of information. I was thinking about buying a book that could explain these files and what not in details if it exists. I'm wondering where do you guys learn about these details?

---

### Post by starcannon on 2009-10-04
> **Kill-Switch said:**
> Thank you very much. I wanted to learn more about GNU/Linux, it's becoming a hobby so I'm very curious about these things. Searching for these things doesn't come up with these types of information. I was thinking about buying a book that could explain these files and what not in details if it exists. I'm wondering where do you guys learn about these details?
Try this book first, it's free and very good [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by inobe on 2009-10-04
it's actually /usr

when you install a source application using ==prefix=/usr will aloow the application to be setup in a user land rather than system.


so say if i wanted to compile midori from source, i would extract the tar and run the configure command, keep in mind' i am cd'ed into that folder

```
./configure ==prefix=/usr
```

when that's done

```
make
```

finally

```
make install
``` 

now if you have **checkinstall** "installed" you can run that command and it will create a backup pre-compiled .deb for later use, this will prevent having to re-compile the same application.

more information

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

---

### Post by inobe on 2009-10-04
> **Kill-Switch said:**
> I see, thank you for the reply. :)

I won't touch it or anything but in the future, I heard there's going to be a time for a user where he/she must compile a program from source if it's not in the repository. ** I'm curious to know why the instructions on "how to compile from source" implies that those .tar needs to be saved in usr/local/src.** This is because I been wanting to dual boot other distros as well along with ubuntu and it seems like those distro doesn't have the certain repository that makes it easier to install.

i missed one point.


tar balls should be saved in your documents somewhere you know.

there is no reason to put anything over there by the means of drag and drop.


one other point.

after running the checkinstall command you will notice it created the .deb and it will be located in /usr/local/src/deb

---

