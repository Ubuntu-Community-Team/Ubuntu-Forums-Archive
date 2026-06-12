---
title: "How to  move/rename a mount point?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-03
Hi there!
I just partitioned my disk to make some space for ubuntu and I made a 3rd partition for shared data as well. During the installation I was prompt for a mount point for my 3rd partition..and as I didnt know what to put I just tried "data" and what I got is a 150gb data folder!
I would like to make it my home folder if poss, or at least move it inside my home. Please dont presume I know what I'm doing..I'm hitting the ubuntu road just 2days now! ;) thx!

---

### Post by llamabr on 2009-03-03
Post the output of 

```
cat /etc/fstab
```

and 

```
df
```

---

### Post by webwiller on 2009-03-03
christian@christian-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=35c79155-9d6a-4bf5-907f-89d1804193c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=49AA-CA20  /data           vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=70909eba-38c6-43bb-985b-24424b691ff2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by webwiller on 2009-03-03
christian@christian-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             30597204   4420880  24622040  16% /
tmpfs                  1553852         0   1553852   0% /lib/init/rw
varrun                 1553852       108   1553744   1% /var/run
varlock                1553852         0   1553852   0% /var/lock
udev                   1553852      2840   1551012   1% /dev
tmpfs                  1553852       104   1553748   1% /dev/shm
lrm                    1553852      2004   1551848   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda5            156396704     97904 156298800   1% /data

---

### Post by taurus on 2009-03-03
Is Ubuntu the only OS on that machine?  If it is, it's much better to reformat your /dev/sda5 from vfat to ext3 and mount it somewhere in your $HOME like $HOME/share.

---

### Post by webwiller on 2009-03-03
No, it is dualboot win/ubuntu

---

### Post by taurus on 2009-03-03
I don't think it is a good idea to mount a vfat filesystem in your $HOME since it doesn't play well with permissions and ownership.  However, you can make a link to it from your $HOME though.

---

### Post by webwiller on 2009-03-03
What I need is actually to have my docs, music, pics, video in that shared partition. I dont really care about moving it, what I care about is that my menus (i.e. in the places menu) point to that "data" folder. I mean..can I create a docs)music/video ect folders inside "data" partition and make menus point at it? So that if I open my places menu I find docs/music/pics/video which are actually in that data partition?

---

### Post by taurus on 2009-03-03
Instead of mounting it to /data, why not mount it to /media/data.  I think that is what you want.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change the mount point from /data to /media/data.

```
UUID=49AA-CA20 **[COLOR="Blue"]/media/data[/COLOR]** vfat utf8,umask=007,gid=46 0 1
```
Save it.  Now, you need to create the new mount point.

```
sudo mkdir /media/data
```
Reboot and your /dev/sda5 is now mounted to /media/data and there should be an icon on your desktop, pointing to /media/data.

```
df -h
```

---

### Post by webwiller on 2009-03-03
Ok, yes!;) This is half the job! Fine, is there somehow now, where under the menu "places" I can put docs/music/pics/videos pointing at the new media instead of pointing at the default ones under the home folder?
thx!!

---

### Post by neanderthalman on 2009-03-03
> **webwiller said:**
> Ok, yes!;) This is half the job! Fine, is there somehow now, where under the menu "places" I can put docs/music/pics/videos pointing at the new media instead of pointing at the default ones under the home folder?
thx!!

I've been looking for something similar, and found a symbolic links useful for such a thing.  For my purposes, I wanted the "Music" folder for two separate users to point to my old windows "My Music" folder, so each users login would behave as if the mp3's were in their own /home folder.

The syntax for a symlink is

ln -s target link_name


So, for what I set up, I did the following:

```

cd ~
sudo rmdir Music
ln -s /media/D/My\ Documents/My\ Music Music

```

Now, when I hit "Music" in the Places menu, it appears as if I'm in /home/neanderthalman/Music, but I'm really manipulating files in /media/D/My Documents/My Music.

The same will work for any of the above folders.  I also added a "Downloads" and "Torrents" symlink, and they automatically showed up in "Places".

