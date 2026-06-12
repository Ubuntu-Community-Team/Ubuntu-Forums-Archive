---
title: "Removing Ubuntu"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-04-03
I need to remove as im taking my laptop to get it fixed by geek squad and since the terms require i have to only have Windows in order for them to work on it..

i need a link/guide to delete ubuntu and its partition on my drive.....i hope its easy..thanks

---

### Post by SunnyRabbiera on 2009-04-03
Ah heck with the geek squad, you are better off trying to find a local computer repair shop.
Much cheaper :D

---

### Post by D1ZZ4ZZT3R on 2009-04-03
seriously, don't give in to the tyranny. but, if you can't find a local comp repair shop or, at least, someone you or a friend might know who fixes computers, you'll have to elaborate on your situation. are you already running windows in a dual boot? do you have a copy of windows available? is it a startup disc (one of those things that returns you to how the computer was when you bought it. dear god **SHUDDERS**) or, is it an actual windows cd? what's your situation?

---

### Post by |Mitch| on 2009-04-03
> **SunnyRabbiera said:**
> Ah heck with the geek squad, you are better off trying to find a local computer repair shop.
Much cheaper :D

x2

---

### Post by Skol312000 on 2009-04-03
i got a recovery cd for vista that will reset the computer to factory settting and i really really really dont wanna use that lol

i just need Ubuntu and the grub thing loader gone...i wanna keep all my info and not touch Vista if possible...please guys...

---

### Post by SunnyRabbiera on 2009-04-03
Were you under warranty?
If not just take it in, screw em if they cant figure out your OS.

---

### Post by Skol312000 on 2009-04-03
i need to remove it...

i cant have anything but Vista..

so i need to know how to remove it..

if anyone can help i would appreciate it

---

### Post by SunnyRabbiera on 2009-04-03
Is it a hardware issue or software issue?
If its hardware then I would not care about their rules, A PC is a PC.

---

### Post by D1ZZ4ZZT3R on 2009-04-04
> **SunnyRabbiera said:**
> Is it a hardware issue or software issue?
If its hardware then I would not care about their rules, A PC is a PC.


naw, dude, they WON'T work on it unless it has windows.


and skol, as far as saving your info, if it's pictures and stuff, i'd say just back it up on a flash drive or cd's. then, use the system restore but, i'm telling you, find someone else, screw geek squad. there's no good, valid reason that you should have to compromise your own integrity (if you will) just because they have stupid rules. and, chances are, like you've already been told, it would probably be cheaper. just ask around, check the yellow pages.

also, how is your hard drive partitioned? do you have a home partition with all your data, and one with your OS? it might be possible to system restore on the OS partition and still maintain your data on the home partition but, because windows and linux use different formats, it might not be. someone here has to know more about it than i do. maybe you can edit the thread title to something more specific to attract more knowledgable people.

---

### Post by D1ZZ4ZZT3R on 2009-04-04
i just had another idea, can you take your hard drive out and bring it in that way? i mena, if they ask why, just tell them you use linux and you weren't willing to put windows back on your hard drive just so they'd work on it. if you have an old hard drive sitting around, put windows on that and bring that to them. there's always a workaround.

---

### Post by Bios Element on 2009-04-04
Heck, Just take the hard drive out. I'm willing to bet that'd work just fine. That's what I had my uncle do with his linux laptop and they didn't care. That'll work fine if it's a hardware issue.

---

### Post by asmoore82 on 2009-04-04
[COLOR="Blue"]Microsoft.com: How to Remove Linux - [http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)[/COLOR]

:KS

---

### Post by Skol312000 on 2009-04-04
i have windows Vista.

i just did a factory reset with my Vista Cd and i dont think ubuntu is out..

what can i do to make sure UBUNTU gets DELETED??

---

### Post by raymondh on 2009-04-04
I'm trying to remember this so bear with me. And you'll need the VISTA install disc

In Vista

Control panel and look for the disk management tool.  I think it's along with the defrag tool.  Click open and click the ubuntu partition.  You'll have option to delete Ubuntu partition. Then reformat same partition to NTSF.  Then resize/expand Vista. Whatever it is, do not delete Vista partition.  BE SURE YOU KNOW WHAT IS THE VISTA and THE UBUNTU PARTITIONS.  Vista uses NTSF whilst Ubuntu Uses EXT format

Important to fix MBR. This is where you'll need the install disc.

Boot install disc.  Click next for time and language. Click REAPIR COMPUTER (I think that's how it's worded). Click OS > recovery options > command prompt.  Type bootrec.exe/fixMbr

I think that's it.  Sorry for the lack of more details.  Am answering this on-the-fly and from what I remember.

Google can be your friend as well.

Good luck

---

### Post by Didius Falco on 2009-04-04
Skol,

Is your PC booting directly into Windows now, without getting the Grub boot loader?

If so, it probably wiped all the partitions except the one where your Windows restore is and set the rest of the HDD back to one Windows partition.

To make sure, simply boot up using the Ubuntu cd (make sure the Bios is set to boot from CD first) and choose the "try without making any changes to my PC" option.

Once it loads up, go to  System > Administration > Partition Editor to launch GParted.

Load Gparted and and take a look at the partitions. If you see any that are listed as Ext2, Ext3 or Linux Swap, delete them. You can then resize the Windows partition to reclaim all the free space.

---

### Post by Skol312000 on 2009-04-04
ok i did that...how do i rezize expand..
?

i now freeup my hard drive of ubuntu so ubuntu is not there..and when i start up i dont see GRUB..that doesnt mean it isnt ther i guess..

anyways

how do i resize/expand vista?
after i freed up all that space...
when i go to my computer...it doesnt show it as free space..i chose a path''c/"new folder" i dont know...please help




EDIT HUGE!!  this messege was written before DIDUS posted his messege

im about to go try what DIDUS said tho..

---

