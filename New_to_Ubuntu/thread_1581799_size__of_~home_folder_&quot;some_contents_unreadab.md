---
title: "size  of ~/home folder &quot;some contents unreadable&quot;"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by oldsoundguy on 2010-09-25
Trying to copy my ~/home folder to new Jump drive for backup, etc.  Turns out the 8gb drive I got was too small now (been a while since I did the backup)
So, went to the home folder, opened it and selected file system .. did the ctrl/h to show hidden files (nothing popped up) .. then a right click and properties to find out the actual SIZE of the contents.                     

That is when I got the message:
"some contents unreadable" on the pop up.

What is unreadable?  And WILL this make a difference IF AND WHEN I can copy it to a bigger Jump drive?

BTW, it took FOREVER for the final results of size to be determined!

TIA

(mods .. if this is in the wrong place .. feel free to move it.)

---

### Post by Kr4zyl3gz on 2010-09-25
Bump For Some Help =] Not 100% sure so i wont put my foot in my mouth

---

### Post by muteXe on 2010-09-25
what happens if you open your file manager up with root privileges and then again try and look at the sizes?

---

### Post by oldsoundguy on 2010-09-25
and just how do I gain root privileges in the file manager?
(open in terminal?  What is the command line?)

---

### Post by oldsoundguy on 2010-09-27
Bumpty, Bumpty, Bump .. Bump City!!

---

### Post by sanderd17 on 2010-09-27
the bump worked :p

open nautilus by pressing alt+F2 and typing
```

gksudo nautilus

```

---

### Post by sanderd17 on 2010-09-27
maybe baobad can see the files: ALT+F2 and type

```

baobab

```

---

### Post by Paqman on 2010-09-27
> **oldsoundguy said:**
> did the ctrl/h to show hidden files (nothing popped up) .. 

Er, you should have got about a million .folders when you did that. Nothing in your own home folder should need root to see or copy (although the contents of other users home folders will).

---

### Post by oldos2er on 2010-09-27
Do you have /home on its own partition? When was the last time you ran fsck on it?

---

### Post by oldsoundguy on 2010-09-27
No, ~/home is NOT in it's own partition .. what I eventually am trying to do is copy it to a thumb drive for back-up and for use in updating.

My 8gb thumb turned out to be too small (and I got a LOT of copy errors on top of that)

Would love to get this procedure down before I actually NEED to have it in one way or another.

Have a 16gb thumb drive "in the mail".

---

### Post by philinux on 2010-09-27
> **oldsoundguy said:**
> No, ~/home is NOT in it's own partition .. what I eventually am trying to do is copy it to a thumb drive for back-up and for use in updating.

My 8gb thumb turned out to be too small (and I got a LOT of copy errors on top of that)

Would love to get this procedure down before I actually NEED to have it in one way or another.

Have a 16gb thumb drive "in the mail".

Applications>accessories>Disk usage analyser. Then click scan home.

In your previous posts were you looking in /home/YourUsername i.e Places>Home Folder and then press ctrl h. Or View >show hidden files.

---

### Post by oldsoundguy on 2010-09-27
hmmmm tells me I have 82 items with 988.4meg .. I can see why the 8gb did not work .. and I now see that the 16 should do FINE with room to spare!

THANKS philinux!!

Now, how am I to copy without those errors? Drag and drop did not work.

---

### Post by philinux on 2010-09-27
> **oldsoundguy said:**
> hmmmm tells me I have 82 items with 988.4meg .. I can see why the 8gb did not work .. and I now see that the 16 should do FINE with room to spare!

THANKS philinux!!

Now, how am I to copy without those errors? Drag and drop did not work.

988.4 meg is less than 1gig :confused:.

---

### Post by oldsoundguy on 2010-09-27
Then why would it not copy?  At a loss here.  

(Lousy at reading decimal points .. must be age catching up!! LOL)

All that is on the drive is Lost + Found folder.

---

### Post by Paqman on 2010-09-27
> **oldsoundguy said:**
> 
Now, how am I to copy without those errors? Drag and drop did not work.

That's likely going to be due to a problem with the destination device (or it's filesystem).

Might have better luck with rsync. But if the device is that thrashed out, do you really want to use it at all?

---

### Post by oldsoundguy on 2010-09-27
> **Paqman said:**
> That's likely going to be due to a problem with the destination device (or it's filesystem).

Might have better luck with rsync. But if the device is that thrashed out, do you really want to use it at all?

Brand new Lexar twist.  Been through the G-Parted set up routine and the drive mounts.

---

### Post by Crazedpsyc on 2010-09-27
Notice he said he went to the filesystem before pressing alt+h. There shouldn't be hidden files or folders there. Also, just try running the following from a terminal:
```

cp ~/ /media/*yourdevice*/backupfolder/

```
where *yourdevice* is the name of you flash drive as seen from nautilus

