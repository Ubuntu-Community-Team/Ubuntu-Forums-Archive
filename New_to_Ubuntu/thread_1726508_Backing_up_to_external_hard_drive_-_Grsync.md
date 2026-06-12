---
title: "Backing up to external hard drive - Grsync"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by chris282 on 2011-04-11
Hello all,

I recently decided to do the sensible thing and start backing up my hard drive to an external drive.  Since I know nothing, the obvious way to do this seemed to be to copy and paste my home folder, which seemed to work fine.

I was then advised that while this will work, an easier solution may be to use the command rsync, which will update the files that have been changed rather than over-writing everything.  Obviously there's plenty of information available on how to do this, but I ended up getting a bit confused about what I was supposed to be excluding and including, so in the end I decided to use a GUI program.

I now have Grsync installed, which again, seems to work fine, but takes about ten minutes longer to run than copying and pasting did.  C&P takes about twenty minutes, Grsync takes about half an hour.  I haven't messed about with the settings, I promise.  Can anyone suggest what, if anything, I'm doing wrong?

Thanks in advance,

- Chris.

---

### Post by Nickjpost on 2011-04-11
I've noticed that program does take longer than jst copy and paste, but it does not seem that you are doing anything wrong. Personally, I like to make sure I have /home backed up and don't sorry too much about anything else. I believe that the default settings for Grsync include /home anyways

---

### Post by SoFl W on 2011-04-11
I have a function set up in my ".bashrc" file that uses the copy command.

```

   function mybackup { # -- backup my home directory to the external RAID drives
   cd /home
   cp -pru USERNAME /media/PATH_TO_EXTERNAL_DRIVE/
   cd
   }
```I just call the script "mybackup" from the terminal.  I am sure others here will have opinions on it.

---

### Post by seawolf167 on 2011-04-11
Take a look at these [two]("https://help.ubuntu.com/community/rsync") [pages]("https://help.ubuntu.com/community/BackupYourSystem") for how to use and backup your system with rsync.

You can also use sbackup which is a GUI frontend for rsync

```
sudo apt-get install sbackup
```

Another option is [Clonezilla ]("http://www.clonezilla.org")which images your entire drive (or single partitions) and stores them to an external drive.

---

### Post by Blasphemist on 2011-04-11
This made me think that I should now have a backup run. I looked into my configuration and found that a KDE backup was installed, Nepomuk. I don't use KDE so I uninstalled that and instead chose Back In Time for gnome from the software center.

It seems very easy to use and I set it to backup my home every hour and to use smart remove. Here is a screeshot of the smart remove settings. I'll post if I have any issues.

---

### Post by chris282 on 2011-04-11
Thanks for your fast responses, folks!

seawolf - appreciated, but this rather takes me back to where I started.  Everything on these pages suggests that the best solution for me is to use Grsync for an incremental backup.

SOfI - looks like another perfectly fine way to copy my files, but is there any advantage to this over drag and drop?

Nick - yep, that's basically all I want to do too.  Good to hear it's not just me.  :)

Unless I'm missing something vital, it seems I'd be just as well to go back to my original system.  Yes/no?

---

### Post by CaptainMark on 2011-04-11
use ```
rsync -av [source] [destination]
``` to back up all files in [source] to [destination], if you want to also remove files from the back up you have deleted use ```
 rsync -av  --delete [source] [destination]
```
Watch out with the delete version because it will erase anything youve erased from your main drive, make sure you recover files you didnt mean to delete first. Also i have it in  script so you can tweak around with other options and add features when you learn the command better. 
Ps. the first time you run it WILL take a long time, but after that it will be real quick

---

