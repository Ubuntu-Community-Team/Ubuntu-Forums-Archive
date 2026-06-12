---
title: "Moving a file.  This ought to be easy."
date: 2010-02-06
forum: New to Ubuntu
---

### Post by lile001 on 2010-02-06
I'd like to move a file.  Sounds easy right?  

I'd prefer to use nautilus, and I can see the file there, but I don't have permissions to do anything to it.  

I can do sudo nautilus, but when I do that, I don't see the file. (Yup, I'm looking at two screens of the same folder, one says the file is there, one says it isn't. Don't argue with me, that's what I am seeing. I can't explain this either.)  Ok, forget the easy way. 

I can go to a terminal [trembles in fear] and attempt to type in some kinda gibberish to move the file. This file is a nice backup of my /home folders after I finished my taxes called homebackup.tgz. Good time for a backup! 

 However, there is a key problem:  the place I am trying to move the file to is an external drive named "My Book".  The name has a space in it.  [I didn't name it, I just bought it that way.  It was on sale and holds 1TB, what can I say?].  Any Terminal command seems to get very confused about things with a space in the name. 

How do I move a file called /homebackup.tgz to a drive called My Book?

---

### Post by Roasted on 2010-02-06
Put names with spaces in them in quotes:

sudo mv /home/frank/file /media/"My Book"

---

### Post by Temposs on 2010-02-06
Seeing a screenshot of your nautilus situation would be helpful, rather than having to take your word for it.

---

### Post by nothingspecial on 2010-02-06
You need to escape the space with a \

For example```

mv homebackup.tgz /media/My\ Book
```

White space (gaps or spaces in filenames etc) has special meanings to the linux shell. So you need to tell the shell you actually mean a space. \ does it.

---

### Post by nothingspecial on 2010-02-06
> **lile001 said:**
> 
I can do sudo nautilus

Oh, and you should do [COLOR="Red"]_gksudo_[/COLOR] nautilus

---

### Post by switch10 on 2010-02-06
> **nothingspecial said:**
> You need to escape the space with a \

For example```

mv homebackup.tgz /media/My\ Book[\CODE]

White space (gaps or spaces in filenames etc) has special meanings to the linux shell. So you need to tell the shell you actually mean a space. \ does it.

you can use either:
[code] "My Book" 
```

or 

```
 My\ Book 
```

You should never use 

```
 sudo nautilus 
```

instead use 

```
 gksu nautilus 
```

use gksu with all GUI

---

### Post by lile001 on 2010-02-06
> **switch10 said:**
> 

```
 sudo nautilus 
```instead use 

```
 gksu nautilus 
```use gksu with all GUI

OK.  Looks the same to me.  What's the difference?

File still isn't there with gksu nautilus.  I'd post a screenshot but have no idea how.  One screen shows this file in root, the other does not show it.  Everything else looks the same.

---

### Post by lile001 on 2010-02-06
> **nothingspecial said:**
> You need to escape the space with a \

For example```

mv homebackup.tgz /media/My\ Book
```White space (gaps or spaces in filenames etc) has special meanings to the linux shell. So you need to tell the shell you actually mean a space. \ does it.


Thanks! this is exactly what I needed!

---

### Post by nothingspecial on 2010-02-06
You should use gksudo (gksu) to run graphical applications.

Where is the file and where do you want to move it to.

You do a screenshot by going accessories > screeenshot in your menu.

---

### Post by nothingspecial on 2010-02-06
> **lile001 said:**
> Thanks! this is exactly what I needed!

Glad you got it sorted :p

---

### Post by lile001 on 2010-02-06
I was able to use the mv command and escape the space, but then got an error.  

Well this started to work and then it gave an error message that the file was too large.  Good thing I didn't try to back up the entire system, just the /home folders, it would have been really large then. 

The file I am trying to move appears to exist on the external drive, and reports itself to be 92 GB.  The drive seems to think it has 833 GB free.  Drive isn't full.  

Same file appears on my file system, reports to be 59.7 GB.  So they don't appear to be the same file.  This isn't really going very well.  I wonder if I have a backup or not?   I'm really confused.

---

### Post by cwalker1960 on 2010-02-06
have to agree with you on this one .. I just can't grasp how i am the only . primary . root  user and linux denies me permission to do things.. WTF.. I feel your pain , but i don't have an answer yet.. what i do know is it can be accomplished through a terminal. and another thing I don't get why doesn't anyone mention tying in a terminal sudo -i   that way you don't have to keep typing sudo before every command and you don't get logged out after "whatever minutes"  sudo -i    there i said it

---

### Post by nothingspecial on 2010-02-06
sudo is a good thing.

passwords are a good thing.

If you want an unsecure system - do away with them.

It`s perfectly possible.

Then there is the saying, if you don`t know how to do it then you probably shouldn`t, and if you do know how to do it then you wouldn`t.

Having said that, this is linux..... do what you will.

---

### Post by theozzlives on 2010-02-06
> **lile001 said:**
> I was able to use the mv command and escape the space, but then got an error.  

Well this started to work and then it gave an error message that the file was too large.  Good thing I didn't try to back up the entire system, just the /home folders, it would have been really large then. 

The file I am trying to move appears to exist on the external drive, and reports itself to be 92 GB.  The drive seems to think it has 833 GB free.  Drive isn't full.  

Same file appears on my file system, reports to be 59.7 GB.  So they don't appear to be the same file.  This isn't really going very well.  I wonder if I have a backup or not?   I'm really confused.

You sure it's not formatted FAT32?

---

### Post by switch10 on 2010-02-06
> **nothingspecial said:**
> sudo is a good thing.

passwords are a good thing.

If you want an unsecure system - do away with them.

It`s perfectly possible.

Then there is the saying, if you don`t know how to do it then you probably shouldn`t, and if you do know how to do it then you wouldn`t.

Having said that, this is linux..... do what you will.

+1.  This is how things work in Linux.  It is what makes my system secure.  You can make it just as unsecured as Windows if you want.

If you are moving things around within you home folder you should be fine.  No passwords necessary.

---

### Post by lile001 on 2010-02-06
[ homebackup.tgz is different size on one drive and on the other]

> **theozzlives said:**
> You sure it's not formatted FAT32?

It is possible the external drive is FAT32.  I am not sure how I would know.  Would that make the two files report different sizes?

---

### Post by lile001 on 2010-02-06
> **nothingspecial said:**
> sudo is a good thing.

passwords are a good thing.

If you want an unsecure system - do away with them.

It`s perfectly possible.

Then there is the saying, if you don`t know how to do it then you probably shouldn`t, and if you do know how to do it then you wouldn`t.

Having said that, this is linux..... do what you will.

Well, enough philosophy, I'm not trying to run an insecure system or anything, jsut trying to backup after doing my taxes.   So far, I've just managed to make a mess.  Let's see, is there a way I can verify that these two files are the same?

---

### Post by DaveInPhx on 2010-02-06
Drop into the terminal and rename your file, ie:

move mytaxbackup.tar mytaxbackup1.tar

Then try the copy operation to the external drive again. This should give you 2 copies on the external drive which should be the same size since they are stored on the same medium.

A better method might be to move the tar file from root into your home directory, then you should be able to use the GUI tools on it.  You may need to change the owner of the file (chown).

Hope that helps! :)

