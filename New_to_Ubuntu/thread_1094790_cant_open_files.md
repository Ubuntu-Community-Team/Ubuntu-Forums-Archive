---
title: "cant open files"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by ExplicitViper on 2009-03-13
i installed Counter-Strike Source and Steam. They are both on my desktop, but the icon has the orange lock on it. when i double click them, nothing happens.... how do i fix this?

---

### Post by taurus on 2009-03-13
Who is the owner of those two files (or could be directories)?  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by ExplicitViper on 2009-03-13
Root..... why isnt my normal (impeialviper) user the owner of the file? because i installed it under the user imperialviper

---

### Post by taurus on 2009-03-13
I don't know how to install it but you can change it back so you would be the owner now if you want.

```
sudo chown impeialviper:impeialviper /home/impeialviper/Desktop/filename
ls -la ~/Desktop
```

---

### Post by ExplicitViper on 2009-03-13
well i managed to change the Steam.desktop to the user imperialviper, but i am unable to change Counter-Strike Source.desktop or Counter-Strike Source.lnk. i keep getting the error: 

chown: cannot access `Source.desktop': No such file or directory

im guessing its because it has the space in it. but when i try to rename it on my desktop, it gives me the error:

Sorry, could not rename "Counter-Strike Source" to "CSS": Unable to rename desktop file

gahhh this is irritating


oh and that Steam.desktop, still dosnt open, i even changed the permissions to open as a exe file

---

### Post by taurus on 2009-03-13
If there is a space in the name, use the quotes, "filename with space".

Can you at least post the output of this command?

```
ls -la ~/Desktop
```

---

### Post by ExplicitViper on 2009-03-13
root@ubuntu:~/Desktop# ls -la ~/Desktop
total 28
drwxr-xr-x  2 imperialviper imperialviper 4096 2009-03-12 23:18 .
drwxr-xr-x 45 imperialviper imperialviper 4096 2009-03-12 22:51 ..
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc~
-rw-r--r--  1 root          root           295 2009-03-11 23:45 Counter-Strike Source.desktop
-rw-r--r--  1 root          root           883 2009-03-11 23:45 Counter-Strike Source.lnk
-rwxrwxrwx  1 imperialviper imperialviper  321 2009-03-12 23:18 Steam.desktop

---

### Post by ExplicitViper on 2009-03-13
now i have gotten

root@ubuntu:~/Desktop# ls -la ~/Desktop
total 28
drwxr-xr-x  2 imperialviper imperialviper 4096 2009-03-12 23:18 .
drwxr-xr-x 45 imperialviper imperialviper 4096 2009-03-12 23:27 ..
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc~
-rwxrwxrwx  1 imperialviper imperialviper  295 2009-03-11 23:45 Counter-Strike Source.desktop
-rwxrwxrwx  1 imperialviper imperialviper  883 2009-03-11 23:45 Counter-Strike Source.lnk
-rwxrwxrwx  1 imperialviper imperialviper  321 2009-03-12 23:18 Steam.desktop


but i am still unable to double click and run these files...

---

### Post by taurus on 2009-03-13
> **ExplicitViper said:**
> now i have gotten

**[COLOR="Red"]root[/COLOR]**@ubuntu:~/Desktop# ls -la ~/Desktop
total 28
drwxr-xr-x  2 imperialviper imperialviper 4096 2009-03-12 23:18 .
drwxr-xr-x 45 imperialviper imperialviper 4096 2009-03-12 23:27 ..
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc
-rw-r--r--  1 imperialviper imperialviper  196 2009-03-08 23:30 .asoundrc~
-rwxrwxrwx  1 imperialviper imperialviper  295 2009-03-11 23:45 Counter-Strike Source.desktop
-rwxrwxrwx  1 imperialviper imperialviper  883 2009-03-11 23:45 Counter-Strike Source.lnk
-rwxrwxrwx  1 imperialviper imperialviper  321 2009-03-12 23:18 Steam.desktop

but i am still unable to double click and run these files...

Are you in root's directory or are you in imperialviper's directory?

```
pwd
```

If you log in as root when you install or run those, then root would be the owner then.

---

### Post by ExplicitViper on 2009-03-13
/home/imperialviper/Desktop

everytime i go into termial i type Sudo bash   so i dont have to keep entering the password

---

### Post by taurus on 2009-03-13
Why do you have to keep entering your password unless you want to modify files outside your $HOME.  Then you would use sudo.  Again, you don't have to put sudo in front of a command if you are changing/moving/modifying/etc. stuff in your own $HOME.

```
cat Steam.desktop
```

---

### Post by scphan on 2009-03-13
yep, it's not good practice to sudo unless you have to, otherwise you run the risk of unnecessarily modifiying the wrong stuff

---

### Post by scphan on 2009-03-13
> **ExplicitViper said:**
> well i managed to change the Steam.desktop to the user imperialviper, but i am unable to change Counter-Strike Source.desktop or Counter-Strike Source.lnk. i keep getting the error: 

chown: cannot access `Source.desktop': No such file or directory

im guessing its because it has the space in it. but when i try to rename it on my desktop, it gives me the error:

Sorry, could not rename "Counter-Strike Source" to "CSS": Unable to rename desktop file

gahhh this is irritating


oh and that Steam.desktop, still dosnt open, i even changed the permissions to open as a exe file
can you find the executable for the software directly, go to its install directory and execute it from there

also do 'cat' for the counter strike files

---

