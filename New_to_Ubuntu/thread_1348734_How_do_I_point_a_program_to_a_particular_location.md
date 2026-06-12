---
title: "How do I point a program to a particular location?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-07
Hi I am trying to get dropbox in ubuntu to point to a NTFS partition?

(Ubuntu has been made able to write in NTFS - if that is the correct way of phrasing that!).

My understanding is that this is done by symnbotic linking?

thanks!

In fact after some research: -s, --symbolic

Create a symbolic link. This lets you link across filesystems, and also see the name of the link when you run ls -l (otherwise, there's no way to know the name that a file is linked to).

How do I apply this please :) - reference to dropbox pointing to the correct folder that it must sync with? Thanks

---

### Post by bodhi.zazen on 2009-12-07
ln -s location_a location_b

Example, say you have a data partition , mounted at /media/data, with a directory music, and you want music to be in your home director at ~/musis

ln -s /media/data/music ~/music

see man ln for additional info

---

### Post by listerdl on 2009-12-07
> **bodhi.zazen said:**
> ln -s location_a location_b

Example, say you have a data partition , mounted at /media/data, with a directory music, and you want music to be in your home director at ~/musis

ln -s /media/data/music ~/music

see man ln for additional info

Thanks.

Could you please translate this for me, (this is some advice I was given on another forum)?

 ln -s /path/to/My Dropbox /home/henry/Dropbox

Does that mean what you are saying that it is telling the program to look in a particular folder?

Urgh.

I tried the above and this is what happened:

henry@Toshiba:~$ ln -s /home/henry/media/storage/My Dropbox /home/henry/media/storage/Dropbox
ln: target `/home/henry/media/storage/Dropbox' is not a directory

Any ideas what happened - thanks very much,

---

### Post by bodhi.zazen on 2009-12-07
Your path has a space in it. 

So ..

Use tab completion

ln -s /path/to/my<tab key> ~/Dropbox

Or escape the space with a \

ln -s /path/to/My\ Dropbox ~/Dropbox

or use quotes

ls -s "/path/to/My Dropbox" ~/Dropbox


In terms of telling your program to use ~/Dropbox, take a look at the options ;)

I am not familiar with Dropbox, but most applications have options or a configuration menu.

---

### Post by listerdl on 2009-12-07
> **bodhi.zazen said:**
> Your path has a space in it. 

So ..

Use tab completion

ln -s /path/to/my<tab key> ~/Dropbox

Or escape the space with a \

ln -s /path/to/My\ Dropbox ~/Dropbox

or use quotes

ls -s "/path/to/My Dropbox" ~/Dropbox


In terms of telling your program to use ~/Dropbox, take a look at the options ;)

I am not familiar with Dropbox, but most applications have options or a configuration menu.

THANKS -

Sorry last question - how do i find out the path? Apparently I can drag the folder to the desktop using left click and ALT to select link here.....

That told me that this folder is located here /media/storage/Dropbox - should I also include before that home/henry/ then the above?

Thanks!

---

### Post by bodhi.zazen on 2009-12-07
Try 

```
locate Dropbox
```

---

### Post by listerdl on 2009-12-07
thanks - didnt work - it just did an empty output...

---

### Post by bodhi.zazen on 2009-12-07
Update the database (the database is updated every 24 hours, so I assume you kust installed Dropbox ).

```
sudo updatedb
locate Dropbox
```

---

### Post by listerdl on 2009-12-07
thanks for this - i really appreciate your help.

That definitely worked - so I did this:

henry@Toshiba:~$ ln -s /home/henry/Dropbox/home/henry/My Dropbox
ln: creating symbolic link `Dropbox': File exists

Why is it telling me that - I want the command to make Dropbox contain the syncd files.......

---

### Post by bodhi.zazen on 2009-12-07
switch the order on your command

ln existing_file new_location 

so ...

ln -s /home/henry/My\ Dropbox /home/henry/Dropbox

or, since ~ == /home/henry

```
ln -s ~/My\ Dropbox ~/Dropbox
```

---

### Post by listerdl on 2009-12-07
thanks....

I did your advice but it seems to always produce the same output which is: 

