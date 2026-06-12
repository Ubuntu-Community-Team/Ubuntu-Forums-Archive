---
title: "Should I reinstall or is there a better way."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by hortstu on 2010-05-04
First here's how I have my drive is partitioned...

```
all the partitions are under one extended partition sda1

sda5.....ext3.....hardy heron...............14.3GB
sda6.....ext3.....hardy home................2.86GB
sda7.....ext3.....lucid.....................14.3GB
sda8.....ext3.....lucid home (nope).........2.86GB
sda10....ext3.....shared data storage.......109GB
sda9.....ext3.....swap......................5.72GB
```

Now I had it set up, when I installed hardy, to put my lucid home in a separate partition but I accidentally put it in the same partition as the lucid OS.

I've only put about 2 hours into setting up lucid and getting it the way I want it.  I've got a long way to go.  Should I reinstall lucid or is there an easier faster way to move my /home to the partition that I want it on?

Thanks

---

### Post by philinux on 2010-05-04
You could back up your home folder including the hidden config folders and then restore it after the reinstall.

Or there is this.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I would choose which ever was the quicker.

---

### Post by xumuk37 on 2010-05-04
I would re-format /dev/sda10 as /home and copy there all from /dev/sda6or8, then just reinstall lucid wherever you want and point /dev/sda10 as /home without formatting...

---

### Post by hortstu on 2010-05-04
> I would re-format /dev/sda10 as /home and copy there all from /dev/sda6or8, then just reinstall lucid wherever you want and point /dev/sda10 as /home without formatting... 

Thanks xum but that's my data partition.  I keep everything there documents pictures etc.  If I format that I lose everything.  That partition is much more important than any OS.

---

### Post by xumuk37 on 2010-05-04
delete patitions that you don't need and move data there...

---

### Post by hortstu on 2010-05-04
> delete patitions that you don't need and move data there... 

Thanks but until I get lucid set up the way I want all partitions are in use.  Eventually hardy won't be necessary anymore.

---

### Post by xumuk37 on 2010-05-04
It's what I'm trying to tell)

---

### Post by galdren on 2010-05-04
another tip: save a list of all the packages you have installed so you can reinstall them all easily when you've upgraded.

as for the home dir...yea just make a backup somewhere...friend's pc, usb drive, burn to a disc, anything..

---

### Post by sadaruwan12 on 2010-05-04
> **xumuk37 said:**
> delete patitions that you don't need and move data there...

His correct and to add something it seems like you have your lucid home folder in a separate partition so just leave it like that and reformat the lucid root partition and install the OS there after you reboot your system will be as same with themes and any other modifications but you've to install any programs that you've installed during your earlier lucid installation.

---

### Post by exodus_ on 2010-05-04
Do I understand correctly that you meant to put /home for lucid in /dev/sda8, but instead you skipped that step and /home is on /dev/sda7 with the lucid release?

If this is the case, you could simply make a copy of your home directory somewhere outside the /home directory and then edit /etc/fstab to mount sda8 as /home.  You could then mount /home copy your home dir back, and it will always mount at bootup since it will be in /etc/fstab, just like it would have been if setup had been configured to do so :)

If this is the case, I would be happy to help you do this.

---

### Post by sandyd on 2010-05-04
no need for reinstall. in nautilus, click show hidden files. copy all files from your current home folder to the data partition. (im on my phone right now) so im going to let someone else explain how to mount the data partition using fstab. it should be mounted to /home/username. existing /home/username folder contents (including hidden files) must be deleted first or weird things may happen.

---

### Post by hortstu on 2010-05-04
[QUOTE=exodus]Do I understand correctly that you meant to put /home for lucid in /dev/sda8, but instead you skipped that step and /home is on /dev/sda7 with the lucid release?[/QUOTE]

Yes.  I didn't skip the step I just did it wrong but you understand the results.

I have an idea about what you're saying but I think I need a little bit more guidance accomplishing the goal the way you describe.  Thanks for the offer I'd gladly take you up on it.

---

