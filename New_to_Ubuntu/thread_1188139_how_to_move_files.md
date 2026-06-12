---
title: "how to move files"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Jannes. on 2009-06-15
How can i move files from my desktop to my external harddisk???

What i want is moving files from my desktop to my external harddisk...

One problem i have to do it trough terminal...

I cant see my desktop so i have to move them trough terminal...

---

### Post by Celauran on 2009-06-15
```
mv /path/to/file /path/to/destination
```

Example: Say your username is james and your external drive is mounted on /mnt/USB-HDD

```
mv /home/james/Desktop/* /mnt/USB-HDD
```

This will move everything from your desktop to the external drive. You could also substitute mv with cp -R to copy instead of move.

---

### Post by zvacet on 2009-06-15
Type in yerminal

```
cd Desktop
```

and when you are there 

```
sudo cp filename /path/to/desired/partition/folder
```

This way you will copy files to your desired place.When you move files where you want them to be you can delete files from desktop.You can do same hing with 

```
sudo mv filename /path/to/desired/partition/folder
```

But in case you type something wrong you will spend sime time looking where your files are.

---

### Post by leandromartinez98 on 2009-06-15
Nothing against using the terminal. But what you mean by "can't see your desktop"? Click on Places->Desktop and your file is to be there.

---

### Post by Jannes. on 2009-06-15
haha

I boot perfect but after the loading part of ubuntu with the logo and the bar...

I see black screen and only my mouse is visible...

So i have to do CTRL+ALT+F1 but im not shure my external drive is mounted :D

in fact the problem is i dont know what the name is of my extern harddisk

---

### Post by leandromartinez98 on 2009-06-15
Ah... Then use the command line. Your desktop folder is:

/home/yourusername/Desktop

and probably, if mounted, your external drive is in 

/media

use:

ls /media

and check within the folders there if one of them is your external drive,
usuall /media/disk

If not you will have to mount it.

---

### Post by Jannes. on 2009-06-15
for info about my black screen see this     [http://ubuntuforums.org/showthread.php?t=1185778](http://ubuntuforums.org/showthread.php?t=1185778)

mhm if i boot, see my black screen with mouse press CTRL-ALT-F1, login i end here...

jannes@jannes-Desktop ...

there i press /media

it says it cant find someting


i stuck my ext hdd in again and it gave smth.
so what now

---

### Post by leandromartinez98 on 2009-06-15
> **Jannes. said:**
> for info about my black screen see this     [http://ubuntuforums.org/showthread.php?t=1185778](http://ubuntuforums.org/showthread.php?t=1185778)

mhm if i boot, see my black screen with mouse press CTRL-ALT-F1, login i end here...

jannes@jannes-Desktop ...

there i press /media

it says it cant find someting


i stuck my ext hdd in again and it gave smth.
so what now

The command is 
```

ls /media

```

---

### Post by Jannes. on 2009-06-15
there i only see 

cdrom cdrom0 cdrom1

---

### Post by leandromartinez98 on 2009-06-15
> **Jannes. said:**
> there i only see 

cdrom cdrom0 cdrom1

What exactly to you want to do? You probably better boot your PC with a Ubuntu Live CD, with which you will be able to see both your harddrive and your external harddrive using the gui, and then move this file. Your external harddrive does not seem to be mounted, but given that you are just now learning commands it will be a bit complicated to get you to do that.

---

### Post by Jannes. on 2009-06-15
ok lets try that

---

### Post by Jannes. on 2009-06-15
im on my live CD now

Thanx for the help, everything is copied, lets reinstall ubuntu now :)

---

### Post by leandromartinez98 on 2009-06-15
> **Jannes. said:**
> im on my live CD now

Thanx for the help, everything is copied, lets reinstall ubuntu now :)

Glad it worked! Good luck!

---

### Post by Jannes. on 2009-06-15
So, now im on my installed ubuntu...

Im going to reboot after every install i do so i know where my problem is...

grtzz

U will hear me later with other problemzz!!

thanx for the help

---

