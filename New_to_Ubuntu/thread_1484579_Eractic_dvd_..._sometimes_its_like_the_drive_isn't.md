---
title: "Eractic dvd ... sometimes its like the drive isn't there"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-15
*** If a search for DVD playback problems or no DVD playback brought you here ... there's lots of red herrings as I worked through lots of different things with much help that seemed to pop up - what I thought worked is in the 17th post ***

I sooooooooooooo wish I'd spelled "erratic" right in the title

Muddling though an upgrade to 10.04 from 8.04

After upgrade had the "flashplugin-nonfree" problem but resolved it ...


System seemed perfect ... til I went to bed ...

In the morning my system didn't respect me though

It was like the DVD drive wasn't even there ... no recognition of the drive no icon on the desktop for the DVD ... couldn't play CD's  

Found this advice:

sudo /usr/share/doc/libdvdread4/install-css.sh

rebooted

it worked for a few minutes


then I was back where I stared

tried again same thing

How can I permanently fix this?


Any advice would be muchly appreciated :)

By the way ... I popped a Live CD for 9.10 in the drive and restarted the system and it worked just fine ... so the drive does work.

** seemingly unrelated problem .. I lost access to these forums after the dvd cutout ... told me the URL was invalid ... can't see how that would be related but ... it did happen at the same time sooooo ... ummm ...

---

### Post by anothernewuser on 2010-05-15
Hmmmm ... launched Empathy ... video crashed ...

Now VLC has just ... stopped .... It's still showing up on the quick menu bar at the top though ... despite the fact i closed it


Does Empathy not play nice with other children?

Now the VLC icon is gone ... took several minutes

If i try to right-click and launch the DVD with VLC nothing happens ... well not nothing ... VLC appears on the screen but doesn't start the movie ....

If I try to open the disc ... get this info:


Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.


And now that I think about it Empathy was open every time it crashed ...

Weird and wonderful.  Going back to Pidgin I suppose if there's no fix about.

Well ... if there's a connection ... it ain't specifically Empathy ... video crashed with Pidgin running as well ... sigh ....

And now the video crashed with neither Empathy nor Pidgin running so scratch that connection I guess.

*** This was entirely a red herring except that it appears that doing anything else made a crash slightly more likely ***



Still looking for that one big score though ... no one but me seems to be reading but I'll keep making notes as I go along.

** seemingly unrelated error number 2 - my system clock has reset to the wrong time


Restart seems to fix up the video issues ... a bit ... after restart  - regardless of what commands I enter or don't - I have what appears to be a fully functional DVD player but any number of things makes it crash and then I'm back to a system that seems to have no DVD player.

Latest thing to crash the video ... printing a document from gedit ... now the printer doesn't work either ... sigh ... under Printer Properties and then Printer State it says: Stopped - Filter "usr/lib/cups/filter/rastertogutenprint.5.0" for printer "Stylus_C3900" not available: No such file or directory ...
Since this is the first thing I've tried to print after upgrade not sure if this issue has been here since the upgrade or not.

I think I installed a new printer driver and this seems fixed - for now (insert ominous music here).

Note to me :) ... after the video crashes ... I can still listen to Internet radio stations  but its really choppy and jumpy ... a restart fixes this problem.

---

### Post by anothernewuser on 2010-05-17
Sooooooooooo ... where am I today some 20 hours after I last gave up on this you may or may not ask?

Well ... here's the deal:

When the system starts up it *seems* to be perfectly functional however attempts to play a DVD with VLC start out fine then after some apparently random number of minutes the DVD playback just stops .

Further attempts to play the same DVD with VLC give the error info:

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

Movie Player gives the message: 
An error occurred

Could not open location; you might not have permission to open the file.


Until VLC crashes all media *seems* to play well ... youtube videos ... internet radio ... the dvd drive functions.

After crash well - youtube videos still play though perhaps they are a bit choppy .. who knows really lots going on.

Perhaps on next restart I will see if a CD causes crashes.  Or if some other player crashes running DVDs.

Maybe I'll change to another DVD as well. Hmmm



I have Ubuntu-restricted-extras installed ... I have followed these instructions from Medibuntu:

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh


