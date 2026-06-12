---
title: "my files are locked when booting from CD"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by UncleAlan on 2010-09-24
Following an update that locked up my PC on reboot last week ( a problem that appears to have been ongoing for years and is unsolved) I obtained a boot CD. Now when I boot from the PC I can get to my files via PLACES-81GB Filesystem-Home XXXXX Folder.
 
However most of the folders are locked and I cant do anything with them as it says I am not the owner. I am  and If I could somehow tell it my password I presumably would have access.
 
So I need to Either be able to boot from the CD and tell it my Password or have some instructuion that works to fix the fsck lock up. (some have tried but nothing works).
 
I am in need of backing up some files somehow then I am going to install a later version as the locked up one is 9.10.
 
Things are getting some what fraught !!!!
 
Thanks Alan

---

### Post by Rubi1200 on 2010-09-24
The original post is old, but the principles still apply and it should work on the Ubuntu CD as well:
[http://ubuntuforums.org/showpost.php?p=903240&postcount=1](http://ubuntuforums.org/showpost.php?p=903240&postcount=1)

Once you have access, rescue your files and then try cleaning up the system.

---

### Post by halj32 on 2010-09-24
have you tried right clicking on the folder & opening as admin??

---

### Post by coffeecat on 2010-09-24
> **UncleAlan said:**
> However most of the folders are locked and I cant do anything with them as it says I am not the owner.

.....

Things are getting some what fraught !!!!

Fear not, I have the answer. :) Co-incidentally I was answering very much the same question earlier today. Have a look at my posts #10 and #13 in this thread:

[http://ubuntuforums.org/showthread.php?t=1581073](http://ubuntuforums.org/showthread.php?t=1581073)

#10 explains why you are not the owner when you are in the live CD session. The UID is different. You need to open a root nautilus with 'gksudo nautilus'. But then it gets difficult to find your files. #13 tells you how to navigate to your home folder on the hard drive.

---

### Post by Rubi1200 on 2010-09-24
@coffeecat

Sorry for the obvious question, but why not just chroot into the file-system? That way not only can one get files, but also perform system maintenance.

---

### Post by coffeecat on 2010-09-24
> **Rubi1200 said:**
> @coffeecat

Sorry for the obvious question, but why not just chroot into the file-system? That way not only can one get files, but also perform system maintenance.

The way I read the OP's first post is that the files may be "locked" simply because of permissions problems. It may be that they have 740 permissions and with the different UID between the 'ubuntu' live session account and the OP's UID on the HD, that would be one explanation for the 'lock'.

But I accept that a fsck might be necessary. But you don't need to chroot to do a fsck, or to copy files. A beginner would be more comfortable with the GUI. And this is the **absolute** beginner's forum, after all. I would hesitate to describe or suggest a chroot here. It might frighten someone. :p

But thanks for posing the question. I may very well have misunderstood the original problem. What's your read of it?

---

### Post by Failboat88 on 2010-09-24
gksu nautlius

Type that into terminal. Then on the files you want, change the permission. If you have a ton of files there may be ways to do it all in command line. I did it file by file. 

If you don't change the permission; when you move the file it will still be locked.

Edit: Someone beat me to it. =)

---

### Post by UncleAlan on 2010-09-24
Thankyou for this, however although I think I understand it I dont have anything like it mentions! Running from a Ubuntu 9.10 live cd I have got to the Brown desk top and  This now has 3 icons. "Examples, Install Ubuntu 9.10 and 81GB Filesystem." I can drill down through my old files although I dont think they are all there. Some folders and files have a cross by them. If I left click on one such file then right click I get a drop down menu but there is no mention of the word action.
 
Sorry I dont know what a GUI is. Yes I am a dunce , I have installed Ubuntu  and windows on PCs and even managed to follow simple codes in Ubuntu before but now I need instructions that are very simple. Its almost there yet so far away!!! 
 
Failboat 88 that souds a good fix but where would I type gksu nautlius ???
 
Thanks Alan

---

### Post by Rubi1200 on 2010-09-24
In the terminal which you can access by going to Applications > Accessories > Terminal.

Just be aware that using gksu will give you root privileges; please be very careful and if you are unsure ask here first.

