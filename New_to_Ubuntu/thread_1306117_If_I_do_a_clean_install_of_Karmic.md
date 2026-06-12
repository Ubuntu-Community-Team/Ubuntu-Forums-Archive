---
title: "If I do a clean install of Karmic"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-30
I have a 320Gig HD running Juanty with a seperate partition for the Home. If I do a clean install of Karmic will it cause me to loose my home partition? And if it works will the home partition work with Ext4?

---

### Post by philinux on 2009-10-30
> **captgadget said:**
> I have a 320Gig HD running Juanty with a seperate partition for the Home. If I do a clean install of Karmic will it cause me to loose my home partition? And if it works will the home partition work with Ext4?

Backup just in case.

Just dont format your home partition. **And dont just set ext4 for home it will trash your data**. To get ext4 for your home partition you'll have to back it all up, reformat to ext4 then restore your data.

---

### Post by captgadget on 2009-10-30
So what you are saying is that the existing home partion will not run with Karmic. Is that correct?

---

### Post by VastOne on 2009-10-30
> **captgadget said:**
> So what you are saying is that the existing home partion will not run with Karmic. Is that correct?

It will. You have to be careful in setting what file type (ext3, ext4). If you are running Jaunty in ext3 I would stay with it through the new install and then convert to ext4 after you have installed Karmic. 

Te selection process of your drive and partitions is very important, make sure you get it right.;)

---

### Post by alphaniner on 2009-10-30
Just don't format the partition /home is on.  Tell the installer to mount it on /home, but make sure it doesn't format it and **don't** set the filesystem type to ext4.

If you are unsure about *anything* during install, post screenshots.

---

### Post by Dougie187 on 2009-10-30
> **captgadget said:**
> So what you are saying is that the existing home partion will not run with Karmic. Is that correct?

no that is incorrect. Karmic just formats all partitions to ext4 by default, but karmic can still read ext3 partitions. As long as the / partition is ext4 karmic shouldn't complain. The /home partition can be whatever you want, preferably ext3/ext4.

He is just saying that if your /home is ext3 now, and you do a clean install of karmic without reformatting /home then /home will not be ext4. To get /home to be ext4 you have to backup all of your data in /home, format it to ext4, and then replace all of your data.

---

### Post by bobbob1016 on 2009-10-30
> **philinux said:**
> Backup just in case.

Just dont format your home partition. **And dont just set ext4 for home it will trash your data**. To get ext4 for your home partition you'll have to back it all up, reformat to ext4 then restore your data.

No, he is not saying that at all.  He is saying just to make sure you pick the same partition type.  For instance, if your /home is ext3, select ext3 in the installer.

Open a terminal, and type "gksu gparted" without quotes.  Find /home, and note what the partition type is, along with any other data partitions.

Start the Karmic install.

On the "partition" section, select Manual.

*****YOU WILL USE YOUR DATA IF YOU CHECK FORMAT THIS DRIVE OR MARK*****
*****IT AS A DIFFERENT PARTITION TYPE THAN IT ACTUALLY IS**************
(the default under Ubuntu for the past few years is ext3, if you originally formatted them with Ubuntu, they are probably ext3)

Find your /home partition and click Edit, then set it as the partition type you noted before, and set "use as" to /home.

Find your / (or your root partition) and set that to ext4 and you can format / only if you are 100% sure your home and your / are on different partitions.

Select your other partitions, and do the same, you have to say "mount at /media/drive1" or wherever you want it to mount.

I did these steps, and it worked fine.  But as stated above, backup just incase.

---

### Post by captgadget on 2009-10-30
Thanks, I will try it tonight after doing a backup!

---

### Post by VastOne on 2009-10-30
> **captgadget said:**
> Thanks, I will try it tonight after doing a backup!

Great idea and if you run into any issues, we will be here to help

---

### Post by captgadget on 2009-10-30
I left my home partition as Ext3 and everything seems to work. Is it necessary to format to Ext4? One other question - my resolution is only 800 X 640. Is there a way for me to get better?

Thanks

---

