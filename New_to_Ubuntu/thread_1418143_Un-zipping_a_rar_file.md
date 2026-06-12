---
title: "Un-zipping a rar file"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Durfa on 2010-02-28
Hello. I am very new to Ubuntu. I recently downloaded it. Everything is great so far. Although i have encountered a problem, i downloaded a .rar file and i can't seem to open it. I have tried looking for probgrams that people have suggested ex. Unrar, but i can't seem to find anything.


If anyone can help me it would be greatly appreciated.


Thank you.

---

### Post by yeats on 2010-02-28
> I have tried looking for probgrams that people have suggested ex. Unrar, but i can't seem to find anything.

unrar is probably the most straightforward... where are you looking?  At a terminal you can do:

```

sudo apt-get install unrar
```

and then 

```
unrar *filename.rar*
```

where *filename.rar* is the file you're trying to decompress.  You'll have to be in the directory where the file lives to run the command successfully, either that or name its full directory path.

---

### Post by sisco311 on 2010-02-28
Go to System -> Administration -> Synaptic Package Manager search for the unrar package & install the non-free version. You may have to enable the multiverse repository (Synaptic -> Settings -> Repositories).

---

### Post by Durfa on 2010-02-28
Okay. I have gone into a Terminal and typed in what you told me.

Once i type that it comes up saying

> [sudo] password for matt:

Thats pretty self explanatory, its asking for my password, but it wont let me type anything:???:

---

### Post by theozzlives on 2010-02-28
"RAR" works with the Archive Manager, it's in the repos.

---

### Post by Martin Marshalek on 2010-02-28
```
sudo apt-get install p7zip-full
```

This will allow you to unzip virtually anything and you can just do it by right clicking like you usually would, no command line necessary (though if you're into that sort of thing you can).

---

### Post by shihkster1015 on 2010-02-28
go to terminal and type "sudo apt-get install rar"
for the password part, you technically "are" typing
it's just ubuntu's safety feature, SO others can't guess how many letters are in your pass

---

### Post by Martin Marshalek on 2010-02-28
It won't show what you're typing as a security measure (some of this can be annoying at first but it pays off). Just run the command and type your password when it prompts for it with no errors and then hit enter.

---

### Post by webtechquery on 2010-02-28
Hi there
Simply double click on the rar file, and it will be automatically opened in Archive Manager for GNOME i.e. File Roller.
If it wont work, simply goto System -> Adminitrative Tasks -> Synaptic Package Manager
And search for rar. You will find some of the rar software over there. Simply install one and u will get what u want.

Thanx

---

### Post by 3rdalbum on 2010-02-28
Once you've installed the 'unrar' package, Ubuntu's archive manager will automatically use it when needed.

---

### Post by shihkster1015 on 2010-02-28
7z's also a really good program to unpack. 
It supports multiple formats
[www.7-zip.org]("http://ubuntuforums.org/www.7-zip.org")

Sorry, windows only

---

### Post by shihkster1015 on 2010-02-28
i would say that using this code
```
 sudo apt-get install rar
```
is the easiest way

---

### Post by d4_user on 2010-02-28
after doing
"sudo apt-get install unrar"
don't you have to do 
"make install"

?

---

### Post by shihkster1015 on 2010-03-01
> **d4_user said:**
> after doing
"sudo apt-get install unrar"
don't you have to do 
"make install"

?

Make install is where you compile a downloaded file. When you do sudo apt-get install XX, ubuntu does everything for you, so make install is not necessary

---

### Post by cascade9 on 2010-03-01
> **shihkster1015 said:**
> 7z's also a really good program to unpack. 
It supports multiple formats
[www.7-zip.org]("http://ubuntuforums.org/www.7-zip.org")

Sorry, windows only

Actually...

> **7-Zip** works in Windows 7 / Vista / XP / 2008 / 2003 / 2000 / NT / ME / 98. There is a port of the command line version to Linux/Unix.

[http://www.7-zip.org/](http://www.7-zip.org/)

I've used p7zip on debian/ubuntu more than once. Mostly I'm using Xarchiver now so I dont bother anymore, p7zip seemed to work as well as anything. 

BTW OP, Xarchiver works fine with with .rar files once you've got the unrar packages.

---

