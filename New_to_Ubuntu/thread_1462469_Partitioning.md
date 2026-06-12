---
title: "Partitioning"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by llmunro on 2010-04-25
Hello!

I'm very impressed with the 10.04 RC version of Ubuntu and wanted to install it on my desktop so that I'd be dual booting Win 7 and Ubuntu.  At one point, I was dual booting Windows 7 and Linux Mint and at one point had to reinstall Win 7, which left me with a 17.7 GB partition left over from Mint (that is no longer available in the boot menu) that I'd like to install Ubuntu over.  

I am a bit confused about the partitioning process--when I run the Ubuntu installer, it correctly detects Win 7 as well as the Linux Mint partition.  I assume that I need to manually specify the partitions, but I'm a bit confused when I get to Step 5 of the installer.  I can see the Mint partition, which says "sda5 (ext4)" at the top with the colored bar and I can see it in the table below.  If I select the sda5 (ext4) from the table, my options are "change," "delete," or "revert."  What options do I need to select at this point so that I can install Ubuntu over Mint?

(Hope that makes sense...I'm glad to clarify if not!)

Any thoughts or ideas would be appreciated!
Thank you!
Best,
Lisa

---

### Post by oldfred on 2010-04-25
Welcome to the forums.

Did you select manual partitioning? You should just be able to choose the mint partition, tell/select it to be / (root) and tell it if you want it formated. If you have a separate /home of course you do not want to format that partition. In my install it found the existing swap(s) without any help. 

Total install took me 9 minutes into the partition I had for beta. It took longer to run all the updates than the install.

---

### Post by llmunro on 2010-04-25
Hello!  Yes, I selected manual partitioning and the installer found all the partitions automatically.  When I select the sda4 (ext4) from the list and click "forward" I get a message that says, "No root file system is defined. Please correct this from the partitioning menu."  I'm not sure what this means or what to do so that I can select this partition for the Ubuntu install.  

Thoughts?

Thanks much for your help!

Best,
Lisa

---

### Post by srs5694 on 2010-04-25
I haven't memorized the Ubuntu install process, but I believe you should select the target partition and then choose "change" from the menu. You should then be able to select options to create a new filesystem on (aka "format") the partition and set its mount point (which should be root, or "/").

---

### Post by llmunro on 2010-04-25
Aha!  It was setting the mount point that I couldn't figure out, but I think I've got it going now...at least, the installer claims that it is installing something somewhere! :)

Would this be the same process to follow to re-install Ubuntu 10.04 once the final version comes out?

Thanks for all the help! I'm really looking forward to trying out Ubuntu! :)

Best,
Lisa'

---

### Post by oldfred on 2010-04-25
It is my understanding that you do not have to reinstall as running all the updates will get you to the same as the new install.

I plan on reinstalling because I am testing my conversion process and will have a different partition to use as my working install. The beta partition will not then be used till the 10.10 version is out.

---

### Post by llmunro on 2010-04-25
Thanks so much for all of the help!  Ubuntu shows up on my start menu, along with Windows 7, so I guess I have done something right! 

And, congrats to the Ubuntu team--its beautiful and I'm looking forward to exploring it! :)

Happy Sunday!
Best,
Lisa

---

