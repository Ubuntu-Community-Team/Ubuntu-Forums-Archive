---
title: "Mount filesystem failed after system crash"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Nick Brohman on 2010-02-20
[COLOR=Red][I][B][COLOR=Blue]This is marked as solved....it isn't....I did a clean install of Mint7, then decided on 9.04 and finally put 9.10 back on the 'top.....the problem still exists, just not on my 'top as of 25.03.10....
[/COLOR][/B][B][COLOR=Blue][COLOR=Red]
So far the HD seems to OK.....the reason for the problem appears to be an update taken some hours before the crash.....it also appears to be another problem that the community cannot help me solve,,,,,
[/COLOR]
This time last week, 0830 Sunday, AEST, I was in the throes of a heart attack with another on the way...luckily with the the next one, I was already in Prince Charles Hospital and that's a good place to be, in a situation like that.
The upshot of all this is that I can now no longer get to a shop to get the HD tested, nor do I have the wherewithall to enable me to get a technician to visit me.
If someone can read my subsequent posts to this thread, determine how I can repair the problem, if it is OS related, I would appreciate that. 
[/COLOR] 
[/B][/I][/COLOR]
G'day to the Forum Community,

[B]I'm putting this in Absolute Beginners because I really an am AB.
[/B] 
My laptop is a Compaq Presario CQ61 with a 500 GB Samsung HD with 9.10 installed, no other OS. I'll have to find an e-mail written a month ago to find the rest of the specs, if required.  

[I][B]I have striven to be concise in asking for help with this problem, all of the reasons for it would greatly increase the post.
[/B][/I] 
This started after the 'top crashed whilst using K3B to burn a CD 'in the field'. When I booted the next day, I got an automatic filesystem check which I tried to ignore, had done so twice before, when I got this message:- 

Mount filesystem failed (the rest of the message I've forgotten tho' there is supposedly a program running).

I've **read many threads **on this subject and am presently running this command:-     

fsck -y /dev/sda1 

This is with kernel 2.6.31-17 Recovery mode.

I ran this command in...19 without success, and used mountall as well.....no good there.

Currently, the fsck command has been running for over 4 hrs. and I'm at this point:-

[B]Warning...fsck.ext3 for device /dev/sda1 exited with signal 7 ?
rootxxxxxx-laptop:~#    [ 1762.597761] end_request: I/O error, dev sda sector 843269855
[ 1762.599791] end_request: I/O error dev sda, sector 843269863 
udevd-work[666]: 'sbin/bikid -o udev -p /dev/sda1'unexpected exit with status 0x0007

[ 1762.606475] end_request:I/O error, dev sda, sector 580306471
.....as above line........
udevd-work[666]: 'devkit-disks-part-id /dev/sda1 unexpected exit with status 0x0007

[1770.0634721] end request: I/O error, dev sda, sector 539231223

followed by 11 lines of '...Buffer I/O error ondevice sda1, logical block...'
then a string I/O errors on dev sda.
[/B]    
I've been told that it can take some time, but this has been at this point for well over 3 hours. I know something is happening as there is a flashing **_**

My 64 bit LiveCD will not mount.

[COLOR=Red][B]I am a novice computer user with no knowledge of M$ or X OS. I wish to increase my ability with, and knowledge, of Ubuntu. 
[/B][/COLOR] 
I created this problem with what I did after the crash and I want to fix it.

If I turn off the 'top and start again, I shall only exascerbate the problem.

[B]Advice and assistance will be much appreciated and I will be forever grateful for the knowledge I gain.
[/B] 
BTW I am using gedit, on my PC, to write this. At least I have one computer that 'works'.

Thank you and cheers

---

### Post by Gone fishing on 2010-02-20
Your doing what I would - however, it might be easier to reinstall if your /home is on a separate partition. Just remake the root partition and make sure you don't format /home.

---

### Post by Nick Brohman on 2010-02-20
> **Gone fishing said:**
> Your doing what I would - however, it might be easier to reinstall if your /home is on a separate partition. Just remake the root partition and make sure you don't format /home.
 
Thank you but I don't know how to partition and I can't enter anything other than command lines....I have to have clear directions for that process as well.

I'm not trying to re-install, just trying to get the 'top to boot. It was bought new 3 weeks before this happened and I've been looking for a solution for 1 week.

If I insert the LiveCD, it is not read.

There is something stopping the process.

At present it's still at the point where it was 7 hrs ago.

Thanks and cheers

---

### Post by Nick Brohman on 2010-02-20
This is the thread where I found what I thought was the solution as the error message is very similar, or the same as, mine...

