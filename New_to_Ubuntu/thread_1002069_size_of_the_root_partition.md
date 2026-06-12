---
title: "size of the root partition"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-12-04
hi everyone.i am using hardy heron with a root partition sized 20 GB.can the bigger size of the rot partition slow down ubuntu?is it true that my system would have been faster if i had restricted its size to say,10 GB?

---

### Post by mbsullivan on 2008-12-04
> can the bigger size of the rot partition slow down ubuntu?is it true that my system would have been faster if i had restricted its size to say,10 GB

Nope. Not a worry.

Partition voodoo for speed (such as locating your swap disk @ the center of the platter and creating a small ext2 /boot/ partition) really don't matter, anymore. Furthermore, I don't think that a root drive was ever really something that people did for speed.

The one thing that might make a moderate speed difference for your / partition is to format it to be ext3, instead of xfs. Ext3 tends to be slightly better for handling many small files (like are common on /), whereas xfs typically wins out on operations with large files (like may be common on /home/, if you keep a separate partition). 

In general, though, this topic is **not** worth any consternation.

Mike

---

### Post by mapes12 on 2008-12-04
The size of /(root) will have no impact on the speed of your system. What leads you to believe that this is an issue?

BTW - Swap should be circa twice your installed RAM. This may impact but only if RAM is struggling with high demand applications like video and games.

---

### Post by garwaymatt on 2008-12-04
I am fairly sure it wouldn't make any difference to the speed.

---

### Post by stonecoldjha on 2008-12-04
i am presently using a resierfs (instead of ext3) root partition.my system becomes pretty inresponsive and slow when i am moving a big directory(say almost 30 GB) from one partition to the other.is this fairly common?my specs are pretty decent if not very good,i mean i have 2 gigs of RAM,a 2 GHz Core2Duo processor,an nvidia Geforce 6200(256 MB).

---

### Post by scorp123 on 2008-12-04
> **stonecoldjha said:**
> i am presently using a resierfs (instead of ext3) root partition.my system becomes pretty inresponsive and slow when i am moving a big directory(say almost 30 GB) from one partition to the other. ReiserFS is good for tons of small files but sucks at handling large files. For tons of large files I'd prefer XFS. Ext3 is somewhere in the middle (which makes it a good allrounder). I would assume that the issue you experience is because of ReiserFS and maybe small RAM? Filesystem performance can be greately increased if there is enough RAM around which can be used for caching. Also: how exactly are you moving those 30 GB? Based on my experience I'd recommend "rsync" for such large transfers (or "grsync" if you prefer to have GUI for this one) instead of "cp" or "drag & drop" in a file manager. "rsync" does a better job at buffering and caching the stuff it has to copy. Depending on what you are copying you might get more performance out of your system if you used "rsync", IMHO.

---

### Post by stonecoldjha on 2008-12-04
i straight away right clicked a directory titled music(that contained over 30 GB music)and chose 'cut',then went to another partition and pasted.how do i install rsync and use it?

---

### Post by stonecoldjha on 2008-12-04
also,when i tried using xfs for root partition,i was given a message during installation that it is not compatible with GRUB,and i should better use LILO.my question is how to use xfs as root file system?

---

### Post by Paqman on 2008-12-04
> **stonecoldjha said:**
> how do i install rsync and use it?

Rsync is built-in, but it's a command line app. If you want a GUI for it, try grsync as suggested.

(G)rsync is a very cool tool. Say you want to move a folder to a backup location. Rsync can do that, and will act similar to a copy/paste. The really cool part is that if you changed a few files in the source folder, then did the rsync again, only the changes would be transferred, making it extremely fast. This makes it very popular for backups.

---

### Post by scorp123 on 2008-12-05
> **stonecoldjha said:**
> also,when i tried using xfs for root partition,i was given a message during installation that it is not compatible with GRUB,and i should better use LILO.my question is how to use xfs as root file system? UNIX-style partitioning, e.g. you'd make a separate /boot partition (120M is enough) and make that one Ext3 (so GRUB has nothing to complain about), and you make the rest (/, /usr, /opt, /var, /home, /tmp ... yes, I'm old-school) or just "/" in your case XFS.

---

### Post by nakama85 on 2008-12-05
in response to the original question.
Size wont make a difference.
The only thing that may make a minor difference is placement

If root is on the first part of the disk you will have slightly faster access due to how many times the disk has to rotate for the head reader to read information (I know I slaughtered this explanation).

I hope you understood.

Conversely that means your home partition is further out on the disk making it slightly slower to access information. However in truth you wont notice much of a difference at all if any.

---

### Post by scorp123 on 2008-12-05
> **stonecoldjha said:**
> how do i install rsync It's already there.

> **stonecoldjha said:**
>  and use it? Please read the manual for all options: ```
man rsync
``` (use the cursor keys to navigate; press Q to quit)

If the command line is not for you (why not??? It's a powerful and useful tool and worth learning!!) search "Synaptic" (System > Administration > Synaptic) for "grsync". That's a graphical front-end.

Command line "rsync" example: ```
rsync -av --progress ~/Music/* /path/to/backup/Music/
``` ... that would copy all files and folders underneath the "Music" folder in your home directory to a location "/path/to/backup/Music/" ... it would only the files that are different and skip what's already there. The parameter "-a" means that it should keep file permissions intact (usually this a desirable feature), "-v" means that it should give feedback about what it is doing ("verbose") and "--progress" means that it should show a progress bar for every file that it is copying (it's easier to spot where it gets stuck that way).

---

### Post by stonecoldjha on 2008-12-05
as far as upgrading RAM goes,i am a bit skeptical about that because when i open the system monitor while such a huge directory is being moved,i hardly see some 400 MB being used out of 2 GB.would it not remain the same,if the RAM were 4 GB or something higher?also,is there a way to ensure that the unoccupied RAM is made use of in such heavy processes so that the system doesn't slow down?

---

### Post by scorp123 on 2008-12-05
2 GB of RAM should be enough.

---

### Post by stonecoldjha on 2008-12-05
so then why does it slow down while i do such things?

---

### Post by malathion on 2008-12-05
> **stonecoldjha said:**
> so then why does it slow down while i do such things?

Because you are using the wrong file system, as other users here have explained to you.

---

### Post by stonecoldjha on 2008-12-05
please tell me what i should use?

---

### Post by stonecoldjha on 2008-12-05
today i was using a program devede and while it was at work(for about 2 hrs.),it had brought down my system to the knees,i mean it had made it pretty slow.i was in fact invoked of the memories of my good old windows days.how is that?my system specs are pretty fine.

---

### Post by Paqman on 2008-12-05
> **stonecoldjha said:**
> please tell me what i should use?

Simple solution: ext3 all the way
More techy solution:

> **scorp123 said:**
> UNIX-style partitioning, e.g. you'd make a separate /boot partition (120M is enough) and make that one Ext3 (so GRUB has nothing to complain about), and you make the rest (/, /usr, /opt, /var, /home, /tmp ... yes, I'm old-school) or just "/" in your case XFS.

---