### Post by raymondh on 2009-04-04
control panel>system & securityty > administrative tools > create and format hard disk partitions

That'll bring up the disk management tool

---

### Post by raymondh on 2009-04-04
> **Skol312000 said:**
> 

how do i resize/expand vista?
after i freed up all that space...
when i go to my computer...it doesnt show it as free space..


Gparted or Disk management (Vista) can expand the existing Vista partition.  In Disk management, right click on the existing partition and you ought to see the option to expand.

Also, if you're booting into windows now, then you don't have to fix Mbr

---

### Post by Didius Falco on 2009-04-04
Skol,

Okay, you are nearly done. Since it's now booting directly into Vista, Grub is history, and you've deleted the partitions that Ubuntu was using.

All that's left to do is to reclaim the free space, and that's not even needed to meet the Geek Squad requirements.

You should do that from Vista, using the advice raymondhenson provided. The disk management tool in Vista should have a help file that will explain how to resize/expand the partition.

I'd encourage you to try Ubuntu again, though. Remember, you can always install it right in Windows using Wubi, and remove it using Add/Remove Programs in the Control Panel.

---

### Post by Skol312000 on 2009-04-04
ok well im in UBUNTU now i clicked "try ubuntu without change to your computer" from the Ubuntu live CD and i opened Gparted..can i get some instructions for gparted now that im in it please...i need to join my empty space and add everything to Vista,...please

---

### Post by phantom3113 on 2009-04-04
> **asmoore82 said:**
> [COLOR="Blue"]Microsoft.com: How to Remove Linux - [http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)[/COLOR]

:KS

That looks like it *might* be a bit outdated. It tells you to insert the Linux "floppy disk". I can't remember the last time a floppy disk was used for anything. :P

---

### Post by Didius Falco on 2009-04-05
Skol,

What is Gparted reporting? Is it showing "Unallocated space"?

---

### Post by Skol312000 on 2009-04-05
yes sir it was..i moved backj to vista becasue u and the other helpful person have told me...Unallocated space its what Gparted reported...im trying to do it in Vista now..to joing both the "unallocated with the one occupied by vista currently

---

### Post by majamba on 2009-04-05
deleting Linux? what the hell?

usually you can find guys that do repairs on craiglist just don't see why neeed some company to repair computer vista. I am hopping that ban vista follows in other states not only texas.

---

### Post by Skol312000 on 2009-04-05
should i leave my "recovery" alone?

---

### Post by Skol312000 on 2009-04-05
omg....Vista wont let me clikc "Extend Volume" after i right click on both the "occupied partition" and the "unocupied"/free space one...

lol
wow...what now?

the "freed up partiton" it sais "Healthy (logical drive)


i also deleted all the previous path i assigned the "free space one" before..
so it has no path....and stilll no luck on resizing...

---

### Post by snkiz on 2009-04-05
burn a boot disk in vista then get parted magic live cd wipe out ubuntu and use the boot disk to fix the mbr. I think parted magic can do it to. Do you plan on putting Ubuntu back on? (hope so ;) ) don't forget to image your Ubuntu partition first, assuming you have a spare drive. Also available on parted magic I believe.

---

### Post by Skol312000 on 2009-04-05
i dont think i need to do that...

i got rid of ubuntu and grub....i just need to join both the free partition with tthe occupied partition (vista) together so i can use my whole drive...

---

### Post by Didius Falco on 2009-04-05
> **Skol312000 said:**
> should i leave my "recovery" alone?

If Recovery is a partition definitely leave it alone. I have no experience with the Vista OS, so load up the help file and it should tell you how to recover the free (Unallocated) space.

Like I said before though, you can always do that later if you want to, you already meet the Geek Squad requirement of only running Windows.

---

### Post by Skol312000 on 2009-04-05
yes. but i wanna make sure!

i just wanna give it back to them like it was..
so guys, the help doesnt help me....
what can i do?  this is  abig  deal..

---

### Post by Didius Falco on 2009-04-05
Okay, I just did a bit of quick research on the Vista disk management tool. It has a wizard that will walk you through it. Just select the Vista partition (it may be called a "volume" in the vista tool) and choose to extend it.

It should bring up a dialogue box that allows you to set how much to extend it. That box will tell you a number representing how much you can extend it. Simply put that same number in the "how much to recover" part and hit continue.

That should do it.

---

### Post by Skol312000 on 2009-04-05
Thats the problem... When i right click (so i can choose "extend") it shows the word "extend" in grey and not black.. So i cant select it... This also happens on the "freed up drive"...

What do i need to do in this situation?

---

### Post by Didius Falco on 2009-04-05
Okay, Here are some options for you:

1. Read this for an alternative way to do it from within Vista: [http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work](http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work)

2. Go back to the Ubuntu cd and boot into the "Try w/o any changes" option. Load Gparted (see instructions in a previous post if needed).

Follow the directions found  here: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

3. The easiest thing to do, if option 1 doesn't work, would be to just delete the Vista partition (NOT the recovery partition!!), make one NTFS partition and reinstall/recover Vista again.

One of these three options should do the trick for you. I'll be around for a little while yet, so I'm hoping to see you back with a "Success!!" report.

---

### Post by Skol312000 on 2009-04-05
Lets say i were going to restore to factory settings using the windows recovery disks...
Would that fix everything? I mean i do already have ubuntu and grub deleted... Would it be under only one partition? Or two (including recovery)which is fine???

---

### Post by Skol312000 on 2009-04-05
> **Didius Falco said:**
> Okay, Here are some options for you:

1. Read this for an alternative way to do it from within Vista: [http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work](http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work)

2. Go back to the Ubuntu cd and boot into the "Try w/o any changes" option. Load Gparted (see instructions in a previous post if needed).

Follow the directions found  here: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

3. The easiest thing to do, if option 1 doesn't work, would be to just delete the Vista partition (NOT the recovery partition!!), make one NTFS partition and reinstall/recover Vista again.

