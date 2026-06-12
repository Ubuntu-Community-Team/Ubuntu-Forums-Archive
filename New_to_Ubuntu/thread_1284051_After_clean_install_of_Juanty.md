---
title: "After clean install of Juanty"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-06
I no longer have a partition named Home. It got renamed to /media/disk-2. Is there a way now to point everything in the direction of that disk where I have all my information stored? Like now I have to reinstall the printer and now when I back up my gnucash I have to select that partition.

---

### Post by HarrisonNapper on 2009-10-06
Can you mount /media/disk-2 and then move it to /home/yourusername?

---

### Post by captgadget on 2009-10-06
It is mounted on the desktop but I'm sure how to move it like you are suggesting. I have to leave for work now and will check when I get back this evening.

Thanx

---

### Post by Sarmacid on 2009-10-06
You can use fstab to have the disk auto mount on startup.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Bölvaður on 2009-10-06
> **Sarmacid said:**
> You can use fstab to have the disk auto mount on startup.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
follow the instructions to mount it to something like /data

now press alt+f2
```
gksu nautilus /
```
right click on the directory linked for that partition you want, and create a symlink.
now drag that link to your /home folder, add .old to your user folder and rename it to your user name.

you will need to merge somethings (hidden files, ctrl+h)

---

### Post by HarrisonNapper on 2009-10-06
Why would he need to create a symlink? Couldn't he just cut/paste it as his actual home directory?

---

### Post by Bölvaður on 2009-10-06
> **HarrisonNapper said:**
> Why would he need to create a symlink? Couldn't he just cut/paste it as his actual home directory?

yes but then he would just be creating 2 sets of his homefolder that are identical. I guess he could delete one of them, but then he'd have an empty partition that isnt doing anything.

---

### Post by HarrisonNapper on 2009-10-06
True enough. I mean, I'm not dogging having your home folder on a separate partition; in fact, I'm a huge proponent of that strategy; I'm just saying if he does want it all on one, he could move it all to his native partition and use GParted to give him some extra space to use without having to worry about automounting.

---

### Post by captgadget on 2009-10-06
Boy! Now I am confused. I got the disk mounted as you can see in the screen shot. I included a screen shot of the gparted so you can see what is going on. My "old" Home folder is on the 105.0 GB Media. Now, I'd like to click places and have my home folder show up on the 105.0 GB Media. I have no idea how to create or what to do with a symlink so I'd need some direction here.

Thanx to you all.

---

### Post by Paqman on 2009-10-06
For future reference, when you reinstall you should pick "manual partitioning", select the partition with your old home folder, designate the mount point as /home, and make sure it isn't going to be formatted. The set up your root, swap, etc and your all set.

---

### Post by captgadget on 2009-10-06
Exactly what I did, but I didn't name it home since it was already set as home. So then I lost it and now I would like to have it recoginized. All my data is in there.

---

