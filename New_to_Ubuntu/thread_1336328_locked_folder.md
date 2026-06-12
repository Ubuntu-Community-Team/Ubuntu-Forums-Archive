---
title: "locked folder"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by crowdedelevator on 2009-11-24
okay i downloaded files, and it had a lock on the icon, and i cant even friggin delete the thing!
wth do i do?!?!?!

---

### Post by cariboo on 2009-11-24
Please watch your language, this is a family friendly forum. 

You can run Nautilus (the file Manager) as root to manipulate locked files/directories. Press Alt-F2 and type:

```
gksudo nautilus
```

If you move any files to the trash can they will end up in root's trash can, they will be located in /root. Remember to empty roots trash can before closing nautilus.

---

### Post by crowdedelevator on 2009-11-24
> **cariboo907 said:**
> Please watch your language, this is a family friendly forum. 

You can run Nautilus (the file Manager) as root to manipulate locked files/directories. Press Alt-F2 and type:

```
gksudo nautilus
```If you move any files to the trash can they will end up in root's trash can, they will be located in /root. Remember to empty roots trash can before closing nautilus.

thanks, but it wouldnt show me the contents of...anything.  and sorry about language... thats why the shortening and noncursing words

---

### Post by crowdedelevator on 2009-12-06
> **crowdedelevator said:**
> thanks, but it wouldnt show me the contents of...anything.  and sorry about language... thats why the shortening and noncursing words
its been weeks and i have yet to have anyone tell me anything helpful.
when i open nautilus, no files show

---

### Post by Paqman on 2009-12-06
Right click on the icon and go to the permissions tab. Who owns the file and what do they have permission to do to it?

---

### Post by gdonwallace on 2009-12-06
Did you run nautilus as superuser (root)?  (the gksudo command will run commands in x-windows as root.

Another way of trying it is to open a terminal type su and enter your root user password.  But be very careful, if you do this, this transfers you to the root user, and you can delete your entire file system at this point.  

If you know what directory the file is in, type cd /<dir name> , it will take you to that directory and then type rm <file name> that should do it.

If that does not delete the file, paste the output of **ls -l**  This will list out the files with permissions and ownership showing.  That will help us help you.

---

### Post by crowdedelevator on 2009-12-06
> **gdonwallace said:**
> Did you run nautilus as superuser (root)?  (the gksudo command will run commands in x-windows as root.

Another way of trying it is to open a terminal type su and enter your root user password.  But be very careful, if you do this, this transfers you to the root user, and you can delete your entire file system at this point.  

If you know what directory the file is in, type cd /<dir name> , it will take you to that directory and then type rm <file name> that should do it.

If that does not delete the file, paste the output of **ls -l**  This will list out the files with permissions and ownership showing.  That will help us help you.

youre speaking clingon to  a starwars fan.
its a folder on my desktop. all i want to do is move it to my home folder but i cant

---

### Post by corncob on 2009-12-06
> **cariboo907 said:**
> Please watch your language, this is a family friendly forum. 

You can run Nautilus (the file Manager) as root to manipulate locked files/directories. Press Alt-F2 and type:

```
gksudo nautilus
```

If you move any files to the trash can they will end up in root's trash can, they will be located in /root. Remember to empty roots trash can before closing nautilus.

This opens Nautilus in root's folder, the only non-hidden item in it is root's desktop which has nothing in it.  Go down the menu and open File System and find YOUR home folder.
I myself have used
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```
which I got off this forum but have lost the reference to it.  I actually made a launcher for it on the task bar.  Right click on the task bar, select Add to Panel, then Custom Application Launcher, and Add.

---

### Post by wojox on 2009-12-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jtellerelsberg on 2010-03-25
Did Paqman's suggestion help you? I've had success with that method myself: 
1. right click on the folder
2. click Properties
3. go to the Permissions tab
4. set the File Access option to "Read and Write" for at least my owner account if not Group and Others as well
5. click "Apply Permission to Enclosed Files" button toward the bottom
6. click "Close" button.
Done.

Like I said, that's worked for me before, but not 100% -- for example I am now confronted with a DVD that my coworker burned for me on a Mac or Windows machine, I'm not sure which, and I am blocked from opening any of the folders or files on the disc, nor can I copy them to my harddrive, nor can I change the permissions. That's why I came to the forum to see if I could get help with that. I'll keep looking.

---