GUI = [http://en.wikipedia.org/wiki/Graphical_user_interface](http://en.wikipedia.org/wiki/Graphical_user_interface)

By the way, the cross next to files and folders may indicate a permissions problem; did you change permissions when the system was working properly? If so, do you remember what you did?

---

### Post by Rubi1200 on 2010-09-24
> **coffeecat said:**
> The way I read the OP's first post is that the files may be "locked" simply because of permissions problems. It may be that they have 740 permissions and with the different UID between the 'ubuntu' live session account and the OP's UID on the HD, that would be one explanation for the 'lock'.

But I accept that a fsck might be necessary. But you don't need to chroot to do a fsck, or to copy files. A beginner would be more comfortable with the GUI. And this is the **absolute** beginner's forum, after all. I would hesitate to describe or suggest a chroot here. It might frighten someone. :p

But thanks for posing the question. I may very well have misunderstood the original problem. What's your read of it?
Yes, you are right about not wanting to scare people away! I think the problem is likely one of permissions, though we have not heard from the OP if, or how, that was achieved.

Thanks for answering and for your input; much appreciated.

---

### Post by UncleAlan on 2010-09-24
Thanks for your replies, Had a look at a few bits and I now recognise the screen for the command as I have used instructions there before. Some good things to look up and I very much appreciate all your help as I am in a stunned state fearing all is lost (still think some is).
 
shall post update when soon,
 
Thank you again
Alan.

---

### Post by JKyleOKC on 2010-09-24
> **Rubi1200 said:**
> I think the problem is likely one of permissions, though we have not heard from the OP if, or how, that was achieved.It would be automatic, I think, since the OP's User ID on the HD installation would be 1000 and I have no idea what UID the live CD assigns for its default user "Ubuntu" but I'm reasonably sure that it's NOT 1000 since that would prevent assignment of that value to the new user when doing the install...

UncleAlan, don't let this posting confuse you too much; it's just an aside to the other folk helping in the thread. The main point, from your perspective, is that you don't have the same permissions when using the live CD as you do when logged into the HD installation, because the "UserID" number is different. Some of the others seemed to be feeling that you made some changes to the permissions and I'm pointing out that no such changes were necessary to get the actions you're seeing...

---

### Post by coffeecat on 2010-09-24
> **JKyleOKC said:**
> The main point, from your perspective, is that you don't have the same permissions when using the live CD as you do when logged into the HD installation, because the "UserID" number is different. Some of the others seemed to be feeling that you made some changes to the permissions and I'm pointing out that no such changes were necessary to get the actions you're seeing...

+1. I tried to make this point and I'm really glad someone's emphasised it more clearly than I did.

---

### Post by UncleAlan on 2010-09-25
HI CoffeCat,
 
Inching forward slowly..On step forward 9/10 of one back.  Booted from CD, Applications-Accsessories-Terminal  at the cursor typed gksudo nautilus and pressed enter. I got a Root file Browser AND the message reproduced in full below. I had a look at the Root File Browser. On the Left side of the main screen under the title Places was listed Root,Desktop, File System,Network, Trash. File system has many folders and one is home.
 
I am a little confused now as I think the message below means I am not quite at the place referred to in post 13of your instructions (which I do understand)
 
Thankyou for your patience.
 
 
 
 
[FONT=Times New Roman][SIZE=3]To run a coomand as administrator (user “root”), use”sudo<command>”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]See “man sudo_root” for details.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[EMAIL="ubuntu@ubuntu:~$"][FONT=Times New Roman][SIZE=3][COLOR=#0000ff]ubuntu@ubuntu:~$[/COLOR][/SIZE][/FONT][/EMAIL][FONT=Times New Roman][SIZE=3] gksudo nautilus[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3](nautilu:3217): Eel-CRITICAL **:eel_preferences_get_Boolean: assertion ‘ preferences_is_initialised()’ failed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Inializing nautilus-gdu extension[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]** (nautilus:3217): WARNING **: No marshaller for signature of signal ‘UploadFinished’[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]** (nautilus:3217): WARNING **: No marshaller for signature of signal ‘DownloadFinished’[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]** (nautilus:3217): WARNING **: No marshaller for signature of signal ‘shareCreateError’[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Nautilus-Share-Message: Called “net usershare info” but it failed: ‘net usershare’ returned error 255: net usershare: cannot open userhare directory /var/lib/samba/usershares. Error No such file or directory Please ask your system administrator to enable user sharing.[/SIZE][/FONT]

---

### Post by coffeecat on 2010-09-25
First, ignore all those alarming messages you get in the terminal. That's just the system gibbering to itself. :)

I'll describe a slightly different way from my post #13 in that other thread. To navigate correctly is somewhat bewildering, so hold on to your hat!

In the live CD, go to the Places menu at the top of the screen. Click on the entry that corresponds to the hard drive partition you are trying to access. This is very important. When you click on the Places entry, a nautillus file browser will open. Close it - if you use it, you will encounter your permissions problems again.

Now do 'gksudo nautilus' in the terminal, and ignore what the terminal is muttering. A Nautilus file browser will open with just a Desktop icon in the main pane. This file browser window gives you full root powers, so be careful. In the left pane, under 'Places', click on 'File System'. You will be presented with a plethora of folders starting with /bin. This is the root filesystem of the live CD, **not** your hard drive install. Double-click on the /media folder. There will, hopefully, be one folder in /media. I cannot tell you its name because this varies depending on local factors. If there is one folder, double-click on it. If there are more, try them each in turn. When you open the correct one, you will be presented with a plethora of folders just the same as before. **There is an important difference.** This is the root filesystem of your hard drive partition. If you do not see these folders, you have mounted the wrong partition from the Places menu.

If you are seeing all these folders, double-click on /home. You will see a folder named with your user name. This is your home folder on the hard drive. Double-click on this and you are home in both senses of the word. You can now use drag and drop in the GUI to copy your files to an external USB drive. Use a USB drive formatted FAT32 or NTFS otherwise you will encounter permissions problems when you try to access them from the USB drive next time.

**Important caveat**: what I have described is for if your home folder was in the root partition of your Ubuntu system. If you created a separate /home partition, you have to mount the home partition from the Places menu and, in fact, your stuff will be easier to find. Post back if you had a separate home partition.

---

### Post by UncleAlan on 2010-09-26
Hi Coffeecat, when I installed 9.10 soths back I just went with the instructions on screen to install and remove windows. Thereafter it worked and I didnt do anything with partitions the system sorted it all out.
 
I am now proceeding to carry out instructions. Fingers crossed.

---

### Post by UncleAlan on 2010-09-26
Hi Coffeecat,
 
A FANFARE of Trumpets !!!!!
 
I can see and open my fiolders and files !!!! I still seem to have lost some photos which is a puzzle as I cant remember the order of the files , but at least the Family history is saved !!!! 
 
There is a BUT.
 
Having got my file open on the screen I plugged in my memory stick ( it does work as I have just used it on the vista pc) but the Ubuntu pc isnt detecting it. It used to. 
 
I was expecting the memory stick to show up in the left pane under the drive I am reading my files from. Then I was expecting to click and drag items from the right pane into the memory stick on the left pane, go back to the brown desk top where I would have expected to see an icon for the stick right click to choose safely remove it and see if the vista pc could read it as it used to.
 
 
I cant thank you enough for you patience and help so far and the others that have commented to help my understanding of Ubuntu. If all else fails at least I can now take photos of the info on screen. LOL.

---

### Post by coffeecat on 2010-09-26
> **UncleAlan said:**
> Having got my file open on the screen I plugged in my memory stick ( it does work as I have just used it on the vista pc) but the Ubuntu pc isnt detecting it. It used to. 
 
I was expecting the memory stick to show up in the left pane under the drive I am reading my files from. Then I was expecting to click and drag items from the right pane into the memory stick on the left pane, go back to the brown desk top where I would have expected to see an icon for the stick right click to choose safely remove it and see if the vista pc could read it as it used to.

Not only should the USB stick appear in the Places column, but a nautilus browser window should open for you as well. Have you got another USB stick you could try, or a USB hard drive? If not, try using Vista to backup anything on that USB stick you need and then use Vista to reformat it. It's possible that there's a filesystem corruption on the stick that Vista can cope with but not the Ubuntu live CD. A bit of a long shot but worth trying.

---

### Post by UncleAlan on 2010-09-26
Hi Coffecat,
 
I think as I am somewhat a dork in these matters I was inserting the memory stick at too late a stage. Anyway I reformated it on the vista pc to rid it if the windows toxins as I think some frontpage files were possibley giving grief. Then I tried again inserting the stick at the brown screen before doing the Drill into the root. Then I had two Items under places with an up arrow shape and I was in business. Tried to copy some files to the stick and the colours on my screen all went grey, the CD drive made some horrible sounds which it always has when writing or reading a big file and then things went normal. I checked things were on the stcik, went back to my new found files and then the brown screen to safely remove the stick. I put it in the vista and transferred to a folder even I can find and tested.
 
**IT WORKS !!!!!!!**
 
Well nearly.... only joking, I didnt want to upset things by trying to convert an OSD spreadsheet into XlS as I know when it goes back to a Ubuntu system it will work.
 
 
Just a final query - is there a way of viewing what I had in my bookmark list for the internet? I have a couple of hobby sites I use for ordering and can never remember them. Also can I see what Software I had installed? 
 
**THANKYOU AGAIN** for your **extreme patience** and help dealing with a person who has little experiance of the 'Dark side' When backed up I shall do a fresh install of Ubuntu 10s latest full version and back up every time !!!
 
To all who helped with this issue I have learnt from you Thankyou
 
Alan

---

### Post by Zimmer on 2010-09-26
Bookmarks...
You will need to navigate to your old Home folder (gksudo nautilus ) and then hold CTRL and pres  h.
This will reveal hidden files and folders.

Folder you need is 
.mozilla>firefox>'randomcharacters'.default   
(where randomcharacters could be anything  eg. ACvrl65.default )

and look for the file bookmarks.html

copy this file and save it safe.
You can either open it with Firefox to view links and/or when you restore an Ubuntu install copy it to the corresponding location in the new install.

---

### Post by coffeecat on 2010-09-26
I'm glad you got your files. Before I answer your question about bookmarks, will you tolerate a little sermonising? :wink: There's an old adage in the computer world: your personal data is much more valuable than the medium on which it is stored. There's another: backup, backup and backup again. Oh, and did I say to backup?

I'm obsessive about backing up. I can replace a defunct USB stick. I can replace a faulty computer. I can't replace my files if I lose the one and only copy. I keep backups on my fileserver, two USB hard drives and two USB sticks. So - whether it's a hardware problem or an unbootable borked operating system I can repair the computer and/or reinstall the OS and restore my data from a backup I've already made.

What I'm not very good at is keeping extra copies off-site. What if I had a fire that destroyed my house and belongings? Hopefully my insurance company would restore the house and replace the belongings, but what if all my backups went up in smoke? Something to think about. Time to buy a handful of USB sticks, perhaps.

Moralising over. :)  

