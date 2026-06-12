---
title: "file hierarchy in the terminal and the operation of the terminal"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by tbrownarcher on 2010-10-31
Ubuntu 10.10

I'm sorry, I'm starting to embarrass myself because of the # of questions i have but I have no other option that I know of ...  

I want to know the heirarchy of the system. 

In the gui under places, apparently my home folder (directory) is nate. 

So, trying to get to the download folder while in terminal and in the home folder I have typed several things here they are ..... cd nate , cd /nate , cd /downloads , cd downloads , cd home cd /home.  Nothing works ....

Also when the terminal first opens what directory/folder is it in ?  It reads like this .... nate@home2:~$ I don't know where that is.

---

### Post by papibe on 2010-10-31
To go to your home:
```
$ cd
```
To list the files in the actual directory:
```
$ ls
```
You'll see Download, Music, Pictures, etc. To go to Music:
```
$ cd Music
```
To go back to your home directory:
```
$ cd
```
If by any reason you got lost and don't know where you are, use pwd to show the actual dir:
```
$ pwd
/home/nate
```
I hope it helps.

---

### Post by peculiar penguin on 2010-10-31
> Nothing works ....Read up on the difference between relative and absolute paths, and remember that file and directory names are case sensitive in Linuxland.

---

### Post by tbrownarcher on 2010-11-01
> **papibe said:**
> To go to your home:
```
$ cd
```
To list the files in the actual directory:
```
$ ls
```
You'll see Download, Music, Pictures, etc. To go to Music:
```
$ cd Music
```
To go back to your home directory:
```
$ cd
```
If by any reason you got lost and don't know where you are, use pwd to show the actual dir:
```
$ pwd
/home/nate
```
I hope it helps.

yes it helps ..... things there i did not know ...

---

### Post by tbrownarcher on 2010-11-01
> **papibe said:**
> To go to your home:
```
$ cd
```
To list the files in the actual directory:
```
$ ls
```
You'll see Download, Music, Pictures, etc. To go to Music:
```
$ cd Music
```
To go back to your home directory:
```
$ cd
```
If by any reason you got lost and don't know where you are, use pwd to show the actual dir:
```
$ pwd
/home/nate
```
I hope it helps.

yes it helps ..... things there i did not know ... thanks,
Na

---

### Post by tbrownarcher on 2010-11-01
> **peculiar penguin said:**
> Read up on the difference between relative and absolute paths, and remember that file and directory names are case sensitive in Linuxland.

Yes! Thanks!  I did forget the case sensitive thing in linux.


thanks,
Nate

---

### Post by oneNF on 2010-11-01
free ubuntu handbook
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Verbeck on 2010-11-01
everything is  under** /**
your home folder is  **/home/nate**
the downloads **/home/nate/Downloads**

*but since the terminal open in your home folder you can do **cd Downloads**

hope this helps

---

### Post by Drenriza on 2010-11-01
> **tbrownarcher said:**
> Ubuntu 10.10

I want to know the heirarchy of the system. 

Also when the terminal first opens what directory/folder is it in ?  It reads like this .... nate@home2:~$ I don't know where that is.

Absolute path
**cd** **/home/nate/Desktop/pictures/dogs**

Relative path.
If you open your terminal and type **pwd** you can see you start in **/home/nate** if you then type **cd Desktop/pictures/dogs**

**cd** - change directory
**cd ..** - jump one folder back

The system hirachi
type **man hier 7** and enjoy

---