One of these three options should do the trick for you. I'll be around for a little while yet, so I'm hoping to see you back with a "Success!!" report.

Awesome, thanks for the links i appreciate it... I think im just gonna try the erasing of vista and then reinstalling again. I will do this tomorw as it is late where im at, thank u, and we will talk tomorow if u are fonna be available

---

### Post by -kg- on 2009-04-05
> **Skol312000 said:**
> omg....Vista wont let me clikc "Extend Volume" after i right click on both the "occupied partition" and the "unocupied"/free space one...

lol
wow...what now?

the "freed up partiton" it sais "Healthy (logical drive)


i also deleted all the previous path i assigned the "free space one" before..
so it has no path....and stilll no luck on resizing...

Do you by chance have an Extended partition in there?  If you have your free space contained within an Extended partition, then you will not be able to extend your Vista (Primary) partition into that space without first deleting the Extended partition.  An Extended partition is a special type of Primary partition in which you can create Logical Partitions.  See [this page]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics") and the Additional Notes on partitions from [this page]("https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions") for a more detailed look at what I'm talking about.  Check out the whole [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") section.

I wish I could have caught this thread earlier.  I can't for the life of me see what having Linux in dual boot with Vista would have to do with anything, especially if you're bringing it back for hardware issues.

I bought this laptop from Best Buy as well, and they had no problem with it; as matter of fact, they sold me the Ubuntu disk that I installed it on this computer with.  Not too long ago I brought it in, under warranty, to have the display replaced. But if they had real issues with it, there was something you could do:

You could have edited your menu.lst configuration file to automatically boot Vista instead of Ubuntu, then set the delay to zero.  It would have booted into Vista automatically and instantly, and it is unlikely the "geek squad" would even notice.  I've never done this and I don't know whether there might be a flash of the menu screen, but I'll bet there is a way that the display could be turned off, as well.

Once you got it back from the store, you could go in with your live CD and edit the menu.lst back to the original or, if you saved it, replace that menu.lst file with the one you saved as backup.

Anyway, since the point is moot now, what you need to do is check and make sure you don't have an Extended partition created containing the free space.

Check out [this page,]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition") which will show you what an Extended partition looks like under GPartEd.  If you see an extended partition, just delete it then try to extend the Vista partition with Vista's tool again.

---

### Post by Skol312000 on 2009-04-05
No ext , i formated it and set it too ntfs before earlier today...
Still cannot join... I guess ill just restore to factory settings again , but delete my current partition of Vista...

---

### Post by -kg- on 2009-04-05
> **Skol312000 said:**
> No ext , i formated it and set it too ntfs before earlier today...
Still cannot join... I guess ill just restore to factory settings again , but delete my current partition of Vista...

Yes, the ext partitions will have been contained within the Extended partition, making them Logical partitions.  Read the Documentation I referred you to, especially the section on [Extended Partitions.]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition")

---

### Post by presence1960 on 2009-04-05
> **D1ZZ4ZZT3R said:**
> i just had another idea, can you take your hard drive out and bring it in that way? i mena, if they ask why, just tell them you use linux and you weren't willing to put windows back on your hard drive just so they'd work on it. if you have an old hard drive sitting around, put windows on that and bring that to them. there's always a workaround.

I see from your tag you are also ACIM student yes?

---

### Post by presence1960 on 2009-04-05
> **Skol312000 said:**
> yes. but i wanna make sure!

i just wanna give it back to them like it was..
so guys, the help doesnt help me....
what can i do?  this is  abig  deal..

just make the extra partition NTFS and use it as a data partition. If you made it a logical partition, delete it and create a primary NTFS partition. You will have Vista on one, your recovery partition and a NTFS (Vista) data partition. You are making more out of this than is necessary. Maybe like you said it is late, get some shuteye, relax and rethink this in the morning.

P.S. Skol you should do a google search of LUG (Linux Users Group) to see if there is one in your area. it may benefit you to contact the group because they usually have set days to meet and a lot of members are available to offer help in person. I think this would benefit you since you have been having nothing but trouble since trying Linux. A little one on one face to face may be better for you. just a suggestion since I see you struggling big time here.

---

### Post by Skol312000 on 2009-04-05
If i use the recovery disk and click on "reset to factory settings"
will that be like it was when i first got it?

no partitions?  casue if tahts so...thats what i will do..
please>

---

### Post by raymondh on 2009-04-05
> **Skol312000 said:**
> If i use the recovery disk and click on "reset to factory settings"
will that be like it was when i first got it?

no partitions?  casue if tahts so...thats what i will do..
please>

skol,

try something out.  The "old" ubuntu partition which you reformatted to NTSF.  try to delete that same partition again and keep it unallocated.  Then, go to the Vista partition and see if you can extend Vista.  My apologies if I could not be accurate in my previous posts'.  I was on-the-road and posting during a coffee break

Another poster was also right.  you could edit the boot menu in ubuntu to boot Vista ASAP without anyone seeing Ubuntu.  Anyway, you wanted to erase ubuntu.

Good luck

---

### Post by Skol312000 on 2009-04-05
I tried a factory setting restore again and i still have 3 partitions.." Vista/ Recovery/ and the ntfs free space...omg. How do i do this... Why cant i just combine them two and have only "Vista/ Recovery"

---

### Post by egalvan on 2009-04-05
> **Skol312000 said:**
> I tried a factory setting restore again and i still have 3 partitions.." **Vista/ Recovery/ and the ntfs free space..**.omg. How do i do this... Why cant i just combine them two and have only "Vista/ Recovery"

You have  **Microsoft** Vista, **Microsoft** Vista Recovery, and **Microsoft** NTFS partitions.

is Geek Squad still refusing to work on the machine?

Is this a "warrant" issue?

