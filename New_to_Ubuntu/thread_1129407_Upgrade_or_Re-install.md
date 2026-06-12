---
title: "Upgrade or Re-install?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by XubuRoxMySox on 2009-04-18
[COLOR="Purple"]**SOLVED! Hope this thread helps someone else:**[/COLOR]

I have 8.10 and the upgrade looks super easy - just like every other update. Awesome! But...

I'm hearing a lot of people with 8.10 say they're doing a fresh install of Jaunty when it's released, rather than an upgrade, so I have two questions:

1. - Is a fresh install *better* than an upgrade? And

2. - If I copy my [COLOR="Purple"]/home[/COLOR] directory onto a flash drive, will that work as a back-up for a either an upgrade *or* a new install?? If so, can I just copy-and-paste my saved [COLOR="Purple"]/home[/COLOR] directory into (or over) the new one?

That'd be just awesome if it's really that simple!

Thanks,
Robin

---

### Post by JakeHinojosa on 2009-04-18
heres what i know:

if you upgrade using the update manager, it will keep all of your files.

if you do a fresh install, all files are lost.

so you decide

---

### Post by RazVayne on 2009-04-18
I have (or better say I HAD) the same dilemma,but they I thought:It's and OS man!Its bloody important,ya know!...so Im gonna go with a fresh install...It seems like its also the general consensus of the Ubuntu population.

---

### Post by Bölvaður on 2009-04-18
well what you get by updating is that you keep the same programs as you have already installed, but just with new repositories behind them so they will probably be upgrated. Also all the config files in your /home will stay the same.

The reasons why some people do fresh install is because there is less odds of breaking hardware compatibility and also because having old config files may not do your new programs any good at all. (I should switch to my o.0 type of smiley face now...).

What I try to do is make a /data partition where I keep all my data and let all the config files keep being in the /home as part of the / partition.
But I either bookmark my folders in /data or make links (similar to shortcuts but only as a directory). That way I have all my data ready if I do fresh installs or install few OSes that I feel should be able to access my data like normal.

---

### Post by doas777 on 2009-04-18
> **JakeHinojosa said:**
> heres what i know:

if you upgrade using the update manager, it will keep all of your files.

if you do a fresh install, all files are lost.

so you decide

my recommendation is that next time you reinstall, you create a separate home partition for your profile data. that way you don't lose any files or settings, even if the system partition is reformatted. 

it also allows you to easily reinstall an os if something goes horribly wrong, and gives you increased security as you can set special mount options that can protect your systems from your users.

Reinstalls are usually recommend, as they process is much more predictable. there are a lot of automatic decisions in the upgrade algorithm that makes it more complex and less reliable. reinstalling the os from scratch and reinstalling your apps is usually much safer.

just my 2 bits

---

### Post by XubuRoxMySox on 2009-04-18
> **JakeHinojosa said:**
> heres what i know:

if you upgrade using the update manager, it will keep all of your files.

Yup, that's the assumption. But it doesn't sound wise to do such a major update without backing up all my stuff first, so **here's my only question now**:

If I copy my /home directory to a flash drive or a CD, is that a sufficient **backup**? Can I **restore** by just copying the saved /home directory back to the 'puter (overwrite or paste it into the "new" /home directory)?

Thanks very much,
Robin

---

### Post by RazVayne on 2009-04-18
> **dixiedancer said:**
> Yup, that's the assumption. But it doesn't sound wise to do such a major update without backing up all my stuff first, so **here's my only question now**:

If I copy my /home directory to a flash drive or a CD, is that a sufficient **backup**? Can I **restore** by just copying the saved /home directory back to the 'puter (overwrite or paste it into the "new" /home directory)?

Thanks very much,
Robin

Are you afraid of backwards compatibility?You shouldnt be...there is no problem regarding that,and a cd or flash should be enough of a backup...

---

### Post by XubuRoxMySox on 2009-04-18
> **doas777 said:**
> my recommendation is that next time you reinstall, you create a separate home partition for your profile data. that way you don't lose any files or settings, even if the system partition is reformatted.

That sounds like a great idea! How do I do that? Step by step please if you don't mind... or point me to the appropriate thread... how do I know what size and how to retrieve it and all that stuff. 

Thanks!
-Robin

---

### Post by leef on 2009-04-18
This thread covers how to do he back up;

