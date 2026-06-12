---
title: "[SOLVED] making backup disk from (pref) quickstart, how"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-07
hi all.  sorry if i missed the answer elsewhere but i have been reading so many posts/info pages on this that i am now totally confused.
i am using quickstart to make backups of / and /home and these are stored on /backup .  my partitions read as follows 
```
/dev/sda1            6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris

```
and the partitions are as follows

```
/dev/sda1       ext3         /backup
/dev/sda2       ext3         /data
/dev/sda4       extended
   /dev/sda5    ext3         /
   /dev/sda6    linux-swap

```
okay, i am making backups but what i really want to know is should the worst happen will these be able to restore my system to what i have now.  i am pretty confident that i would be able to restore the data, but its all the other stuff.  would i be able to boot from disaster?  ideally i would like to create a bootable restore disk that would wave the magic wand and put things back like whatever had never happened (i'm such a klutz i am quite likely to break my system, i already have done once).
so if anyone can give me - well - not even beginners instructions on how i can do this i will be very grateful.  or if you can point me at clear instructions - suitable for a half wit - it needs to be a disk cos i dont have an external drive.
sorry to be so wordy but i need to get it clear for my own mind and this is how i work best.
thanks again
nigel

---

### Post by capnthommo on 2009-01-09
bump
:confused:

---

### Post by robert shearer on 2009-01-09
An alternative may be to investigate Remastersys for Ubuntu.
It creates a live cd of your current install, apps and configurations/updates.
 
Some links here.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

I have used this many times to back-up, reinstall or pass on to others and never had a problem.

Search on the Ubuntu forum for other Remastersys posts and experiences.

Hope this is of help:)

Note that the current Remastersys has a GUI and can be found after install in the System=> Admin menu.

---

### Post by talsemgeest on 2009-01-09
Remastersys is a good app, but I do like quickstart. If you back up your /, then it is easy enough to get it back to where you were. Just reinstall ubuntu, install quickstart, then restore your backup.

---

### Post by capnthommo on 2009-01-09
> **robert shearer said:**
> An alternative may be to investigate Remastersys for Ubuntu.
It creates a live cd of your current install, apps and configurations/updates.
 
Some links here.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

I have used this many times to back-up, reinstall or pass on to others and never had a problem.

Search on the Ubuntu forum for other Remastersys posts and experiences.

Hope this is of help:)

Note that the current Remastersys has a GUI and can be found after install in the System=> Admin menu.



Hi robert.  thanks, i will have another look at 'remastersys'.  but i tried it a few weeks ago and didn't have a good experience.  okay so that was almost certainly down to me but i would like to try and stick with 'quickstart' if it can be made to do what i want.  thanks though, and i shall look at the links and try it out
cheers
nigel

---

### Post by talsemgeest on 2009-01-09
> **talsemgeest said:**
> Remastersys is a good app, but I do like quickstart. If you back up your /, then it is easy enough to get it back to where you were. Just reinstall ubuntu, install quickstart, then restore your backup.

> **capnthommo said:**
> Hi robert.  thanks, i will have another look at 'remastersys'.  but i tried it a few weeks ago and didn't have a good experience.  okay so that was almost certainly down to me but i would like to try and stick with 'quickstart' if it can be made to do what i want.  thanks though, and i shall look at the links and try it out
cheers
nigel
Note my post.

---

### Post by capnthommo on 2009-01-09
hi talsemgeest.  i was just composing my reply, i wasn't ignoring you.  thanks.  okay i have backed up and now have
Tar_config_backup      3.1 Kb
Tar_home_backup        4.2 Gb
Tar_system_backup      4.9 Gb
plus a 69 byte directory file
i assume i can burn these to a DVD using maybe Brasero disk burner - data project.  but i have a couple of questions about this process.  firstly, the system backup tar is 4.9 Gb which is a little too large for one disk, so what files should/can i leave out from the disk or can i split it over two disks.  secondly, do i need to burn any more than the system backup, because isnt this / and doesn't this include everything eg data.  or have i got this completely wrong?  and thirdly, just to get it straight, i would reinstall ubuntu from my live disk,  then install 'quickstart' then restore the backup, and then (if it isn't already on 'system') restore data (i guess this would have to be on another disk.
thanks for the help
i will understand this one day
nigel

---

### Post by talsemgeest on 2009-01-09
As far as I know, the "/" backup will back up everything on your computer except what mdaplow (the guy who created quickstart) has excluded, such as /dev. If you back up "/" you will not have to back up anything else. As for the file being > 4.5GB, I'm sure there are a few easy ways to split the file, but my minds gone blank (it is too late in the night.) You could probably buy a dual-layer dvd and burn it to that, but those are a bit more expensive.

Hope this helps :)

---