If so, contact the corporate office and have them explain why having **Microsoft** Vista on your machine invalidates the "warranty".

If this is not warranty issue, then do as other posters have suggested...
find another repair shop.

No **reputable** repair shop will refuse to look at **hardware** problems if they can't find Microsoft installed.

I know XP installation allows erasing/deleting of partitions, but I have never used Vista (and **never** will...far too much DRM/restrictions/DMCA junk).

ErnestG

---

### Post by Skol312000 on 2009-04-05
Its ok, i need and want to learn how to take Ubuntu off, i think im gonna et another laptop and have Ubuntu dedicates to it, i do want Vista on this one... I dont know what to do....

---

### Post by the8thstar on 2009-04-05
> **Skol312000 said:**
> I tried a factory setting restore again and i still have 3 partitions.." Vista/ Recovery/ and the ntfs free space...omg. How do i do this... Why cant i just combine them two and have only "Vista/ Recovery"

You CANNOT rejoin the Vista partition and the empty NTFS partition.

However, you can delete the empty NTFS partition with the LiveCD and THEN extend the Vista partition onto the unallocated space left after that.

If you leave your Recovery partition untouched, nothing will happen to it.

---

### Post by raymondh on 2009-04-05
> **the8thstar said:**
> You CANNOT rejoin the Vista partition and the empty NTFS partition.

However, you can delete the empty NTFS partition with the LiveCD and THEN extend the Vista partition onto the unallocated space left after that.

If you leave your Recovery partition untouched, nothing will happen to it.

skol,

8thStar is right.

KEEP THE NTSF PARTITION (the old ubuntu) UNALLOCATED, and then extend the Vista partition.  

My fault when I advised you to reformat.  As I said, it's been a while since I've done this and I was answering your plea for help while  "on-the-go".

Lastly, relax.  You achieved your goal of not having a "foreign" OS in your laptop.  If they ask you, tell them the extra partition is "you were thinking of having your own "media & data" separate from the OS.

---

### Post by Skol312000 on 2009-04-05
Ok, are you guys talking about a Gparted live cd or the Ubuntu live cd, 
My free partition (ntfs) how do i make that unnalocated?

---

### Post by Skol312000 on 2009-04-05
Oh oh!! I got it RAW now... Not ntfs... However "vista is ntfs.


What live cd... Since the partition is now RAW, does it change anything?

---

### Post by the8thstar on 2009-04-05
Well, assuming that RAW = unallocated, and assuming you're currently using the Ubuntu LiveCD, then resize the Vista partition and make it take the whole unallocated space.

---

### Post by Skol312000 on 2009-04-05
Ok sir! Thanks!

I have a Gparted live cd.. So i guess ill just use that instead of the Ubuntu live cd since ubuntu uses Gparted anyways...

That shouldnt  be a problem...right?

---

### Post by raymondh on 2009-04-05
Any disk utility tool will do.  You can use the live CD and run gparted from that.  You can use your own gparted disk.  You can also boot into vista and run the disk management tool.


Now that you have the extra space unallocated/Raw/nada/glitch (whatever anyone decides to call it) ....

