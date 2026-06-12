---
title: "Some basic knowledge"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by OllieGab on 2008-12-11
As a total beginner with Linux and Ubuntu I seem to lack some basic skills. For instance, when trying to save or move certain files I sometimes get an error message saying I don't have permission to carry out the actions.
Surely, I as the owner of my computer, would like to be able to do all that is needed. There must be some setting or likewise that will give me total control of my computer and operating language?

Ollie

---

### Post by halitech on 2008-12-11
physically you may own the hardware but when it comes to the OS, you only "own" your home directory, root owns the rest of the system. In order to do anything outside your home folder, you need to do it as sudo. This is to prevent us from doing something stupid to the OS.

---

### Post by Duck2006 on 2008-12-11
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by halitech on 2008-12-11
> **Duck2006 said:**
> [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

thanks for the link, I knew there was one around somewhere, just couldn't think where and didn't want to go digging for it :)

---

### Post by Bloch on 2008-12-11
bin    etc         initrd.img.old  mnt       root  tmp          vmlinuz
boot   home        lib             opt       sbin  usr          vmlinuz.old
cdrom  initrd      lost+found      proc      srv   var
dev    initrd.img  media           Recycled  sys   $VAULT$.AVG



That's all the directories I have. Each branches out to subdirectories. Under /home there is onlt one user: bloch

So /home/bloch is the only directory (with all subdirectories) where I can move and delete as I please.

If you open a terminal and enter the command
sudo nautilus
(your password will then be requested) 
then in the window that opens you can move and delete files as you please, as you have super-user powers.
IT IS DANGEROUS TO WORK AS SUPER-USER
and there is rarely a need to access the system files directly by this method.

---

### Post by mgmiller on 2008-12-11
> If you open a terminal and enter the command
sudo nautilus
(your password will then be requested) 
then in the window that opens you can move and delete files as you please, as you have super-user powers.

Plese do not use sudo nautilus.
99 times out of 100 you have no problems, but that 1 in 100 is really bad.

If you want to run nautilus as root use this code:
```
gksu nautilus
```

sudo is only for terminal, non graphical things.

gksu is for running graphical applications with root permissions.

```
gksu nautilus
```

will give you total control to move, copy, erase, etc. ANYTHING on the drive.
It also makes it possible to really frak your system if you do something wrong.

Please be careful with your new super powers......

---

### Post by OllieGab on 2008-12-11
Thanks very much! That really helped. I have a feeling this is going to be a slow (but pleasant) journey to "linux-user-ship".
The reason I tried to copy a file from my Documents folder to the home folder of python 2.5 was that, when trying to open a just saved text file (as a .py file, just trying it out) I was not able to open it, then beleiving that the reason was that it had to reside in the same folder as python itself. I don't really believe that is needed but I had to try it as I got an error message trying to open by typing: python filename.py
Ollie

---

### Post by mkvnmtr on 2008-12-11
There is not much you can't do to your system. My problem is remembering how I did it last time. Then if I have to search for a thread like this it takes me a couple of days to get it done. Now every time I learn how to do something new I make a note in Tomboy so I can do it again. I think I should try zim and make a wiki of all this stuff.

---

### Post by Michael.Godawski on 2008-12-11
> There is not much you can't do to your system. My problem is remembering how I did it last time. Then if I have to search for a thread like this it takes me a couple of days to get it done. Now every time I learn how to do something new I make a note in Tomboy so I can do it again. I think I should try zim and make a wiki of all this stuff.

Just popping in. 
I am from the Education Focus Group from the BT.
You can add your wish, your idea for a course, article or essay dealing with Ubuntu Essentials or advanced stuff to the sticky in this Absolute Beginner Forum.

thx
Michael

---

