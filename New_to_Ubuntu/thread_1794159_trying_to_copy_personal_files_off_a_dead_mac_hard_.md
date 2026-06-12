---
title: "trying to copy personal files off a dead mac hard drive via usb drive reader on unbun"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by sdd125 on 2011-06-30
trying to copy personal files off a dead mac hard drive via usb drive reader on unbuntu.  

The drive is a fujitsu 160gb hdd formatted for mac
the drive reader is a apricorn multi reader via usb
the ubuntu computer is a nokie booklet 3g running ubuntu 10.10


the problem is i do not have permissions nor am i the owner of this device according to ubuntu when i try to click on the documents folder.

I have been trying all day getting advice everywhere with no success please help.

---

### Post by fabricator4 on 2011-06-30
> **sdd125 said:**
> trying to copy personal files off a dead mac hard drive via usb drive reader on unbuntu.  

The drive is a fujitsu 160gb hdd formatted for mac
the drive reader is a apricorn multi reader via usb
the ubuntu computer is a nokie booklet 3g running ubuntu 10.10


the problem is i do not have permissions nor am i the owner of this device according to ubuntu when i try to click on the documents folder.

I have been trying all day getting advice everywhere with no success please help.

Open the file manager in SU mode:

```
gksudo nautilus
```

You should now be able to access the drive, if it's not pooched.  Make sure you exit from the superuser file manager when you're finished, and be careful.  It's possible to seriously break your system if you move or delete the wrong things.

Chris.

---

### Post by sdd125 on 2011-07-01
Hi, I entered the command and was able to copy some files from my documents, I can not get the files off my desktop or other areas however.  Is the command to leave super user mode ' exit ' ?
I have tried rebooting and entering the super user command you gave and I still cant get items off the desktop or other areas. when I entered the super user command you gave it starts spitting out all these errs in terminal mode, it seems hinky but I did get some of the my document files, I just want to get the rest and I'm so close, thank you for your help Chris.

---

### Post by fabricator4 on 2011-07-01
> **sdd125 said:**
> Hi, I entered the command and was able to copy some files from my documents, I can not get the files off my desktop or other areas however.  Is the command to leave super user mode ' exit ' ?
I have tried rebooting and entering the super user command you gave and I still cant get items off the desktop or other areas. when I entered the super user command you gave it starts spitting out all these errs in terminal mode, it seems hinky but I did get some of the my document files, I just want to get the rest and I'm so close, thank you for your help Chris.

Hi, no that instruction should have opened the grahical file manager with SU privileges. I'm not sure how you managed to copy files if not with the file manager.

Try this: Hold the <alt> key and press <F2>.  You should get a dialog to run a command.  Just type the same command "gksu nautilus" into the dialog and click the "Run" button.  It should then open the file manager (Nautilus is the file manager in Ubuntu) and you should be able to use it to copy your files.

Chris

---

### Post by sdd125 on 2011-07-01
Hi Chris, I'm not sure how I did either it only worked one time, i just typed the command you gave me in the first reply in terminal, it asked for my password, i typed it in and it opened a window i used to browse to my docs, but i could see in terminal it was spitting out errs saying failed this and that, i tried rebooting after i copied some word files, but no luck.  I just tried your new instructions and it says 'error while copying 123.doc. there was an error copying the file into home/user1/Desktop. *then when I click show more details* Error opening file: Permission denied.

---

### Post by sdd125 on 2011-07-01
Can anyone please help?

---

### Post by sdd125 on 2011-07-01
so to be clear before chris helped me, i couldnt even view the folders under Users/mymacbook now i can view documents and desktop etc...but can't copy or move them. im getting closer....

---

### Post by sdd125 on 2011-07-01
what i've learned.

I used both commands Chris gave me, it works, all though it is a bit retarded and unclear why....

Copy and paste, no permission

same response when I drag and drop.

BUT

if I use the right click send to, it works, but only if i send it to certain locations, desktop and home.....

So this will take a while but ill get my info.

---

### Post by collisionystm on 2011-07-01
I do not know how handy you are with terminal... but.... You can try to copy your files from there.

Open Terminal

Switch to root terminal

```
sudo bash
```

if the drive is connected via USB, browse to it

```
cd /media/<drive>
```

change to your home directory on the MAC that has your files

```
cd /destination
```

Check your MAC drive permissions