...if using Vista, right click on the Vista partition and extend.  Then you're done since you told us yesterday that you can boot into vista with no MBR problem.
...if using gparted (from it's own disk or thru the live CD), you will see the option to resize amongst the tabs above.

---

### Post by Skol312000 on 2009-04-05
thats the big problem

In vists when i right click it wont let me choose extend"  its in gray and i cant control it..
remeber it is not in ntfs format like the normal "Vista partition"

when using Gparted i click resize or extend...and nothing happens...i dont need to make it bigger or smaller...i just want it to be part of Vista..so i can use it in Vista


should i format it in NTFS"
?

---

### Post by Didius Falco on 2009-04-05
> **Skol312000 said:**
> thats the big problem

In vists when i right click it wont let me choose extend"  its in gray and i cant control it..
remeber it is not in ntfs format like the normal "Vista partition"

when using Gparted i click resize or extend...and nothing happens...i dont need to make it bigger or smaller...i just want it to be part of Vista..so i can use it in Vista


should i format it in NTFS"
?

Skol,

If it's now showing the free space as "raw" that means that is an unformatted partition.

If you simply let Vista format it as NTFS, Vista will see it and you'll be able to use it.

It will be assigned it's own Drive letter - for example, Vista itself will be on the C: drive, your CD drive will be D: drive and the new NTFS partition will be the E: drive.

The actual letters of drives other than C: may be different, but a quick look in your File Manager or My Computer will let you see which is which.

There are advantages to using a separate partition. You can use it to store downloads, mp3's, etc. That way, reinstalling Vista down the road won't overwrite those files.

The only possible disadvantage would be if your Vista partition gets full, but with modern hard drives being so large, that problem is more theoretical than anything.

---

### Post by Skol312000 on 2009-04-05
yeah i only let Vista have 80 gb...and i got 203 gb on the empty one so i want it fgor VISTA..

here are screenshots...should i format to NTFS?

i wsant to combine C WITH D..

---

### Post by Didius Falco on 2009-04-05
> **Skol312000 said:**
> yeah i only let Vista have 80 gb...and i got 203 gb on the empty one so i want it fgor VISTA..

here are screenshots...should i format to NTFS?

i want to combine C WITH D..

Okay, if you want to make it all one partition, just delete the D: partition completely. Then resize the C drive to take up all available space.

You should then wind up with just 2 partitions on your PC.

If, after deleting the Raw partition, you are still getting the problem of the resize option being grayed out, first try rebooting and trying again. If that doesn't work, check the links I posted last night for using the Vista partitioner from the command line from inside Vista.

On Edit: Thanks for the screenshot . That makes it a lot easier for the rest of us to see exactly what is going on.

You have a logical partition inside an extended partition. In order to successfully  make the C: drive take up all available space, you first have to delete the logical drive, then delete the Extended partition.

After you've done that, where the D: drive is now should show as free or unallocated space.

I suspect this is why you ran into the "grayed out" problem before.

---

### Post by Old_Grey_Wolf on 2009-04-05
I would have taken a different approach when dealing with Geek Squad. I would have edited "menu.lst" and set timeout to 0, uncommented hiddenmenu, and changed the default boot order to be the Microsoft Windows OS. I would then back up my /home just in case they messed things up. I doubt they would ever know that another OS was installed. However, I probably wouldn't use Geek Squad in the first place.

But it is too late for that now. :(

---

### Post by Skol312000 on 2009-04-05
> **Didius Falco said:**
> Okay, if you want to make it all one partition, just delete the D: partition completely. Then resize the C drive to take up all available space.

You should then wind up with just 2 partitions on your PC.

If, after deleting the Raw partition, you are still getting the problem of the resize option being grayed out, first try rebooting and trying again. If that doesn't work, check the links I posted last night for using the Vista partitioner from the command line from inside Vista.

On Edit: Thanks for the screenshot . That makes it a lot easier for the rest of us to see exactly what is going on.

You have a logical partition inside an extended partition. In order to successfully  make the C: drive take up all available space, you first have to delete the logical drive, then delete the Extended partition.

After you've done that, where the D: drive is now should show as free or unallocated space.

I suspect this is why you ran into the "grayed out" problem before.


ok i deleted the 
'D" and it now says "Free Space"
BUT (omg) the "extend volume" is still grayed out..


so i should try the Command line stuff?

---

### Post by Didius Falco on 2009-04-05
post another screenshot, please. It really helps in knowing what is going on.

---

### Post by Skol312000 on 2009-04-05
> **Didius Falco said:**
> post another screenshot, please. It really helps in knowing what is going on.



here you go...

---

### Post by Didius Falco on 2009-04-05
Okay Skol,

Now, if you look at your screen (or the screenshot) you'll notice that there is a darker green box around the light green area that says "free space".

Look down at the bottom of the screen and you'll see that the free space is inside an extended partition.

You have to delete that extended partition. After you do, that whole block of space will be black and will say "unallocated space".  That's when you'll be able to expand the C: drive to reclaim all that space.

After you have  deleted the Extended partition, you should no longer run into the "grayed out" problem. The reason it was grayed out was because all that free space was inside an extended partition, and there was no where for the C: partition to expand to.

---

### Post by -kg- on 2009-04-05
What it looks like to me is that you still have an Extended partition surrounding the free space.  Look at the bottom for the color code legend.  The green that you see surrounding the free space is an Extended partition.

I'm going to give you step-by-step:

[LIST=1]
Boot on to your GPartEd Live CD.
Once there, you will see [something like this]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition") (Scroll down to the second screenshot).

2. See the line on the list below the graphics that says, "Extended" under the "Filesystem" column?  If you have one of those, delete it.

3. Boot back into Vista, and you should then be able to extend your Vista partition into the (actual) free space.[/LIST]

Hope this helps.

<edit>  The reason I told him to boot to the GPartEd Live CD is that I saw no way to delete the Extended partition from Vista.  It doesn't even have the Extended partition listed in the partition lines above the graphics.  Anyway, the same thing needs to be accomplished.

---

### Post by presence1960 on 2009-04-05
> **Skol312000 said:**
> Its ok, i need and want to learn how to take Ubuntu off, i think im gonna et another laptop and have Ubuntu dedicates to it, i do want Vista on this one... I dont know what to do....

Skol, do you hear what you are saying? I quoted it for you to see. **_You do have Vista, You have C Drive with Vista OS, you have a Vista recovery partition (E Drive) and a NTFS partitition. NTFS is Windows not Ubuntu!_** There is no Ubuntu left, period. BTW I suggested earlier to delete the partition as did others.

FYI when you use the recovery CD it will only recover your C partition- that is why the third partition remains. It is a Windows partition so bring it to geek Squad against mine and other forum members opinion and get done to it what needs to be done. You haven't even gotten it there yet and already your mind is running miles ahead of where you are. Take it one step at a time. You want no trace of Ubuntu? you have that. All your partitions are Windows, so bring the lappy to them. If they ask why there is a 3rd partition tell them you created it to store videos and music. You really are making something out of nothing. Before you say or think anything else why don't you drop it off and see what they say?

P.S. I think you really could benefit from a LUG (Linux Users Group) group. There is probably one in your area. A little face to face help will bridge the gap. Somewhere along the line the translation of what people post gets lost. That is not meant as a put down, but as a suggestion to help you catch on to Linux. I have watched you struggle tremendously on here. I even went back and read your other threads and posts, which confirms what I see. Getting that extra help will definitely be a plus for you.

Above all else take a deep breath and relax! Go to geek Squad then come back to the community.

Edit: I responded to an earlier post, but now I see you have a logical partition with free space. That's OK, take it to geek Squad it is not evidence of Ubuntu. Your HDD is totally Windows with some free space.

---

### Post by night_fox on 2009-04-05
NNNNNOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO



](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

You should have backed up everything important, made the partition hidden, and followed OldGrayWolf's advice. That way, they would never find out that you had linux, because if they insist on having only windows, then they probably aren't geeky enough to know. Then, even if they use a live cd, they would be unlikely to find anything.

---

### Post by presence1960 on 2009-04-05
Skol, out of curiosity, why are you bringing it to Geek Squad anyway?

---

### Post by -kg- on 2009-04-05
> **night_fox said:**
> 

You should have backed up everything important, made the partition hidden, and followed OldGrayWolf's advice. That way, they would never find out that you had linux, because if they insist on having only windows, then they probably aren't geeky enough to know. Then, even if they use a live cd, they would be unlikely to find anything.

And like *I* said before, I bought the Ubuntu Live CD from Best Buy (which is the Geek Squad).  If they didn't approve of Ubuntu Linux being on your laptop, then why do they sell the Live CD?

However, a good exercise in Partitioning.  Please do read the information on the Community "How To Partition" page.  I basically (re)wrote it.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by presence1960 on 2009-04-05
> **-kg- said:**
> And like *I* said before, I bought the Ubuntu Live CD from Best Buy (which is the Geek Squad).  If they didn't approve of Ubuntu Linux being on your laptop, then why do they sell the Live CD?

However, a good exercise in Partitioning.  Please do read the information on the Community "How To Partition" page.  I basically (re)wrote it.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I hear you! After going back and reading Skol's threads and posts there is definitely a problem with communication and/or comprehension. This is not a knock on him/her, just an observation based on Skol's interaction with the community. Skol is definitely welcome here, but may need some "extra credit" such as like what they do in school. That's why I suggested Skol look for a LUG group in his area. Maybe some face to face help would be beneficial in getting him up to speed on some basic concepts.

Nevertheless Skol stay with the community no matter what you choose to do.

---

### Post by -kg- on 2009-04-05
> Nevertheless Skol stay with the community no matter what you choose to do.

Absolutely!  Everyone is a valued member here, and we'll always be doing our best to get you through whatever issues you face.

):P

---

### Post by Skol312000 on 2009-04-05
> **presence1960 said:**
> Skol, out of curiosity, why are you bringing it to Geek Squad anyway?

Laptop i bought comes with 4 months free if i go to Geek Squad, so that is it....





THANK YOU ALL FOR THE AWESOME HELP AS EVRYTHING YOU GUYS HAVE TOLD ME WORKED, IM sorry that i have caused any of you annoyance it bother me a lot (this issue of not being able to combine partitions) evrything is awesome now and i greatly appreciate your time and help though all of this.

here in couple of days i will install ubuntu ,casue i already miss it

---

### Post by Skol312000 on 2009-04-05
> **presence1960 said:**
> I hear you! After going back and reading Skol's threads and posts there is definitely a problem with communication and/or comprehension. This is not a knock on him/her, just an observation based on Skol's interaction with the community. Skol is definitely welcome here, but may need some "extra credit" such as like what they do in school. That's why I suggested Skol look for a LUG group in his area. Maybe some face to face help would be beneficial in getting him up to speed on some basic concepts.

Nevertheless Skol stay with the community no matter what you choose to do.

i always willl, this is by far the best community for support i ever experience...and its free which is insane that it offers such awesome "service"

im sorry im not too tech savvy to understand most of the things..and i love Ubuntu and minds that think Ubuntu

---

### Post by billgoldberg on 2009-04-05
> **Skol312000 said:**
> i need to remove it...

i cant have anything but Vista..

so i need to know how to remove it..

if anyone can help i would appreciate it

Seriously dude, screw those guys.

Let someone fix it.

---

### Post by billgoldberg on 2009-04-05
> **-kg- said:**
> Absolutely!  Everyone is a valued member here

If everyone is a valued member, nobody is.

---

### Post by Didius Falco on 2009-04-05
I'm just glad it all worked out the way you wanted it to work out.

---

### Post by presence1960 on 2009-04-05
> **Skol312000 said:**
> i always willl, this is by far the best community for support i ever experience...and its free which is insane that it offers such awesome "service"

im sorry im not too tech savvy to understand most of the things..and i love Ubuntu and minds that think Ubuntu

Well Skol good luck with geek Squad. See you back here soon :popcorn:

---

### Post by rhcm123 on 2009-04-05
> **asmoore82 said:**
> [COLOR="Blue"]Microsoft.com: How to Remove Linux - [http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)[/COLOR]

:KS

hahahaHAHAHAHAHAHAHA
most un-read article they have

---

### Post by Skol312000 on 2009-04-05
> **Didius Falco said:**
> I'm just glad it all worked out the way you wanted it to work out.
Thanks man, ytouve been great help!


> **presence1960 said:**
> Well Skol good luck with geek Squad. See you back here soon :popcorn:

ASAP ofcourse... i already had to use "CTRL-ALT-Delete" at least 4 times

---

### Post by raymondh on 2009-04-05
Glad you got it worked out skol.

Come back anytime.

Raymodn

---

### Post by Skol312000 on 2009-04-06
im not going anywhere..

i just got my laptop back, and i decided not to return Ubuntu on this one and keep ubuntu only on my older computer..

not a neglect at all..
its just that i like to dedica one OS per system...

does this site also have some Windows section/>?

---

### Post by albinootje on 2009-04-06
> **Skol312000 said:**
>  i just need Ubuntu and the grub thing loader gone...i wanna keep all my info and not touch Vista if possible

I suggest to "fix" your MBR [MS-Windows software for that was mentioned on this forum several times, I forgot the kind-of-silly name it had) so that it only load MS-Vista, that should be enough.

Or do you really think that the tech people are gonna complain that 
there was an unknown partition on your disk ?

---

### Post by raymondh on 2009-04-06
> **Skol312000 said:**
> im not going anywhere..

i just got my laptop back, and i decided not to return Ubuntu on this one and keep ubuntu only on my older computer..

not a neglect at all..
its just that i like to dedica one OS per system...

does this site also have some Windows section/>?

Skol,

Have you tried Virtualization? I'm a newbie to linux (< 3 mos.) Virtual Box allows me to virtualize win XP on my linux/ubuntu computer.  For my Mac, I use VMWare fusion.  There's a little learning curve but nothing you cannot handle.  The benefit?  Think of it as a whole OS (windows, in this case) inside your linux.  And if you don't like it, just delete it without harming your linux install.

Nevertheless, welcome back.

---

### Post by lhb1142 on 2009-04-07
> **Skol312000 said:**
> im not going anywhere..

i just got my laptop back, and i decided not to return Ubuntu on this one and keep ubuntu only on my older computer..

not a neglect at all..
its just that i like to dedica one OS per system...

does this site also have some Windows section/>?

:KS I just came across this thread and I wish I had seen it earlier.

You want to get the computer back to "exactly the way it came when you bought it?"

That's simple! FIRST, back up everything of importance - documents, photos, music, etc. to an external hard drive.

Then download and burn to disc DBAN - Darik's Boot and Nuke. (The download is an iso file which will burn to disc directly.) (To find DBAN, just Google it.)

Set your computer (in the BIOS) to boot from CD first. Insert DBAN disk in CD tray, then reboot.

The entire hard drive will be "wiped" of everything. The process will take a few hours.

Then, using your Windows discs, reinstall Windows. When the installation is finished, your computer will be in "pristine" Windows Vista shape, configured exactly as it was when it came from the factory.

Then the idiots at the Geek Squad should have only minimal trouble fixing whatever is wrong with it, assuming they know what a computer is! ):P