> **UncleAlan said:**
> Just a final query - is there a way of viewing what I had in my bookmark list for the internet? I have a couple of hobby sites I use for ordering and can never remember them. Also can I see what Software I had installed? 

There used to be with pre-version 3 Firefox. You could "drill down" - I like that - into the hidden .mozilla folder in your home folder and copy a file called bookmarks.html which contained all your bookmarks. There is still a bookmarks.htmll file but it doesn't contain your personal ones. Since Firefox 3 was launched there is a much more sophisticated database handling your personal settings and I don't think there's a single file you can rescue. You have to be running firefox to export either a html or json file with your settings - which isn't feasible in this case.

What you could do is to copy the whole .mozilla folder and contents onto your backup drive. You will have to ctrl-H to view hidden files to do this - all hidden files and folders have a leading full-stop. But I'm not sure whether copying this onto a Windows-formatted drive will work. I believe, but I'm not certain, that certain permissions have to be retained in the .mozilla folder and these will be lost in a Microsoft filesystem. Then what you do is to put the .mozilla folder and all contents in your home folder in the new installation. The big advantage is that your bookmarks, passwords, cache, browsing history and settings are all copied over. However...

**Health Warning** - using a Microsoft filesystem will mean that every file in .mozilla will be made executable when copied back into a Linux filesystem. This might be a security risk - I hope someone might comment, clarify or correct me. And if you were to format the USB drive with a Linux filesystem, when you copy with the root nautilus, everything will probably be owned by root, which causes more problems. Easily fixed by an experienced user but something to think about.

