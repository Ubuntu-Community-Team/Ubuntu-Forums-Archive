---
title: "Synchronize Writer docs between Ubuntu and Vista"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Wheel on 2010-03-10
Hi all,
I've been using Writer on Vista for a couple of years.  I was delighted to find it included with my recent install of Karmic.  

Is there a way to save a doc edited on one system to both Vista and Ubuntu?

Something along the lines of Firefox's Xmarks extension?

For now, I'm just using Ubuntu for all of my Writer needs, but occasionally I find myself on Vista (less and less these days as I get the hang of Ubuntu) and I get an idea for some story or other that I'm working on (just for fun; I'm not a pro).  In that case, I need to re-start and boot to Ubuntu to change the doc.  Kind of a nuisance. 

Has anyone ever tried to do this?  Is it even possible?

---

### Post by gamerchick02 on 2010-03-10
You could get a dropbox account: [http://dropbox.com](http://dropbox.com) and save your documents in there and they'll be on both computers.  You can access this through the web and the program you install on your computer.  Drobox works both in XP/Vista/7 and Ubuntu.

There's also the option of saving everything to an external drive and having it plugged in all the time.

Not sure if that's what you want though.

Amy

---

### Post by eriktheblu on 2010-03-10
Assuming this is a dual boot machine, why not just store the file on a Windows partition?

---

### Post by undecim on 2010-03-10
If you can access your Vista partition from ubuntu, you can link your Documents directory on Ubuntu to your Documents directory on Windows. Both OSs should be able to read your Windows partition.

start by renaming your Documents folder.

Then, just find your documents directory on windows (in ubuntu usually something like /media/Vista/Users/username/Documents"), open a terminal and run```
ln -s /media/Vista/Users/username/Documents ~/Documents
```where /media/Vista/Users/username/Documents is your windows document folder.

The you can copy all your old Ubuntu documents there, and your documents should be effectively synced

---

### Post by Wheel on 2010-03-11
Thanks for the quick replies everyone.

> gamerchick02
**Re: Synchronize Writer docs between Ubuntu and Vista**
         You could get a dropbox account: [http://dropbox.com]("http://dropbox.com/") and save your documents in there and they'll be on both computers. You can access this through the web and the program you install on your computer. Drobox works both in XP/Vista/7 and Ubuntu.

There's also the option of saving everything to an external drive and having it plugged in all the time.

Not sure if that's what you want though.

Amy   I've taken a cursory look at Dropbox and it looks promising.  Since I'm only concerned with several megs of text docs, the service is even free.  Nice.   I have done nothing as yet, but I may well go this route.


> eriktheblu
             **Re: Synchronize Writer docs between Ubuntu and Vista**
         Assuming this is a dual boot machine, why not just store the file on a Windows partition?     
Yes.  Dual boot.  Have done very little with partitions, but I *do* enjoy tinkering.  I know that many people create a separate partition just for data storage.  I have not.  Is this what you're suggesting? 

 To date I have 5 partitions: Vista file system, Vista recovery, which I'm considering deleting since I'll likely never use it (I have the Vista install disks, which I used last December to clean install), Linux extended partition and the 2 Linux logical partitions inside of it--the actual file system and the Swap.

I have used the Vista Disk Management tool exactly once--to prepare for the Ubuntu install--and have never installed gparted.

What's your opinion on the better tool to use?


> undecim              **Re: Synchronize Writer docs between Ubuntu and Vista**
 If you can access your Vista partition from ubuntu, you can link your Documents directory on Ubuntu to your Documents directory on Windows. Both OSs should be able to read your Windows partition.

start by renaming your Documents folder.

Then, just find your documents directory on windows (in ubuntu usually something like /media/Vista/Users/username/Documents"), open a terminal and run     Code:
     ln -s /media/Vista/Users/username/Documents ~/Documents 
where /media/Vista/Users/username/Documents is your windows document folder.

The you can copy all your old Ubuntu documents there, and your documents should be effectively synced     

This is kind of what I was thinking of.  Once set up, would this work permanently?  Or would I need to re-run it after each document gets changed.  And would it work* both ways*?  I mean can I change a doc in Vista OR Ubuntu and see those changes on the opposite system?

---

### Post by Wheel on 2010-03-15
Any further comments or any clarification of the above posts would be most welcome.

---

### Post by cerealtx on 2010-03-15
Did not see it addressed anywhere but it also depends on how you formated your partions, you can not freely access back and forth, i have a NTFS partition with my music and distros ect ect so that i can access it on windows, and nix

---

### Post by Helkaluin on 2010-03-15
Edit: misread. Please ignore.

---

### Post by gottijr on 2010-03-15
> **Wheel said:**
> Thanks for the quick replies everyone.

 

Yes.  Dual boot.  Have done very little with partitions, but I *do* enjoy tinkering.  I know that many people create a separate partition just for data storage.  I have not.  Is this what you're suggesting? 

 To date I have 5 partitions: Vista file system, Vista recovery, which I'm considering deleting since I'll likely never use it (I have the Vista install disks, which I used last December to clean install), Linux extended partition and the 2 Linux logical partitions inside of it--the actual file system and the Swap.


This is kind of what I was thinking of.  Once set up, would this work permanently?  Or would I need to re-run it after each document gets changed.  And would it work* both ways*?  I mean can I change a doc in Vista OR Ubuntu and see those changes on the opposite system?

  I'm not a very experienced linux user but i will try to help. If i do a mistake anyone pls correct me.

  The main idea was to start saving your documents from Linux in the Windows Vista documents folder. This way you will make your Ubuntu documents to be the same folder as Vista documents with a "sim link" between folder (something like that)

  ```

  ln -s /media/Vista/Users/username/Documents ~/Documents

```

  Should run that from terminal. What does it do? Creats a link between

  A /media/Vista/Users/username/Documents    -    B ~/Documents

  A ( is where your vista partition is mounted and don't forget on username (actually is your vista username))

 B "~" this will create a folder linked to your vista - in your home Ubuntu directorie.

  After all this done he said you should copy all you documents in that folder (ubuntu home directory/Documents) and this way you will be able to see it from both Ubuntu or Vista

  Yes is permanent.

  I haven't worked with dual boot, so someone pls advice if the windows partition will automount in /media/vista

  thank you

  p.s. if i've done any mistakes pls correct me.

---

### Post by Wheel on 2010-03-22
Thanks, gottijr.

I do get the idea about creating a symlink between the 2 folders.  And I was able to create such a link (it's sitting in my home folder) with the suggested terminal command.  I've still got some tinkering to do with this to make it work for me.

In the meantime, I have set up a dropbox account (thanks again, gamerchick02) and this has given me effectively the same type of functioning.

I will continue to learn the subtleties of the command line work and the way in which Vista and Karmic co-exist (sometimes they don't play well together).  I really do want to get this set up locally on my hard drive without the need for dropbox.

In time I will figure this out, but for now I'm calling this issue "solved".

Thanks again everyone.

---