[http://ubuntuforums.org/showthread.php?t=186310](http://ubuntuforums.org/showthread.php?t=186310)

if I were you I would just copy your home directory to the flash drive and when you go to restore it make sure that you give your new user owner ship of the directory otherwise you'll get errors.

```

sudo chown user -R /home/user

```

most settings are stored in hidden directories so copy the actual /home/**user** directory which will automatically get the hidden files in the user's home directory.

---

### Post by XubuRoxMySox on 2009-04-18
> **RazVayne said:**
> Are you afraid of backwards compatibility?You shouldnt be...there is no problem regarding that,and a cd or flash should be enough of a backup...

Omygosh, I'm scared of *everything* where 'puters are concerned, LOL! But maybe I haven't been clear about my question:

Copy my [COLOR="Purple"]/home[/COLOR] directory to the flash card to **back it up**, fine. Okay.

Now to **restore** it (assuming it got lost or I'm doing a fresh install), I just copy-and-paste my [COLOR="Purple"]/home[/COLOR] directory back *into* the new /home folder created by the new install? Or do I overwrite the new one with the old one?

The backup-and-restore threads I've been able to find here are about *applications* used to do it, but they're full of those scary command lines typed in a Terminal window. Yikes!! LOL, I'm scared of the terminal.

It just seems like it'sd be so much simpler to **back up** [COLOR="Purple"]/home[/COLOR] to a flash and then copy it into or over the new one to **restore** my fonts, documents, pictures, preferences, e-mail settings, bookmarks, all that.

Right?

Thanks again, and I hope this is more clear,
Robin

---

### Post by doas777 on 2009-04-19
> **dixiedancer said:**
> That sounds like a great idea! How do I do that? Step by step please if you don't mind... or point me to the appropriate thread... how do I know what size and how to retrieve it and all that stuff. 

Thanks!
-Robin

this tutorial covers how to create a seperate home partition AFTER haveing installed ubuntu: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

for creating a seperate partition at install:
1) backup your data to another location that will not be affected by this install
2) start the install  process and proceed until you reach disk partitioning
3) Select Manual Partitioning
4) you will be shown a list of your partitions and their types/sizes.
make note of which partition is which. be sure you can identify each of your partitions.
5) delete the previous ubuntu partition. you have already backed up your userdata, right?
6) create 1 4-8GB partition of ext2/3/4 in the unused space. set its mountpoint to "/"
7) you should see your previous swap partition. if you do not, create a 2-5GB swap partiton. 
8) create another partition with the rest of the unused space, of type ext2/3/4(whatever your preference) and set its mount point to "/home"
9) continue with your install until you are finally booted into ubuntu.

that should do it.
have fun

---

### Post by presence1960 on 2009-04-19
I backed up my /home partition and did a clean install of 9.04RC formatting / & /home to ext4. boot & shutdown time cut dramatically, speed is great and suspend/hibernate now works when it never did in 8.04 or 8.10 for me. Looks like a winner so far, but only time will tell!

---

### Post by DJonsson2008 on 2009-04-19
Dixie Dancer: You might consider using something like simple-backup-config as well if you have DVD or CD burner make a reduntant [another] backup of your files.

As a noobie I did not find anything extordinarily complicated about
restoration, 

I certainly was careful in making sure my new logon/password,
computer name and essential install parameters were EXACTLY the same as the old install.

simple-backup-config's default restore component also restores usr and var directories which i'm not sure those are necessary. in some cases I've use simple-backup-config to back up and then have used an archive manager to decompress and move the files manually rather than using simple-backup's restore gui.

Remember any method of effective backup includes multiple copies,
and that you only have as much secure storage as you have redundant backup.

Backup, reinstall and restoration is a slightly scary rite of passage with any OS, and its good to make a couple of drills of it before getting too far invested in any OS -- or have someone who can confidently do it for you. Whatever the case make sure you have multiple backups and the probability is good you can sort most of it out given sufficient time, on the restore.

---

### Post by 3rdalbum on 2009-04-19
Yep, copying your home directory to another disk and then copying it to the new system will work fine. Just make sure that you back up the hidden folders inside the home directory as they hold all your settings.

A lot of people are doing a fresh install so they can format their hard disks to the new ext4 format, which is said to give speed benefits.

---

### Post by Sef on 2009-04-19
> A lot of people are doing a fresh install so they can format their hard disks to the new ext4 format, which is said to give speed benefits.

ext4 is not yet stable, so if you prefer not to take chances, use ext3 still.

---

### Post by presence1960 on 2009-04-19
> **Sef said:**
> ext4 is not yet stable, so if you prefer not to take chances, use ext3 still.

I have everything on my /home partition backed up twice: to a second internal HDD and an external usb HDD. rsync does it nicely! So if ext4 fouls up I can just reinstall. So far the speed has been noticeably improved, especially on boot and shut down.:popcorn:

---