---

### Post by NCLI on 2010-02-06
> **lile001 said:**
> [ homebackup.tgz is different size on one drive and on the other]



It is possible the external drive is FAT32.  I am not sure how I would know.  Would that make the two files report different sizes?

If the drive is formatted as FAT32, it cannot store files larger than ~4GB. You can find out what filesystem it uses with the Disk Utility in Karmic, or by installing gparted.

---

### Post by lile001 on 2010-02-06
> **DaveInPhx said:**
> Drop into the terminal and rename your file, ie:

move mytaxbackup.tar mytaxbackup1.tar

Then try the copy operation to the external drive again. This should give you 2 copies on the external drive which should be the same size since they are stored on the same medium.

A better method might be to move the tar file from root into your home directory, then you should be able to use the GUI tools on it.  You may need to change the owner of the file (chown).

Hope that helps! :)

Now I have two files on the external drive, one named homebackup.tgz and one named homebackup1.tgz, each now reporting 4 GB (that's different than before) and a file homebackup1.tgz on my regular drive reporting 59.7 Gb.  There's no way these files ont he external drive are complete, I'd say.  Both times the mv command ended in an error message "File too large"   

I think I should dump all these and start over.  But where?

---

### Post by Paqman on 2010-02-06
> **cwalker1960 said:**
> I just can't grasp how i am the only . primary . root  user and linux denies me permission to do things.. WTF.. 

You aren't the only user on your machine. If you're connected to the internet then there are literally millions of people and machines that have access to it. 

It's important that your machine is able to authenticate you for who you are and not one of them.

---

### Post by ptn107 on 2010-02-06
Be careful when using **gksu nautilus**.  It will open up into the *root accounts* home folder (/root) not *your* home folder (/home/user).  That's probably why you didn't see anything when running gksu nautilus. Root's home folder is almost always empty since Ubuntu disables it.

---

### Post by lile001 on 2010-02-06
> **NCLI said:**
> If the drive is formatted as FAT32, it cannot store files larger than ~4GB. You can find out what filesystem it uses with the Disk Utility in Karmic, or by installing gparted.

Whew! This is getting way over my head too fast.   The heck with it.   Can't seem to make a file over 4 GB, so I'll assume it is FAT 32.  

So much for using this as a backup, eh?  

Maybe I should just copy the files onto it en masse, without using tar.  

Either that, or nuke the drive and reformat it some other way.  Given my level of expertise, that will likely result in a pile of smoking ruins and no backup for the taxes.

---

### Post by NCLI on 2010-02-06
> **lile001 said:**
> Whew! This is getting way over my head too fast.   The heck with it.   Can't seem to make a file over 4 GB, so I'll assume it is FAT 32.  

So much for using this as a backup, eh?  

Maybe I should just copy the files onto it en masse, without using tar.  

Either that, or nuke the drive and reformat it some other way.  Given my level of expertise, that will likely result in a pile of smoking ruins and no backup for the taxes.

Don't worry, reformatting is easy with Gparted, and we're here to walk you through it ;)

