---
title: "How to mount ipod"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by gshockxc on 2010-02-09
How do I mount a device so that I have root privileges?

---

### Post by rcayea on 2010-02-09
I believe you would open terminal and type:

"sudo mount /dev/sdd1 or whatever your device is. I also think you should check /etc/fstab to be sure your device is able to be mounted.

---

### Post by x33a on 2010-02-09
first note the device name
```
sudo fdisk -l
```

Create a mount point under /media
```
sudo mkdir /media/ipod
```

now
```
sudo mount /dev/sdb1 /media/ipod
```

assuming /dev/sdb1 to be the ipod.

---

### Post by gshockxc on 2010-02-09
> **x33a said:**
> first note the device name
```
sudo fdisk -l
```

Create a mount point under /media
```
sudo mkdir /media/ipod
```

now
```
sudo mount /dev/sdb1 /media/ipod
```

assuming /dev/sdb1 to be the ipod.

Making progress.  The device name is /dev/sdb.  But when I run 

```
sudo mount /dev/sdb1 /media/ipod
```

I get the following: 

```
mount: you must specify the filesystem type
```

Thanks,

---

### Post by rcayea on 2010-02-09
If you are using ext4 type:

sudo mount ext4 /dev/sdb1 /media/ipod

If you are using ext3 type:

sudo mount ext3 /dev/sdb1 /media/ipod

That should do the trick. Hope if helps.

---

### Post by x33a on 2010-02-09
try
```
sudo mount -t vfat /dev/sdb1 /media/ipod
```

---

### Post by gshockxc on 2010-02-09
I tried all of the options both of you gave me.  The ext3, and ext4 options didn't seem to work for me.  

this did seem to work at first, but then I tried to unmount and mount again to make sure that I did it correctly.

```
$ sudo mount -t vfat /dev/sdb1 /media/ipod
``` gives me this error

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I'm not sure if I screwed something up.  

The other question I have is, that I've named the ipod "Kristan's iPod" so when I plug it in, it automatically mounts to it's own location in /media, AND I've still got the /media/ipod folder that I created using 

```

sudo mkdir /media/ipod

```

Shoud I sync it to iTunes and change the name to 'ipod'?

Thanks,

---

### Post by gshockxc on 2010-02-09
> **rcayea said:**
> I believe you would open terminal and type:

"sudo mount /dev/sdd1 or whatever your device is. I also think you should check /etc/fstab to be sure your device is able to be mounted.

How do I check /etc/fstab?  

I tried 
```

sudo /etc/fstab

```
command not found.

Then I tried ```
 /etc/fstab
``` and got 

```
 bash: /etc/fstab: Permission denied 
```

Thanks for your help.

---

### Post by Cheezespread on 2010-02-09
> **gshockxc said:**
> 
The other question I have is, that I've named the ipod "Kristan's iPod" so when I plug it in, it automatically mounts to it's own location in /media, AND I've still got the /media/ipod folder that I created using 

```

sudo mkdir /media/ipod

```

Shoud I sync it to iTunes and change the name to 'ipod'?

Thanks,

Its just the name of the folder that you have created to mount your ipod. It doesnt matter if you give it any name , I believe. You also said that your ipod is automounted in /media under a different name. In that case you could skip this process of creating a mountpoint yourself if you can perform read/write operations on the ipod. Else , you can add an entry in fstab which permits your user account to do so.

---

### Post by Cheezespread on 2010-02-09
> **gshockxc said:**
> How do I check /etc/fstab?  

I tried 
```

sudo /etc/fstab

```
command not found.

Then I tried ```
 /etc/fstab
``` and got 

```
 bash: /etc/fstab: Permission denied 
```

Thanks for your help.


fstab is a file which helps you to specify the mount points and options which go along with it - like your permissions , mount point , whether it should undergo a filesystem check and many more. Its more of a file which a user creates to inform the system that 'If I am connecting this drive to my machine , I need it this mounted this way '.


you can try 

```
gksudo gedit /etc/fstab
```
let us know if you face any issues

gksudo is preffered for anything GUI as I understand - basically its the sudo command to be used along with any GUI editing.
gedit - a tool like notepad to view the contents of the file you specify.

---

### Post by Orion8 on 2010-02-09
I'm not certain what you're trying to do here.  Why mount the iPod as root?  If you iPod has been initialized with a Windows version of iTunes it should mount up in /media all by itself with none of the complicated stuff above needed.  It should also load  up in Rhythmbox, and you can add files to it there.  I've had some problems using Rhythmbox to do this, so I switched to gtkpod, which is available in the repositories, and things have gone much better.

If your iPod was initialized on a Mac then you may have trouble depending on what kind you have: a large iPod is likely formatted to file format HFS+ and I have not found a good way to deal with this except to return it to factory condition on a PC and try again with gtkpod.  You can copy files to a Mac initialized iPod as root but only to store data -- at least, I cannot get mine to play songs transfered that way.

In conclusion, I have used a friend's PC with iTunes to make an iPod work in Ubuntu using gtkpod.  This was a small, flash based iPod.  I have also used my wife's Mac laptop to maintain another larger HFS+ iPod.  I hope this all makes sense.

