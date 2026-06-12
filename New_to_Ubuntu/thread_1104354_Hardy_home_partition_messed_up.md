---
title: "Hardy home partition messed up"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-03-23
Last night I attempted to move my /home to another partition. Things did not go to well. I followed the guide at [psychocats.net]("http://psychocats.net/ubuntu/separatehome") as closely as I could but unfortunately was left with an un-bootable system. I do have a live CD and can get to the desktop that way but am rather helpless navigating in the terminal to edit various files or folders. 

I successfully created a new partition that is in ext3 format. My old/present /home resides on /dev/sda6 and the new partition is on /dev/sda8. My old partition (sda6) is now completely full as a result of backing up my /home on that partition. The new sda8 partition now (as of this morning) has a complete copy of my present sda6 partition but only has less than 2 gigabytes free. 

My immediate problem seems to be how to edit the /ext/fstab file using the live CD - it doesn't want to let me replace fstab with fstab_backup.

Another problem has to do with the state of my old/present home folder which now has a folder called home_backup under it. The home_backup folder has an empty remastersys folder under it, and a michael folder. Both of these folders have this morning's date on them - the last time I attempted to follow the directions on psychocats. 

Another home_backup folder also exists. Under it are three folders, home, michael and remastersys. The home folder is empty as is the remastersys folder. the michael folder appears to be full and the folders and files under that folder appear to have original file dates extending from about a year ago. 

Could one of you nice folks please give me a hand in rectifying this mess?

---

### Post by drs305 on 2009-03-23
Let's just start with being able to access your files.

Boot to the livecd. Open a terminal (Applications, Accessories, Terminal).

Make a new mount point, mount your old sda6 partition, and open a root file browser to move or delete files from your original home. (You might instead want to just try to restore everything the way it was before to get your system working again.):
```

sudo mkdir /mnt/sda6
sudo mount /dev/sda6 /mnt/sda6
cd /mnt/sda6
gksudo nautilus /mnt/sda6
```

Repeat the process for your / partition so you can edit fstab. I guess it was also on sda6 but don't want to make any assumptions. (If it was on sda6, just "cd /mnt/sda6" and then proceed). Replace XX with the system partition (sdXX >> sda1 if sda1 is where your system is installed):
```

sudo mkdir /mnt/sdXX
sudo mount /dev/sdXX /mnt/sdXX
cd /mnt/sdXX
sudo cp etc/fstab etc/fstab.original # note there is no / before "etc"
gksudo gedit etc/fstab
```

---

### Post by Michael Dooley on 2009-03-23
Thanks drs305. I'll get back to you in about 30 minutes. You instructions look promising. Thank you for your swift reply.

---

### Post by Michael Dooley on 2009-03-23
drs305, your directions have put life back into the Hardy machine. In particular, your code directions -

```
sudo mkdir /mnt/sda6
sudo mount /dev/sda6 /mnt/sda6
cd /mnt/sda6
gksudo nautilus /mnt/sda6
```

enabled me to edit my fstab and my /home directory on my sda6 partition to the point that I could successfully boot that partition. Of course, it was pretty jammed with un-needed information, so I couldn't do much. 

I once again booted via the Live CD and investigated my new sda8 partition. It had a lot of stuff in it but not what I expected at all. I am resizing both partitions before I clean up sda6 and get it ready to be backed up properly. Then I'll see if I can use sda8 as my new /home partition.

Many thanks drs305. You have saved the local bacon here, that's for sure.

Got any advice on a possibly clearer set of directions for moving one's /home directory to another partition?

---

### Post by drs305 on 2009-03-23
> **Michael Dooley said:**
> 
Got any advice on a possibly clearer set of directions for moving one's /home directory to another partition?

Glad you have your system back up.

I haven't used psychocat's instructions in a long time but many have. Copy/paste often prevents mistakes, but with the number of user's of his instructions I am pretty sure they still are accurate.

Without knowing exactly where your problem occurred it would probably be difficult to find out where it went wrong. 

If you want to try some other links from the past year (which I have not tried):
[http://helpforlinux.blogspot.com/2009/03/move-home-to-its-own-partition.html]("http://helpforlinux.blogspot.com/2009/03/move-home-to-its-own-partition.html")

[http://www.ubuntu4life.com/node/30]("http://www.ubuntu4life.com/node/30")

---

### Post by Michael Dooley on 2009-03-23
> **drs305 said:**
> I haven't used psychocat's instructions in a long time but many have. Copy/paste often prevents mistakes, but with the number of user's of his instructions I am pretty sure they still are accurate.

That was my thought too. I am looking primarily to find some hidden, probably obvious step that I missed. And, I think that your first [link]("http://helpforlinux.blogspot.com/2009/03/move-home-to-its-own-partition.html") has already provided me with the unfortunate missing step. I'll let everyone know what happened once I successfully get /home transfered and running as expected.

Thanks for taking the time to help me and many others drs305.

---

### Post by drs305 on 2009-03-23
Glad to help. I'll be off the forums for most of the next few days.

Please post back, especially if you find the problem. And if you do, let us know what you did differently or which link you followed so others can bypass problem areas and proceed more directly to a solution.

---

### Post by Michael Dooley on 2009-03-31
Sorry to be so long in responding. I had other work to do... fortunately.

In the Psychocats "Create a separate home partition in Ubuntu" how-to, I somehow messed up on the following command sequence and did not copy my /home contents to the new partition but instead copied the Live Cd's /home contents. I expected to see a real long list of files being copied but saw something flash by in a few seconds. At this point I was suspicious - but not suspicious enough to stop following the directions and figure out what had gone wrong.

```
cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
```

Using drs305's directions above, I was able to see what had been accomplished (and what had not) and was able to mitigate my blunder to the point of being able to re-boot my old system with a functioning old /home. 

I had previously (right after my initial screw-up), tried using the code below that Psychocat had shown under the heading "What if it doesn't work?" but had mistakenly entered this code in a terminal using the Live CD.

```
chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit
```

I got a couple of errors including a "chown: cannot access /home/michael/.gvfs: Permission denied" error and things didn't improve as far as being able to boot into a working system. 

Upon rereading his instructions, I tried again - after I had successfuly copied my /home contents to my new partition. This time, I booted up using the recovery mode and entered the code above in the recovery terminal. That proved to be quite important and it did the trick.

The next time I rebooted, I had my new /home mounted and was ready to see if everything worked as expected - which it did, once I copied several files from /root to the new /home. These were text files that I had recorded in the interim so that I could tell what I had done to (1) get in this mess and (2) what I had tried to do to get out of it.

By the way, I discovered several rather interesting threads in the forums by searching on the /home tag rather than typing "/home" in the search box. I recommend this tactic to anyone else that might have some sort of problem after trying to create a separate /home partition.

One of the clearest descriptions I found on the net was [here]("http://www.everythingexpress.co.uk/index.php?option=com_content&task=view&id=17&Itemid=6"), marred only by faulty formatting that produced two number four steps and omitted a number seven step. Not perfect, but helpful in that it explained each step for the reader. I liked that.

Thanks again drs305. And all the others who answer questions like mine

---

### Post by drs305 on 2009-03-31
Thanks for taking the time to post the results of your efforts. It should help others who may be considering the same move. 

If you feel like a step needs to be clarified I'm sure psychocats would like to hear from you. Lot of users still refer to his instructions. There is a link at the bottom of his page with a contact link.

See you on the forums.

---

