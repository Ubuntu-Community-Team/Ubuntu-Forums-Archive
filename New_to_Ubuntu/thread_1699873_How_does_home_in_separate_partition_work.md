---
title: "How does /home in separate partition work?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by tyler9 on 2011-03-04
I'm unclear about how a hard-disk partition for the /home folder works.

Say I want to dual-boot Ubuntu and Mint on a single hard drive. 

So each distro requires its own partition. If I create a partition for my /home folder, does that mean this /home folder is shared between these two distros? 

So if I work in Unbuntu and save file1.doc in Documents folder; then work in Mint and save file2.doc in Documents folder, both file1.doc and file2.doc are acessible from both distros?

I do want /home on a separate partition to protect it when I upgrade or reinstall Ubuntu/Mint. But I'm not clear on sharing; or whether I have to create a /home partition for each distro.

Am I understanding this correctly?

---

### Post by cek on 2011-03-04
In a dual boot situation, you will create separate root partitions (/), one for each distro.  Only create one /home partition, and during the install make sure each distro is using the same partition.

Then anything you have in /home will be available in both distros.

---

### Post by grahammechanical on 2011-03-04
My concern is with the hidden files in the Home Folder. I may be wrong but the two installations may have different configurations, or the same programs in each installation may have different configurations. This may cause conflicts and may require a format and re-installation to solve.

I experienced conflicts with the different Nvidia drivers that were activated and then de-activated to be replaced with a later version. I could not get enhanced appearance effects working. Then I re-formatted the /home partition, re-installed and now I have an enhanced desktop.

This I my worry and it stops me from assigning the same /home partition to more than one installation, even of Ubuntu (say 32 bit and 64bit) let alone different distributions.

Regards.

---

### Post by tyler9 on 2011-03-04
Thank you, cek.

"...and during the install make sure each distro is using the same  partition."

The choices will be in the installation UI, correct? If so, I'm probably competent enough to follow directions ;) but if not, I want to be prepared. 

So with a 500GB hard drive, for my setup, I'll need partitions for
Ubuntu
Mint
/home directory
swap file

Does this look correct for a low-demand home desktop user? I don't have many large files--no video, images, music--mostly documents.

Edited to add:
grahammechanical:
"My concern is with the hidden files in the Home Folder. I may be wrong  but the two installations may have different configurations, or the same  programs in each installation may have different configurations. This  may cause conflicts and may require a format and re-installation to  solve."

Uh-oh. A complication. I shoulda known...

What about this: Is it possible to make only one folder shared? Such as /home/tyler9/Documents?

Whether I do this or not, as a technical Q I'm wondering.

---

### Post by garyed on 2011-03-04
This is interesting with using more than one version of Ubuntu.
Is it safe to use the same home partition between different versions?
Can't it cause a conflict with different programs & setups of different versions etc..?
I've been afraid to do it.

---

### Post by stoogiebuncho on 2011-03-04
> **grahammechanical said:**
> My concern is with the hidden files in the Home Folder. I may be wrong but the two installations may have different configurations, or the same programs in each installation may have different configurations. This may cause conflicts and may require a format and re-installation to solve.

I experienced conflicts with the different Nvidia drivers that were activated and then de-activated to be replaced with a later version. I could not get enhanced appearance effects working. Then I re-formatted the /home partition, re-installed and now I have an enhanced desktop.

This I my worry and it stops me from assigning the same /home partition to more than one installation, even of Ubuntu (say 32 bit and 64bit) let alone different distributions.

Regards.

This.

It's not a good idea to use the same /home partition for different linux distributions because it can really mess up your settings.

If you want to have a place to share files between OSes on a dual boot, you'd be better off to set up a separate partition for that purpose.

Alternately, you could set up a /home partition in one OS, and then mount it in your other OS.  As long as you're not mounting it as the /home folder in the second OS, you shouldn't have any problem with settings conflicts.

---

### Post by tyler9 on 2011-03-04
Thanks, stoogiebuncho.

"If you want to have a place to share files between OSes on a dual boot,  you'd be better off to set up a separate partition for that purpose."

Would this be as simple as making a partition for a directory named Shared containing the subdirectories I need--Documents, Photos--and then mounting Shared in whatever distro I boot into?

"Alternately, you could set up a /home partition in one OS, and then  mount it in your other OS.  As long as you're not mounting it as the  /home folder in the second OS, you shouldn't have any problem with  settings conflicts."

So if I have /home partition for Ubuntu, then boot into Mint, I can access this /home directory that's on the Ubuntu partition? If so, then as long as my mount point/directory is not the root  /  there's no prob? And since I'll have a partition for /home in each distro, this causes no prob?

---

### Post by stoogiebuncho on 2011-03-04
> **tyler9 said:**
> 
Would this be as simple as making a partition for a directory named Shared containing the subdirectories I need--Documents, Photos--and then mounting Shared in whatever distro I boot into?


Yes, that's all you would need to do.

> **tyler9 said:**
> 
So if I have /home partition for Ubuntu, then boot into Mint, I can access this /home directory that's on the Ubuntu partition? If so, then as long as my mount point/directory is not the root  /  there's no prob? And since I'll have a partition for /home in each distro, this causes no prob?

This is also correct.  If your partition is mounted as /home in Ubuntu, all you have to do is make sure that it is NOT mounted as /home in Mint and your settings will be fine.

Having a shared partition is probably the less confusing option, but it does require setting up one more partition.  Either method should work.

---

### Post by spillin_dylan on 2011-03-04
The other alternative to sharing a /home between distros (and even different versions of the same distro) is to use one /home partition, but have different usernames on each distro, so that they still have all their own separate configurations (i.e. .gnome2/ folders, etc...)  You might need to do some work to solve permissions issues, but it certainly is possible.  

I personally have 3 versions of Ubuntu and Debian Lenny all happily sharing a home partition with the same user, although I generally only boot Ubuntu 10.04, so the others sometimes need a little tweaking....

---

### Post by tyler9 on 2011-03-04
For an example, if I'm in Mint and want to see existing hard drive partitions, is there both a GUI and command-line way of doing this? 

And for a /home directory existing on its own partition, what GUI or commands are used to mount this /home directory?

---

