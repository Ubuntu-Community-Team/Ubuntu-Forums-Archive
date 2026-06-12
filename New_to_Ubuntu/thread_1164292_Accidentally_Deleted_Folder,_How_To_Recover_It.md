---
title: "Accidentally Deleted Folder, How To Recover It?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Auzzie666 on 2009-05-19
Hey, while trying to remove a theme I installed, I accidentally deleted the entire theme folder instead! lol

This is what went down:

root@ubuntu:/home/auzzie# sudo rm -rf SlicknesS /usr/share/themes

as you can see, it removed the entire themes folder, not just the 'slickness' folder.

Is there any way I can get this back? I basically lost all my themes right there, would be great if I can recover them, or just get the default ubuntu theme pack back at the very least.

Thanks!

---

### Post by PocketDog on 2009-05-19
If [this](https://help.ubuntu.com/community/DataRecovery) doesn't help it's still a useful bookmark :-)

---

### Post by Auzzie666 on 2009-05-19
Seems a little over my head :/

---

### Post by cariboo on 2009-05-19
You may want to have a look at the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") package that is in the repositories. It should help you restore the missing directory.

---

### Post by starcannon on 2009-05-19
+1 for Testdisk and Photorec.
For sure the price of recovering is going to require some homework, but if the data is important, then the homework is worth it. In addition to the page PocketDog posted I will post [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) .

Read PocketDog's page first, if you simply accidentally deleted a a folder, and have a healthy hard drive then its probably advisable to skip to [https://help.ubuntu.com/community/DataRecovery#Photorec](https://help.ubuntu.com/community/DataRecovery#Photorec) .

I've used Photorec twice now, and while I'm no wiz at it yet, I can say that its not terribly difficult to figure out.

Oh be sure to look at TestDisk's undelete files tutorial as well I should think: [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)

GL

---

### Post by Auzzie666 on 2009-05-19
Of the links provided, I was leaning toward testdisk, however Im not sure which version I need, and sudo apt-get isnt having any of it.

---

### Post by Mornedhel on 2009-05-19
Mmh ?

apt-cache show testdisk works for me (in Jaunty). sudo apt-get install testdisk should work.

---

### Post by Auzzie666 on 2009-05-19
Ive got testdisk installed, but I cant seem to locate the directory where the file was deleted within testdisk. I have a windows partition as well for cad software

---

### Post by scorp123 on 2009-05-19
> **Auzzie666 said:**
> root@ubuntu:/home/auzzie# sudo rm -rf SlicknesS /usr/share/themes  That's what you get for being logged in as "root" :D

And in case you were not told before ...
**[COLOR="Red"]DO NOT WORK AS "root" !![/COLOR]**

You now know why :D

Seriously though ... you should check your syntax before you issue dangerous commands. Being "root" and wanting to use "rm" => dangerous. Better check the manual first if you really got the syntax right:
```
man rm
```

> **Auzzie666 said:**
>  ... it removed the entire themes folder, not just the 'slickness' folder.  Of course it did. Because that's exactly what you told it to do. Know thy syntax!! ;)

> **Auzzie666 said:**
>  Is there any way I can get this back? Honestly, I would not bother with this. Why not just reinstall the themes? e.g. ```
sudo apt-get --reinstall install gnome-themes
sudo apt-get --reinstall install tropic-look
sudo apt-get --reinstall install human-theme
sudo apt-get --reinstall install gnome-icon-theme
sudo apt-get --reinstall install hicolor-icon-theme
```
.. and so on.

This should pull the default OS themes (human, hicolor) from the Internet repos, plus add a few extra themes (gnome-themes, tropic); thus restoring the default theme location "/usr/share/themes"

Any extra themes that you may have downloaded and installed by hand (via tar.gz file) should then be easy to add again once all the OS defaults are back.

Honestly ... I'd do it this way and not bother with restoring the files. Restoring would take waaay longer then just simply reinstalling the themes again.

---