---

### Post by DarthScape on 2010-09-27
~/home doesn't make much sense does it? wouldn't that mean /home/yourname/home  ?

---

### Post by oldsoundguy on 2010-09-27
> **DarthScape said:**
> ~/home doesn't make much sense does it? wouldn't that mean /home/yourname/home  ?

Abbreviation .. 

And I managed to get all files to display ..

Now to be able to copy them to the drive .. problems the same as I stated in the first post.

---

### Post by Paqman on 2010-09-27
Check that you haven't got tons of stuff sitting in the trash on your destination drive that's preventing you from copying new stuff over.

---

### Post by oldsoundguy on 2010-09-27
hoooo boy ... this is a FRESHLY FORMATTED (ext3) drive

---

### Post by psusi on 2010-09-27
You have to be more specific.  "It won't copy" is not an error description.  What exactly did you try, and what exactly were the results?

---

### Post by Crazedpsyc on 2010-09-27
try viewing hidden files on the device too, just to see if the manufacturer included junky bloatware like most do these days

---

### Post by oldsoundguy on 2010-09-27
> **psusi said:**
> You have to be more specific.  "It won't copy" is not an error description.  What exactly did you try, and what exactly were the results?

"The folder "home" cannot be copied because you do not have permissions to create it in the destination."

---

### Post by oldsoundguy on 2010-09-27
> **Crazedpsyc said:**
> try viewing hidden files on the device too, just to see if the manufacturer included junky bloatware like most do these days

FORMATTED the drive.  That removes everything.

---

### Post by philinux on 2010-09-27
> **oldsoundguy said:**
> "The folder "home" cannot be copied because you do not have permissions to create it in the destination."

Places>Home Folder then ctrl h. Edit>select all the drag the lot to your stick.

---

### Post by oldsoundguy on 2010-09-27
> **philinux said:**
> Places>Home Folder then ctrl h. Edit>select all the drag the lot to your stick.

same  message ..

"The folder "home" cannot be copied because you do not have permissions to create it in the destination."

---

### Post by psusi on 2010-09-27
When you format the drive, if you don't do it via the disk utility and check the box to take ownership, then the root directory is owned by root, so you can't write to it.  To fix it, do the following in a console:

sudo chown username.username -R /media/foo

Where username is your user name, and foo is the name of the disk.

---

### Post by bsalem on 2010-09-27
The "Some Contents Unreadable" generally means that you do not have permissions to read files in the directory. It can be caused by many different events. I get it on a busy NTFS (Windows) filesystem mounted by Linux.

Since the dir is /home it could be caused by you not having access to files on another subdir besides your home directory, such as another account's files. It can also be due to root owning /home. This is a good case where knowing the command line can tell you more than the file browser. If root created files in your home dir, that can cause it as well.

If your home dir is too large to fit on a stick, copy subdirs to the stick, also it is better for the stick to save archives than lots of small individual files. Learn to use the archiver programs or tar and zip from the command line to break the problem into smaller chunks. If I only have a few MB to copy I use tar from the command line. If I am doing incremental backups I use tar with find to select the newest files. You can get a full dump of a subdir that you know wll fit and use a combination of commands to create incrementals. This is not the time for details; go think of ways to whittle the problem down to a managable size, first.

---

### Post by oldsoundguy on 2010-09-27
> **psusi said:**
> When you format the drive, if you don't do it via the disk utility and check the box to take ownership, then the root directory is owned by root, so you can't write to it.  To fix it, do the following in a console:

sudo chown username.username -R /media/foo

Where username is your user name, and foo is the name of the disk.


THANK YOU .. Was using G-Parted (old habits die yard) .. never even NOTICED the "disk utility"!! OMG that makes it SOOOOOOO much easier

And guess what!!

FILES TRANSFERED AND VERIFIED!!


Thanks to all of you for your time and help .. now I can crash and burn and RESTORE.


Marking this as solved.

---

### Post by Crazedpsyc on 2010-09-27
Unfortunately, there are ways around that like on one brand of flash drive I have gotten it simulated (or one might call it spoofed) a disk that you couldn't unmount erase or format. I finally got rid of it with the uninstall option in the program itself, although I had to wipe it several times after that as well

---

### Post by oldsoundguy on 2010-09-27
An FYI .. I have using Lexar products for years starting back in the days of tape backup.  I use their CF cards and SD cards for photography and for my PDA units .. so it was automatic I would go with their flash drive .. simply because in over 10 years I have NEVER had a Lexar product go bad or give me any trouble .. but ONCE .. and that was MY STUPID FAULT for buying a CF card UNSEALED and it put a virus  on the Windows machine I was using .. took me about 12 hours to fix the damage to a machine that was NOT MINE! (they lacked an updated AV and it got through!!)

---

