---
title: "What do I do?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by jermza on 2010-12-27
I've been struggling with this for an hour.  I'm a newbie and have absoutely no idea what to do.

All I'm trying to do is install Gimp's CMYK Separator plugin and don't know how to copy as per the following instruction.  Nothing I'm doing works.

> **Installing Separate manually **

 Once you have obtained the [source tarball]("http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz"), you can unpack it using the usual tar command: 
 tar xvf separate-VERSION.tar.gz
where VERSION would be the version of Separate plug-in (0.1 at the time of this writing). 
Copy a file called *separate* (located inside the extracted *separate* directory) into Gimp's plug-in directory: 
 cp separate/separate /usr/lib/gimp/GIMPVERSION/plug-ins/
where GIMPVERSION would be the major version number of Gimp (2.0 at the time of this writing). 
When you start Gimp the Separate will be recognized and reachable through *Image > Separate* menu. 
[B] 
[/B]

---

### Post by howefield on 2010-12-27
Where are you getting stuck ?

It looks like only two commands which need to be run, are you having trouble with the second one ?

Try using the cd command to navigate into your extracted separate folder and you'll probably need to precede the copy command with sudo to write to that folder.

---

### Post by jermza on 2010-12-27
> **howefield said:**
> Where are you getting stuck ?

It looks like only two commands which need to be run, are you having trouble with the second one ?

Try using the cd command to navigate into your extracted separate folder and you'll probably need to precede the copy command with sudo to write to that folder.

That's the thing.  I don't know what to do.  What does "Try using the cd command" mean?

---

### Post by Trandre on 2010-12-27
i am not a wizard in this myself, but cd, means Change Directory and can be used as in Ms-dos.

type:
famfem@ubuntu:~$ cd /usr
famfem@ubuntu:/usr$ cd lib

and so on until you are in your directory

---

### Post by amsterdamharu on 2010-12-27
Ok, no problem. You might get used to the terminal later. There are some simple tutorials for using the terminal out there but for your current problem:

copy the separate-gimp2-0.3_linux.tar.gz file to your desktop

press alt + F2, type gnome-terminal and click run.

This will get you in a black screen where you can type in commands.  Copy and paste the following commands in the terminal (black window).
```
cd ~/Desktop
tar xvf separate-gimp2-0.3_linux.tar.gz
sudo cp separate-0.3_linux/separate /usr/lib/gimp/2.0/plug-ins/
```

I assume you have gimp 2.0, if anything goes wrong then copy and paste the entire output of the terminal here and post it. 

To copy and paste from/to the terminal you can use your mouse control + c and control + v don't work in the terminal.

---

### Post by howefield on 2010-12-27
Double click on your downloaded file and extract to your home folder.

Then run the following command from a terminal, (Applications > Accessories > Terminal)

```
sudo cp separate-0.3_linux/separate /usr/lib/gimp/2.0/plug-ins/
```

---

