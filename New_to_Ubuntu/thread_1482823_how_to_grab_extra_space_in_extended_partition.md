---
title: "how to grab extra space in extended partition"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by eddski on 2010-05-14
I have my ubuntu distro in an extended partition and i have some room at the end of the extended partition. is there a way to use some of that room for other partitions inside the extended partition? can i only add size if it directly adjacent to the empty space?. Ex. my /home is 60% full and I give it more space, can it be done? thanks in advance

---

### Post by Paqman on 2010-05-14
You can slide partitions across so that the empty space is anywhere, but it will be very slow, because it basically involves copying the whole partition from one place to another.

To make any changes to partitions that your system is on, you'll need to boot up into your LiveCD. Partitions can't be modified while they're in use. By default the LiveCD also mounts your swap partition to improve performance. To unmount it, simply right click on it in Gparted and "swapoff".

---

### Post by BoneKracker on 2010-05-14
Back up your data first.

---

### Post by srs5694 on 2010-05-14
Another option is to create a new partition wherever it's convenient in partition/physical layout terms and then mount that partition where it's convenient in directory structure terms. For instance, if you've got 50GB of free space that's not adjacent to your /home partition but you want to expand /home space to store digital photos, you could create a 50GB partition, mount it at /home/yourname/photos, and then create or copy digital photos into /home/yourname/photos. This is not as flexible as expanding /home because you'll be limited to 50GB for /home/yourname/photos and you won't be able to use that space for other purposes. (Well, not without employing other workarounds, such as additional partition splits or symbolic links.)

FWIW, it's awkward changes like this that make me like [Logical Volume Management (LVM).](http://tldp.org/HOWTO/LVM-HOWTO/) Instead of putting filesystems on inflexible partitions, you put them on logical volumes, which can be added, deleted, expanded, and shrunk much like files, without concern for where they exist on a disk, in a sector-by-sector sense.

---

### Post by BoneKracker on 2010-05-14
I started to say that but was feeling lazy. :)

That's also a good way to have an encrypted directory for sensitive stuff, to put more restrictive mount options on a subset of your files, or to use a different filesystem for a particular type of file (e.g. a whole lot of small files or huge files).

LVM makes sense on a stable system or one with rolling release (where you're not rebuilding it every six months because somebody dropped the "upgrade" bomb on you).

---

### Post by Elfy on 2010-05-14
I would +1 the make a new partition and mount it option.

What you need to remember as well is that to add space to a logical partition inside the extended - you need to resize the extended before it will be there for to add to the logical.

+1 to back up as well ;)

---

### Post by eddski on 2010-05-15
thanks guys, it worked exactly to what I wanted and more(a complete backup)! The only problem is it took a very long time. I had to move the swap file, maybe that's why ,but thanks again for the instructions.

---

### Post by BoneKracker on 2010-05-15
Glad you succeeded.

For future reference, moving the swapfile was a waste of time.  Swap is throw-away.

Assuming you were booted from a CD, your on-disk swap filesystem is trash.  You could have just deleted the partition and made a new one in the new location (with the command 'mkswap /dev/whatever'.  Much faster.

Even if you were using some kind of live cd that's too smart for its own good and automatically making use of your on-disk swap partition, you just say 'swapoff /dev/whatever' and then delete the partition.

---

### Post by eddski on 2010-05-16
for bonekracker, could you give me a little more info on those commands, im still new, sorry about that.

---

### Post by BoneKracker on 2010-05-16
Some live cds will look for a swap partition on the disk and activate it.  Some won't.  I don't know if yours does.  If you boot up from the cd, open gparted, and can delete the swap partition, then you don't need to know any of this for now (unless you're just interested).

_More information on those commands:_
Open a terminal and type```
man swapoff
```
(press q to exit)

Then type```
man mkswap
```

_For some other time:_ There is a man page for virtually every command on a Unix-like system. (Try 'man man' first, to learn about the man pages (manuals).  Then to learn some command-line basics, explore 'man cd', 'man ls', 'man less', 'man cp', 'man mv', 'man chown', 'man chmod'.  To edit a file in the terminal, you can just type 'nano filename'.

_As a quick example for above:_

To see what you're swap partition is, just type:
grep swap /etc/fstab

(see 'man grep'; grep is how you search for a line in a file; grep is very useful and fast)

Let's say that says your swap parition is "/dev/sda8".

To turn off swap, you can type:
```
swapoff /dev/sda8
```

Or, to turn off all swap, you can just do
```
swapoff -a
```

Then you would proceed with what you were doing (I think you were using gparted).  After you had deleted the swap partition, made the extended partition larger, and created a new partition to hold swap, you would put a swap filesystem on that partition.  I gave you a command to do that (mkswap), but it occurs to me now that you can also put filesystems on partitions using gparted, so you don't really need it.  Anyway, it works just like the above:
```
mkswap /dev/sda8
```

---

### Post by eddski on 2010-05-17
thanks, i need to remember to look at man pages

---

