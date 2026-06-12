---
title: "hard drives"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-12
Hello,

I need help with a hard drive. It's an internal hard drive an I connected it already, I just can't view the files on it. :'(

It's a secondary hard drive and it has Windows XP on it  well at least it used to :P I'm just tryna get files from that hard drive..

---

### Post by bekind2thenoob on 2009-03-12
Any more info? which os are you using? new or old harddisk? are you sure it has files on it? SATA or IDE? how have you connected it?

---

### Post by taurus on 2009-03-12
Have you installed Ubuntu on a harddrive or are you running it from the LiveCD?

Open a terminal and post the outputs of these commands here, running one line at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by lil_kid1333 on 2009-03-12
My primary OS is Ubuntu and the other hard drive I just connected is my friends. He had Windows xp but some things happened so now we're trying to view it on my computer.

Its old, I'm pretty sure it has files, and about the SATA or IDE, idk what that is :P I connected it internally I unplugged my cd rom and used those cables to connect the hard drive.

It's a Maxtor hard drive

---

### Post by lil_kid1333 on 2009-03-12
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2c8e2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       19270   154786243+  83  Linux
/dev/sda4           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             146G  102G   37G  74% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  208K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.8M  249M   2% /dev
tmpfs                 252M  256K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by taurus on 2009-03-12
If it's old, then it's probably a PATA (or an EIDE) drive.  Make sure you have set the jumper on the back properly.  Then, go into the BIOS to see if the system, BIOS, even detects that harddrive.

---

### Post by lil_kid1333 on 2009-03-12
Don't I press or hold F2 to go into BIOS?

---

### Post by bekind2thenoob on 2009-03-12
Its different for different BIOS it should say either at the to or bottom of your computers boot screen (the first screen you see after you startup)

---

### Post by taurus on 2009-03-12
On one of my machines, I have to press the Del key.  And some old Dells here at work, we have to use <Ctrl><Alt>Enter but for the newer Dell machines, either F2 or F12.

---

### Post by lil_kid1333 on 2009-03-12
Ok I went to BIOS and the primary master was a bunch of weird symbols O.o and had 360gb and I have no idea what that is... 

my hard drive was like third master which has 160gb and I tried to detect the other one (my friends) which is 80gb but no luck :(

oh yeah I forgot to mention his hard drive is infected big time. We can't log in, that's why he wants to get some files through my ubuntu. 

Maybe it's the virus that made the primary master with a bunch of weird symbols? It said 360gb but his is only 80... :s

edit:btw we know it's connected right cause we touched his hard drive and it was warm.

---

### Post by hockeyhead019 on 2009-03-12
umm... bad idea to actually touch the HD haha... but you might be hosed if the bios can't figure out what you've connected

---

### Post by taurus on 2009-03-12
If his windows is hosed by virus, wouldn't it be much easier to leave the harddrive in his machine and try to boot his machine with Ubuntu LiveCD?  Then, see if you can access his harddrive from the LiveCD and if you can, mount an external drive and copy files from his internal drive to the external drive.

---

### Post by lil_kid1333 on 2009-03-12
lol I know but at least try :)

and what you mean hosed?? :S

---

### Post by hockeyhead019 on 2009-03-12
meaning ruined, screwed, messed up, f***** up haha, just meaning you can't get onto the drive from the windows OS

---

### Post by lil_kid1333 on 2009-03-12
> **taurus said:**
> If his windows is hosed by virus, wouldn't it be much easier to leave the harddrive in his machine and try to boot his machine with Ubuntu LiveCD?  Then, see if you can access his harddrive from the LiveCD and if you can, mount an external drive and copy files from his internal drive to the external drive.

Well we didn't think of that :s well it was a hassle taking it out and we did so is their any way to view them here now that we have the hard drive here?

---

### Post by taurus on 2009-03-12
Then you need to check the jumper and/or cable to make sure everything is connected right.  And if the BIOS doesn't detect that harddrive, no OS will detect it, either.

So it's up to you if you want to play around with the jumper and/or cable or if you want to put it back to his machine (reset the jumper back to where it was before) and see if you can access his harddrive from Ubuntu LiveCD.

---

### Post by lil_kid1333 on 2009-03-12
yes sir we're going back xD thanks dudes i'll report back on my mission :P

---

### Post by hockeyhead019 on 2009-03-12
the only thing that i can suggest is take it out of the current computer, check the wiring and re install it into the computer and then try again... make sure to disconnect power and all of that good stuff before touching any of it though

---

### Post by sailthesea on 2009-03-12
I suppose a couple of hints about hardware handling/assembly are a little late now?;)

---

### Post by theozzlives on 2009-03-12
I smell incorect jumpers, or hardware failure. Not virus.

---

### Post by hockeyhead019 on 2009-03-12
that would make sense, can you boot into windows at all from your friends computer? or does it just sit... if it sits you might have destroyed ur HD which could help explain why it was warm when you touched it even though you didn't have it show up... maybe a short or something somewhere

---

### Post by sailthesea on 2009-03-12
How are you doin guys?
Don't rush things and try not to touch any more stuff inside the case 
 Carefully must you tread

---

### Post by lil_kid1333 on 2009-03-12
> **theozzlives said:**
> I smell incorect jumpers, or hardware failure. Not virus.

trust me IT HAS a virus ;) Let me explain 

If I try it on friends computer it loads windows but then when it gets to choose a user, I choose the user it loads but then logs off I tried safe mode and same thing!!

Even after doing a windows repair installation it would not let me log in :S

so now we're back and put the had drive in and now I ran beautifull Ubuntu off the livecd thing and now i'm here for help... 

my question is, how do I view the files on the hard drive?

---

### Post by lil_kid1333 on 2009-03-12
> **sailthesea said:**
> How are you doin guys?
Don't rush things and try not to touch any more stuff inside the case 
 Carefully must you tread

too late we already shock ourselfs to death my friend is laying beside me twitching... lol jk xD

---

### Post by jerome1232 on 2009-03-12
If you pull down the Places menu, it should be listed in there, it'll either be named by the volume label or it's size. Clicking it's icon in the places menu should mount the drive and place an icon on your desktop. You can then click the icon on your desktop or the same icon in your places menu to browse the contents of the drive.

report back if there are any errors.

---

### Post by lil_kid1333 on 2009-03-12
[IMG]http://img16.imageshack.us/img16/8964/thing.png[/IMG]

That's the only thing that came up :s

---

### Post by taurus on 2009-03-12
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by lil_kid1333 on 2009-03-13
Well guys i'm sad to say but... My friend got owned pretty badly by some damn good hacker... I would give that fuu props seriously but **** him...

anyways the reason the hard drive didn't work on my pc is cause my friend has a Sony computer and his friend(which is pretty damn good with computers) told him sony hard drives are only for sony computers thats the reason my computer didn't detect it..

and then idk what happened but then the same problem happened with ubuntu livecd, it wouldn't let me log in :s 

At least im lucky to say that my computer didnt read the hard drive or else i'd be getting owned too... but to make sure i'm scanning it...

Well anyways thanks guys for all your help :) we actually loaded ubuntu only once and it read the hard drive but we couldn't access it but it didnt load ubuntu right, the top part where it says Applications Places and System didnt show or the bottom part either it wasn't the monitor so that's when I restarted his pc and then that's when it didn't let me log in no more... worst thing i've ever seen O.O

---