### Post by Blasphemist on 2011-04-11
I think copy/paste was your original solution but no matter, it seems set up once with a good visual interface and run via cron so I can't forget to do it works for me. This is a write up on lifehacker of the solution I chose.
[http://lifehacker.com/#!5212899/back-in-time-does-full-linux-backups-in-one-click](http://lifehacker.com/#!5212899/back-in-time-does-full-linux-backups-in-one-click)

---

### Post by SoFl W on 2011-04-11
> **chris282 said:**
> SOfI - looks like another perfectly fine way to copy my files, but is there any advantage to this over drag and drop?

It makes sure you get everything.
Once you type the command it does all the work without a screen notification.
You could use the function as a CRON job.

Not really outstanding advantages, but I am an old school command line type of person.

---

### Post by chris282 on 2011-04-11
> **CaptainMark said:**
> use ```
rsync -av [source] [destination]
``` to back up all files in [source] to [destination], if you want to also remove files from the back up you have deleted use ```
 rsync -av  --delete [source] [destination]
```Watch out with the delete version because it will erase anything youve erased from your main drive, make sure you recover files you didnt mean to delete first. Also i have it in  script so you can tweak around with other options and add features when you learn the command better. 
Ps. the first time you run it WILL take a long time, but after that it will be real quick

Hi CaptainMark - sorry, this is probably deeply stupid, but the name of my external hard drive is 250GB EXT (with a space) so I've entered rsync -av  --delete /home/chris /media/250GB EXT which starts copying to a new file called EXT in /media.  I don't seem to have the option to rename the ext HD.  Help?

---

### Post by chris282 on 2011-04-11
Additional - tried 250GB_EXT and got this error:

chris@chris-desktop:~$  rsync -av  --delete /home/chris /media/250GB_EXT
sending incremental file list
rsync: writefd_unbuffered failed to write 531 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/media/250GB_EXT" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
chris@chris-desktop:~$

---

### Post by CaptainMark on 2011-04-11
what contents do you have in /media ? my backup drive is named passport and mounts straight to /media so my version would look like ```
rsync -av --delete /home/mark/ /media/passport/mark/
```which gives me an exact copy of my full home directory including the folder named mark placed in /media/passport, you can fiddle with the formatting to give different results but this is best for me, im not sure if its neccesary but its best to have /media/passport/mark/ already there, it may create it anyway im not sure

edit: also i found it works more reliably with the ending slashes,  so /home/mark/ not just /home/mark

---

### Post by CaptainMark on 2011-04-11
hang on sorry i wasnt really paying attention to your post, the terminal wont recognise a space as a space, it is looking for /media/250GB and then its seeing EXT after it and is treating it as an arguement use```
rsync -av /home/chris/ /media/250GB\ EXT/
```
note the backslash tells the terminal to consider the space as part of the directory name, this is the same with all terminal commands, for example if your have a file named 'text file' in your home then ```
rm /home/chris/text file
``` will throw up an error but ```
rm /home/chris/text\ file
``` will work fine

---

### Post by chris282 on 2011-04-11
Thanks again, CM.  Backslash solved that little problem, and I learnt something.  Always good!  However I did get the error message:

rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

Folder links, possibly?

In addition, it still doesn't seem faster than copy and pasting.  On the second time of running the command, it took about twenty minutes.  I don't mind that, I don't think it's a massive length of time, and I'm not particularly tied to copy and paste or anything - I'm really just wondering if there's any special reason other than personal preference not to do it.

If I just want to back up my home files is there any genuine benefit to the Rsync command, or am I just being advised to do something because that's the way someone else does it?

It seems like it ought to be quicker, but is that actually the case?  Or, as I suspect, am I doing something wrong again?  :confused:

---

### Post by CaptainMark on 2011-04-11
seen as i just done a full reinstall today when i copied my back up to my hard drive and then re ran rsync, the first took go took about 30 minutes, and now 2minutes 30secs. thats on a 25gb home folder. when i re run its straight away again it took 13 secs, it depends how much has changed in the home folder between back ups. 

Do you know about scripts, i would make a bash script with the command in so you know its identical and then you can time how long it takes to run.  If your running it twice in a row then the second run should be very short, literally a few seconds, if not, somethings up. 

As to the error message ive not seen that one before, looks like its copying a file but not copying something about it, maybe permissions.

Just googled it, do you have another file system or partition mounted inside your home folder, looks like rsyncs defaults fallover at symbolic links and mounted partitions

---

### Post by chris282 on 2011-04-11
Hey CM.  Well the error relating to symbolic links looks like it's talking about WINE folders:

rsync: symlink "/media/250GB EXT/.wine/dosdevices/c:" -> "../harddiskvolume0" failed: Operation not permitted (1)
rsync: symlink "/media/250GB EXT/.wine/dosdevices/d:" -> "/media/HP v210w" failed: Operation not permitted (1)
rsync: symlink "/media/250GB EXT/.wine/dosdevices/d::" -> "/dev/sdb1" failed: Operation not permitted (1)
rsync: symlink "/media/250GB EXT/.wine/dosdevices/e::" -> "/dev/sr0" failed: Operation not permitted (1)
rsync: symlink "/media/250GB EXT/.wine/dosdevices/z:" -> "/" failed: Operation not permitted (1)

so I don't think that's a major issue.

I'm afraid I don't know anything about scripts, so I've copied the command line from above:

rsync -av /home/chris/ /media/250GB\ EXT/

and pasted it into the CLI.  I've done that twice, back to back, making no changes to any files in between.  Both running times were identical - a shade under twenty minutes.  Having sat there and watched it (fun) I noticed that all the music files were copied on both occasions, taking a couple of seconds for each.  Something is definitely up.

---

### Post by CaptainMark on 2011-04-12
Hmm yeah it shouldn't do that, how many gb's are we talking about, if you add the word time before your command it will give you the runtime of it. I'll jot a script when I get home later, they are great for speeding up routine tasks on the terminal.

---

### Post by QLee on 2011-04-12
chris282,
Have you tried with any of the available grsync options to see if you can acheive what you want, which seems to be speedup of backup?

For example:

Ignore existing

Size only

or the Advanced option of,
Copy symlinks as symlinks

---

### Post by chris282 on 2011-04-12
sent 14987227306 bytes  received 1061972 bytes  14488438.16 bytes/sec
total size is 30244166934  speedup is 2.02
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

real    17m15.069s
user    3m10.692s
sys    5m26.088s


Hi CM, here's what I got at the end of the latest try.  We can safely ignore the error bit, I think (see previous).  My home folder contains 18.3GB.

Thanks for posting QLee.  I'm going to crack on with the command line for the moment though, because I'm interested to see why it isn't behaving as it should.

---

### Post by QLee on 2011-04-12
[QUOTE=chris282]...
Thanks for posting QLee.  I'm going to crack on with the command line for the moment though, because I'm interested to see why it isn't behaving as it should.[/QUOTE]
Sure, no problem.

The command line rsync equivalents of the options I mentioned in Grsync are:

--ignore-existing (skip updating files that exist on receiver)
--size-only (skip files that match in size)

-l (copy symlinks as symlinks)

As CaptianMark has mentioned, if you run another run immediately after the first it should run faster because files should not have changed. At least, most of them should not have changed.

---

### Post by CaptainMark on 2011-04-12
did you try running the command again literally twice in a row, the second run should take a few seconds, if not its doing something unexpected, and at the moment youll get the same results from grsync and rsync because one is just a graphical frontend for the other, essentially they do the same thing but grsync has a gui. i cant imagine why it would copy your music all over again when it doesnt need to, unless you have a media player that is rewriting id3 tags everytime it plays a track, this would be unlikely but possible

---

### Post by QLee on 2011-04-12
We can see that there was some speedup, 2, on the last run which should indicate that the rsync was faster than when the cp was done. I wonder if the transfer speed of the external drive is affecting things. 

Maybe try with -z (compress the data during transfer).

I agree with CaptainMark, let's see the results from two or three runs in rapid succession.

Are any of these files very large files?

---

### Post by QLee on 2011-04-12
> **chris282 said:**
> ... I noticed that all the music files were copied on both occasions, taking a couple of seconds for each.
...
Were they copied both times or were they checked, I see you have -v, verbose selected.


[Edit] I feel a bit silly for asking this but, we're not trying to copy permissions to a filesystem that doesn't retain them, are we?

---

### Post by mikodo on 2011-04-12
Hi,

When I was struggling as a noob to understand Rsync, none of the guides I found online spoke of the command to bring information back from a backup disk etc. to it's source file/folder/partition/whatever.

As far as I could figure out ... if the backup was in a format as such:

```
rsync -av [/source/] [/destination/]

```

then the return of the data would be, I THINK:

```
rsync -av [/destination/] [/source/]

```


Here is an example of mine with the UUID of my backup partition.

```
rsync -azvv /home/mikodo/ /media/6c12ee63-f305-484d-80d0-9f413e799fc0/
```

And for return:

```
rsync -azvv /media/6c12ee63-f305-484d-80d0-9f413e799fc0/ /home/mikodo/
```


Just in case you were wondering about what MIGHT be the rsync command for returning data, to your source.

Hopefully an authority, can confirm what I wrote, if you feel someone should and you ask for it.

;)