---

### Post by gshockxc on 2010-02-10
Yes, it does help.  Normally, I just use my iRiver mp3 players.  But this iPod belonged to someone else, and they upgraded to an iTouch.  So now I have this one too.

I'm not sure what I'm trying to do either, other than get the ipod to work with a player so I can add songs to it.  It was last sync'd with a mac.  And I've had exactly the same problem you've mentioned.  I can find it in both Rhythmbox and gtkpod, but I can't do anything.  It's read-only.  

I was following some instructions I found in a post here, and it took me to a support section of the Ubuntu site, don't even remember where now.  The first step was to mount the ipod.  It was connecting automatically, but being a noob, I figured that maybe there was something specific I needed to do to get it to connect so that I had root privileges to add/remove files.

  Anyway, there's all kinds of documentation that tells me Amarok, gtkpod, and Rhythmbox should work with my ipod.  But I have yet to find anything that will actually work.

It's a 4th gen ipod. And the models listed in gtkpod don't match with the model on the back.  So I don't know what's going on.

Any suggestions?

---

### Post by Orion8 on 2010-02-10
Sorry, maybe somebody that knows more can help you.  I can't add anything really new to my above post but I can expand a bit.  Basically, I gave up and created another user on my wife's Mac just to manage my late generation iPod... I am lucky to have her computer available as I can't find a fix in Linux.  My buddy has an old iPod shuffle and when we reformatted it using an Apple utility it has been working in gtkpod as far as I know.  I will ask him today and see if it is still working.  Of course, being a smaller flash-based player it formatted to FAT32, which is well-supported all over. Plus, it is old so gtkpod is more likely to work.  This reformatting was necessary due to it getting messed up in Rhythmbox.  If I recall, after adding files in Rhymbox the thing said it was half-full but had no songs on it.  iTunes showed those files as data files, not songs, which makes me think some sort of song index was not updated by the operation.

I have not done this in 6 months or so, but you could do some googleing for "Ubuntu HFS+" and see what you find.  Last I checked support was not good which is why I gave up, having access to a Mac.  Next time I get an mp3 player I will shop around and find one with better compatibility! 

Good luck, let me know if you find a fix, I am interested.

---

### Post by gshockxc on 2010-02-10
The documentation that I came across was from a search I did here, and someone had posted the link to documentation.  I believe the instructions indicated that there's a SysInfo file in the ipod.  There's a checksum that happens, and if gtkpod can't find that unique firewire ID, then it can't match the check sum, or something like that.  Anyway, what I was supposed to so was run a command in terminal, which I did successfully, get a 16 digit Hash number, put 0x... in front of it, save it in a text file, and uploaded it to my ipod.  Problem is that there's already a SysInfo file there, and I can't overwrite it because it's read-only.  So 'I think' gtkpod will work, if I can somehow unlock my ipod.

I've also had issues with songs that I've got, which aren't recognized.  Separate issue, but gtkpod says that it doesn't recognize songs on the ipod, and I need the mp4v2 library.  but there are no instructions in gtkpod on how to download or install such a file.  So I'm kind of stuck.  But thanks for your background info.  

It might be that it's actually a 5th gen ipod nano - honestly, I can't tell the difference.  It's the first ipod i've ever used, and this is why I haven't gone to ipod sooner.  Such a PITA!  But it might be the reason why gtkpod isn't supporting my device.  As you said, if it was an older unit, it might work better.

Thanks, and let me know if you find out anything.  I'll keep posting here as I learn more.

---

### Post by nothingspecial on 2010-02-10
Have you got a friend or family member with a windows computer running iTunes?

Restore your ipod in that.

Then do [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8803616&postcount=180")

If you truly have no access to iTunes in windows then you have to turn off journaling in your hfs+ mac formatted ipod. I am unsure how you do this.

---

### Post by Orion8 on 2010-02-11
You are way ahead of me, Gshockxc -- I never tried that hard!  Sounds like a fun challenge, though not one I have time for at the moment.  Nothingspecial's link looks promising, though it looks like you need to reformat what you have to get started.

---

### Post by gshockxc on 2010-02-11
I should find a better hobby.  I'm staying up way too late at night trying different things to get my nano 5G to work with gtkpod.  Everying so far has resulted in it still being read only.  I think I need to breakdown and sync it with a windows iTunes machine first.  Somehow that seems to write the Firewire ID.

No matter what I do, I can't get access to the SysInfo file, and that's the root of all my problems right now.  I haven't been able to get past that.

---

### Post by Orion8 on 2010-02-15
Sounds like a good hobby to me!  I stay up way too late when I get on one of these projects as well.  Good luck with the iPod.

---

### Post by gshockxc on 2010-02-16
Solved!!!  

I can't take any credit for this.  It's all thanks to 'nothingspecial'.  

What did work: I was able to read the songs and copy those to gtkpod before re-formatting my 4th gen nano.
What didn't work: I couldn't write anything to it.  
What I did: Connected to machine with Windows 7, downloaded iTunes, clicked Restore, and reformatted the ipod.
What I'm doing now: Putting music on my iPod!!!  

I LOVE LINUX!!!  :guitar:

---