---

### Post by webwiller on 2009-03-03
I have a directory /home/webwiller/music
lets say..and I want to put it under /media/data/music
what command should I type exactly? I dont understand all those slash and how to fit them in my case:(
Should I delete existing music folder or I get 2of them?

Then I can do the same for all my folders I understand...

---

### Post by neanderthalman on 2009-03-03
> **webwiller said:**
> I have a directory /home/webwiller/music
lets say..and I want to put it under /media/data/music
what command should I type exactly? I dont understand all those slash and how to fit them in my case:(
Should I delete existing music folder or I get 2of them?

Then I can do the same for all my folders I understand...

Absolutely you can do the same for all of your folders - the backslashes are needed when there is a space in the file name.  My Documents needs to be entered as My\ Documents, else it looks for two separate folders, one called "My", the other called "Documents".

I assume your /home/webwiller/music is actually /home/webwiller/Music created by default - the capitalization matters in Linux.  Assuming so, the commands you need are as follows:

```

cd ~
rmdir Music
ln -s /media/data/music Music

```

The first command puts you in your home directory.  The second removes the existing Music folder - make sure it's empty first.  The third creates a link with the symbolic (-s) option, with /media/data/music as the target, and "Music" as the name of the link.

---

### Post by webwiller on 2009-03-03
It didnt work...
It deleted the directory "music" from inside the home folder, but it did not create a link in /media/data and the link in places doesnt work anymore reporting the error that no application refers to it.

This is what I get:

christian@christian-laptop:~$ ln -s /media/data/musica Musica
ln: creating symbolic link `Musica': File exists

Do I need to create a directory musica inside /media/data first?

---

### Post by webwiller on 2009-03-03
The music link in places menu is still pointing at /home/music, that's why it says such file/directory doesn't exist

---

### Post by neanderthalman on 2009-03-03
> **webwiller said:**
> It didnt work...
It deleted the directory "music" from inside the home folder, but it did not create a link in /media/data and the link in places doesnt work anymore reporting the error that no application refers to it.

This is what I get:

christian@christian-laptop:~$ ln -s /media/data/musica Musica
ln: creating symbolic link `Musica': File exists

Do I need to create a directory musica inside /media/data first?

Can you post the results of the following two commands?

```
ls -R ~
```
and
```
ls /media/data
```

That will tell me the contents of your home folder, and the folders in your /media/data folder.  Then I can help customize the commands you need.

---

### Post by neanderthalman on 2009-03-03
Where exactly do you intend to store the music files?  /media/data/musica ?

---

### Post by webwiller on 2009-03-04
Sry...I had to go to sleep;)
Well..the first code u gave me...I included as an attachment cause is very long (I made it with text editor and gave it .txt extension...dont know if I did it right!)
The second one is this:

/home/christian/Video:
christian@christian-laptop:~$ ls /media/data
Christian  Musica
christian@christian-laptop:~$

---

### Post by webwiller on 2009-03-04
What I intend is to store all my stuff (docs/music/videos&anything else) in  my media/data partition, leaving the / partition just for ubuntu and new software.
Therefore I need my places menu to point to my /media/data as if it was my home.
I dont want to use my home for my docs at all!
Same way I have for windows, OS&software in c:\ and everythingelse in d:\. I just want to find all my stuff in the same place if I log into ubuntu or win.
(at least 'till I know what I am doing in ubuntu...with win I know hot to do some audio/video editing...with ubuntu I am like a child trying to find my way round in the basics...it's a bit frustrating!)

---

### Post by neanderthalman on 2009-03-04
I think I'm getting a better understanding what you want to do.  In fact, it's very close to what I've set up on my computer - closer than I thought before.

Let me describe what I have set up:

I have, on the same partition as root, a /home directory for each user.  On a separate partition, all of my music, movies, and documents are stored in the typical windows XP folder setup.  What I have done is link them together using these symbolic links.  It will "look" like the files are sitting under the home directory - but they are actually on the equivalent to a D drive.

Your files don't actually move to the /home directory - they remain on the shared partition.

The second method would be to change your users home directory to /media/data/christian under the "users and groups" settings box.  The issue is that the home directory contains a lot of hidden configuration files that will make an untidy mess in your user folder under windows if you simply change the location of your home folder to /media/data/christian.  Because files are hidden differently by ubuntu than windows, they'll be all over the place when you boot to windows and look for your media.  The symbolic linking will separate your configuration files from your data and media, so it's a lot cleaner when you boot to windows.

Compare the outputs from the following two commands to see how many hidden files we're talking about:

```
ls ~
ls -a ~
```

See what I mean?

The ls -R ~ command pumped out much more information than I was expecting, which suggests that you successfully created a symbolic link to /media/data/Christian.  It's a transparent link, so I really can't tell from that output whether you've created a link, or already had files in your home folder.....

As an aside:
The output you added to the text file appears to be a copy & paste from the terminal, and was long enough to get cut off by the maximum length in the terminal window.  There's a neat trick you can use in such a situation:

```
ls -R ~ > ~/output.txt
```

This will perform the same file listing as before, but send the output directly to a text file called "output.txt" in your home (~) folder.  It will not get cut off by the limitations of the terminal window.  Text files in linux don't need a .txt extension, though it certainly makes it more familiar.  I don't think we can overestimate the need for a little familiarity when struggling to learn a new OS.  Such things (like my drive letter mount points) have helped me immensely.  Posting the file created by the command above may be helpful, but we first need to see what symbolic links, if any, have been created in your /home folder.


Allrighty, back to the situation at hand.

Post the results of this command:

```
ls -l ~
``` 

It will list the contents of your home folder in "long" format, which is useful for thinks like permissions, but it will also clearly show what is a folder, what is a file, and most importantly, what is a link.

Here's the same command on my computer:

```
neanderthalman@Humphrey-Ubuntu:~$ ls -l
total 2740
drwxr-xr-x 2 neanderthalman neanderthalman    4096 2009-03-02 23:26 Desktop
-rw-r--r-- 1 neanderthalman neanderthalman 1186648 2009-02-15 19:59 Desktop Feb 09
lrwxrwxrwx 1 neanderthalman neanderthalman      22 2009-03-02 23:10 Documents -> /media/D/My Documents/
lrwxrwxrwx 1 neanderthalman neanderthalman      51 2009-03-02 23:25 Downloads -> /media/D/My Documents/Downloads/Unsorted Downloads/
lrwxrwxrwx 1 neanderthalman neanderthalman      26 2009-02-14 21:05 Examples -> /usr/share/example-content
lrwxrwxrwx 1 neanderthalman neanderthalman      31 2009-03-02 23:05 Music -> /media/D/My Documents/My Music/
lrwxrwxrwx 1 neanderthalman neanderthalman      34 2009-03-02 23:14 Pictures -> /media/D/My Documents/My Pictures/
drwxr-xr-x 2 neanderthalman neanderthalman    4096 2009-02-14 21:36 Public
-rw-r--r-- 1 neanderthalman neanderthalman 1591522 2009-02-16 10:16 Screenshot.png
drwxr-xr-x 2 neanderthalman neanderthalman    4096 2009-02-14 21:36 Templates
drwxr-xr-x 5 neanderthalman neanderthalman    4096 2009-02-15 16:06 Themes
lrwxrwxrwx 1 neanderthalman neanderthalman      54 2009-03-02 23:25 Torrents -> /media/D/My Documents/Downloads/Bit Torrent Downloads/
lrwxrwxrwx 1 neanderthalman neanderthalman      32 2009-03-02 23:15 Videos -> /media/D/My Documents/My Videos/

```

Lets pick out one specific line to focus on.

```
lrwxrwxrwx 1 neanderthalman neanderthalman      22 2009-03-02 23:10 Documents -> /media/D/My Documents/
```

The first section of information is lrwxrwxrwx.  The l indicates that it's a link, and the rwx means I have full read/write permissions for everybody.  The last bit of information on the line is "Documents -> /media/D/My Documents/".  This indicates that the link is named "Documents", and points to /media/D/My Documents/

Also, to make sure that /media/data/Musica is a folder and not a link in the wrong place - post the output of the following command as well

```
ls -l /media/data
```

---

### Post by webwiller on 2009-03-04
Right...this is it:

christian@christian-laptop:~$ ls -l ~
total 656
lrwxrwxrwx 1 christian christian     26 2009-03-01 20:34 Examples -> /usr/share/example-content
-rw-r--r-- 1 christian christian 604015 2009-03-04 22:05 Firefox_wallpaper.png
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:42 ls -R ~
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:40 ls -R ~~
drwxrwx--- 2 root      plugdev    16384 2009-03-04 03:02 Musica
drwxr-xr-x 6 christian christian   4096 2009-03-04 23:40 Scrivania

and:

christian@christian-laptop:~$ ls -l /media/data
total 112
drwxrwx---  3 root plugdev 16384 2009-03-04 15:44 Christian
drwxrwx---  2 root plugdev 16384 2009-03-04 19:45 Documenti
drwxrwx---  2 root plugdev 16384 2009-03-04 19:48 Downloads
drwxrwx---  2 root plugdev 16384 2009-03-04 19:47 Immagini
drwxrwx--- 10 root plugdev 16384 2009-03-04 20:09 JDownloader
drwxrwx---  2 root plugdev 16384 2009-03-04 03:02 Musica
drwxrwx---  2 root plugdev 16384 2009-03-04 19:48 Video

I think directories are in the right place (following your great explaination! thx!) but my links arent at all...isn't it?!

---

### Post by webwiller on 2009-03-04
and:

christian@christian-laptop:~$ cd ~
christian@christian-laptop:~$ ln -s /media/data/musica Musica
ln: creating symbolic link `Musica/musica': Operation not permitted

---

### Post by neanderthalman on 2009-03-04
Ok.  What I'm seeing is you have a directory called ~/Musica  (or /home/christian/Musica), and you have a directory called /media/data/Musica.  The question right now is - which of these two contains your music files?

I ask the question, as I do not want to tell you a command that will delete them accidentally.

What we want is for your music files to be in /media/data/Musica, and to replace the directory ~/Musica with a symbolic link.

Can you post the contents of the following two commands?

```
ls ~/Musica
ls /media/data/Musica
```

Other than the mysterious "Musica" folder, everything is perfect, and we can try making a link with, say, your documents.

The command, exactly as you need, is as follows

```
cd ~
ln -s /media/data/Documenti Documenti
```

Which wouldn't be complete without further explanation. "cd ~" will first move you to your home directory /home/christian/.  The ~ symbol is an easy shortcut for the home directory of the current user.  Next, "ln" is the command to create a link in the current folder, and "-s" is the 'symbolic' option.  Then, we have the target of the link "/media/data/Documenti", and finally the name of the link, "Documenti".

---

### Post by webwiller on 2009-03-04
?? Where is the "tilde" symbol on my keyboard by the way? I managed copiying&pasting till now...but...I need to know where it is..:-%

---

### Post by neanderthalman on 2009-03-04
> **webwiller said:**
> ?? Where is the "tilde" symbol on my keyboard by the way? I managed copiying&pasting till now...but...I need to know where it is..:-%

ah....hrm.  You know, I've never seen an italian keyboard before.  For a US standard, it's directly above the tab key.  I don't see one on an italian keyboard.

I found this though [http://ubuntuforums.org/showthread.php?t=532918](http://ubuntuforums.org/showthread.php?t=532918)

With the suggestions of the PgDn key and AltGr + ^

---

### Post by webwiller on 2009-03-04
This is it:

christian@christian-laptop:~$ cd ~
christian@christian-laptop:~$ ln -s /media/data/Documenti Documenti
christian@christian-laptop:~$

---

### Post by neanderthalman on 2009-03-04
excellent.

now try 

```
ls -l
```

And in the list you should find a link called Documenti that points to /media/data/Documenti.

Enter

```
cd Documenti
ls
```

and it should show you your documents.

Also, check in places to see if "Documenti" now takes you to your files.

---

### Post by webwiller on 2009-03-04
Yes!!
I have my Documenti link now!
(dont worry for my files...till I sort things out they lie on my media-box as a back-up;) all these directories I playing round with are just empty)

I have a problem deleting the Musica directory inside my home(where do I find home symbol on keyboard?), I get the error: device or resource busy...but I'm not running any program and the folder is just empty :-%

---

### Post by webwiller on 2009-03-04
christian@christian-laptop:~$ ls -l
total 656
lrwxrwxrwx 1 christian christian     21 2009-03-05 00:54 Documenti -> /media/data/Documenti
lrwxrwxrwx 1 christian christian     26 2009-03-01 20:34 Examples -> /usr/share/example-content
-rw-r--r-- 1 christian christian 604015 2009-03-04 22:05 Firefox_wallpaper.png
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:42 ls -R ~
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:40 ls -R ~~
drwxrwx--- 2 root      plugdev    16384 2009-03-04 03:02 Musica
drwxr-xr-x 3 christian christian   4096 2009-03-05 00:37 Scrivania

fine...right?

---

### Post by neanderthalman on 2009-03-04
> **webwiller said:**
> Yes!!
I have my Documenti link now!
(dont worry for my files...till I sort things out they lie on my media-box as a back-up;) all these directories I playing round with are just empty)

I have a problem deleting the Musica directory inside my home(where do I find home symbol on keyboard?), I get the error: device or resource busy...but I'm not running any program and the folder is just empty :-%

Not sure why you're getting that message.

One problem is that you're apparently not the owner of ~/Musica.  When you did ls -l ~, it showed root as the owner of the Musica folder.

drwxrwx--- 2 **root** plugdev 16384 2009-03-04 03:02 Musica

Lets try this

```
sudo rm -Rf ~/Musica
```

Try AltGr + ^ or PgDn and see if one of those gives you a ~ symbol.

---

### Post by neanderthalman on 2009-03-04
Again, I should explain the code.  You probably know sudo, but just in case - it will run the command "as root".  rm is the command for remove, -Rf will remove all files and folders within and including the target, and then we specify the target as ~/Musica


Alternatively, we can try 

```
sudo rmdir ~/Musica
```

where rmdir is the command for "remove directory".

Also, make sure you don't have any other terminal windows or nautilus windows open, in case one of them is the cause of your "device or resource busy" error

---

### Post by webwiller on 2009-03-04
christian@christian-laptop:~$ cd ~
christian@christian-laptop:~$ ln -s /media/data/Video Video
christian@christian-laptop:~$  ln -s /media/data/Downloads Downloads
christian@christian-laptop:~$  ln -s /media/data/Immagini Immagini
christian@christian-laptop:~$  ln -s /media/data/Christian Christian
christian@christian-laptop:~$  ln -s /media/data/Musica Musica
ln: creating symbolic link `Musica/Musica': Operation not permitted
christian@christian-laptop:~$ 

As you can see...everything's fine BUT music...any clue?

---

### Post by webwiller on 2009-03-04
christian@christian-laptop:~$ sudo rmdir ~/Musica
rmdir: failed to remove `/home/christian/Musica': Device or resource busy
christian@christian-laptop:~$

---

### Post by neanderthalman on 2009-03-04
> **webwiller said:**
> christian@christian-laptop:~$ cd ~
christian@christian-laptop:~$ ln -s /media/data/Video Video
christian@christian-laptop:~$  ln -s /media/data/Downloads Downloads
christian@christian-laptop:~$  ln -s /media/data/Immagini Immagini
christian@christian-laptop:~$  ln -s /media/data/Christian Christian
christian@christian-laptop:~$  ln -s /media/data/Musica Musica
ln: creating symbolic link `Musica/Musica': Operation not permitted
christian@christian-laptop:~$ 

As you can see...everything's fine BUT music...any clue?


Yes, the problem is that there is already a directory called Musica, and we can't create a link with the same name.  We first need to delete the existing directory using either sudo rm -Rf ~/Musica or sudo rmdir Musica, then create the link.  sudo is necessary as the Musica owner is owned by root, according to your ls -l you just posted.

---

### Post by neanderthalman on 2009-03-04
Did some searching, there must be some process currently accessing the Musica folder.

It might be another terminal, it might be a file system browser (nautilus).  I'm not sure of what command would show what process it is.

If necessary, you could always try the windows method - restart the computer and try it again.

---

### Post by webwiller on 2009-03-04
hristian@christian-laptop:/home$ cd ~
christian@christian-laptop:~$ rmdir Musica
rmdir: failed to remove `Musica': Device or resource busy
christian@christian-laptop:~$ cd /media/data
christian@christian-laptop:/media/data$ sudo rmdir Musica
rmdir: failed to remove `Musica': Device or resource busy
christian@christian-laptop:/media/data$ 


As you see...it's like the two directories Musica, one in /home and the other in /media/data seem connected somehw, because I cant remove none of the two and I get same answer...thery're busy...yee...with each other!

---

### Post by webwiller on 2009-03-04
how do I show all running processes? (task manager)

but I think it's some how involving both directories named the same in two different directories....

---

### Post by webwiller on 2009-03-04
christian@christian-laptop:~$ cd ~
christian@christian-laptop:~$ sudo rmdir Musica
[sudo] password for christian: 
christian@christian-laptop:~$ ln -s /media/data/Musica Musica
christian@christian-laptop:~$ ls -l /media/data
total 112
drwxrwx---  3 root plugdev 16384 2009-03-04 15:44 Christian
drwxrwx---  2 root plugdev 16384 2009-03-05 01:09 Documenti
drwxrwx---  2 root plugdev 16384 2009-03-04 19:48 Downloads
drwxrwx---  2 root plugdev 16384 2009-03-05 00:36 Immagini
drwxrwx--- 10 root plugdev 16384 2009-03-04 20:09 JDownloader
drwxrwx---  2 root plugdev 16384 2009-03-04 03:02 Musica
drwxrwx---  2 root plugdev 16384 2009-03-04 19:48 Video
christian@christian-laptop:~$ ls -l
total 640
lrwxrwxrwx 1 christian christian     21 2009-03-05 01:14 Christian -> /media/data/Christian
lrwxrwxrwx 1 christian christian     21 2009-03-05 00:54 Documenti -> /media/data/Documenti
lrwxrwxrwx 1 christian christian     21 2009-03-05 01:13 Downloads -> /media/data/Downloads
lrwxrwxrwx 1 christian christian     26 2009-03-01 20:34 Examples -> /usr/share/example-content
-rw-r--r-- 1 christian christian 604015 2009-03-04 22:05 Firefox_wallpaper.png
lrwxrwxrwx 1 christian christian     20 2009-03-05 01:13 Immagini -> /media/data/Immagini
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:42 ls -R ~
-rw-r--r-- 1 christian christian  17763 2009-03-04 13:40 ls -R ~~
lrwxrwxrwx 1 christian christian     18 2009-03-05 01:46 Musica -> /media/data/Musica
drwxr-xr-x 3 christian christian   4096 2009-03-05 00:37 Scrivania
lrwxrwxrwx 1 christian christian     17 2009-03-05 01:12 Video -> /media/data/Video


Worked-out true?
ty very very very much mate;)

How do I mark this as "solved"?

It's time to open a new thread now...cause I cant get no sounds out of my notebook. Sound work only with line out speakers...but internal ones dont:(

---

### Post by neanderthalman on 2009-03-04
You're very welcome!  Glad it worked in the end.  What was preventing the deletion of the Musica directory?

The "mark as solved" is a forum feature that was recently disabled.  I think you can edit the title of the original post, but that's it.

Best of luck with the speakers.

---

### Post by webwiller on 2009-03-04
I dont know wha was preventing from deleting...as you said, I just did it the windows way, I rebooted ubuntu and it worked!
see you mate;)

---