---

### Post by chris282 on 2011-04-12
Hi guys, in answer to your questions:

1. I have run the command literally twice in a row, but I'd be happy to do this again and post the results.  I'll leave it to the morning though, since it's getting on a bit here.  My understanding is that this **should** take a few seconds without compression, so I'll leave -z until we've established why the command isn't behaving as expected.  I've made very few changes to any of the files since running the original copy, other than to a few text documents, which I wouldn't expect to make a significant difference.

2. None of the files are unusually large to the best of my knowledge.

3. I'm guessing the music files were copied due to the timescale involved, but that is just a guess.  I'd expect copying all the music files to take a few minutes, and it does.  I definitely haven't played all the tracks since the original post.

4. My answer is even sillier - I honestly couldn't tell you.  How do I find out (and what does it mean)?

Thanks for the help so far - much appreciated!

***

mikodo - thanks for that also, hopefully I'll get far enough to test it out.  :)

---

### Post by mikodo on 2011-04-13
Yes, with any backup solution; one should test it's accuracy of the returning  data from backup against that; that has been deleted at the source (something duplicated or expendable).

Good Luck!

---

### Post by chris282 on 2011-04-13
Using command: time rsync -av /home/chris/ /media/250GB\ EXT/

sent 14973748604 bytes  received 1049312 bytes  14336809.88 bytes/sec
total size is 30260813808  speedup is 2.02
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

