---
title: "Partition nightmare!"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-09-24
I started using Linux almost a year ago and started with it only on my desktop (which was already partitioned). Then I decided to just clear the HD and install linux and windows side by side but made the mistake of installing them on the sdb hard drive (smaller) thinking that I would use the larger hard drive to house my /home folder. The set up is like this right now:

Hard drive A (/dev/sda) - 232.88gb
-Home partition (102.33gb)
-Storage partition (130.56gb)

Hard drive B (/dev/sdb) - 111.79gb
-Ubuntu partition (102.33gb)
-Windows partition (4.88gb)
-swap (4.58gb)

I want to change to a set up looking like this:

Hard drive A (/dev/sda) - 232.88gb
-Ubuntu (30gb)
-Windows (10gb)
-swap (2gb)
-/home partition (rest)

Hard drive B (/dev/sdb) - 111.79gb
-Storage partition

My question is:
1.Can I just back up my data, install linux on hard drive a, format a 10gb partition with partition editor, drop the windows files in there and change the boot set up? (I just really don't want to reinstall windows because I would have to figure out how to migrate all my ipod touch stuff over to the new install)

If i can't:
How do I install linux on the old partition in sdb that I have now and set it up to use the /home partition that I currently have set up in sda?

I thank anyone who has any advice in advance

---

### Post by mikewhatever on 2009-09-25
I think you can try cloning the Windows partition with Partimage, Clonezilla or Ntfsclone. Check if the cloned Windows works, if it does, install Ubuntu. I doubt simply copying the files would work.

As for the second option, that seems to be your current setup. Do you want to reinstall Ubuntu?

---

### Post by TadeoDiaz on 2009-10-16
Sorry for the delay in response (was out of the country).

I guess what I wanted to do is rearrange the partitions so that my home folder could have more space (it's currently full). But it makes more sense to just keep my same set up and reinstall ubuntu now that you point it out. Just a question:

If I reinstall ubuntu in the current ubuntu partition do I just select that partition when in the live installer? Would there be a conflict if I then reset the home folder to my home partition?

Thanks for your help in advanced

---

