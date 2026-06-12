---
title: "changing ownership"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Islewolf on 2010-01-14
Very new to Linux, and running Ubuntu after my laptop decided to break Windows.  

Anyway, my question is I have some files on an external HDD that I would like to transfer to my laptop, but I am being told that I can't because I am not the owner of the "File System" drive that I want to add them to.  

How can I change ownership so that I can do that without messing up my system?  Current owner is root.

Thanks in advance for the help.  I have enjoyed the learning experience that I have had here in the forums.

---

### Post by audiomick on 2010-01-14
Where are you trying to move the files to? It seems strange that anywhere that you would normally be wanting to move to, e.g. your home folder, should not belong to you the user.

---

### Post by ~sHyLoCk~ on 2010-01-14
What filesystem is the exernal HDD in? I think ntfs-3g will solve your problem if it's ntfs, else the command you are looking for is "chown".

---

### Post by xeross on 2010-01-14
You can either change ownership by chowning the external hdd

```
sudo chown -R username:username /path/to/hdd
```

Or you can start the file browser as root which allows you to copy them over

```
sudo nautilus
```

---

### Post by Islewolf on 2010-01-14
I am trying to move the file from the external HDD to the main HDD of the laptop.  the file system on the external HDD is ntfs.  The name of my computer's HDD is named "File System".  Is that my home HDD?

---

### Post by unmole on 2010-01-14
By 'Filesystem' i think he means / as that is what you see when you click 'Computer' in 'Places'

Do not I repeat DO NOT even think of changing the owner ship of 'Filesystem'. I guarantee you, you WILL break your system. If we are clear with, lets move to copying files. There are somethings you should know/consider.


[LIST=1]
[*]/ (Filesystem) is not meant to store user files.
[*]The place to do that would be your 'Home Folder' as you see in the 'Places' menu.
[*]For some reason you STILL want to copy files into / type the following in the terminal (Applications>Accessories> Terminal)
[/LIST]
 ```
 gksu nautilus 
```You will be asked for your password and a new window will be opened and from this window alone, you will be able to paste files into /. But keep in mind, your 'Home Folder' is where you should actually keep your files.


Hope that helps.


P.S. See this link for more [http://www.comptechdoc.org/os/linux/manual2/rootdir.html](http://www.comptechdoc.org/os/linux/manual2/rootdir.html)

---

### Post by Morbius1 on 2010-01-14
You don't want to change ownership of "File System" on your laptop. Try transfering the data from the external HDD to some folder in your home directory. 

/home/Islewolf/Documents or something

---

### Post by Morbius1 on 2010-01-14
Sorry, simultaneous posts it seems. 

unmole was by far more eloquent than I.

---

### Post by unmole on 2010-01-14
> **xeross said:**
> You can either change ownership by chowning the external hdd

```
sudo chown -R username:username /path/to/hdd
```Or you can start the file browser as root which allows you to copy them over

```
sudo nautilus
```

IMHO it is good practice never to use sudo for graphical applications.
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by audiomick on 2010-01-14
> **Islewolf said:**
> I am trying to move the file from the external HDD to the main HDD of the laptop.  the file system on the external HDD is ntfs.  The name of my computer's HDD is named "File System".  Is that my home HDD?
That's why I asked "where to":D I think you are just trying to put things where they shouldn't be going. What unmole and Morbius1 wrote is correct.

If it is "just" data files you are trying to move, put them in your home folder. If it is something you know for sure has to be somewhere else, put it there with
```
gksu nautilus
```
but be really sure about what you are doing.

Do not change any permissions on the file system of your laptop. There is usually no reason to do so, and lots of very good reasons not to.

edit +1 unmole on the tip about not using sudo for graphical applications. I would have put in the same link to explain.

---

### Post by caravel on 2010-01-14
"File System" is the icon that Nautilus uses to refer to /

You should be able to create a directory in your ~ and copy the files there.  Or you can mount the NTFS partition and use that as is?

---

### Post by Islewolf on 2010-01-14
Thanks to all that posted.  Yes, I wanted to move files into the Home directory, but obviously I didn't really know what I meant until it was said.  Thanks again.

---

