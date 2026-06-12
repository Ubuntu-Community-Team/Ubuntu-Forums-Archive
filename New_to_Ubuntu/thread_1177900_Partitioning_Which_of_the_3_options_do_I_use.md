---
title: "Partitioning: Which of the 3 options do I use?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by held7over on 2009-06-03
My /home just got wiped out in installing Ubuntu 9.04.

Maybe I forgot how to do this. I obviously selected the wrong option in the partion routine. I was moving from 8.10 to 9.04. I have had bad experiences in the past with online upgrades, so prefer to do manual upgrades.

In the partition manager, I picked the last option #3, manual partitioning. I told it the mount point for / was EXT3 and enabled formatting for that partition. Swap was identified already. And I told it which partition was my /home partition was and that it was EXT3 but DID NOT enable Formatting. 

It wiped my /home clean, loosing all my data.

Which of the three choices should I have picked???

 But I started with 8.04, then later I did an new install of 8.10 I thought by using this same option #3 Manual Partitioning, which worked.  Has something vital changed or am I mixed up as to which to select???

---

### Post by chrisod on 2009-06-03
It should have worked based on what you described. It sounds like you accidentally selected "format" for /home.

---

### Post by held7over on 2009-06-04
That's the thing. When I did /home I looked at it twice to make sure it was not enabled to format before I accepted it. Then, after it refreshed the partition layout I looked again. "/" was enabled to be formatted. Swap and "/home" were not enabled to be formatted. I told it then to go for it, and it then drew a new page, and said it was going to format "/" Swap, and "/home". 

When I saw that, I backed up back to the edit, and did it again, the same way, making sure that "/home" was not set to be formatted. Again checked it when it refreshed the layout, and it was not set to be formatted. But when I told it to do it, it again said "/home" was going to be formatted. I finally decided that maybe it was simply going to set the /home partition to EXT3 (which had been before in 8.10, as I just couldn't believe this kind of bug would be on a install cd.) So, I let it do its thing.

It showed "/" and "/home" being set to EXT3, which seemed to fit my assumption. Then it formatted "/". IT NEVER SAID IT WAS FORMATTING "/home" I WATCHED! But it sure did.

The whole thing has left me feeling a bit uneasy, as I have 3 other computers I was going to upgrade this way. 

Have you heard of anything similar happening to anyone else? ;)

---

### Post by louieb on 2009-06-04
> **held7over said:**
> ... picked ... manual partitioning. 
I told it the mount point for / was EXT3 and enabled formatting for that partition.
Swap was identified already.
And I told it which partition was my /home partition was and that it was EXT3 but DID NOT enable Formatting. 


Weird thats all I have to say. I've done version upgrades (using the **alternate **CD) several times that way. Including going from 8.10 to 9.04. 

Just the obvious questions.
Are you sure /home was on a separate partition?  On your other PCs use the mount command to be sure. 
Did you change to file-system type from something else to ext3?

---

### Post by held7over on 2009-06-04
The file system was already EXT3. I was surprised though that Ubuntu didn't seem to know that already.

Yes. It definitely was it's own partition. Ubuntu had already recognized the partitions, as all I had to do was click on them, hit edit, and tell it what kind of mount point it was.

I am not sure what you mean by using the mount command on my other PCs, as wouldn't I be inside the installer routine, as I would have booted up on the LiveCD, and again be :pfaced with only 3 choices in the Partition Manager?

---

### Post by presence1960 on 2009-06-04
That's why most of us recommend backing up your data regularly and especially prior to any partitioning operation. Although partitioning has a great success rate, there is always a chance of data loss or corruption during the operation. Hopefully you had a back up of your data and do not join the ranks of those who have been burned because they neglected to have a back up.

---

### Post by held7over on 2009-06-04
I was thinking maybe my CD was corrupted, but I used K3b to burn it and it automatically runs a md5sum as I understand it.

I have a second drive the same size as the primary drive. It takes about 7 hours to copy /home to the second drive and ties up my cpu a lot, so, instead, once the initial copy was done, I have been trying to manually update the thing as I make changes. Basically, I lost a week of email letters and a few trivial things from what I can tell, nothing greatly distressing, since I could retrieve any letter I need from gmail's archives, that just leaves a few notes and a little clutter one accumulates. So, I am not burned, my eyebrows just got singed. :p

I had just recently installed the second drive, wanting to research setting up a mirror disk using RAID LEVEL ONE if this older system will support it. I haven't gotten to that yet, and suspect I am going to need a different controller.

Someone mentioned that a better way for me to go might be using "rsync" the other day. I think he said that when you run it, it only transfers what has changed to the backup disk. That sounds pretty cool, if I understood him correctly. I am wondering if, since my second drive is partitioned the same as my first drive and has 9.04 installed, if I couldn't just somehow have rsync keep the who drive updated so the the OS is up to date also? -Going "/" to "/" between drives.

This guy told me that cp does not give an exact copy, as it leaves out some hidden things, whereas rsync can be flagged to keep it perfectly exact. But looking briefly so far at "info rsync" it looks a bit over my head. I have no idea what switches I should enable or how to correctly construct the command so that I don't slaughter myself. I have been looking for an example of someone else doing this same thing I want to do, so that I could just copy something tested that worked, as it looks to me that I will be testing the command with my real data. (I know, I know, No guts, not glory! But that is how I just wiped my first drive.....gulp!):p

---

### Post by held7over on 2009-06-04
I guess I should add I have been using Konqueror in split window pane mode to copy from one drive to another. I don't know how to construct a statement on the command line that hops to another drive....yet.:(

---

### Post by Miljet on 2009-06-04
rsync is indeed the best way to keep backups. Your friend was right, it only copies those files that have changed. You can even set it up to do automatic backups through cron.

