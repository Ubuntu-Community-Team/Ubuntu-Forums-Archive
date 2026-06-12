---
title: "Win XP diappeared all of a sudden after few days of linux"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by udayspatel on 2010-07-16
Hi,

I have come across a very typical problem. I installed 10.04 version on my dell 260 as a dual boot over my windows XP and it has been working smooth since the last couple of months. I have also installed and tweaked it to an extent that my whole family now uses only Linux. 

I used to use Windows in between for specific applications. I have not used Windows in the last 20 days or so but yesterday when I try to boot through Windows XP it just does not boot. Every time I select the option I would be able to see the first screen showing the windows logo and then it does not go forward. After this point it just restarts itself. 

I tried booting in safe mode and on command prompt but it just would not start. It would restart itself every time I give a selection.

I have also tried using the install CD and tried to repair installation but it just does not work.

I am very happy with Linux and do not want to remove Linux and reinstall after installation of windows. Please help me with a solution by which I can just re-install Windows and leave Linux intact. I am a new user and have gone through a lot of pain to bring my Linux installation to the state that it is now. Re-installing Linux and setting it all up would be a great pain.

Please Help....

---

### Post by waynefoutz on 2010-07-17
You can reinstall Windows, and leave the Linux partition intact. 

The problem with that though is you are going to lose your GRUB menu, and it will boot straight up into Windows. You'll need to reinstall Grub2 at this point, it's easy enough, this page gives you three different methods to reinstall grub2


