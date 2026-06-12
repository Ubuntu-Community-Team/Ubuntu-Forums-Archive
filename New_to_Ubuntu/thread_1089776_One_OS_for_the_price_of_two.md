---
title: "One OS for the price of two"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-03-07
HP-200Gig HD-D:/ 10 Gig partitioned backup, empty-3.2GHz-One Gig RAM, Had XP Pro, Service Pack 3 installed and doing well.  I have an Acronis cloned copy, on a 120 Gig External HD.  I wanted Ubuntu 8.10 as an alternative OS to work on the Internet, retiring XP from hazardous duty.  I planned to install 8.10 on drive D: and leave XP on drive C: so my son could play his games etc OFF LINE.  I didn't really know what I was doing and installed Ubuntu 8.10 on the whole HD, completely erasing XP Pro.  No disaster, I have the cloned copy on the external HD. The problem is I still do not know what I'm doing about getting the partitions right and the right programs in the right place, and absolutely do not want to mess up XP on the HD, as I do not have a CD for it.

---

### Post by starcannon on 2009-03-07
You will need to choose Manual when you get to the point of partitioning in the Ubuntu Installer. Then choose the location where you would like Ubuntu to reside. While your there, be sure to set up /home on its own partition. Root or / will be more than comfortable with 20gb, in fact I regularly set it up on 8gb, and on a few Asus Eee's set it up on as little as 4gb, create another partition >=Amount of System RAM installed in your machine (if you are planning a RAM upgrade go ahead and make swap >= the proposed RAM upgrade); Then give the rest to /home. Do not check the "format box" on any of the windows partitions, do format /home on this initial install, but in the future if you ever need to reinstall Ubuntu, or do a distribution upgrade, do not format your /home.

Or alternatively you can follow this guide, it should give you the jist of things, however it does not create a seperate /home partiton, it kinda does everythign for you. [http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html)

GL

---

### Post by Yed Ied on 2009-03-07
Should I do a quick wipe on the HD.  Ubuntu doesn't recognize drive "L" where the Ext.HD will be?  Then download the cloned XP and partition from XP?

---