real    17m23.996s
user    3m8.228s
sys    5m17.588s
chris@chris-desktop:~$ 

And again, immediately afterwards...

sent 14944591198 bytes  received 1051921 bytes  14186656.97 bytes/sec
total size is 30224380473  speedup is 2.02
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

real    17m33.198s
user    2m55.887s
sys    5m12.948s

---

### Post by CaptainMark on 2011-04-13
Hmm this definitely doesn't seem normal, try omitting the wine related folders, but use as many files as you can, so possibly alter your command to just sync your music or just your photos, the bigger file the better, then run the command twice in a row again, if the second run is really quick we can assume that these wine directories are slowing things down and we can jot up a script to avoid those files

---

### Post by chris282 on 2011-04-13
Using command: time rsync -av /home/chris/Music/ /media/250GB\ EXT/Music/

sent 19023 bytes  received 1685 bytes  41416.00 bytes/sec
total size is 17467611934  speedup is 843519.99

real    0m0.233s
user    0m0.012s
sys    0m0.032s

That was significantly quicker!

---

### Post by psusi on 2011-04-13
My guess is that you have a hidden directory in there ( starts with a . ) that has MANY small files in it.  That will slow rsync down like you are seeing, and since hidden files are not shown in nautilus by default, they would not have been copied when you copied and pasted.

Another possibility is that if your external drive is FAT32, its timestamps only have a 2 second resolution which could be causing rsync to think it the timestamp is different between the two copies, so it has to do a full read of both to compare.

---

### Post by chris282 on 2011-04-13
Additional:

If I run the command for the back up of the entire home file:

     rsync -av /home/chris/ /media/250GB\ EXT/

I can watch the music files transfer one...

by...

one...

