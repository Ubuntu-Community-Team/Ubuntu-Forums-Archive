---
title: "Mass delete locked folders?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Palehorse Redivivus on 2009-06-12
Hi all,

I'm very new to Ubuntu as of two days ago.  After installing it, I used a file recovery program to try and salvage some documents I lost a while back.

Unfortunately now I've got about 2,000 folders in my home folder, all locked, and eating up a massive amount of space.  I've done every search I could think of; figured out how to change the permission of a folder, how to delete a folder, how to log into the root account... but nothing showing me how to use root privileges to mass delete 2000 folders on my main user account all at once.  

I'm REALLY hoping I don't have to delete all of these, using the terminal, one at a time... little help?

Thanks!

---

### Post by Azrael3000 on 2009-06-12
to delete a folder you can use
```
sudo rm -R ~/folder_to_delete
```

if you have all of your folders in one directory (maindir) where there is NOTHING else (no hidden files, NOTHING) then use
```
cd ~/maindir
sudo rm -R *
```

[COLOR="Red"]DO NOT[/COLOR] do this in your home directory ~

---

### Post by hayden92 on 2009-06-12
Azrael has given you the correct command, but be warned that it can be VERY dangerous if you remove the wrong directory.

Make absolutely sure that you are not in the "home" (when you open a terminal, this is the default location that you will be in) or "/" folder (root)

---

### Post by Palehorse Redivivus on 2009-06-12
Thanks for the replies.  :)

I mistyped -- the 2000 locked folders are in my user folder, along with the other things that were there to begin with; music, desktop, etc.  I take it deleting the desktop is not a good idea.  ;)

Hm... any way to change the *permissions* on everything in there so I can just delete them by hand in one shot?

---

### Post by nandemonai on 2009-06-12
> **Palehorse Redivivus said:**
> Thanks for the replies.  :)

I mistyped -- the 2000 locked folders are in my user folder, along with the other things that were there to begin with; music, desktop, etc.  I take it deleting the desktop is not a good idea.  ;)

Hm... any way to change the *permissions* on everything in there so I can just delete them by hand in one shot?

```
sudo chown -R username:username ~/
```

Replace username with your user and this should make you the owner of everything in your home directory (which you should be anyway).

Then you should be able to browse to your home dir and select all the directories you want to delete.

---

### Post by presence1960 on 2009-06-12
> **nandemonai said:**
> ```
sudo chown -R username:username ~/
```

Replace username with your user and this should make you the owner of everything in your home directory (which you should be anyway).

Then you should be able to browse to your home dir and select all the directories you want to delete.

+1

why delete them? when you copy them over again the same thing is going to happen. Use the chown command to change ownership and get access to your folders/files.

---

### Post by Palehorse Redivivus on 2009-06-12
Thanks Nandemonai; that worked.  Unlocked and deleted.  Eeeexcellent.
Thanks also to everyone else who replied!  Cheers,
--PH

---

### Post by spsmiler on 2009-07-17
> **presence1960 said:**
> +1
 
why delete them? when you copy them over again the same thing is going to happen. Use the chown command to change ownership and get access to your folders/files.
 
Hi there,
 
How do I use chown
 
reason I ask is that... 
 
I had a SD memory card which went bad and I saw on a thread here about a recovery tool called PhotoRec, which is part of something called testdisk. A link to that thread is below...
 
[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)
 
So, I downloaded it and after several attempts I got it to install (it only needed double clicking - I was expecting it to be more challenging! :D ) and after not being able to find any links to it either on my desktop or in the Applications menu I decided to try an old DOS trick and run it from the Linux equavelant, which is Terminal.
 
To my delight the software started up, and after making me type in a password (because the screen said that I needed to run the software as root) I was able to scan the SD card and extract what I could.
 
Not knowing any better I saved the data in my home directory, which seemed to be a good idea at the time, but having saved what I wanted to an external HD I then tried to delete (from this computer) the folders with the recovered files. But I was unsuccessful as the computer says that they are owned by root, and therefore whilst I can view them, I cannot delete them.
 
Having read a few threads here I can see that logging in as root is disabled (which esplains why I was unable to do so) and to be quite candid I am not really looking to do this, as being a windows techie I understand about user security and why it is never good to log in as 'adminstrator'. (This also explains why on new installs one of the first things I do is create a password for the administrator account).
 
so, all I want to do is find a way to delete these files. Changing ownership sounds good to me - providing I can do it! please help!
 
TIA
 
Simon
 
ps, the computer is one of the new Acer Aspire netbooks; its dual boot win XP and Ubuntu netbook remix, and one reason for using Ubuntu is to try and expand my skillset... The Ubuntu partition is only 8gb, so having almost 4gb of SD card data locked in it is not so good. Since then I've worked out how to save data to the 80gb 'shared' partition which I set up to store data accessible to both OS's.

---

### Post by Ketusmondai on 2010-05-28
> **nandemonai said:**
> ```
sudo chown -R username:username ~/
```




All the files on my external HD are locked, and have become read-ony files.
I tried the above code and got the error message :-
 
:chown cannot access '/home/keith/.gvfs': permission denied

Any clues please? I am, and will always be, a beginner with ubuntu.

---

### Post by Azrael3000 on 2010-05-29
sorry but did you replace username with yours (I assume it's *keith*).

secondly this command won't help you when it comes to the files on an external hd.

I suggest you get the tool MountManager from the repositories. It basically is a GUI to edit /etc/fstab. Although not that user friendly you should find the entry to give users read and write access. After that save the configuration, disconnect your drive and then reconnect and you should be good to go.

If you need further help let me know.

---

### Post by Ketusmondai on 2010-05-31
I don't know what I did, but it's ok now!
Thanks anyway.

---