Start with [this guide]("http://www.mepisguides.com/Mepis-6/Install/gparted/gparted-set-partition.html"), then ask here if there's something you don't understand. It's a little dated, but still accurate. Just remember to select your external disk in the upper-right dropdown-menu.

Format as NTFS if you want to be able to continue to use it under Windows. If not, format it as ext4. Oh, and be aware that you will lose everything on the drive by formatting it.

---

### Post by lile001 on 2010-02-06
> **NCLI said:**
> Don't worry, reformatting is easy with Gparted, and we're here to walk you through it ;)

Start with [this guide]("http://www.mepisguides.com/Mepis-6/Install/gparted/gparted-set-partition.html"), then ask here if there's something you don't understand. It's a little dated, but still accurate. Just remember to select your external disk in the upper-right dropdown-menu.

Format as NTFS if you want to be able to continue to use it under Windows. If not, format it as ext4. Oh, and be aware that you will lose everything on the drive by formatting it.
What the heck.  It was on sale for $43, if I ruin it, it will make a great paperwieght.  Here goes nuthin!!!!!

---

### Post by malspa on 2010-02-06
Sounds like a Western Digital external hard drive.  I have one and it has a "My Book" folder, something like that, so that sounds like what you have.  Anyway, I used GParted and shrank the FAT32 partition and then used ext3 format for the rest of the drive.

I used ext3 because I was using rsync to copy stuff to the external drive and I was told that rsync has some issues copying to FAT filesystems.  I'm used to using ext3 for everything anyway, so I just changed the rest of the drive to that.

---

### Post by NCLI on 2010-02-06
> **lile001 said:**
> What the heck.  It was on sale for $43, if I ruin it, it will make a great paperwieght.  Here goes nuthin!!!!!

It won't be a paperweight no matter how bad you mess up with formatting software, I assure you of that :p

---

### Post by lile001 on 2010-02-06
> **lile001 said:**
> What the heck.  It was on sale for $43, if I ruin it, it will make a great paperwieght.  Here goes nuthin!!!!!

Yup, anybody want a used paperweight?  GParted ended in failure, and asked me to save the details.  I think I will name the file "Smoking Ruins.html".    What else can go wrong today?

---

### Post by NCLI on 2010-02-06
xD What was the error?

---

### Post by lile001 on 2010-02-06
> **lile001 said:**
> Yup, anybody want a used paperweight?  GParted ended in failure, and asked me to save the details.  I think I will name the file "Smoking Ruins.html".    What else can go wrong today?


Here is what the error file says:

GParted 0.4.3

Libparted 1.8.8Create Primary Partition #1 (ext4, 931.51 GiB) on /dev/sdc  00:00:21    ( ERROR ) 
            create empty partition  00:00:11    ( SUCCESS ) 
            path: /dev/sdc1
start: 63
end: 1953520064
size: 1953520002 (931.51 GiB) 

set partition type on /dev/sdc1  00:00:10    ( SUCCESS ) 
            new partition type: ext4 

create new ext4 file system  00:00:00    ( ERROR ) 
            mkfs.ext4 -j -O extent -L "backupdrive" /dev/sdc1 
            mke2fs 1.41.4 (27-Jan-2009)
/dev/sdc1 is mounted; will not make a filesystem here!

---

### Post by NCLI on 2010-02-07
That's nothing serious, you just have to unmount the drive before gparted can work with it ;)

Just right-click the partition you were trying to format, then choose "Unmount," and repeat what you did before.

---

### Post by lile001 on 2010-02-07
Tried this all again and it seems to be working.  So far no smoke or flame is coming out of the drive which makes me suspicious.

---

### Post by NCLI on 2010-02-07
We will be eagerly awaiting the results :p

---

### Post by malspa on 2010-02-07
I think you're gonna get this one taken care of, lile001!

---

### Post by NCLI on 2010-02-07
I'm still mystified as to why root couldn't see a file an ordinary user could though :confused:

Anyway, I hope everything works out for you Lile, 'cause I'm off to bed for today. I'll be back tomorrow if your problem still hasn't been fixed :)

---