But if I just back up the music files:

     rsync -av /home/chris/Music/ /media/250GB\ EXT/Music/

it's done in an instant.

The external hard drive is a Sumvision 3.5" e-sata II Apex Plus.

---

### Post by CaptainMark on 2011-04-13
Okay so its possible that when rsync hits the symlinks for wine, its finds an error and after that it will insist on copying all files in full from that point onwards, (im guessing here really ive not come across this before)
im really gunning for the symlinks because fat32 doesnt support them but the -a option will try to follow them (ive never have any symlinks in my home folder so wouldnt have had this)
heres a few commands i would try, i know it may take some time if it takes 20 mins a pop but if it works will save you a bundle of time in the long run. ```
rsync -av --no-l --delete /home/chris/ /media/250GB\ EXT/
```the use of the --no-l option should ignore symlinks,```
rsync -v --delete /home/chris/ /media/250GB\ EXT/
```just removing the -a option will not preserve file permissions owners etc but will not follow symlinks either

After trying that ive really hit my limited knowledge of rsync im afraid, best of luck to you

---

### Post by chris282 on 2011-04-13
Hi CM,

I've tried both with the following results.  The first command doesn't seem to have made much of a difference:

sent 15385560157 bytes  received 1057210 bytes  15302453.87 bytes/sec
total size is 30383508289  speedup is 1.97
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

real    16m45.100s
user    3m16.756s
sys    5m10.235s

The second brings up this error:

rsync: --delete does not work without --recursive (-r) or --dirs (-d).
rsync error: syntax or usage error (code 1) at main.c(1443) [client=3.0.7]

But once I removed --delete I got this:

skipping directory .

sent 8 bytes  received 12 bytes  40.00 bytes/sec
total size is 0  speedup is 0.00

real    0m0.045s
user    0m0.008s
sys    0m0.000s

This looks like progress to me.  :D

---

### Post by CaptainMark on 2011-04-14
In that case add the -r option in because its only scanning the top directories.

---

### Post by chris282 on 2011-04-15
Curses.  Send back the balloons and cancel the dancing girls.

```
time rsync -rv --delete /home/chris/ /media/250GB\ EXT/
```gives me:

sent 15371205091 bytes  received 955519 bytes  14253278.27 bytes/sec
total size is 30234521206  speedup is 1.97
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

real    17m57.919s
user    3m16.632s
sys    5m21.876s

---

### Post by CaptainMark on 2011-04-15
maybe then make a script at least as a work around
save just save this in a basic text file and make sure its marked as executable, ```
#!/bin/bash

rsync -av --delete /home/chris/Music /media/250GB\ EXT/Music 
rsync -av --delete /home/chris/Videos /media/250GB\ EXT/Videos 
[etc, etc.]
```i would start as just the music folder as you know this runs in less than a second, keep adding more lines and folders until you have located the problem folder, thats the best i can help you with this  im afraid,

run the script by double clicking it and run in terminal or if the file is on your desktop and the file is called script then run```
time ~/Desktop/script
```

---

### Post by chris282 on 2011-04-19
Hello, I'm afraid I'm still having difficulties with this.  After creating and running the bash script, all my music files were recopied again.  This happened a couple of times, and then it only resaved a few, but I'd been messing about with the script by that point, so I went back to the command line and started again from scratch with

[PHP]rsync -av --delete /home/chris/ /media/250GB\ EXT/[/PHP][FONT=Verdana]
to ensure I was working with a fresh backup.  As expected, this took the usual 20 minutes.

sent 15066201461 bytes  received 1134666 bytes  14397836.72 bytes/sec
total size is 30280541068  speedup is 2.01
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

I then used the command that had worked previously on the music files

[/FONT][PHP]rsync -av /home/chris/Music/ /media/250GB\ EXT/Music/[/PHP][FONT=Verdana]
and as before, this worked in a flash.

sent 19347 bytes  received 1725 bytes  42144.00 bytes/sec
total size is 17530018152  speedup is 831910.50