### Post by capnthommo on 2009-01-09
okay thanks a lot, that helps.  i think 'quickstart' allows to leave out files so i can have a little explore and see if that's an option.  failing that, as you say, i can get double layer disks, thanks again, it's time to go play with the system (and hopefully not bust it this time.
cheers
nigel

---

### Post by mdpalow on 2009-01-09
> **capnthommo said:**
> okay thanks a lot, that helps.  i think 'quickstart' allows to leave out files so i can have a little explore and see if that's an option.  failing that, as you say, i can get double layer disks, thanks again, it's time to go play with the system (and hopefully not bust it this time.
cheers
nigel

I'm surprised to see your / back-up is so large. Granted, I haven't backed up 'Intrepid' with QuickStart, so I'm not sure how big the / back-up is after a clean install to confirm your file sizes.

Regardless, the quickest/easiest/cheapest solution for you would be to buy a 16 gig flash drive and dump the back-ups to that drive. Or, you can get another hard drive.

thanks,

mdpalow

---

### Post by robert shearer on 2009-01-09
> **capnthommo said:**
> Hi robert.  thanks, i will have another look at 'remastersys'.  but i tried it a few weeks ago and didn't have a good experience.  okay so that was almost certainly down to me but i would like to try and stick with 'quickstart' if it can be made to do what i want.  thanks though, and i shall look at the links and try it out
cheers
nigel

Remastersys backs up the configured install and will fail if too much data is included. It is important to save data to another h/d or have a separate data partition from the outset.

Here is some advice from the Remastersys site that I have found to be vital to the successful backing-up procedure.



> The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes. Mine generally is just a bit over 1 gig.
Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.

Also look for the following folder: /var/cache/apt/archives. That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system. The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason. You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more.



Remastersys, aptoncd and an external drive for data works for me.:)

---

### Post by capnthommo on 2009-01-09
hi mdpalowand robert.  you both query he size of my backup.  i have been a tad puzzled over that too.  i think from when i made a backup this afternoon using ```
"tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /"
``` that i have all my data files (music, photos etc) on my / directory as well as on my /data directory.  i know when i made the Tar it doubled the size of my / directory until i went ```
 "sudo nautilus" 
```and copied it to the /backup and then deleted the original on /.  my worry was that when i did this it would disappear entirely, and that /backup only read from what was on / but since it appears to still be in backup and gone from / i guess its ok.  Am i right to assume that this means i can go ```
"sudo nautilus"
``` again and delete all my data files from / and that they will still be on /data which is what i wanted in the first place?
i did notice that as the backup tar was being made it was going through endless reps of eg xxxsong on a) / b) /usr c) /home and so on.  does this mean that at present i have these things saved in more than one place?
See what happens with a little knowledge?  you get into the confused state i have been in for the last fortnight.:confused:
thanks loads for the help
nigel

---

### Post by capnthommo on 2009-01-09
I am going to close this one now because i think it's moved on to another issue, eg i managed to delete my /home directory and couldnt get back on the system.  so with no other usable machine to hand my only option was to re-install from the original live disk.  now i'm back i can sort out the mess so  will open a new thread when i have thought about it for a while.  thanks to all for the help, you can see i need it, i'm a danger to myself!  it's what happens when a person gets a bit too clever for their own good.
thanks again
nigel
:)

---

### Post by talsemgeest on 2009-01-09
Post a link to the new thread and I will see if I can keep helping you.

---

### Post by robert shearer on 2009-01-10
> **capnthommo said:**
>  i'm a danger to myself!  it's what happens when a person gets a bit too clever for their own good.
thanks again
nigel
:)

Keep on being dangerous!! That is what will advance your Linux experience fastest.

All experimentation is worthwhile! Sometimes it works and sometimes it crashes and every time we learn something new.

I haunted our local trash recyclers untill I had enough parts to put together a second compy just to experiment on.
Then I experimented and at first I broke it at least every other time.!!

Then it was one in three and then one in four and so it went untill now I know I can reinstall to the "just before state".

If you have only the one compy it seems a BIG risk to try out anything new at all.

(and think how the Windownistas feel when it has cost $$$$ and will cost more if they break it)

For a little outlay (P3/512 Mb ram/20 Gig h/d, NO O/S! should be less than $50) You could have the best Linux learning tool one could ever own.

All this fun and the back-up of your main compy to do the day to day stuff on.

Once your experiment works then you can apply it to the main compy and have a faster fresher fabulouser time with low/no risk.

Play with your food when you've eaten all your toys.!

---

### Post by capnthommo on 2009-01-10
hi, thanks to you both.  as to a second machine, i just need to get the windows fixed on the family desktop and at least i can contact forums if disaster strikes.  shouldn't be a problem, just need to ask a relative who knows/has xpdisk.  if i had my choice i would just load ubuntu on it and take it from there but i live with m/s people.  as you say, experimentation is how you learn - if this had happened 3 weeks ago i would have been lost but now i was able to put it right, and i have all my data on the ensmallened original linux partition and it copies over so its just a matter of time etc.
i certainly intend to get an external disk for backing up, but the carpentry business here is not too healthy at prtesent so i simply can't afford it (havent worked at all for 2 and a half months).  dont worry, its a high priority.
anyhow, thanks again and i will post a question in the next coup-le of days when i get things straight in the head.  anyway, its the weekend and theres rugby to watch.
thanks again
nigel:guitar:

---

