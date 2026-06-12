---
title: "Can't empty trash - other fixes don't work!"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2009-03-09
I tried to download something today, only to be told that I had literally 0 space left on my hard drive.  I deleted a lot, tried to empty the trash, and it stalled.  Now it says the trash has been emptied, but there's still no space.

I've found other fixes for this, but they all involve going to some sort of trash folder, which I don't seem to have.  Any ideas?  I'm using Intrepid, if that helps.

EDIT: Permissions are not the problem.

---

### Post by scragar on 2009-03-09
Intrepid moved the trash folder. It's in **~/.local/share/Trash** now I think.

---

### Post by unknownwarrior33 on 2009-03-09
If only it were that simple.  I don't have a trash folder there, or anywhere.  I did a search of the entire hard drive, and there was no trash folder anywhere on the entire drive.  Note that it's still saying the trash is empty, but that I have no space.  I even tried making a dummy trash folder in the correct location, but it wouldn't let me because it said there wasn't enough space.

---

### Post by unknownwarrior33 on 2009-03-09
I played around with some things, and found that when I try to delete something, it says it can't send it to the trash, giving this reason:

```
Unable to create trash dir /home/jake/.local/share/Trash: No space left on device
```

and says it has to delete the file immediately rather than putting it in the trash.  But, it doesn't actually free up any space.

EDIT: Another oddity: I'm installing updates, and I'm not getting any errors about lack of space.

---

### Post by cariboo on 2009-03-09
I would suggest you ope a Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and 

```
sudo apt-get autoremove
```

The first command will clean out the archived packages in /var/cache/apt/archives, the second command will remove unneeded dependencies.

One of the first things I do is get rid of the trash icon and go to Places-->Home Folder-->Edit-->Preferences-->Behaviors, and enable Include a Delete Command that bypasses Trash

Jim

---

### Post by Berserker v7 on 2009-03-09
If you use torrent clients like Vuze to download and delete some downloaded files without removing their corresponding entries from vuze, they dont show the disk space as freed. You will have to remove those entries to get back the space... hope this helps :)

---

### Post by mc4man on 2009-03-09
You might as well take a look at 
df -h
df -i


> One of the first things I do is get rid of the trash icon and go to Places-->Home Folder-->Edit-->Preferences-->Behaviors, and enable Include a Delete Command that bypasses Trash

There's another file management in gksudo nautilus, I tend to stay away from except for the same, it bypasses the root trash

---

### Post by unknownwarrior33 on 2009-03-09
Thanks very much; that definitely freed up some space, and it appears that deleting in general is working properly now.  However, it didn't free up the 20+ gigabytes that should have been freed from the things I deleted when I learned of this problem.  Any ideas on fixing that?

---

### Post by unknownwarrior33 on 2009-03-15
It appears this isn't a permanent fix; I keep having the same problem over and over.  Any thoughts on why?  Thanks in advance.

---

### Post by drs305 on 2009-03-15
You might want to take a look at the tutorial in my signature line. It deals mostly with finding and deleting hidden trash files but covers some other methods to find out what is taking up the space.

Often a system that keeps filling up is a backup program saving data to /media/xxx instead of to the device that is supposed to be mounted on /media/xxx.

---

### Post by unknownwarrior33 on 2009-03-17
The thing is, following previous advice in this thread, I've started just deleting things instead of putting them in the trash.  The thing is, I'll delete stuff permanently and the freed space won't be reported.  So, if it says I have 10 GB free, and I delete 7 GB permanently, it will still say I have 10 GB free.  Nothing in Trash folders, nothing in lost+found; it just acts as if the files are still there.  I currently have at least 10 GB unusable because of this.

---

### Post by drs305 on 2009-03-17
This is puzzling. Using SHIFT-DEL should immediately increase the available free space by the size of the deleted file.

Have you run the following to ensure you have located all your trash bins?
```

sudo find / -type d -name *Trash* 

```
If you find any entries you can open a file browser with "gksudo " and manually remove the Trash folder and subfolders with SHIFT-DEL to delete them and free up space. If you just hit DEL on a trash folder it will just move it to ... the trash! Use caution with SHIFT-DEL since anything you delete via this method is not recoverable.

If you still have problems, please tell us the method you are using to report the resulting free space (system monitor, baobab, du, df, etc.)

---

### Post by unknownwarrior33 on 2009-03-19
I'm running that search now.  I've been using nautilus to find my free space, by right-clicking in my home folder and clicking Properties.

---

### Post by unknownwarrior33 on 2009-03-20
No luck from the search.  Here's something weird that I've noticed though: if I do that sudo apt-get autoremove thing, anything I delete afterwards will actually delete.

---

### Post by drs305 on 2009-03-20
> **unknownwarrior33 said:**
> No luck from the search.  Here's something weird that I've noticed though: if I do that sudo apt-get autoremove thing, anything I delete afterwards will actually delete.

This could be freeing up just enough space to allow you to delete a small amount of trash. If it's a space problem SHIFT-DEL should work, but from your posts I am guessing it is not.

mc4man asked you to run "df". If you run "**df -h**" do you have much free space left on your system partition? Other than a space issue, I don't know why your deletions aren't working.

---

### Post by unknownwarrior33 on 2009-03-21
df is showing the same amount of remaining space as nautilus, unfortunately.

---

### Post by gali98 on 2009-03-21
You might check with a ubuntu live cd with df and see if the disk usage is still reported the same... if so your filesystem may be a bit wacky and:
You probably need to fsck it...
You will need to do it when the filesystem is not mounted...
So boot into a ubuntu cd or some kind of linux cd.
(I will assume you are using the ubuntu one...)
Get to a terminal and make sure the disk is not mounted:
sudo umount -a
then fsck it...
sudo e2fsck -p /dev/sda1
(This will assume that your filesystem is in fact at /dev/sda1... You may have to root around, but it should be that one..)
That has fixed problems like this before for me. Hope it helps...
Kory

Be very careful when doing all this. Do not under any circumstances run fsck on a live system.. (i.e. running a check on a filesystem that is mounted..)
I accept no responsibility if you hose your system. yada yada... Use at your own risk. :)

---

### Post by halitech on 2009-03-21
could you post the results of df -h for us to look at?

---