```
ls -lh

```
Try to change the permissions ( not sure if this will work )

```
chmod -R 770 *
```

Now 

```
cp -R * /destination to save to
```

---

### Post by Lkm on 2011-07-01
If you don't 'own' the files, you could try changing the owner of the relevant files using the command  'chown'.

If you navigate to the correct directory in the command line then
```
sudo chown root file_or_folder_name 
```
The above command would change the owner of a file or folder to root.

After that you may use
```
sudo chmod 777 file_or_folder_name 
```
This changes the file permissions to 'all', so you may copy them  anywhere.

After that you can either copy using the command line or the user interface.


[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by collisionystm on 2011-07-01
For folders...

sudo chown -R root /folder

You must include the -R for recursive.

For file permissions, if changing it to root as the owner, you need only do 

sudo chmod -R 700


Sorry, don't mean to be a pain, just thought it could use a little perfection =/

---

### Post by Lkm on 2011-07-01
> **collisionystm said:**
> I do not know how handy you are with terminal... but.... You can try to copy your files from there.

Open Terminal

Switch to root terminal

```
sudo bash
```if the drive is connected via USB, browse to it

```
cd /media/<drive>
```change to your home directory on the MAC that has your files

```
cd /destination
```Check your MAC drive permissions

```
ls -lh

```Try to change the permissions ( not sure if this will work )

```
chmod -R 770 *
```Now 

```
cp -R * /destination to save to
```


Just incase you're new to BASh, here the '*' means 'all files and folders in current directory' and the -R or -r is recursive(apply to all subfolders).
This approach looks good but you'll have to use 'sudo' in front of chmod.
(I'm not sure if it matters if you chown first or not.)

---

### Post by collisionystm on 2011-07-01
No Sudo in front of chmod because he already did a sudo bash

---

### Post by Lkm on 2011-07-01
> **collisionystm said:**
> 

For file permissions, if changing it to root as the owner, you need only do 

sudo chmod -R 700



I'm quite new too so I'm not entirely sure, but doesn't that change the permissions to 'all' for root only? So you'd still have to sudo to copy?

---

### Post by collisionystm on 2011-07-01
> **Lkm said:**
> I'm quite new too so I'm not entirely sure, but doesn't that change the permissions to 'all' for root only? So you'd still have to sudo to copy?


Well,

in your instructions you told him to do a 

```
sudo chown root
```

SO

Doing that will change the owner of all the files in that command destination to ROOT

Chmod uses 3 digits 99% of the time, although it used to be 4 way back in the day.

The format is Chmod <user><group><others>

# Permission   7 full   6 read and write   5 read and execute   4 read only   3 write and execute   2 write only   1 execute only   0 none

A  7 will invoke privileges to do a RWX read, write, execute. 

So in essence, 

Chmod 777 allows RWX for Users, People in the group and others that are neither the owner or in the specified group.

Be aware, that if you change the owner to ROOT ( i realize I made this mistake in my posting ) that chmod does nothing. Root ignores file permissions entirely, that is why its dangerous to use. 

Hopefully that helps a bit....

---

### Post by fabricator4 on 2011-07-01
> **sdd125 said:**
> Hi Chris, I'm not sure how I did either it only worked one time, i just typed the command you gave me in the first reply in terminal, it asked for my password, i typed it in and it opened a window i used to browse to my docs, but i could see in terminal it was spitting out errs saying failed this and that, i tried rebooting after i copied some word files, but no luck.  I just tried your new instructions and it says 'error while copying 123.doc. there was an error copying the file into home/user1/Desktop. *then when I click show more details* Error opening file: Permission denied.

That's the problem with giving instructions for a graphical interface - it's so hard to explain and difficult to follow.

Are you trying to copy to/from a completely different file manager window, one that does not have root privileges?

It's probably time to go CLI and change the ownership of the files on the drive as others have suggested.  First we'll look in /media to see what the drive is mounted as:

```
cd /media
ls
```

You'll see it will list any drives that have been mounted via USB.  Say you see the directory "dirname" here, in the following instructions just replace dirname with the correct name on your system.  It may even be a string of numbers and letters, in which pressing the TAB key will help you auto complete the name.  Where I put "name" replace this with your login name.

```

sudo chown -Rv name:name /media/dirname/*

```

That's it.  You should now be able to access all the files with file manager without having to use the gksudo trick.

See how you go...

Chris

---