---

### Post by bubwitmaingay on 2009-04-07
Why MS Windows only? Can't computer technicians repair computer using GNU/Linux? In short, they don't fix Macs too? Oh what a bother! Hehehe.

Anyway here's three situations you might be under:

1. **Installed Ubuntu, wiping-out the original MS Windows**. In this situation, you just need to get a MS Windows Installer, say XP or Vista perhaps and run it, partitioning and erasing everything on your HDD during Windows installation.

2. **Dual-boot, installing Ubuntu within MS Windows**. Just uninstall Ubuntu like it was another software in your device.

3. **You are in situation #1 and can't install Windows because it is too expensive**. My advice, look for a capable computer technician that is not hypnotized by MS Windows and is enlightened by GNU/Linux.

8)

---

### Post by Didius Falco on 2009-04-07
> **lhb1142 said:**
> :KS I just came across this thread and I wish I had seen it earlier.

You want to get the computer back to "exactly the way it came when you bought it?"

That's simple! FIRST, back up everything of importance - documents, photos, music, etc. to an external hard drive.

Then download and burn to disc DBAN - Darik's Boot and Nuke. (The download is an iso file which will burn to disc directly.) (To find DBAN, just Google it.)

Set your computer (in the BIOS) to boot from CD first. Insert DBAN disk in CD tray, then reboot.