And:
--2010-05-17 14:18:07--  [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8068 (7.9K) [text/plain]
Saving to: `/tmp/dvdcss-FAgk1S/Packages'

100%[======================================>] 8,068       10.8K/s   in 0.7s    

2010-05-17 14:18:09 (10.8 KB/s) - `/tmp/dvdcss-FAgk1S/Packages' saved [8068/8068]

--2010-05-17 14:18:09--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-FAgk1S/libdvdcss.deb'

100%[======================================>] 38,036      30.7K/s   in 1.2s    

2010-05-17 14:18:11 (30.7 KB/s) - `/tmp/dvdcss-FAgk1S/libdvdcss.deb' saved [38036/38036]

(Reading database ... 186070 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-FAgk1S/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


To me that looks ok ... but I'm really new at this - it's not screaming out at me to fix something.  I do see that it's replacing a program with itself there at the end but it was different the first time ... I just ran it again to have the output here ... 

I even chucked in a bonus command:

sudo chmod 660 /dev/sr0; chgrp cdrom /dev/sr0

Though I'm not sure why ... just seemed like it was sort of suggested to try it.
To be fair it came with the qualifier "(replace with the path to your dvd drive)" .... did I? Ummmm .... Didn't I? Ummm .. did I have to? Ummmm ...
Anyway that's the command as I ran it.



Sooooooooooo where am I ... I have a system that crashes and goes a bit wonky when I play DVDs ... perhaps that's why I have a DVD player near the TV.

Could it just be this DVD I wonder ... hmmmm ... Would Kermit the Frog really do that to me?

I'll keep happily plugging along trying to work this out somehow ...  no more posts today I suppose unless I get more suggestions though I will make notes here as I notice or try more :)

Enjoy.


Geez I wish I'd spelled "erratic" right in the thread title - a couple days looking at that hasn't been good for me. Though it does make this thread exceptionally easy to search for.

---

### Post by Mr. Hibba on 2010-05-17
Hmm, this is a strange issue... 

Do you happen to have any data DVDs (perhaps a computer game install DVD) that you could use to test it? 

On a side note, by the sounds of it, sometimes the DVD doesn't show up on the desktop. With the DVD in the drive, what do you get when you type "sudo mount /dev/sr0" without quotes into the terminal? Does it put the DVD icon on the desktop and/or in the Systems menu? 

Mr. Hibba.

---

### Post by anothernewuser on 2010-05-17
Oh thank you thank you for joining me :)

sudo mount /dev/sr0

yields  this:

[mntent]: warning: no final newline at the end of /etc/fstab
mount: no medium found on /dev/sr0


This is after a DVD crash btw ... I can reboot and see what it says then.


Ummm ... data DVDs ... ummm ... I have some old photos on CD let me dig one out ... and see what happens ...






I really am a new user to Ubuntu soooo I dont have any DVD's with data lying about .... I think


Well having swapped in the photo CD and switched to GIMP to play with the photos .... the system tells me a "DVD_Video" is still in the drive and won't access the Photo CD at all.


Let me reboot and see what happens :)


Okie dokie ... after reboot system is correctly telling me there's a data CD in there aaaaaaaaaaaaand I'm discovering I don't know how to use GIMP to access photos on a CD ... working on that one .... ahhh the Photo CD is just gone 




sudo mount /dev/sr0

yields the same output as above



Ok ... have rebooted again as the Photo CD disappeared from the system entirely ... like it didn't exist ... actually more like the drive didnt exist ...

Immediately after reboot:

sudo mount /dev/sr0

Yields: 

[mntent]: warning: no final newline at the end of /etc/fstab
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0



And at the moment GIMP and F-spot are loading images just fine off the CD.


Ummm that last line up there looks like it might be helpful to someone who understands this stuff .... I'm guessing having the drive already mounted is a bad thing.


Hmmm changing to another DVD (bye Kermit) brought up the autostart menu for the first time ever ....

---

### Post by Peter09 on 2010-05-17
Hi
 
> [mntent]: warning: no final newline at the end of /etc/fstab

this line looks like its a mis configuration in fstab.
 
You can edit fstab by this command
 
```
sudo gedit /etc/fstab
```
 
 
 
make sure that the last line in the file is completed with a return. Just move the cursor to the end of the last line and hit return.
Dont do anything else - then save it.
 
It may be worth showing us the contents of this file as it appears that there may be a problem. Have you edited it before?

---

### Post by anothernewuser on 2010-05-17
Ummm ... ok I did that ... and it's removed that particular warning ...

So now:

sudo mount /dev/sr0

Yields :

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0


And to the best of my knowledge I've never edited that ... I certainly haven't edited any files sinces the upgrade ... some sort of mess leftover as a result of the upgrade maybe?



The contents of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=c52d5cd3-58bd-4f8e-a61b-80b01ea2336e / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=E43002173001F17A /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=9a3d2844-0b51-4681-97d4-0fb946d24cf2 /media/sda3 ext3 defaults 0 2
# /dev/sda4 -- converted during upgrade to edgy
UUID=8a5d9acc-94ba-4506-9170-a5ebc783f3d1 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0



References to edgy in there have me mystified ... never used it ... ever.


Hmmmm ... this was an upgrade from 6.06 to 8.04 (only a month or so ago) to 10.04 (only a couple of days ago) ... perhaps I begin to understand why people call for clean installs.  Of course with a questionably functional DVD drive ..not sure it would be all that easy to do a clean install.

---

### Post by Peter09 on 2010-05-17
You do not need to issue the mount command because your CDROM is being mounted automatically with this line in fstab
 
> UUID=8a5d9acc-94ba-4506-9170-a5ebc783f3d1 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

 
If you look in /media/cdrom0 you should see the contents of your CDROM.

---

### Post by anothernewuser on 2010-05-17
I appreciate your help Peter ... I'm glad someone knows what all this means :)

But ...Ummm ... is that good?


Seriously, this is a bit over my head at the moment ... I'm not sure what you just said ... 


Do I have to undo that command somehow? Have I done some sort of fixable damage to the system using this command?

Will it be taken care of on reboot?

And yes the contents of the disk are right where you said they would be.

And assuming I go back to where I was when all this started ... does that leave me with a semi-functional DVD drive again?

By the way ... the system just successfully played an entire DVD with me trying to launch every other application I could ... sooo ... could it be that the first DVD was somehow incompatible with my system?  Could that cause VLC to crash partway through playing it and make the drive just disappear somehow?

Or has this simple edit fixed all?


Oh my ... questions are overwhelming me at the moment.



Honestly, I appreciate the help being offered here... it doesn't take much to see that y'all are clearly much more comfortable with this stuff than I am.

---

### Post by Peter09 on 2010-05-17
You have done no damage - if your system is now working OK then thats it.
 
You could try a reboot and see if things still work.

---

### Post by anothernewuser on 2010-05-17
OK ... rebooted and I've popped the previously offending DVD back in here to see if it crashes out again .. will let you know if it plays through to end or if the issue is still there ...

If it is I may be tempted to pretend I don't own this particular DVD.

Could a simple file edit have fixed this really?

hmmmmm


Will let you know ...


That was quick ... Kermit killed VLC again ... just like always?

Can one DVD really kill off part of the system like that?

Weird.

---

### Post by Peter09 on 2010-05-17
This is most probably the bug.
 
[http://bugs.archlinux.org/task/18431](http://bugs.archlinux.org/task/18431)

---

### Post by anothernewuser on 2010-05-17
Sooooo ... if I'm reading this right ....


It's an error in libdvdnav which causes some DVD's to act all floopy (that's an official term I believe) and some people have fixed it by switching from what was their current version to libdvdnav 4.1.3-2 ....


Can I do that? And would it be an update or a rollback for me?  Looks like a rollback since synaptic is telling me I'm on libdvdnav 4.1.3-6


Would it be wise to roll back what looks to be 4 versions?  Hmmm .. wait for a fix and deepsix kermit in the meantime maybe ....


and by the way ....

*** seemingly unrelated error number 3 .. when launched synaptic gives me this message:
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_lucid-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_lucid-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-security/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_lucid-security_restricted_binary-i386_Packages)

---

### Post by Peter09 on 2010-05-17
Unless your desparate I would just wait for the fix to come through.
 
To get rid of your duplicates,
 
System->Admin->Software Sources
 
Untick the duplicates.

---

### Post by anothernewuser on 2010-05-17
Geez I must sound like I don't know much ....


Alrighty ... I'll sit and wait on the fix and bury offending DVDs under a pile of "important papers"

As far as the duplicates go ... I don't actually see them listed ...


Under "Other Software"

I see 5 listings only 1 of which is ticked ....

3 of the others are marked "disabled on upgrade to lucid"

and the 4th probably should be as it clearly refers to hardy ... but since it's unticked ... ummm ...

I reckon I might be free to just delete those listings anyway.


disabled on upgrade to lucid ([http://packages.medibuntu.org/lucid](http://packages.medibuntu.org/lucid) free non-free)
disabled on upgrade to lucid ([http://packages.medibuntu.org/lucid](http://packages.medibuntu.org/lucid) free non-free) (Source Code)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
Medibuntu - Ubuntu 8.04 LTS "hardy heron" disabled on upgrade to lucid ([http://packages.medibuntu.org/lucid](http://packages.medibuntu.org/lucid) free non-free)
Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron" ([http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy) free non-free)(Source Code)

only the canonical one is ticked.

**** This problem with duplicate lists was cleared up by running sudo apt-get update which was suggested in terminal after I re-added the medibuntu repositories *****




Note to me: the DVD that mucks up my system is identified only as "DVD-VIDEO" whereas all others I try are clearly identified by name. ***This was a red herring ... thats just the way this particular DVD is I think ****


And ... Peter...

If I haven't clearly said it already ... thank you so much for the time and effort you've shown me today ... I do appreciate it ... :)

Hmmm ... wish I could mark a thread as [Resolved As Much As Can Be For Now]

---

### Post by anothernewuser on 2010-05-17
Another day ... another return to this problem ... sigh


Ummm ... I was decided to not play Kermit's Swamp Years ever again .... no real issues there ... but ... Star Trek does exactly the same thing...

There's only 2 things I can see they have in common that seems to be different from the DVDs that have yet to crash my system:

They have warnings that they are dual layered and that they have copy protection.   Surely dual layered discs wouldn't lead to this would they?

Having said that I'll now pop in another copy protected DVD to see ... well ... if it makes my system think there's no dvd player attached ....

of course I'll need to reboot cause ... at the moment the system seems to believe there's no dvd drive attached

sigh

Back to posting info here as I accumulate it ...


Gladiator just crashed the player as well ... aaaaaaaaaaannnd it seems to have copy protection ... Is that my demon?

wonder if I have any that dont have copy protection


Seems I have more DVDs that do cause crashes than don't.


So far I've established that I have 1 DVD that doesnt crash the player ...

Perhaps I just got lucky with it ... but I'll try it again.


I had other issues playing DVDs a week ago when I was using 8.04   but nothing like this.


** seemingly unrelated error number 4 ... noscript wont install an update
Firefox could not install the file at 

[http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-1.9.9.77-fx+sm+fn.xpi](http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-1.9.9.77-fx+sm+fn.xpi)

because: Download error
-228


Throw Casino Royale on the pile of DVDs that I can't play ...
though I;m studying the DVD and case and see no sign of copy protection ... perhaps its just assumed on Sony discs?

For those keeping score:

DVDs I can play:   The Princess Bride

DVDs I can't play:  Kermit's Swamp Years, Star Trek, Gladiator, Casino Royale

Spose I'll pop the 1 that works back in there and see if it still does.

and after a promising start ... it doesnt work anymore either ... sigh

*** In the end it really seems to have had no impact what kind of DVD I put in ***

---

### Post by anothernewuser on 2010-05-17
Well the offending Kermit DVD is playing right now without any apparent trouble ... though it still has a ways to go before it's finished ... and there's always the "will my system still respect me in the morning" test ...


What seems to have worked was ... re-adding the medibuntu repositories and then running update manager ... and then rebooting.

Update manager downloaded six programs .. not sure what all of them were ... but non-free-codecs and w32codecs were among them.


After a reboot VLC seems stable ... I will post if that turns out not to be the case.


But for now this seems to be .... [Solved]


Thank god ... this was driving me batty ... along the way fixed up a couple other small errors with all the help I was offered ....

Now .. bring on the next problem ;)


Sigh ... well the next problem is the previous problem ...played *almost* 2 full DVDs before it crashed again ... as I'm unlikely to ever play 2 full movies between reboots perhaps I can live with that.

Now the DVDs will play .. apparently from start to finish - which I suppose is better than the 5-10 minutes I sometimes got before .. if the computer doesn't do much else ... wonder if it's worth trying to figure out what programs cause it to crash ... probably not ... none of my other clues were worth chasing down ... but ...

Empathy
Pidgin
Java applets within firefox ... still unclear if just firefox will


Now I know CDs have similar problems (and perhaps even youtube videos and internet radio - iffy on those at the moment) ....  They run for a while and then they stop and it seems like the DVD drive isn't even there.  A restart fixes the problem for a while anyway.  Then once the drive "disappears" I can't find anything short of a restart that will make the system acknowledge it again.  In fact, when the system goes to sleep it seems to lose track of the DVD drive.

****Seemingly unrelated error number 5 .... string of fast moving error messages on restart ... couldnt read ... got this message:
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".
and was asked to delete it 
I did ... we'll see what happens next***

Enjoy.

---

