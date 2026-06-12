---
title: "Mapping folders not working?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by jermza on 2011-07-04
I just recently installed 11.04 and then installed Ubuntu Tweak.  I have two hard drives, one with Ubuntu and the other with all my work files.

Ubuntu Tweak has some nice options, including one where you can create new paths to folders.  I simply changed the paths of Documents, Pictures, Music, *etc* to the corresponding folders on my second hard drive.

When I click on Home and then navigate to the changed folders, it doesn't take me to the changed paths.

Am I doing something wrong?

---

### Post by nothingspecial on 2011-07-04
I don't know anything about ubuntu tweak but,

go to your second harddrive, right click the music folder and select make link. Then move that link to your home folder, job done.

---

### Post by jermza on 2011-07-04
Yes, but doesn't that create another link instead of simply mapping the Home folders?  In other words, if I click on Home > Music, then it should take me to my music folder.

Are you saying that I must create the link and then delete the one in the Home folder?

---

### Post by nothingspecial on 2011-07-04
> **jermza said:**
> Yes, but doesn't that create another link instead of simply mapping the Home folders?  In other words, if I click on Home > Music, then it should take me to my music folder.

Are you saying that I must create the link and then delete the one in the Home folder?

That's what I've always done. See screenshot.

[ATTACH]196664[/ATTACH]

---

### Post by jermza on 2011-07-04
That's untidy and not how I had it before I re-installed Ubuntu.

There is obviously a way to map **Home > Music**
to **Home > [2nd hard drive] Music**

Which is what I did in Ubuntu Tweak, but it doesn't seem to do anything.

I had it like that but can't remember how I set it up.

---

### Post by nothingspecial on 2011-07-04
Suit yourself, you'll have to wait for someone who knows about tweak.

---

### Post by jermza on 2011-07-04
Well, if I click on Home Folder, it takes me to the default Home Folder.  I'd simply like, when I click on Home Folder (or Music, Videos, Pictures, etc), to open the corresponding folders on my second hard drive (rather than the one on which Ubuntu is installed).

Surely this is easy enough?

---

### Post by nothingspecial on 2011-07-04
That's exactly what using links does.

If you think the icons with the link arrows are untidy you can change them very easily.

---

### Post by jermza on 2011-07-04
I'll happily do that, but how does one change the Home Folder link?  In Unity, the uppermost launcher is Home Folder, for example.

---

### Post by nothingspecial on 2011-07-04
If you want the entire external disk (or a partition on it) as your Home folder, you'd be better off using it as a seperate /home partition.

---

### Post by jermza on 2011-07-04
Yes, that's what I'm asking...

---

### Post by nothingspecial on 2011-07-04
Does it already contain all the hidden files and folders from a previous installations home, or just your data (Videos, Music etc)?

---

### Post by jermza on 2011-07-04
It contains everything.  The previous installation was completely mapped to the second drive, so the second drive is a 100% replica, other folders included.

The default drive had - and currently has - nothing on it, other than Ubuntu.

---

### Post by nothingspecial on 2011-07-04
I'm in the middle of typing out another really long reply involving lots of sudo this and that and editing system essential config files.

If you would rather not do that (I or you might make a mistake), then perhaps, if you have not tweaked your installation yet, perhaps the easiest thing would be to reinstall and let the installer handle it.

The choice is yours.

To reinstall, go through the process again. When you get to the bit about how you would like to install Ubuntu, choose "Something else"

Select your internal drive and choose edit (or change), give it a mount point of /, select to use it as an ext4 journaling filesystem. Check/tick the format box.

Select your external /home partition and choose to use it as whatever file system it is, give it a mountpoint of /home but

[COLOR="Red"][SIZE="2"]**DO NOT TICK/CHECK THE FORMAT BOX**[/SIZE][/COLOR]

Make sure you have it correct.

Or, I could show you the hard way.......

---

### Post by Morbius1 on 2011-07-04
Let's say your 2nd HD is mounted at /mnt/Data and it has a subfolder named Documents. If you want the Documents folder in your home folder to point to /mnt/Data/Documents then use bind:

Try this out in a terminal first to see if it works the way you want it:
```
sudo mount --bind /mnt/Data/Documents /home/morbius/Documents
```If it works for you then you have a couple of options to make this happen at boot. One is just add the above line to /etc/rc.local right above the "exit 0" line. The other and dare I say more elegant way is to create your own upstart job. 

Either way you will have to make sure that /mnt/Data is automatically mounted first.

I don't like symlinks but that's me.

---

### Post by aeiah on 2011-07-04
> **Morbius1 said:**
> Let's say your 2nd HD is mounted at /mnt/Data and it has a subfolder named Documents. If you want the Documents folder in your home folder to point to /mnt/Data/Documents then use bind:

Try this out in a terminal first to see if it works the way you want it:
```
sudo mount --bind /mnt/Data/Documents /home/morbius/Documents
```If it works for you then you have a couple of options to make this happen at boot. One is just add the above line to /etc/rc.local right above the "exit 0" line. The other and dare I say more elegant way is to create your own upstart job. 

Either way you will have to make sure that /mnt/Data is automatically mounted first.

I don't like symlinks but that's me.

i always add them to my /etc/fstab file

```

/mnt/Data/Documents   /home/morbius/Documents none    bind  0  0

```

---

### Post by Morbius1 on 2011-07-04
@aeiah, 

That's the way I always did it in the past but it doesn't work reliably anymore because of some bugs in mountall ( at least I think that's where the bug is ). It still works in Debian but there's something in Ubuntu that makes it unpredictable. What appears to happen is the system will try to bind /mnt/Data/Documents before /mnt/Data is mounted.

The best solution ( for me ) when dealing with Ubuntu or any of it's derivatives is to create an upstart job and have it dependent on mountall finishing before the bind is executed.

It could very well be that the bug has been fixed and I can go back to using fstab but I haven't kept up with all the bug reports.

---

### Post by aeiah on 2011-07-04
ah, interesting. im still on 10.04 so haven't had issues with it. ill have to bear it in mind when doing a new install. hopefully it'll be fixed though because i have mount --binds coming out of the *** on my main machine.

---