Short answer: it might be problematic.

Good luck!

---

### Post by Zimmer on 2010-09-26
Hi Coffeecat, I have to admit I had forgotten about the latest release of Firefox and the difference in bookmarks.html (perhaps because I have been using Opera for some time now).

However, I created a bookmark in a Kubuntu install and used the Bookmark manager to back it up.. copied the .json file created in the Bookmarkbackups folder to the same named folder in an Ubuntu install and using the Bookmark manager here Restored using that file.

Seemed to work ok, the extra bookmarks I had created were reproduced...

I noticed in my Ubuntu install that there were files in the Bookmarksbackup folder already (dated) but have no recollection of creating them.
If Firefox created (or creates) them automatically under special circumstances (new version, crash etc.) it might be the OP has a useable .json file that he could rescue by copying and restoring...

Just a thought.. :)

---

### Post by coffeecat on 2010-09-26
> **Zimmer said:**
> 
Just a thought.. :)

I'd forgottten about the bookmarksbackup folder. That's the place to go. You're quite right. Thanks.

**@UncleAlan**, forget all my burbling in my previous post. Zimmer is quite right.

Boot up with the live CD and navigate to your home folder the way I described. Press ctrl-H to reveal the hidden files. Double-click on the .mozilla folder, now on the firefox folder, next on the folder named somerandomstring.default, and lastly on the bookmarksbackup folder. In that you will, hopefully, see a number of bookmarks*.json files with * = date. Copy the lot.