ln: creating symbolic link `Dropbox': File exists

What does that really mean?

thanks again! Your help is invaluable!!

---

### Post by chaanakya_chiraag on 2009-12-07
Doing this for Dropbox is easy:
1) Right-click on the Dropbox icon in the top right corner.
2) Click on Preferences...
3) Click on the "Move" button in the "Dropbox Folder Location" section.
- Chiraag

---

### Post by SuperSonic4 on 2009-12-07
It means there is a file called Dropbox in your home folder. You can confirm with ```
ls -A ~ | grep Drop
```

If you delete the Dropbox folder bodhi.zazen's last command should work fine. To delete the (presumably empty) folder ```
rmdir ~/Dropbox
```. Should it not be empty run ```
rm -r ~/Dropbox
```

---

### Post by listerdl on 2009-12-07
Thanks...its just greyed out, otherwise Id happily do that. The fustrating this is that you are unable to physiscally name the path....

I have tried so many things - all i need to do is create a symnlink but it just doesnt work for me...

---

### Post by SuperSonic4 on 2009-12-07
> **listerdl said:**
> Thanks...its just greyed out, otherwise Id happily do that. The fustrating this is that you are unable to physiscally name the path....

I have tried so many things - all i need to do is create a symnlink but it just doesnt work for me...

Greyed out? Who owns the folder inside this NTFS partition? Is it you or root? You may find out by ```
ls -Al /media/disk/folder
```

where /media/disk/folder is where the folder is located. If you're unsure post the output of ```
cat /etc/fstab
``` and ```
ls -R /media
```


You can also run nautilus as root ```
gksu nautilus
``` which gives the file manager root permissions so it can do anything (but be careful)

---

### Post by listerdl on 2009-12-07
> **SuperSonic4 said:**
> Greyed out? Who owns the folder inside this NTFS partition? Is it you or root? You may find out by ```
ls -Al /media/disk/folder
```

where /media/disk/folder is where the folder is located. If you're unsure post the output of ```
cat /etc/fstab
``` and ```
ls -R /media
```


You can also run nautilus as root ```
gksu nautilus
``` which gives the file manager root permissions so it can do anything (but be careful)

ls: cannot access /media/disk/folder: No such file or directory

AND



henry@Toshiba:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=8e94e1fd-1de0-428f-a4e0-5b50e5c8f597 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda4 /media/storage ntfs-3g defaults,locale=en_GB.UTF-8 0 0
henry@Toshiba:~$ 

AND


UUID=8e94e1fd-1de0-428f-a4e0-5b50e5c8f597 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda4 /media/storage ntfs-3g defaults,locale=en_GB.UTF-8 0 0
henry@Toshiba:~$ ls -R /media
/media:
cdrom  cdrom0  floppy  floppy0  storage

/media/cdrom0:

/media/floppy0:

/media/storage:
Dropbox  My Dropbox  $RECYCLE.BIN  System Volume Information

/media/storage/Dropbox:
Photos  Public  TEST MONDAY back

/media/storage/Dropbox/Photos:

/media/storage/Dropbox/Public:

/media/storage/Dropbox/TEST MONDAY back:

/media/storage/My Dropbox:
desktop.ini  Photos  Public  TEST MONDAY back

/media/storage/My Dropbox/Photos:
desktop.ini

/media/storage/My Dropbox/Public:
desktop.ini

/media/storage/My Dropbox/TEST MONDAY back:

/media/storage/$RECYCLE.BIN:
S-1-5-21-254375542-890685618-362742897-1001

/media/storage/$RECYCLE.BIN/S-1-5-21-254375542-890685618-362742897-1001:
desktop.ini  $IFGJ4AU.dropbox  $RFGJ4AU.dropbox

/media/storage/System Volume Information:
tracking.log


XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXxx

The above all seems to indicate that I do have priviledge to write to NTFS and have access to it....

I just deleted the Home Folder Dropbox to stop the ln: creating symbolic link `Dropbox': File exists

Hope this all makes sense!!! :D

---

### Post by SuperSonic4 on 2009-12-07
If you deleted the Dropbox folder does the symbolic link work?

```
ln -s /home/henry/My\ Dropbox /home/henry/Dropbox
```

OR

```
rmdir /home/henry/Dropbox && sudo ln -s /home/henry/My\ Dropbox /home/henry/Dropbox
```

---

### Post by listerdl on 2009-12-07
hmmm

it didnt work. (thanks for your help by the way).

Couple of things, at the home folder there are still some folders called .dropbox, (with the dot before) - should I also delete those?

The central crux of the problem here is that I dual boot windows 7 and ubuntu and have created a NTFS shared partition, (that ubuntu can write to).

Now, Dropbox in windows placed the shared folder at the shared partiton and called it My Dropox, (with My) - whereas Ubuntu calls it Dropox...

If I just place the ubuntu dropbox at say Documents - then cant I make a symnlink to the My Dropbox? Hope that makes sense!!

Thanks again - highly appreciated!

---

### Post by SuperSonic4 on 2009-12-07
.dropbox won't affect this issue so you may do as you please with that

Hold on, is "My Dropbox" is in /media/storage?

If so then try ```
ln -s /media/storage/My\ Dropbox /home/henry/Dropbox
```

again you may need to remove the destination directory in ~ ```
rmdir /home/henry/Dropbox
```

My apologies this is taking so long >.<

---

### Post by listerdl on 2009-12-07
> **SuperSonic4 said:**
> .dropbox won't affect this issue so you may do as you please with that

Hold on, is "My Dropbox" is in /media/storage?

If so then try ```
ln -s /media/storage/My\ Dropbox /home/henry/Dropbox
```

"My Dropbox" - the folder created in Windows is the folder I would like to point to...

This is located in media/storage/My Dropbox

Storage is the name of the partition....

If I click Places > Home Folder > then I see storage on the left hand side....

Thanks ! If there is anything you can suggest id be appreciative!!

---

### Post by SuperSonic4 on 2009-12-07
Fair enough, did the symlink in my last post work?

I think in nautilus there is a "send link to" command or similar but I've never used GNOME so no idea there

---

### Post by listerdl on 2009-12-07
the symlink didnt work in the last post unforunately.....

Can I ask - does a symlink firstly start from the source, like home/then/the/path and then point to the end by going home/then/the end folder?

---

### Post by bodhi.zazen on 2009-12-07
> **listerdl said:**
> the symlink didnt work in the last post unforunately.....

Can I ask - does a symlink firstly start from the source, like home/then/the/path and then point to the end by going home/then/the end folder?

Yes.

---

### Post by chaanakya_chiraag on 2009-12-07
In GNOME, click on Places->Home Folder -> the storage thing in the left hand side.  Right-click on the My Dropbox folder and click on "Make Link".  Then, right-click on the link, click "Cut", go back to your home folder, and click Edit->Paste (That is located on the toolbar at the top).  Finally, rename the link to Dropbox.

---