Finally, I added the --delete command, since this was suggested for the bash script
[/FONT][FONT=Verdana]
[/FONT][PHP]rsync -av --delete /home/chris/Music/ /media/250GB\ EXT/Music/[/PHP][FONT=Verdana]
and got a slightly different result.  This made a change to a single album, taking 25 seconds, and when I ran it again it did exactly the same thing.  Since I had made no changes since my initial backup, this is not what I expected.

sent 684585719 bytes  received 2157 bytes  26846583.37 bytes/sec
total size is 17530018152  speedup is 25.61

Before I go any further back into my script, could you possibly let me know whether this is as it should be?


[/FONT]

---

### Post by chris282 on 2011-04-20
Additional:

Restarting the computer and using command

[PHP]time rsync -av --delete /home/chris/Music/ /media/250GB\ EXT/Music/[/PHP]

re-copies some, but not all albums.

sent 9242822118 bytes  received 5792 bytes  24419624.60 bytes/sec
total size is 17530018152  speedup is 1.90

real    6m18.118s
user    1m55.491s
sys    1m43.758s

Running it again immediately afterwards recopies a single album.

sent 684585719 bytes  received 2157 bytes  24894104.58 bytes/sec
total size is 17530018152  speedup is 25.61

real    0m27.275s
user    0m8.361s
sys    0m7.993s

I can't make head nor tail of this.  :confused:

---

### Post by Zimmer on 2011-04-20
Why not create a log file to view the results.... at your leisure.

sudo rsync -av --progress --delete --log-file=/home/chris/$(date +%Y%m%d)_rsync.log  /home/chris/Music/ /media/250GB EXT/Music/

