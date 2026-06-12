---
title: "chmod to make a file/folder undeletable"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by LeDechaine on 2009-11-10
I've ran into this problem once, and here I am again, because I don't know how I got this chmod or nautilus permissions interface config to work.

Seems to me that nautilus is buggy, i.e.: When you change the permissions of a file, you have to restart nautilus, or re-open your session, or completely restart the computer to enable the permissions to take effect, because nautilus seems to just don't care about the permissions and you can easily trash a "sudo chmod 700" file. It makes no sense, but hey, looks like that's how it works anyway.

So, if it's not the case, what am I doing wrong. I just want to make a file in my home folder undeletable (well, deletable only by root).

Or, if it's not possible, make a folder in my home directory undeletable (deletable only by root), i'll just put the file in there. (This was how I got it to work the last time, a question of parent folder permissions or whatever..)

---

### Post by falconindy on 2009-11-10
A file with permissions of 700 is fully accessible for read, write, and execute by the owner **only**. Nautilus "doesn't care" about the permissions because I'm guessing you're still the owner. Because deletion is so closely tied to the ability to write, making a directory that can't be deleted but still writeable is going to be difficult. If you only plan on putting some files in the folder and leaving it, then just make it immutable like so:
```
sudo chattr +i /directory
```
the 'i' flag can only be set and cleared by a privileged user, and no one (not even root) will be able to write/delete.

Maybe you should describe what your end goal is -- there may be another solution.

---

### Post by Terry of Astoria on 2009-11-10
I tried the following:
```
me@m64:~$ sudo mkdir testy
[sudo] password for me: 
me@m64:~$ rm testy
rm: cannot remove `testy': Is a directory
me@m64:~$ touch testy/test
touch: cannot touch `testy/test': Permission denied
me@m64:~$ sudo touch testy/test
me@m64:~$ rm testy/test
rm: remove write-protected regular empty file `testy/test'? y
rm: cannot remove `testy/test': Permission denied
me@m64:~$ 

```
  I think if you create a file as root then no-one can delete it except root, because it belongs to root.
  If you make a file as your user, and then chmod it 700 then you are the only one able to change it. No one else. To make it unmodifiable by your user, you will have to chmod 400 I think. Or perhaps 000.

---

### Post by falconindy on 2009-11-10
> **Terry of Astoria said:**
> I tried the following:
To make it unmodifiable by your user, you will have to chmod 400 I think. Or perhaps 000.
A folder with 000 permissions can't even be cd'ed into. 500 would give read and execute permissions only to the owner.

---

### Post by Zoot7 on 2009-11-10
> **LeDechaine said:**
> Or, if it's not possible, make a folder in my home directory undeletable (deletable only by root), i'll just put the file in there. (This was how I got it to work the last time, a question of parent folder permissions or whatever..)
```
sudo chown -R root:root <directory name> && sudo chmod -R 700 <directory name>
```
That'll do it for you.

Also here's a great detailed read explaining the permissions
[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

---

### Post by alphaniner on 2009-11-10
> I just want to make a file in my home folder undeletable (well, deletable only by root).

Then make it owned by root:

```
sudo chown root\: *file*
```

But then you will have to use sudo/gksudo to modify it.

---

### Post by LeDechaine on 2009-11-10
Hey hey, thanks for the fast replies!
Didn't knew about the "chattr +i" command, interesting, thanks!

Hmm.. I got it.

```
ledechaine@QuadDamage:~$ sudo mkdir Bunker2
ledechaine@QuadDamage:~$ rmdir Bunker2
**(see, folder deleted even if root created it)**
ledechaine@QuadDamage:~$ sudo mkdir Bunker3
ledechaine@QuadDamage:~$ sudo touch Bunker3/test
ledechaine@QuadDamage:~$ rm Bunker3/test
rm: détruire un fichier protégé en écriture fichier vide standard `Bunker3/test'? y
rm: ne peut enlever `Bunker3/test': Permission non accordée
**(English: permission denied, can't delete file in "Bunker3")**
ledechaine@QuadDamage:~$ rm -rf Bunker3
rm: ne peut enlever `Bunker3/test': Permission non accordée
**(English: can't delete Bunker3 folder: can't delete "test" in it.)**
ledechaine@QuadDamage:~$
```

Long story short: if root creates a folder and it's empty, anyone (?) can delete it.
But if root adds something in it, the folder can't be deleted.
Looks like there's a difference between the file and folders permissions...

Another test:
```
ledechaine@QuadDamage:~$ sudo touch myself
ledechaine@QuadDamage:~$ rm myself
rm: détruire un fichier protégé en écriture fichier vide standard `myself'? y
**(English: Delete? Yes. And then the file is gone!)**
ledechaine@QuadDamage:~$ 
```

Well, maybe it's because [ubuntu stores the sudo password for 5 minutes]("http://ubuntuforums.org/showthread.php?t=229309")

Trying again:
```
ledechaine@QuadDamage:~$ sudo touch myself
[sudo] password for ledechaine: 
ledechaine@QuadDamage:~$ sudo -K
**(Forget the password)**
ledechaine@QuadDamage:~$ rm myself
rm: détruire un fichier protégé en écriture fichier vide standard `myself'? y
**(English: Delete? Yes.)**
ledechaine@QuadDamage:~$
**(And just to be sure...)**
ledechaine@QuadDamage:~$ sudo mkdir Bunker2
[sudo] password for ledechaine: 
ledechaine@QuadDamage:~$ ls
**(it's there.)**
ledechaine@QuadDamage:~$ sudo -K
ledechaine@QuadDamage:~$ rmdir Bunker2
ledechaine@QuadDamage:~$ ls
**(it's gone.)**
```

Conclusion: Whatever the permissions of a file, if it's in a 755 folder like your home directory, it doesn't count, anyone will **still** be able to delete it. Same thing for a folder, except that for the folder, you just have to add something in it!

And **finally**:
```
sudo chmod 700 Bunker
```
And now, you can't delete or "cd" into this folder, except as root! (Exactly what I wanted)

Thanks everyone!

---

### Post by doas777 on 2009-11-10
actually if I recall correctly, ubuntu requires that only you be able to write to your home (and that it must be owned by you). at least I though i got a message saying so a few months ago when playing with service users

---

### Post by coodtec on 2010-08-26
sudo chmod -fR 677 /home/abc

This one work with me.

---

