---
title: "Hi, a little help needed please"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by apmacniven on 2011-07-18
I've decided to make the switch from windows vista to a linux distro.
Im currently using ubuntu via Wubi and after disabling the Unity desktop (I wasnt a fan at all), Im pretty impressed and would love to have a look around other distros, Ive heard Debian and Fedora are very god also.
What I basically would like to do in order to keep my mp3s, videos and other documents from the windows system is to put them all in a separate partition, so I can play about with the main partition and then transfer them all over to the main partition and use the full drive as one, when I settle on a distro.
If anyone could point me in the right direction I would be very grateful.
Thank you very much for reading

---

### Post by ercferret18 on 2011-07-18
You can use GParted (System > Administration) to create partitions.

---

### Post by Vahe Nersesian on 2011-07-18
Do you have more than one partition or only a single partition?

---

### Post by apmacniven on 2011-07-18
As far as Im aware I have 2 partitions each of about 247gb in size, one for the windows system and the other for a linux system, but i wish to merge them into one partition, deleting the windows system, but keeping all my music and documents etc. I would basically like to know the best way of going about this.
thanks for the replies

---

### Post by Mark Phelps on 2011-07-18
If you wish to retain MS Windows, in a dual-boot setup, your best approach would be to create an NTFS data partition and move the file there -- since both Ubuntu and MS Windows can read/write NTFS partitions.

But if you plan to do away with MS Windows real soon, then just COPY (NOT Move) the files into your Linux filesystem, confirm that they will work OK (after rebooting into Ubuntu.  The files in MS Windows will then vanish when you remove MS Windows from the PC.

---

### Post by apmacniven on 2011-07-18
That sounds alot easier thank you!
Can I access the files from ubuntu in order to copy them over? or will I have to do that in Windows?
Also when I come to delete windows can I simply delete the partition it is in?

---

### Post by Swagman on 2011-07-18
how many mp3's do you have ?

You could always upload them to UbuntuONE (remember your login though) then wipe your drive as you see fit and install, then pull them off the cloud again (if you wish)

---

### Post by amjjawad on 2011-07-18
> **apmacniven said:**
> What I basically would like to do in order to keep my mp3s, videos and other documents from the windows system is to put them all in a separate partition, so I can play about with the main partition and then transfer them all over to the main partition and use the full drive as one, when I settle on a distro.


Hello and Welcome :)

Two words: External HDD.

If your files are really important and you can't take a risk to lose these files, better to store them on External HDD. Just in case something may go wrong on your internet HDD.

---

### Post by apmacniven on 2011-07-18
Thanks for the welcome, I have around 40gb to 50gb of files which i wish to keep, so if i could just bump them over partitions I think this would be easier.
I can see the advantages of an external HDD, but I dont own one and dont really want to purchase one just to complete this task, but if needs must lol.

---

### Post by amjjawad on 2011-07-18
> **apmacniven said:**
> Thanks for the welcome, I have around 40gb to 50gb of files which i wish to keep, so if i could just bump them over partitions I think this would be easier.
I can see the advantages of an external HDD, but I dont own one and dont really want to purchase one just to complete this task, but if needs must lol.

It's not a must but definitely better :)


You can create an NTFS Partition and save these files there. NTFS Partitions have a good advantage as both Windows and Linux can access these partitions by default.

---

### Post by decoherence on 2011-07-18
I strongly second amjjawad's suggestion of getting an external HD.

You say you want to eventually merge two partitions. Essentially you will remove one and resize the other which is one of the most dodgy things you can do to a hard drive these days. Depending on how your partitions are set up what you ask may not even be possible without completely wiping out the current partition scheme. 

An external hard drive with your important files backed up will save you time and aggravation, I can practically guarantee it. Even ignoring that it will probably be faster and easier to do what you want with an external hard drive, you also really should back this stuff up before doing this sort of thing to your internal hard drive.

Also, let me suggest an alternate approach. Buy an external hard drive but rather than backing your stuff up on to it, just install your various linux distros on it. When you settle on one, physically swap the external hard drive and the internal hard drive -- you now have a nice linux-only hard drive in your computer and all of your old files are safely accessible from the external hard drive. Copy over the files you want to the new internal drive and congratulate yourself for having a full backup (formerly your running system) on the external drive.

---

### Post by apmacniven on 2011-07-18
thanks for that post decoherence.
your suggestion does seem the most sensible and I will reluctantly put my hand in my pocket for an external HDD (its true what they say about us yorkshireman, we are very stingy)
thanks for all your help guys

---