putting a new label on the external drive without a space in it could be a way to go in the future, too ;)

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync) for simple examples
and this here
[http://rsync.samba.org/FAQ.html](http://rsync.samba.org/FAQ.html)

that may answer some of your queries regarding why files are copied again...

---

### Post by collisionystm on 2011-04-20
> **chris282 said:**
> Additional:

Restarting the computer and using command

[PHP]time rsync -av --delete /home/chris/Music/ /media/250GB\ EXT/Music/[/PHP]re-copies some, but not all albums.

sent 9242822118 bytes  received 5792 bytes  24419624.60 bytes/sec
total size is 17530018152  speedup is 1.90

real    6m18.118s
user    1m55.491s
sys    1m43.758s

Running it again immediately afterwards recopies a single album.

sent 684585719 bytes  received 2157 bytes  24894104.58 bytes/sec
total size is 17530018152  speedup is 25.61

real    0m27.275s
user    0m8.361s
sys    0m7.993s

I can't make head nor tail of this.  :confused:


I was just going through this thread and I cant believe how complicated this has become for you. I use Rsync for everything, I backup my windows servers and unix boxes with rsync to an ubuntu 10.10 server with a buffalo raid 5 storage unit attached. Just use this command

rsync -rqa  /home/chris/* /media/250GB\ EXT/

Do you notice how I included the Asterisk * , it is a wild-card to copy everything. 

Make sure you add this to Crontab so it syncs automatically.

crontab -e

Use NANO if this is your first time using it

enter:    0 1 * * * rsync -rqa  /home/chris/* /media/250GB\ EXT/ to have it sync every day at 1 a.m.

Now hit CTRL+X  and then Y to save

'successfully installed new crontab'

This will grab everything in your home folder, hidden or not.

To check your files, just change directory to your 250 gb hd

cd /media/250GB\ EXT/

now do ls -lh ( LS -LH) to check time stamps on your folders. Keep in mind not all of your time stamps will reflect todays date.

do ls -a (LS -A)  to check for your hidden files

BOOM. Your done. Congrats. Your backing up your stuff.

And for the love of god, 

you do not need to watch these transfers to do not include a -v or --progress. This is unnecessary. you just need q for quiet, r for recursive and a for archive.

---

### Post by rp1987 on 2011-04-20
> **chris282 said:**
> Additional - tried 250GB_EXT and got this error:

chris@chris-desktop:~$  rsync -av  --delete /home/chris /media/250GB_EXT
sending incremental file list
rsync: writefd_unbuffered failed to write 531 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/media/250GB_EXT" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
chris@chris-desktop:~$

Hi all,

Am kinda new to Ubuntu. Using 10.10 Maverick. I have an 500GB extn with a  lot of important data. The company and make of the external is "Western  Digital My Passport Essential". The prob am facing is that it has an  executable called unlock.exe which is compatible for Windows and to my  knowledge in Mac. But am unable to unlock the drive and access my files  in the OS that am using currently. Pls help me out with this. 

I have fast approaching deadlines immediately after the Easter break and  I dont wanna end up working in the last min (like I always do).

Thanks in advance.

Cheers,
rp

---

### Post by collisionystm on 2011-04-20
You have encrypted drive. You need to access your files with windows. Or try WINE to get that unlock.exe

---

### Post by Learning Linux 2011 on 2011-04-20
You could also simply use **tar** to create a "zipped" file of your home directory and send it straight to your external drive.  It would take up more space since all of your files would be backed up instead of just the changed files, but it would be easier to manage.

Here is a script that tells you how to do it:
[https://help.ubuntu.com/10.10/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/10.10/serverguide/C/backup-shellscripts.html)

---

### Post by chris282 on 2011-04-20
What can I say?  collisionystm, you are a shiny golden god.  

Thanks to everyone else who chipped in on this, especially CM.  Your time and patience was massively appreciated.

You guys... :D

- Chris.

PS. I'll mark the thread as solved once we hear back from rp1987.

---

### Post by collisionystm on 2011-04-21
> **chris282 said:**
> What can I say? collisionystm, you are a shiny golden god. 
 
Thanks to everyone else who chipped in on this, especially CM. Your time and patience was massively appreciated.
 
You guys... :D
 
- Chris.
 
PS. I'll mark the thread as solved once we hear back from rp1987.
 
:popcorn:

---

### Post by collisionystm on 2011-04-21
I guess the thread is solved???? No replies....

---

### Post by CaptainMark on 2011-04-30
Ive been thrown back into your boat, ive been testing 11.04 for ages on the alpha/beta but now its full release something seems to have changed because i have files in home in the gwibber config directories that contain a : appparently this makes rsync fail, and also there has been a symlink placed in the .pulse directory and now after i get errors anything after that will do a full copy everytime. Ive been thrown back to the drawing board now

---

### Post by CaptainMark on 2011-04-30
panic over, i solved this simply by re formatting my external hdd to ext2 instead of fat32, if you dont plan on accessing your external drive from your windows install this is an easy option and should sort out your troubles,

also im not sure why this never came up before because my ubuntu one directory has always had a link in it, oh well, solved i think, for now

---

### Post by psusi on 2011-05-02
You really should use ext3/4 instead of ext2.  Ext2 is quite prone to errors requiring length checks especially after a crash or power failure.  Additionally ext3 and 4 have several speed/efficiency improvements.

---

### Post by CaptainMark on 2011-05-03
well i did try ext4 first but still had errors, i just wanted to get my data backed up first. now ive made copies i will try ext4 as it would be my first choice

---

### Post by chris282 on 2011-10-13
Hi all,

I'm returning to this again since I still don't have a particularly satisfactory way to back up files.  I set the cronjob to run in the early hours of the morning, but have just found that this hasn't actually been working.  I've had the PC on standby, not shut down.  If I run the cronjob in the daytime I'm back to the original issue whereby I'm slowed down for twenty minutes a day.
[I][COLOR=Gray]
I also note that my home folder contains 74,961 items, totalling 42.7 GB, while my backup contains 56,774 items, totalling 42.0 GB.
[Additional - after manually running rsync -av this is no longer a problem][/COLOR][/I] 

To recap, my goal is to quickly back up all files once a day.  What are other people doing, and what am I missing that I'm finding this to be such a problem?

Advice?

---

### Post by chris282 on 2011-10-13
Reset as unsolved.

---

### Post by CaptainMark on 2011-10-18
are you using ext4 partitions on your main hdd and your back up location?

---