The entire hard drive will be "wiped" of everything. The process will take a few hours.

Then, using your Windows discs, reinstall Windows. When the installation is finished, your computer will be in "pristine" Windows Vista shape, configured exactly as it was when it came from the factory.

Then the idiots at the Geek Squad should have only minimal trouble fixing whatever is wrong with it, assuming they know what a computer is! 

If you look at at the screenshot attached to post #55, you'll see that your advice would have resulted in Skol nuking his recovery partition, which would have left him with a machine with no O/S and no way to reinstall it.

That's not exactly the outcome Skol was looking for...

---

### Post by thismango on 2009-04-07
Hello all, have read all this with interest.
I'm in a similar situation but with XP. I just can't get Linux to install correctly, even with help from friends, reading posts on this site, etc etc. So reluctantly going back to Windows XP. 

My sister's boyfriend is apparently a Linux expert so I will ask him to install it for me when I next am in their town, but for now I want my drive space back.

Computer is hand-me-down from friend so no original disk and don't want to lose setup.

I have deleted the Linux partitions from within XP but can't get it to extend the original Windows partition. Have tried following command line instructions in Help but it won't do it. Any advice?

---

### Post by presence1960 on 2009-04-07
> **thismango said:**
> Hello all, have read all this with interest.
I'm in a similar situation but with XP. I just can't get Linux to install correctly, even with help from friends, reading posts on this site, etc etc. So reluctantly going back to Windows XP. 

My sister's boyfriend is apparently a Linux expert so I will ask him to install it for me when I next am in their town, but for now I want my drive space back.

Computer is hand-me-down from friend so no original disk and don't want to lose setup.

I have deleted the Linux partitions from within XP but can't get it to extend the original Windows partition. Have tried following command line instructions in Help but it won't do it. Any advice?

use computer mgmt disk manager and format that separate partition as NTFS. Use it as storage for now. Then when you go to your sister's backup or move all data on that partition. This way you already have a partition set aside for Ubuntu. Which will save the install man some work on defragging windows so he can shrink the windows partition to create a partition for Ubuntu. If you do it this way all that work (defrag and shrink Windows partition) is unnecessary. Plus this will get you away from the windows mentality of the OS wants all space in one big partition.

---

### Post by Skol312000 on 2009-04-07
> **Didius Falco said:**
> If you look at at the screenshot attached to post #55, you'll see that your advice would have resulted in Skol nuking his recovery partition, which would have left him with a machine with no O/S and no way to reinstall it.

That's not exactly the outcome Skol was looking for...



thank you, and thank you to the guy that posted that for being late with the post

lol

---

### Post by raymondh on 2009-04-08
> **thismango said:**
> Hello all, have read all this with interest.
I'm in a similar situation but with XP. I just can't get Linux to install correctly, even with help from friends, reading posts on this site, etc etc. So reluctantly going back to Windows XP. 

My sister's boyfriend is apparently a Linux expert so I will ask him to install it for me when I next am in their town, but for now I want my drive space back.

Computer is hand-me-down from friend so no original disk and don't want to lose setup.

I have deleted the Linux partitions from within XP but can't get it to extend the original Windows partition. Have tried following command line instructions in Help but it won't do it. Any advice?


Did you install ubuntu thru wubi?  I ask because of your comment "I have deleted the linux partitions FROM WITHIN xp".

Can you use a live CD > system > adminitration > partition editor (gparted) and post a screenshot of what your disk has/looks like?  

Let's go from there and, of course, your original intention .... install or delete ubuntu?

Thanks.

---

### Post by AFarris01 on 2009-04-08
I wish i'da seen this earlier too...