You first have to install ssh (secure shell). It may even be already installed on your computer. The important point to remember is when you run "ssh keygen" it will create two keys, a public key and a private key. The private key stays on your client computer, the you need to copy the public key to the machine you are using as a server.

It is not terribly difficult. Here is a link to the best tutorial that I found. 
[http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh](http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh)

---

### Post by louieb on 2009-06-04
> **held7over said:**
> ...I am not sure what you mean by using the mount command on my other PCs, 

Its a command line thing **Applications)Accessories>Terminal**

```
mount
```

it will list all the file-systems currently mounted. make sure you see one for /home.

---

### Post by Skip Da Shu on 2009-06-04
> **held7over said:**
> 
I had just recently installed the second drive, wanting to research setting up a mirror disk using RAID LEVEL ONE if this older system will support it. I haven't gotten to that yet, and suspect I am going to need a different controller.

Software raid 0, 1 and 10 in current linux kernels is pretty good in my opinion.  I'm using both RAID 1 (mirror) and on another machine RAID 10 (stripe of mirrors).  I found several good tutorials out there on doing RAID 1 and it was pretty easy but I was NOT doing my OS drive but rather a data drive.  

If your current mobo supports the drive you have then putting a 2nd one up in RAID 1 is all software, no other hardware needed.  If you're doing this for a drive that will contain the installed OS then you need a good image backup to restore to the RAID array once it's built.  Doing a 'data' drive is easier as I just copied everything off to a USB drive (+ most of my /home stuff), took out the USB drive, turned it off, plugged up the two drives to be the RAID 1 array, rebooted and created the array in the live system (no CD), plugged the USB back in and copied the data to the array.  I use this for all the photos, music, etc. etc and in fact I could copy /home over to it's root and modify /etc/fstab to remount it and use it as /home.  Then delete the existing /home partition use Gparted to expand the other partition and add that space to the OS partition... just haven't felt the urge yet.  Anyway I think there's even a tutorial here on doing RAID on Ubuntu (as the OS drive).

On your original problem... It almost has to be that the /dev/sda? you thought was what mounts to /home was not. If home was a sep partition then you should've had at least /dev/sda1, /dev/sda2 and /dev/sda3 (/, swap and home).  

I don't recall what the 2nd option is... 1st is guided, 3rd is manual.  Is the 2nd option "As Is"?  If so that's what you should've used.

My bro' recently used the update manager 'upgrade' and got a good upgrade on several machines to v9.04 from v8.10.  So single step upgrades appear to be working pretty well now.  At least on non-dual boot machines.

As far as making a backup of /home I think the easiest way is via tar:
```
sudo tar -cvpzf /home.tar.gz /home
```
That is from my memory which is always suspect but it's non-destructive so you can try it and see if you end with what I think you should in / and even browse the archive.  Switches in order are: 'Create archive', 'Verbose', 'Preserve file settings', 'gZip compress it' and 'File at' "/" named "home.tar.gz" with all contents out of directory "/home".

The "p" is probably what causes folks problems by not including it and then copying back their permissions get changed.

---

### Post by Miljet on 2009-06-04
The 2nd option is "Guided - Use entire disk."

---

### Post by Skip Da Shu on 2009-06-04
> **Miljet said:**
> The 2nd option is "Guided - Use entire disk."

Well that's no fun.

---

### Post by held7over on 2009-06-05
Thanks for the steer to the rsync HOWto Miljet, I will study it and see if I can't get it up and running and add cron. I like that idea a lot. 

Is there a HOWto that describes the abilities of the Installer's Partition Manager on the three options afforded there?

Thanks louieb on the tip to pre-check my other PC's to make sure what I think are partitions, are, with the use of mount. But I assure you, /home was indeed a partition and the Installer saw it. But, I will make that check on my other PC's just to be sure!!! -Before I use the installer.

---

### Post by held7over on 2009-06-05
OK. So, what does #2 "Guided -- Use the entire drive" mean? I figured that meant it would wipe the whole drive....something I didn't want it to do.

Also, I don't remember it saying Guided on #2, Just - use the entire drive, but then, my memory is going, maybe it did, but I would have still thought the same thing.

I think if I were to have tried #1, which I seem to remember used the word Guided, I would have ended up with two different sets of file systems, one with my data, and one without...like a dual boot system. Right?

---

### Post by presence1960 on 2009-06-05
> **held7over said:**
> Thanks for the steer to the rsync HOWto Miljet, I will study it and see if I can't get it up and running and add cron. I like that idea a lot. 

Is there a HOWto that describes the abilities of the Installer's Partition Manager on the three options afforded there?

Thanks louieb on the tip to pre-check my other PC's to make sure what I think are partitions, are, with the use of mount. But I assure you, /home was indeed a partition and the Installer saw it. But, I will make that check on my other PC's just to be sure!!! -Before I use the installer.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by held7over on 2009-06-05
Thanks Skip Da Shu for the RAID discussion. I have a second system that I want to set up as a server that I will utilize your suggestions on.

And thanks presence1960 for the URL on the partitioning, I have peeked at it, and will review it in depth, but what I meant was, is there something that discusses the 3 partitioning options that are found IN the INSTALLER, as to what they are used for, as obviously I did not understand that option #2 which said "Use the whole Drive" would not wipe out my existing partitions, and so picked option #3, Manual Partitioning, (which I am assured, should have worked, but for some reason something went wrong).

---

### Post by presence1960 on 2009-06-05
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Go here and download the free pdf version of the ubuntu pocket guide. The first section has instructions how to do the install including partition options and what they do.

---

### Post by held7over on 2009-06-05
Thanks presence1960, that will be really helpful!

---