[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by bodhi.zazen on 2010-07-17
> Win XP diappeared all of a sudden after few days of linux

Funny how that happens around here.

I am sorry you are having problems with Windows, I suggest you try asking on a Windows forum,

If all else fails, you can, as indicated above, re-install windows (not as easy as it sounds mind you) and preserve Ubuntu, or use Windows in VirtualBox - may be a better option.

---

### Post by udayspatel on 2010-07-17
Thanks Wayne, I'll give it a shot.
I'll try it tonight and post an update.

---

### Post by Jazzy_Jeff on 2010-07-17
Sounds like your Windows install was corrupted somehow. If you don't use it for anything real important, I would just do a fresh install of Windows using Virtual Box and run it inside Ubuntu when you need it.

---

### Post by Mark Phelps on 2010-07-17
I'm seeing more of these posts all the time these days, and I must admit, having dual-booted XP, Vista, and now Win7 systems, with Ubuntu versions for years, I remain mystified about this problem, primarily because I've never seen it firsthand.

My only guess, and it IS a guess at this point, is that your XP OS filesystem was getting corrupted somehow, such that when you went to reboot it, one or more system files failed to execute properly.

Were you mounting your XP OS partition, either manually, or using FSTAB?

Were you otherwise accessing files on your XP OS partition?

Apart from that, I don't know why you should be having XP filesystem problems that would prevent booting.

---

### Post by k3lt01 on 2010-07-17
I agree with Mark and Bodhi.zazen. My guess is that it is a Windows issue. Windows can and does corrupt itself with monotonous regularity. I have a friend with a Windows only machine and she suffered the same issue. It would just cycle between boot options. Some techy guy said it was a hardware fault, I suggested it wasn't because she had just updated iPhone software and I felt she had somehow corrupted her system. It turned out not to be hardware :D.

Did you update, that you know of, or install something last time you used Windows? I have seen a hdd controller update in Windows cripple a machine, that is why my father now uses Ubuntu exclusively as it was his laptop.

Be very aware that Windows can and does update in the background and you may not have even realised it.

---

### Post by digitalcitizenx on 2010-07-17
I will chime in here and agree that VirtualBox is a better alternative for someone who rarely needs Windows. 

I have Vista and 7 in VB and they both work great.

---

### Post by udayspatel on 2010-07-26
Thanks Guys for all your inputs.
I agree with you guys that windows is a bit funny and with any routine update it has a potential of being corrupted.
I must say though that I had not used it for some time after ubuntu install and the last I used before i found it was corrupted was more than 20 days. But I must say that I had never used it between the last successful use and it being corrupted so there are negligible chances that some file within the FS or the OS must have played up.
While I did not boot windows I used the FS regularly through linux to access files(office) and music that was still on windows FS. But I never used the root FS to create any issue there.

I'll try the VB to install windows but I am not sure what memory and CPU consumption it does. I installed wine to run windows programs and I tried itunes in it. I did manage to successfully install and use itunes but the CPU and memory consumption would go out of the roof to force me to kill the processes.

Anyways, I'll try VB to check if it is better. Meanwhile I'm leaving the thread open in case more people want to keep updating it.

---

### Post by udayspatel on 2010-07-30
Guys,
VB is not a good option for a  medium to heavy application on windows. I have CSS4 installed on windows which I've been using for a long time to maintain my website. There are few key changes I want to make to the site and now I am getting very desparate that my Windows is not working.

Though VB is good. It is only good for small applications as it is memory intensive and my machine only has 1gig of RAM installed.

I need to try the dual boot option again. As I mentioned in the begining of the thread my winxp is corrupt and now need to install it over ubuntu which is a bit of a pain.

I'll try it again, meanwhile keep your comments coming.

---

### Post by ronnielsen1 on 2010-07-30
> Sounds like your Windows install was corrupted somehow. If you don't use  it for anything real important, I would just do a fresh install of  Windows using Virtual Box and run it inside Ubuntu when you need it.

+1

> Though VB is good. It is only good for small applications as it is  memory intensive and my machine only has 1gig of RAM installed.

True. I had to upgrade to 2G for a satisfying experience

>  I have CSS4 installed on windows which I've been using for a long time  to maintain my website. There are few key changes I want to make to the  site and now I am getting very desparate that my Windows is not working.


[http://tips.webdesign10.com/good-css-editor-for-linux-ubuntu](http://tips.webdesign10.com/good-css-editor-for-linux-ubuntu)

---

### Post by rsgangr on 2010-07-30
Hello udayspatel,

I also use Windows for specific applications and have been running a dual-boot system in a low-end box (Celeron 1.7GHz, 1Gb RAM) for about 2 years now.  My Windows XP Prof SP3 is on one HDD and Ubuntu 8.04 is on another.

During this time I have had four Windows "blue screen of death" events. 

In each case I was able to get into "Safe Mode" although it took several attempts. I then went to Control Panel; Add/Remove Programs; Add/Remove Windows Components and then de-selected and re-selected each component that I normally have active. I then ran Windows Update manually. I realise that this "shotgun approach" is not necessarily what a Microsoft Technician might have done but it worked. Unfortunately I was never able to pinpoint exactly what had gone wrong.

By the way, a long time ago I de-activated the "Automatic update" setting. It tends to slow down the machine, usually when I can least afford it and it tries to update software that I do not have. I now run a manual selective update about once a month.

I agree that VirtualBox is not a viable option on a low-end machine - a fast CPU and plenty of RAM seems to be a prerequisite.

You might ultimately have to re-install Windows as suggested by "waynefoutz" above.

I wish you the best of luck!

---

### Post by tarps87 on 2010-07-30
> **udayspatel said:**
> ...I need to try the dual boot option again. As I mentioned in the begining of the thread my winxp is corrupt and now need to install it over ubuntu which is a bit of a pain.

I'll try it again, meanwhile keep your comments coming.

Just too make this clear, reinstalling windows will not/does not **need** to overwrite your Ubuntu install. As long as you have the windows install CD go through the step remove and recreate the **xp partition** and tell it to install there **not** onto the Ubuntu one.
However if you chose this option please backup all important data first just incase the worst happens, this will 'remove' grub so you will not be able to boot into Ubuntu until grub is reinstalled (not Ubuntu just grub). This is one option to get you back up and running, if you have any questions about it just post back.

---

### Post by bodhi.zazen on 2010-07-30
> **udayspatel said:**
> Guys,
VB is not a good option for a  medium to heavy application on windows. I have CSS4 installed on windows which I've been using for a long time to maintain my website. There are few key changes I want to make to the site and now I am getting very desparate that my Windows is not working.

Though VB is good. It is only good for small applications as it is memory intensive and my machine only has 1gig of RAM installed.

I need to try the dual boot option again. As I mentioned in the begining of the thread my winxp is corrupt and now need to install it over ubuntu which is a bit of a pain.

I'll try it again, meanwhile keep your comments coming.

Sorry to learn of your problems with Windows, it must be stressful.

I suggest you post on a Windows forums to see if there is a way to recover.

If not, back up your data and re-install. Just be aware of what partition you are installing into and you will do fine.

To restore grub, see :

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by coolman98 on 2010-07-30
I use xp in vb on my netbook see. it will work

---

### Post by tarps87 on 2010-07-30
> **coolman98 said:**
> I use xp in vb on my netbook see. it will work

Yes it will work but you are running a OS in another OS so the performance will be degraded which I believe is the issue the op had

---

### Post by sydbat on 2010-07-30
> **udayspatel said:**
> I need to try the dual boot option again. As I mentioned in the begining of the thread my **winxp is corrupt and now need to install it over ubuntu** which is a bit of a pain.This bothers me a bit. 

As mentioned by others, reinstalling Windows should have no effect on your Ubuntu install UNLESS you have installed Ubuntu via WUBI. Then, reinstalling Windows WILL remove Ubuntu as well. Or I have read this wrong...

---

### Post by lkraemer on 2010-07-30
If I were in your shoes, I'd be going to a friends house and burn the following LiveCD's:
Supergrub Ver .9799, Gparted, Clonezilla, UBCD, and Ubuntu 10.04.....

Boot from the Supergrub LiveCD, Use the HELP selection and fix
the Windows XP Boot sector. That should get you to where you can at
least boot into XP.
1. Clonezilla
[http://clonezilla.org/](http://clonezilla.org/)
2. Supergrub
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
3. UBCD
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)
(Boot each one to make sure they work properly)

**VISTA ONLY !**
1. Download the "Vista Boot CD" (for your version ...32 or 64 bit)
by searching for it with Google.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Burn the ISO IMAGE as Disk at Once (DAO) and at a SLOW speed. (I use K3B)

2. Try booting the Vista Boot CD, and let it repair the Vista install.
If it should work, then you are back in business.

**BACK to XP !**
BE VERY CAUTIOUS on what you do from now on, because if you select the
wrong option during re-install, you will blow away all your installed
software and data files, before you realize what has happened.  That is
why I would use Clonezilla to copy the drive FIRST!.

When it boots, RUN your Anti-virus program to VERIFY the Drive is CLEAN.
If not CLEAN, I'd then continue by reading up on how to repair from this site:

[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

Or, maybe something here might apply:
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

If you have a M$ Windows CDR you could always try this:
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)
But I'd use Clonezilla to copy the Drive first.  Or at least copy the
Win XP Partitions.  You may want to purchase a new drive, and clone the
existing one, while trying to repair XP.  That way if you mess up, just
copy it over again, and continue until you either get it working, or give up.

Last but not least, you could purchase a New Drive, Install Ubuntu on
it, and then connect your Windows XP Drive, and copy the Data Files to
Ubuntu at your leisure.  Then, format the old drive, install XP, Ubuntu,
and copy your data back to the new XP install.  But, you will still
have to install all your XP software.  Isn't Windows ALMOST the MOST
WONDERFUL OS you've seen!  There is never a dull day, with all the Blue
Screens, Warnings, Virus Detections, Security Alerts, Open Back Doors,
and on and on......Sure makes me happy I converted three years ago.....
Sounds like you will be in for several hours/days of fun!..............

Don't forget your Favorites, Any emails in Outlook, or Outlook Express,
and contacts that are saved on your computer along with any special drivers,
or downloaded files that were installed. If you purchased software you most
likely have those Original CDR's for installing.
(If you need the location of the Outlook files, I can find those on my
old XP system for you, I just don't have it readily available now, since it
has been three years.)
```

"C:\Documents and Settings\USER\Local Settings\Application Data\Identities\{CB92FE8F-XXXXXXXXX-YYYYYYY}\Microsoft\Outlook Express"

```

Oh, one other important thing to remember.  If somehow the XP Registry got
corrupted, it will automatically reset itself to a previous version, but only
after 10+ attempts at booting.  So, with that in mind, I'd use Supergrub
to restore the MBR, then make at least 15 tries at booting.  I'd bet that
some point it starts booting.  I've seen it in the past.  The problem is
I don't remember which Restore Point it uses.  If you pick another one
later than what it selected, it might not boot the next startup.  And, all
that will depend on how many VALID Restore Points are in the system.

So, like I said, you're in for a real bumpy ride.  If you do it correctly,
and in the correct order you will be fine.  Otherwise you will end up blowing
XP away and starting from scratch.  Good Luck....

If I can help....Ask!

lk

---

### Post by ronnielsen1 on 2010-07-31
>  					Originally Posted by **coolman98** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9657104#post9657104") 				
 				*I use xp in vb on my netbook see. it will work*


What do you use the dos for? Seems like anything you need dos for would work in dosbox

---

### Post by udayspatel on 2010-08-05
While you guys try to help me here I have encountered a new issue.  I think I migt just end up re-installing both windows and ubuntu if I am unable to resolve my new issue. The only worry that I have is setting up my wifi to work on linux which I somehow managed this time around. Not sure if i'll be able to do that again. 
[http://ubuntuforums.org/showthread.php?t=1546577](http://ubuntuforums.org/showthread.php?t=1546577)

---

### Post by corrytonapple on 2010-08-05
Try posting your Windows issue Here:
[URL="http://ubuntuforums.org/sevenforums.com"]http://www.winxptalk.com/
[/URL]

---

### Post by udayspatel on 2010-08-09
hello,
Thank you guys for all your help.
I managed to reinstall windows and then re-install GRUB to get ubuntu back

---

### Post by corrytonapple on 2010-08-09
> **udayspatel said:**
> hello,
Thank you guys for all your help.
I managed to reinstall windows and then re-install GRUB to get ubuntu back
You are welcome.:)

---