you don't have to delete ubuntu from your computer for freak squad to fix it... My laptop needed servicing, i dual boot XP and ubuntu on it...took it in, they fixed it no questions asked.

at the very least if it was THAT big of a deal (which its not, really) you could've just told GRUB to default to boot Vista, hide the menu, and use no delay.  then when you got the thing back put it back like you wanted.

That would've been a LOT*easier than wiping ubuntu completely, and going through that whole mess of re-adding the space to the vista partition.

besides, they dont CARE what you're partitions look like, or even how they're formatted... a friend of mine took his computer up there and they reformatted a 100GB NTFS partition into 2 50GB fat32 partitions...for no good reason!  the guy didn't even REALIZE what they did (other than complaining about it slowing down a bunch) until i looked at it myself and found it.

Hell, I wouldve been happy to fix the computer for you! in fact, PM me and let me know if you'd be interested in this in the future, and we'll keep in touch! :)

Best of luck anyway...

---

### Post by Skol312000 on 2009-04-17
well...hello again guys...

i finally got Ubuntu back up and runnig...but i dont see any use for it really....i love the no crashing and stuff but i still go back to Windows...do any of you  feeel this way?

---

### Post by raymondh on 2009-04-18
> **Skol312000 said:**
> well...hello again guys...

i finally got Ubuntu back up and runnig...but i dont see any use for it really....i love the no crashing and stuff but i still go back to Windows...do any of you  feeel this way?

No .... I don't feel that way. 

Why do I have linux .... because it provides the same productivity as my mac; I can make it "as pretty" as my mac; It is as reliable as my mac; And more importantly ... I am in control.

YMMV

---

### Post by rhcm123 on 2009-04-18
> **raymondhenson said:**
> No .... I don't feel that way. 

Why do I have linux .... because it provides the same productivity as my mac; I can make it "as pretty" as my mac; It is as reliable as my mac; And more importantly ... I am in control.

YMMV

Macs? Reliable? I have a vendetta against macs, mostly because of their basic idea. I like my computers to have raw power, not sex appeal - sure it may look good, but if youve got outdated graphics and a crap processor, do you really want to drop another 5000~$ for a new one?

/rant
My main problem with them is the fact that i can't rip the guts out and slam in new parts i bought online, from buckets of manufacturers and in all shapes and sizes. hardware is my main problem with macs. If they supported a 4 hard drive in a RAID 0 array running samba and cups (cups was actually coded by apple) for under 500$ then we'll talk. :shock:

The operating system, nevertheless pleasing to the eye, I have always found is very unstable when demanding programs are running - my friend crashes firefox every hour or so. The OS itself never crashes though, just the programs - which never happens here on ubuntu :). I've found it too unstable for my tastes.

My final complaint is price. I can get a good, powerful, upgradeable laptop for around $1000. The minimum price for the lowest-grade mac is 1200$ - which is outrageous. The box price of the OS is only about $100.

---

### Post by Skol312000 on 2009-04-18
anyone here like Vista?

or use it aside with Ubuntu

---

### Post by presence1960 on 2009-04-18
> **Skol312000 said:**
> well...hello again guys...

i finally got Ubuntu back up and runnig...but i dont see any use for it really....i love the no crashing and stuff but i still go back to Windows...do any of you  feeel this way?

Skol, you know you have the freedom to choose. I love Linux, but frankly Linux is not for everyone. If you see no use for Ubuntu just don't use it! You don't owe this community anything or any explanations. There is no shame in using Windows or Mac for that matter. Why would you spend time on something you see no use for?

I would like to see people use Linux, but it has to be their choice and they really have to want to do it. We'll be here if you ever become "convinced" of the need for Linux in your computing.

P.S. NO! I don't feel that way. I only use windows for 2 things, both work related: 1. MS Office because my employer made it quite clear no Open Office and 2. Adobe Acrobat Professional. They are all I have on my Windows partition besides Firefox. No need for anything else since I don't game. Linux does everything I need to do.

---

### Post by presence1960 on 2009-04-18
> **Skol312000 said:**
> anyone here like Vista?

or use it aside with Ubuntu

I have a legit Vista DVD, but after using it I dumped it and put XP back as my windows on my dual boot setup. IMO Vista is junk. Not trying to get flamed by Vista users just answering Skol's question. My word is not law, just my opinion. :D

---

### Post by Didius Falco on 2009-04-18
Skol,

The O/S is just a tool you use to do things. All operating systems have advantages and disadvantages, and the wise user understands what they are and chooses accordingly. Sometimes this means doing everything under one O/S. For others, they may use two or more operating systems, or variations on operating systems.

Personally, I really enjoy digging around in the guts of an O/S and learning about it, so I get a great deal of pleasure out of the learning experience itself.

My wife, on the other hand, wants it to start up and work, and she doesn't want to know anything about how or why it works. She is the ultimate Black Box User. I take care of all the maintenance/updating of her PC, and so long as the Sims 2 works, and she can access the internet (usually to get more stuff for the Sims 2 <G>), she is a happy camper.

If Vista allows you to do what you want to do, and you are happy with it, use it in good health.

---

### Post by me.translucent on 2009-04-19
what you need is a supergrub disk .that can fix the grub!

---

### Post by hesjnet on 2009-04-19
> **asmoore82 said:**
> [COLOR="Blue"]Microsoft.com: How to Remove Linux - [http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)[/COLOR]

:KS
haha hilarious! 

Simpler solution:

1. Insert and boot from Windows install cd.

2. Choose format drive and install

3. Prepare to get alot more frustrated from now on

---

### Post by presence1960 on 2009-04-19
> **hesjnet said:**
> haha hilarious! 

Simpler solution:

1. Insert and boot from Windows install cd.

2. Choose format drive and install

3. Prepare to get alot more frustrated from now on

That link is funny! :D

---