When you've reinstalled Ubuntu, open Firefox, go to Bookmarks > Organise Bookmarks > Import and Backup > Restore > Choose file and point the thing at your .json file. Bob should now be **your** uncle. :)

---

### Post by UncleAlan on 2010-09-27
Hi Helpers,
 
I have it on my next job list for today to get a bucket load of those sticks.
 
I'll look at the latest help tonight now I'm on a roll !!!!
 
Thanks for that.
 
Alan

---

### Post by UncleAlan on 2010-09-27
Hi Zimmer & Coffeecat,
 
well I did that and there were 5 folders that seem to show dates of the few days before it all went wrong. Not sure if It has all the info but it isnt the end of the world if it hasnt.
 
Now I'll do a new install of Ubuntu and start again a wiser person.
 
Question.
 
Having been stunned by an update that went horribly wrong and then finding out its best to shut down completly and restart rather than doing a re start (as it requested) In futre am I best to never do any updates if it all works and then just reinstall when a proven new version comes along every once in a while? or am I suffering from once bitten twice shy here?
 
Thanks  Alan.

---

### Post by coffeecat on 2010-09-27
> **UncleAlan said:**
> 
Having been stunned by an update that went horribly wrong and then finding out its best to shut down completly and restart rather than doing a re start (as it requested) In futre am I best to never do any updates if it all works and then just reinstall when a proven new version comes along every once in a while? or am I suffering from once bitten twice shy here?

To your last question: I hope so.

I have never, ever had an update that has wrecked my system. That doesn't mean that it doesn't happen, but these days it's rare. I remember back in 2006 that a faulty update  was pushed out by accident. It caused many people's systems to become unbootable. The forums went into meltdown! But a lot was learnt from that and proper QA is much better now.

There's a repository called "proposed" into which all proposed (obviously) updates are put. Some experienced users enable the proposed repository to test these updates. If they survive the testing, they are pushed out into the ordinary repositories which is when most users get them. So you can be assured that when you see updates they will have had some field testing already. Of course, the proposed repository is also the cause of breakages with some unwary users. Some inexperienced users (mostly younger age group for some unfathomable reason :rolleyes:) enable the proposed because they think they're getting the latest and greatest. And then they complain bitterly when they break their systems. So - keep away from proposed unless you want a white-knuckle ride.

Another thing to think about. Updates are mostly for bugfixes and for patching security issues. You would be unwise to avoid them. Let's hope what you experienced was a one-off. Good luck!

---

### Post by Zimmer on 2010-09-27
> **UncleAlan said:**
> ...
 
Having been stunned by an update that went horribly wrong and then finding out its best to shut down completly and restart rather than doing a re start (as it requested) In futre am I best to never do any updates if it all works and then just reinstall when a proven new version comes along every once in a while? or am I suffering from once bitten twice shy here?
 
Thanks  Alan.

Updates do not normally cause problems but UPGRADES can produce odd effects.

My own best practice (for the paranoid) 
when an Upgrade to a NEW VERSION (eg   9.10 to 10.04 etc..) appears is to NOT upgrade, but back up all personal files (I actually have a partition I use to store all data files anyway , and that is backed up elsewhere,too!!) 
and to install the New Ubuntu version from scratch..

There are others who recommend having a separate /Home partition so that one can install a new Version to the / (root) partition leaving the /Home files intact.

I have my doubts about the efficacy of this as there are a lot of hidden folders and settings which may not apply to the new install or even mess it up, but I am not expert enough to confirm or deny this, so I play safe with my personal data files.

ps. 
My Update Manager settings have the Final option 'Release Upgrade' (show new Distribution Releases )  set to 'Never' so that I do not accidentally trigger a New release Upgrade.

---