[http://ubuntuforums.org/showthread.php?p=8851871](http://ubuntuforums.org/showthread.php?p=8851871)

Two more threads I had read, I didn't bookmark any more, just too many....

[http://ubuntuforums.org/showthread.php?t=1337254](http://ubuntuforums.org/showthread.php?t=1337254)

[http://ubuntuforums.org/showthread.php?t=1366591](http://ubuntuforums.org/showthread.php?t=1366591)

I also linked to this page but didn't follow that as i have only one OS on the 'top...

[http://greative.net/index.php/2010/01/solution-mount-file-system-failed-problem-ubuntu-910-karmic-koala/](http://greative.net/index.php/2010/01/solution-mount-file-system-failed-problem-ubuntu-910-karmic-koala/)

As the sun is well and truly over the yardarm, I'm goimg to abort the fsck operation, put some Blues music in a playlist and chill out with a few beers.

I am not going to try again 'til sometime Sunday.

Cheers...

---

### Post by Gone fishing on 2010-02-20
[QUOTE]If I insert the LiveCD, it is not read./QUOTE]

You either have a bad CD or you forgot to tell BIOS to boot from the CD 

I'm wondering about fsck.ext4 -y /dev/sdc1

or

sudo touch /forcefsck

have a look at

[http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck](http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck)

---

### Post by sandyd on 2010-02-20
wouldnt jump to conclusions, but if fsck cant read your HD (hence the i/o errors) it seems that youve damaged your HD physically).

Youll want to get a livecd running immediately and start copying stuff over to somewhere safe.

---

### Post by _khAttAm_ on 2010-02-20
I think your HDD has some errors. I don't know how you couldn't boot with Live CD. Did you try creating a live usb disk and check?

I think the problem is with the HDD. Boot with Live CD and check HDD for errors with Disk Utility (System>Administration>Disk Utility).

---

### Post by Nick Brohman on 2010-02-20
> **Gone fishing said:**
> [QUOTE]If I insert the LiveCD, it is not read./QUOTE]

You either have a bad CD or you forgot to tell BIOS to boot from the CD 

I'm wondering about fsck.ext4 -y /dev/sdc1

or

sudo touch /forcefsck

have a look at

[http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck](http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck)My apologies, but  I don't think you understand my problem..It all started after a crash and the automatic filesystem check on every 25th boot that happened just after the crash.

I'm trying to learn computing using  a Linux OS, I've never intentionally had M$ on one of my computers, except for the  CQ61 & the intention was to have only a Linux OS on that. I had the 500GB HD installed the day after I bought it and swapped the 250 GB that came with the 'top for a DE-link router.

Because I have no kmowledge of M$ or X OS, or any other version of any overpriced OS that is only aimed at dollars in the bank, I'm having many probs, caused by myself, thru' lack of knowledge.

Every one assumes I know M$ or X OS ...I'm sorry but I don't.

There are posts of mine where I state my computing philosophy, I'm not going to repeat them here...the original post to this thread took me at least 3 hours to compose and then edit to maKe sure I gave the most succinct description of my problem.


The Presario that I have now came with a 250 GB HD and Win 7...I could not operate that OS...lack of again...it bamboozled me...I couldn't even get my LiveCD to open so that I could install 9.10....

The LiveCD that I have comes from LINUX magazine of January this year, and only available 2 days past at my local Newsagent. It can be opened on my PC but I'm not prepared to do more than make sure that it can be read. It also appears to be OK.

I'm a novice, I thank you for trying to help me

[B][I'm wondering about fsck.ext4 -y /dev/sdc1

or

sudo touch /forcefsck

have a look at

[http://ubuntuforums.org/showthread.p...ghlight=e2fsck]("http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck")[/B]     ]

I thought that I had ext3, and I don't see anything related to sdc1... I'll go to that thread to for more research, but honestly, 'I'm paddling a barbed wire canoe up a creek without a paddle'....I need simple directions..so when I get my error message I should use the sudo touch /forcefsck...command


Thanks and cheerio

ps...I have just entered the force command and get this message

**touch: cannot touch '/forcefsck' : Read-only file system**

then it asks me for another command.

I'm not going to attempt the first command from the post quoted, I have ext3 & my device is sda1.  My attempts to get to the BIOS aren't always successful. however I changed the boot to the internal CDdrive. I will try to enter BIOS again to re-set that...it's not always successful. My LiveCD was tested OK with my box. The internal drive is spinning but is going to checked by a techie tomorrow.

---

### Post by Nick Brohman on 2010-02-20
Thanks Carlee, but I don't seem to be able to run a LiveCD.

**When I boot with the LiveCD in place, the fiesystem check is the only action happening. The disc is spinning, the check seems to stop the read**. **I don't yet understand how to copy things to somewhere safe.**

---

### Post by Nick Brohman on 2010-02-20
Once again, I just put my finger on the power button to start my laptop, i got the filesystem check that happens every 25th boot and ran into this problem....as
it is Sunday morning here, I will take the 'top back to the shop where I had the Samsung HD installed....but not 'til Tuesday....if you want something done properly, don't get it done on any day ending with a 'y'

This reply was supposed to have the post I'm replying to as a "quote"...**my apologies _khAttAm_ I'm not trying to be impolite here, I'm just very frustrated.**

---

### Post by Nick Brohman on 2010-02-20
Any replies to this thread have to consider the implications of the[COLOR=Red] RED[/COLOR] script in the OP...thank you for your consideration...scarp is better for me as a means of communication...PMs will be appreciated

---

### Post by cmay on 2010-02-20
Seems to me that if he has no usb stick nor can be able to boot the livecd from the dvddrive the solution is further ahead than running a livecd to check it.  

Maybe the wires on the dvddrive is loose or something.  Not sure if this could be the cause eof the filechecking stopping with this error msg.

---

### Post by Nick Brohman on 2010-02-20
Thanks cmay but I can't see how this is possible,  it was reading CDs immediately before the problem arose. I haven't abused the 'top, it has been handled with care.

I will take the 'top back to the shop where I had the HD installed (not where I bought it) on Tuesday coming to get it checked. I was assured that the HD was OK when installed and that it passed the HD check at the time of installation.
 
I can't help thinking that **K3B** is the root cause of this problem, after all, that was the program I was using when the "top crashed. 

Then again, with my lack of knowledge and computing ability, I'm most likely to be the cause for this event. I really want to correct that situation, but I'm not progressing as I thought I would.

Cheers...and thank you for your concern

---

### Post by Nick Brohman on 2010-02-21
> **Gone fishing said:**
> [QUOTE]If I insert the LiveCD, it is not read./QUOTE]

You either have a bad CD or you forgot to tell BIOS to boot from the CD 

I'm wondering about fsck.ext4 -y /dev/sdc1

or

sudo touch /forcefsck

have a look at

[http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck](http://ubuntuforums.org/showthread.php?t=1409754&highlight=e2fsck)G'day ,

I have now read that thread and his errors seem to my errors.

As an inexperienced user/learner, I tried all ways of entering 'CONTROL+D' to no avail.

Another message told me to run fsck manually without two of the letter commands. 

I tried one fsck but that process stalled...got more errors.

As for the OP being told to get some books on Linux, that will be an expensive and useless exercise for me.

I have a copy of a Fedora 4 manual 'Sams Teach Yourself', bought 4 years ago when I bought my first barebox. I bought that because the DVD I had obtained with an APC magazine, could not be opened properly as I didn't have a means of opening it.

I got XP installed as a temporary measure, then tried to get the Sabayon 3.5, the first Linux distro in my possession, failed. 

I found the Fedora book, bought it and got rid of the bloat by installing F4...I didn't have the Net, wasn't interested as I could get that for nothing thru' our Municipal Libraries.

I had 3 months of fun with my music, then mucked things up and stopped using the PC.

18 mths ago, M$ was re-installed, but the promised tuition was not forthcoming.

Within two weeks, I got the Net, installed Ubuntu 7...couldn't get an e-mail account going...installed the Sabayon and was pleasantly surprised when the Net was made available to me. Tried to join their forums, but my e-mail address was not recognised...reasons are in another post...had problems...installed 8.04...same thing...couldn't get an e-mail out because my IP won't help me..

The only good advice a  Me$$er has given me was to sign up with yahoo or whomever other than BigPond...my learning experience started on 28-08-09, the day I joined UF, and started to learn. My real computing experience is only 6 mths..

I have many Linux magazines (and distros) but am Ubuntu to the core.

When I read those magazines, I don't learn much as MS or X OS are referenced, and a lot of the time I'm confused by the jargon.  I really learn well by example. If I'm shown how to, I'll learn and get better at this caper.

I know already that I haven't replied, in one post, correctly...the info is right, just not placed properly.

This seems to be a problem for a few people and it all started, for us, 8 days ago.

I think I have to do something in BIOS but am afraid that I will not do that right. 

Thank you for your reply and attempt to help. I will keep a watch on that thread, I didn't read it originally because of the title.

Cheers

---

### Post by Nick Brohman on 2010-02-22
G'day ,

I've managed to get to the BIOS and reset defaults. 

I then let the filesystem check run its course.

I got the message that starts with Mount of, etc., and finally got CONTROL-D to work

mountall gets to 35% and then I get this message

init: mountall-shell main process (808)   terminated with status 127 
    [COLOR=Red]**A smile keeps appearing where it should be(eight zero eight) and I can't delete it**[/COLOR].
mountall start/starting
fsck from util-linux-ng 2.16
swapon: /dev/disk/by-uuid/ce8f dba3-1442-4c0d-a2cd-8d849c9f02a5: swapon failed: Device or resources busy
mountall: swapon /dev/disk/by-uuid/ce8fd6a3-14d2-4c9d-a2cd-8d849c02a5 [832] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/ce8fd6a3-14d2-4c0a2cd-8d840c9f02a5
/dev/sda1 contains a file system with errors, check forced.
Filesystem checks are in progress (ESC to cancel)
Error reading block 61177969 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
             (i.e/, without -a or -p options)
mountall: fsck / [830] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (826) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@xxxxxxx-laptop:~# (flashing prompt)

I'm not going to start the process again because it will just get back to this point.

The strange thing is, it's the first time I've heard a noise from the speakers...I've had to use the headphone jack to get sound before this.

When I first got to the BIOS, not easy as just pressing Esc does not work. It needs several presses. I changed the boot to the CD option. That didn't work.

When I got to the BIOS again the HD boot option was showing.  That's when I re-set to defaults.

Other than get the CD drive checked, that is the end of my options. If the drive has to be replaced, the 'top will be out of action for another 10 days.

Any/all assistance to help me sort this problem will be greatly appreciated.
 

Thank you and cheers...

---

### Post by Nick Brohman on 2010-02-22
One thing I just noticed. 

I have the wifi turned off as I use an ethernet cable to connect with my router.

When the filesytem check starts, this then goes to blue in lieu of red.

Is this normal when this process starts ?

Being a new 'top, and the first i've owned, I have no experience of what happens on a 'top during filesystem check.

Thank you, I'm ...:confused:

---

### Post by cmay on 2010-02-23
@Nick.
I am afried the HDD is corrupted. its sounds like a hardware issue more than anything even I had hoped it was a kernel moduel jammed or somethng. Hope you get it fixed. 

@community. 
I dont use the forums anymore. its too big and everything happens too fast.  I can just tell you all that I  know nick and been in contact wth him every day for long time.  He is not stupid. he fixes things himself more often than someone gets a chance to help him. he is new to computers though. 

 I wish that the community would help him out more often. nick is actualy one of the nicest people I met for a long time.  I am selective about who I give such credits. 

 I would not speak out this way if had it not been because I am right now going to the hospital for infection  in the kidenys and somehow is getting poisoned from this but should I be sick or worse for long time again then I cant help nick out in anyway. .  I met him over these forums btw.

---

### Post by Nick Brohman on 2010-02-23
G'day cmai, 

Thanks for your support, it's exasperating and frustrating for me.....I searched many threads without a real answer to this....

As I find it very hard to talk with my hands (type), it takes me a long time to get a question right, the circumstances of the problem and any information that I believe the community should have in order to assist me...the original post took about 4 hours to compose, edit and highlight.

I'm learning every day, just that things are going very slowly...the last error message that I've posted above, took two hours for me to do...it's not an excuse, it's just the way things go....I'm not worried about time to fix the 'top as I have my box connected....I'd like to solve the problem as it is ***more *****knowledge** for me...then maybe I can help some one else in the future.

I know, for instance, that one or two of my replies weren't written correctly[COLOR=DarkRed] **and the**[/COLOR] layout was wrong (which I won't change) but by doing that I've learnt more about how to do this...pose a question concisely...problem described, circumstances...ad infinitum...

There's a lot of stuff I'd like to learn about the Message toolbar but that's for another day...

As I listen to Joe Walsh and "Rocky Mountain Way" I'll wish you good health in the future and say G'night.

---

### Post by Nick Brohman on 2010-03-07
Once again I seem to have a problem where I cannot be helped.....

I have also given too much info in the original post.....most answers here suggest running a LiveCD session to get things copied to who knows where....as a computer illiterate person, I really don't understand why I'm not getting things across properly.....

I thought I'd made it clear how this started.....that after all of this happening to me....reading threads, etc., garnering tidbits of info....people think I was trying to boot with the LiveCD...

I'm glad the 'crash team' of the **CCU*** at the **PCH*** are on the ball....it's been easier for me to have my life saved than it has been for me to solve my computer problems...

BTW I have the time and patience to get a solution to this, I just don't have the money to be able to afford the only Linux technician I have found in my city.....and he won't travel past the river so it's catch 22 for me....I am not allowed to drive...

Can someone take the time to give me an in depth critique of my OP....that seems to be all that I will learn from this thread.
[I][B]
"If time were my only worry I wouldn't have a care in the world, because the fella that made time, made plenty of it"...[/B][/I].[B]Tom Kruse (Mailman of the Birdsville Track).

**C*[/B]oronary** *C***are** U**nit**....P**rince** C**harles** H**ospital

---

### Post by Nick Brohman on 2010-03-10
I have resolved the problem by installing Mint 7.....the problem is not solved but will be marked as such...

---