### Post by cmay on 2008-12-11
> **OllieGab said:**
> Thanks very much! That really helped. I have a feeling this is going to be a slow (but pleasant) journey to "linux-user-ship".
The reason I tried to copy a file from my Documents folder to the home folder of python 2.5 was that, when trying to open a just saved text file (as a .py file, just trying it out) I was not able to open it, then beleiving that the reason was that it had to reside in the same folder as python itself. I don't really believe that is needed but I had to try it as I got an error message trying to open by typing: python filename.py
Ollie

i do not get it. why you want to copy a python file from home to python folder. if it is a script you are trying out then create a folder called scripts in your home folder and save those things there . then invoke them by opening the terminal and typing /home/scripts/name_of_file.py  but it only works after you made it an executeable file by typing chmod 755 ./name_of_file.py . sorry if i not understand the reasons or the statement correctly but it is a very bad idea to being copy stuff from your home folder into other folders in the system that are not really ment to hold ohter files than those that belongs to the program it self.

if a file in the home folder is a script that may be bash perl or python and it has the executable flags set right then just open the terminal and type ./filename and the it should run.  and you can also make a hidden folder for these scripts if you use them a lot and then make an alias for them in your bashrc.

---

### Post by bodhi.zazen on 2008-12-11
If you are new to ubutnu, the wiki has some nice tips as well :

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by OllieGab on 2008-12-11
No, I realise what you are saying and I totally agree. The thing was that I was trying out python (I am a total newbie on that as well, as you may have worked out!) and as I couldn't open up a file - from python - that I had written earlier (only a couple of lines of simple code for testing purposes) I thought that maybe the written .py file had to reside in the same folder as python itself.
Which it doesn't, as I have discovered by now!

---

### Post by rhcm123 on 2008-12-11
> **OllieGab said:**
> Thanks very much! That really helped. I have a feeling this is going to be a slow (but pleasant) journey to "linux-user-ship".
The reason I tried to copy a file from my Documents folder to the home folder of python 2.5 was that, when trying to open a just saved text file (as a .py file, just trying it out) I was not able to open it, then beleiving that the reason was that it had to reside in the same folder as python itself. I don't really believe that is needed but I had to try it as I got an error message trying to open by typing: python filename.py
Ollie

I will warn you, and i have learned this the hard way, simple spelling mistakes or miscalculations can instantly ruin your computer. I learned that the hard way when i was making my own configuration files. I copied it from the net, modified it appropriatley, and copied it to what i thought was the configuration directory. 

Turns out, instead of going to /etc, i acidentally went to /bin and overwrote the executable. Which killed several dependancies as well. Which killed the computer. Very sad.


Linux was designed so that basic users (like you) can only modify their own files, not system files. Why? For security reasons, so that a hacker with basic access can't destroy the system, or so that an inept user cant go around deleting files that might turn out to be important. like my sister, who somehow got root access and deleted vmzlinuz. Very bad.


Also, about your problem with your python file. They do not have to reside in the same folder, they just have to be made executable. (There are varying file permissions/ownerships in linux, and this is one of them.) To make it executable, either right click it, go to permissions, and hit make executable, or do the following:

```
sudo chmod 755 /file/directory/
```

---

### Post by rhcm123 on 2008-12-11
Oh, and by the way, another quick note.

Files in the various /home directories are the only ones a user can freely modify.

For instance, george can modify files in /home/george, bill can in /home/bill, etc.
Thats because the creator of a file owns it, and it's permissions by defualt. (this can be changed, of course.

Everything else above this, such as /etc, /bin, /mnt, /dev, /(root), and even /home is owned by root. Root is called the "super user", and, can, in effect, delete the entire computer. Root owns all files and can modify every other file, and is the core (or root) of the system struture. It's essentially god.

Now, I would not suggest randomly changing the ownership of files, or the permissions randomly, or all to you. If you make yourself own everything, and then somebody breaks into your account... BANG. They have essentially root permissions. Also, certain files are supposed to be owned by certain people. (Like the processes files in /etc/init.d)

I would not suggest using root until you learn a little more. But you can exeriment  more safely with the sudo command, which grants the command you write after it root access.

---

