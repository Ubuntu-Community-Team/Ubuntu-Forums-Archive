---
title: "Will I be able to Migrate everything in Karmic's /home partition to Lynx's /home ?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by mikodo on 2010-01-03
Hello everyone,

I want to do a fresh install of Lynx when the time comes. I have never migrated a back-up of a previous releases'/home. I have Karmic's /home on its' own partition and I will configure a /home partition for Lynx. I plan to use rsync/grsync to save Karmic's /home on an external usb drive.

So, will I be able to migrate everything in Karmic's /home to Lynx's /home using rysnc, from the external hard drive? Or, is this just wishful thinking? 

Is there a "best practice" way, to migrate the /home partition to a new release with a fresh install?

Any links that you can forward about this, would be very helpful.

Thanks.

---

### Post by jbrown96 on 2010-01-03
I've moved my /home several times, and it's very easy. When you install just select your /home partition and "edit" it. Chose the FS type and mount point, making sure that "format" is unchecked. That being said, that there is a slight possibility that an app may change it's config settings, which could cause your settings to not work. I've been migrating my settings for 2.5 years and have never had a problem. I have not heard anything about incompatibilities in 10.04 either, so you should be safe.

---

### Post by anewguy on 2010-01-03
I'm a little interested in this as well, as I understood the creation of a separate home partition allowed you to just install a new OS and keep your existing home partition, but I haven't done a new install with that yet to actually know how to do it.

Dave :)

---

### Post by mikodo on 2010-01-03
> **jbrown96 said:**
> I've moved my /home several times, and it's very easy. When you install just select your /home partition and "edit" it. Chose the FS type and mount point, making sure that "format" is unchecked. That being said, that there is a slight possibility that an app may change it's config settings, which could cause your settings to not work. I've been migrating my settings for 2.5 years and have never had a problem. I have not heard anything about incompatibilities in 10.04 either, so you should be safe.
 
Thanks for the reply jbrown96. So, you do this with a fresh install of a newer version all the time? During the install does the "edit" ask where to get the data for the /home? In my case I guess the external hard drive?

---

### Post by k3lt01 on 2010-01-03
I simply copy my /home to an external drive and copy it back after a fresh install. This accomplishes a couple of things:
1. I get to use the new settings before I copy things backe.g new folders in Karmic compared to Hardy and Intrepid and choose what I want to copy back over.
2. Copying your /home backup back to your pc helps to remove any fragmentation from the /home drive.

---

### Post by Methuselah on 2010-01-03
You can tell the installer where to find the various subfolders under root (/).
If you already have a separate partition for home you can point to it and set it to be mounted as /home.
However be doubleplus sure that you did not select 'format' or else bye bye data.
Unlike james96 I have never actually done this but many people report doing it with success.

EDIT: IMO k3lt01's method is 'safer' since you are forced to create a backup.
Really should backup anyway.

---

### Post by mikodo on 2010-01-03
> **k3lt01 said:**
> I simply copy my /home to an external drive and copy it back after a fresh install. This accomplishes a couple of things:
1. I get to use the new settings before I copy things backe.g new folders in Karmic compared to Hardy and Intrepid and choose what I want to copy back over.
2. Copying your /home backup back to your pc helps to remove any fragmentation from the /home drive.

Thanks for your reply k3lt01; Do you use a app like rysnc or anything else to do the copying or do you just copy and paste?

Thanks.

---

### Post by mikodo on 2010-01-03
> **Methuselah said:**
> You can tell the installer where to find the various subfolders under root (/).
If you already have a separate partition for home you can point to it and set it to be mounted as /home.
However be doubleplus sure that you did not select 'format' or else bye bye data.
Unlike james96 I have never actually done this but many people report doing it with success.

EDIT: IMO k3lt01's method is 'safer' since you are forced to create a backup.
Really should backup anyway.

Thanks Methuselah; I do backup with Sbackup now (Newbie still), but I don't like it much and want to learn rysnc.

Thanks for the clear instructions.

Mike

---

### Post by mikodo on 2010-01-03
Reading another thread just now, this site was suggested 

[http://seogadget.co.uk/the-ubuntu-installation-guide/](http://seogadget.co.uk/the-ubuntu-installation-guide/)

Seems it will helpful for me, and maybe other newbies who are also trying not to screw up installs. 

Thanks.

---

### Post by k3lt01 on 2010-01-03
> **mikodo said:**
> Thanks for your reply k3lt01; Do you use a app like rysnc or anything else to do the copying or do you just copy and paste?

Thanks.Just a simple copy and paste although I am going to start playing with syncing next time around.

Edit: and you are most welcome

---

