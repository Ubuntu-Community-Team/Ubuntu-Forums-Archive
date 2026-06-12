---
title: "Thinking about Ubuntu"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by GratefulDean on 2011-02-26
Hello gang!

I have been thinking about running Ubuntu to play around with on my laptop with Win7 for a while.  I am about to do my biannual OS re-install and think now is as good a time as any to do it but I have a lot of questions. 

I am neither a computer genius nor an idiot.  But there are some things which I consider rather basic that I don't understand and some I haven't thought about in a while so they have faded from my rather feeble mind: 

1. how to set up a partition,
2. dual boot vs. VM?  can I run Ubuntu and Windows side by side without rebooting or is that a huge PIA?
3. Since Windows traditional craps out yearly requiring me to reinstall can I do this just on the Win7 partition only?

I am familiar with the various online resources to answer these questions but do you have any recommendation as to where I can find some clear and concise instruction on how to go about this?

Thank you, I really hope I can get this done.

Dean

---

### Post by Frogs Hair on 2011-02-26
1. I set partition up from Windows disk management , meaning I install windows first.

2. A dual boot will require a reboot to switch between operating systems.
   I have never had BSOD or any major failures with any version of Windows.

3. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by evPaseo on 2011-02-26
Dean,

Personally I dual boot Ubuntu and Xp.  Though I rarely use Xp anymore.  I dual boot rather than run Xp in VM because my laptop is rather old and it is unlikely VM would perform well.  That being said, if you are able to run Win 7 then you probably wouldn't have any trouble with VM.
The thing about dual booting Ubuntu with Windows is that Win doesn't play well with others.  Unless things have changed with Win 7, everything else is wiped out during a Windows installation.  So if you're going to be reinstalling it regularly, you don't want to wipe your Ubuntu partition too.  VM may be the best option for you.
Still, you can look at the following link for some good information about dual booting Ubuntu and Windows.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

OR...
You could try a live CD of Ubuntu first, just to get your feet wet.

Best of luck!

---

### Post by Jesse Tustin on 2011-02-26
I recommend DualBoot, but that's an opinion.
Set up a partition in the install selection " Install Along Other Operating Systems"
Yes, you can :) 
Hope this helps, 
Jesse

---

### Post by BHEJU on 2011-02-26
1.
It depends on your use (dualboot or vm) and size of hd.
However, I prefer, 4 partitions if I am dual booting
one for win install (NTFS)
two for ubuntu swap (EXT)
three for ubuntu install (EXT)
four for all my dada (EXT or NTFS)
2. 
Either choice is easy to configure, no PIA.
As to db vs vm, it depends on your use of win and ubuntu. I have used both configurations in the past but since I use win rarely, I prefer VM as I don't have to shut down Ubuntu. But if you plan to use win as much as linux I would suggest dualboot.
3.
Yes you can.
However, there is risk of messing with boot system which might require some extra work if you run into issues.In this case VM is good choice. 

Cheers,

---

### Post by GratefulDean on 2011-02-26
> **BHEJU said:**
> 1.
It depends on your use (dualboot or vm) and size of hd.
However, I prefer, 4 partitions if I am dual booting
one for win install (NTFS)
two for ubuntu swap (EXT)
three for ubuntu install (EXT)
four for all my dada (EXT or NTFS)


So, I can have all my data on another partition? Hmmmm, that sounds pretty sweet. I believe my HD is 250g's and we now store our pics and music externally, or at least move them there regularly I find I'm rarely out of space anymore. 

So the install partitions are for the OS's correct? What is the Ubuntu swap?  How large should each of the first 3 be?  

Thanks for the quick response.

Dean

---

### Post by BHEJU on 2011-02-26
So, I can have all my data on another partition?
Yes, You can, and if you dual boot and make that data partition NTFS, you can access (read and write) to that partition in both win and Ubuntu.
So the install partitions are for the OS's correct? 
Yes, thats where the os is installed.
What is the Ubuntu swap? 
Swap is basically extra memory. and it is advisable to have swap space in diff partition. This is really a dumbed down exp of Linux swap. You should google "linux swap" for more information on it.
How large should each of the first 3 be?
1-25 gig is fine (add 5-10 more if you have lot of big photoshop like softwares)
2- 3gig in general should be fine for swap (but it depends on your ram. I prefer to keep total of ram + swap to about 6 gig.
so, If you have 2 gig ram .. 4 gig swap partition. 
3-25 gig is plenty if you store all your data in data partition.

Cheers,

---

### Post by Dutch70 on 2011-02-26
> **GratefulDean said:**
> So, I can have all my data on another partition? Hmmmm, that sounds pretty sweet. I believe my HD is 250g's and we now store our pics and music externally, or at least move them there regularly I find I'm rarely out of space anymore. 

So the install partitions are for the OS's correct? What is the Ubuntu swap?  How large should each of the first 3 be?  

Thanks for the quick response.

Dean

"swap" is similar to a pagefile in windows, it should be equal to the size of your RAM, if you want to be able to hibernate. (you should read up on this via google)

The other 2 are your choice, depends on how much data you want to put on them. 


If you have to reinstall windows that often, you may want to run it on a VM inside of Ubuntu :P

---

### Post by GratefulDean on 2011-02-27
Alright, I get swap, sort of, and I've decided on the following configuration:

1. Win7 =   35g
2. Ubuntu = 35g 
3. Swap =   4g
4. Data =   the rest about 240g (I forgot I have a 320g HD)

**a.** does win/ubu automatically install program files to their respective partitions?
**b.** how do the OS's know to deposit data to the 4th partition?
**c.** will I have network issues when I am on the Ubuntu side or do I have to install anything there as well.
**d.** what about printer (network), monitor issues?
** e.** can I install Win7, create/shrink that partition, then install Ubuntu, create/shrink that partition, then do the swap and data partitions?

OK, I'm going to do Windows now and check back on my iPhone in a few.

Thanks to everyone for your help.  I'm really excited about this.  I hope I can get it done...

Dean

---

### Post by nm_geo on 2011-02-27
Dean

Download Ubuntu 10.04 or 10.10 on a USB drive.. Test drive it then use it to look at your present drive and plan from there.  You will be glad you have the live USB later.

---

### Post by Paqman on 2011-02-27
> **GratefulDean said:**
> 
**a.** does win/ubu automatically install program files to their respective partitions?


Yes. In fact Windows won't even be able to see the Linux partitions, so it'll be completely oblivious of the fact it's not the only OS on the drive. Linux will know Windows is installed, but won't care.

> 
**b.** how do the OS's know to deposit data to the 4th partition?


That partition is for your data. In Windows it will show up as another driver letter (eg: D: or E:). In Linux you can mount it anywhere you like in the filesystem, but the default will be in the /media folder.

When you want to save something that you want to have access to in both systems, just save it to your shared data partition.

> **c.** will I have network issues when I am on the Ubuntu side or do I have to install anything there as well.

Wired networking will just work, wifi might need a driver. If that's the case, plug in with an ethernet cable and go to System > Admin > Additional Drivers and see what it suggests.

> **d.** what about printer (network), monitor issues?

Shouldn't be a problem, but stuff like this really depends on your actual hardware.

> ** e.** can I install Win7, create/shrink that partition, then install Ubuntu, create/shrink that partition, then do the swap and data partitions?

It'd be easier to do all the partitioning in one go. Shrinking and moving partitions can be very slow.

---

### Post by Dutch70 on 2011-02-27
> **nm_geo said:**
> Dean

Download Ubuntu 10.04 or 10.10 on a USB drive.. Test drive it then use it to look at your present drive and plan from there.  You will be glad you have the live USB later.

+1 Test drive being the key words

Also, be patient & have fun with it. Be prepared to redo things if you change your mind about something, and you probably will.

---

### Post by waynefoutz on 2011-02-27
> **GratefulDean said:**
> Hello gang!

I have been thinking about running Ubuntu to play around with on my laptop with Win7 for a while.  I am about to do my biannual OS re-install and think now is as good a time as any to do it but I have a lot of questions. 

I am neither a computer genius nor an idiot.  But there are some things which I consider rather basic that I don't understand and some I haven't thought about in a while so they have faded from my rather feeble mind: 

1. how to set up a partition,
2. dual boot vs. VM?  can I run Ubuntu and Windows side by side without rebooting or is that a huge PIA?
3. Since Windows traditional craps out yearly requiring me to reinstall can I do this just on the Win7 partition only?

I am familiar with the various online resources to answer these questions but do you have any recommendation as to where I can find some clear and concise instruction on how to go about this?

Thank you, I really hope I can get this done.

Dean

1. Partitioning is done pretty much for you, if you have Windows installed first. You can also do the "Wubi" method, which mounts Ubuntu on a loop mounted file instead of a partition. This lets you try Ubuntu without the commitment of partitioning, and can be easily removed like a Windows application. This is meant to be temporary, so you can try it out,  but some run theirs this way for years. I wouldn't put any critical data on an Ubuntu installed this way. To do this, simply insert the Ubuntu disk while Windows is running, and choose "install inside Windows."  If you go the traditional route, and want to partition, boot from the Ubuntu disk and it will see Windows, you can move a slider to set up how big you want to make your Ubuntu drive, and it will even import all your settings from Windows. 

2. That's up to you. Personally, I do both. Ubuntu is my primary OS, but I have a small partition with XP on it. I also have another XP installed inside of Virtualbox so if I need to do something in Windows, I can launch Windows without exiting Ubuntu. If you run it in seemless mode, it looks like you are running both OSs at once.

3. Ubuntu will never "crap out" like Windows does. My drive is 160 gigs, 20 of it goes to Windows, the rest is Ubuntu. I don't worry about XP degrading  over time like most Windows users have to, because I rarely use it, and when I do, it's normally only for Windows games that I can't get working in Ubuntu.


I would go ahead and reinstall Windows like you planned. Insert the Ubuntu disk while Windows is running, install it like a Windows program. Like I said this will give you a dual booting computer with Ubuntu mounted on a file instead of a partition. Try Ubuntu out. Kick the tires. When you're done, go to Windows' add remove software and uninstall it. If you like it, boot off the Ubuntu CD and install it for real with it's own partition. There's nothing to be afraid of.

---

### Post by GratefulDean on 2011-02-27
> **nm_geo said:**
> Dean

Download Ubuntu 10.04 or 10.10 on a USB drive.. Test drive it then use it to look at your present drive and plan from there.  You will be glad you have the live USB later.

Trying this but keep getting this:

[IMG]http://i678.photobucket.com/albums/vv147/GratefulDeanADV/SyslinuxError.png[/IMG]

I'm not sure what this means other than I won't be able to boot from it.  I set the persistent file size to zero for that.  I'm going to try it again at max to see if it works.

I love when things go awry out the gate...

---

### Post by GratefulDean on 2011-02-28
Firstly, thanks to everyone who has responded.  

As I am want to do, I ran full speed ahead unto the battlements until I found something that worked. I couldn't get it to boot from the thumb drive, we don't have any burnable DVD's so I ended up using Wubi first to boot from, then when that didn't work I used it to install in Windows. My only concern is rendering my computer unable to boot Windows or at least the Win7 installer disc.

A brief critical interlude:
I love it! It’s fantastic. I didn't get a chance to spend more than a couple of hours with it but it really has *almost* everything I need. Chromium with all my Google settings and bookmarks and Dropbox with all my files for work. The only thing it lacks is iTunes so I can sync my iPhone. (but my touch pad worked properly for the first time in over a year.) Because it was installed within Windows I really didn’t dig in too deep.

I had to flip back over to the Win side after, when I tried to set the visual effects to "extra", I was no longer able to dim my screen. Bright light hurts my eyes.

So I'm really looking forward to the install but it looks like it's not going to be as straight forward as I'd hoped.

More questions, some repeats I think:

1. How do I get 10.10 from my thumb drive to boot? I'm kind of stuck until this gets done.
2. After doing all of the above I now seem to have filled up over  190 gbs on my hard drive?  sigh... 
3. So I am going to uninstall my Wubi and if my HD shrinks back to the proper size, which I doubt, I will set up my partitions.  If not I will reinstall Win7 again and start over. 
     3a. 10.10 will allow me to choose the partition to install to correct?
     3b.  will Ubuntu give me the opportunity to set up the swap in the 4gb partition.
     3c. with a 64bit system and 32bit Ubuntu install and 4gb of RAM do I need  a swap?

Thanks,
Dean

PS. I uninstalled, which took  literally 2 seconds, an oddly short time, and my hardrive is still packed.  So I’m going to reinstall Win 7 and try this again in the morning.

---

### Post by waynefoutz on 2011-03-01
I would try another USB stick. I have a 2 gig stick that refuses to be used as a bootable disk no matter how many times I try, and I have a 1 gigger that doesn't mind it at all. Format it, not quick format it, in Windows, before you give up on it. 

Wubi  should have cleaned up after itself, if it didn't, simply delete the c:\ubuntu folder. 

When you go to install, you'll be greeted with a slider graphic, you simply  slide it to the percentage of your disk you want to give to Ubuntu, and it will partition the drives for you. You can do this manually if you want, but for a beginner. I'd let the installer do the task. It will even set up the swap for you as well. Ubuntu is actually easier than installing Windows. One word of caution, after you resize a Windows partition, Windows will run a scandisk the next time it boots. Let it complete the task. I hit the escape key one time, figuring  Windows could skip this and it hosed my Windows install. 

A great resource is Youtube. Go there and search for "Install Maverick Meerkat" and you'll find lots of great instructional videos.

---

### Post by nothingspecial on 2011-03-01
First try making another bootable stick, looks like somethings gone wrong there

Then during the install you will be asked how you want to install ubuntu. Choose manual (advanced).

Select the empty partition, choose to format it ext4 and choose a mountpoint of / (if this sounds like nonsense you should see what I mean when you get there)

Then select the 4 gig partition and choose to use it as swap.

Because, as someone has already mentioned, Ubuntu will see windows but windows will not see ubuntu, if you intend to use windows with iTunes I'd only give Ubuntu a maximum of 10 gigs (You would have to install an awful lot of apps to use more than that). Then keep all your data in your windows partition. Giving 35 gigs to Ubuntu is just wasting 25 gigs of space for your music because it will be unavailable in windows. You will be able to use all your stuff with ubuntu from your windows partition.

---

### Post by mastablasta on 2011-03-01
you can try another USB creator porgramme. A very easy to use with a step by step instal is this one: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by GratefulDean on 2011-03-01
Original Post

Thanks again for the responses. 

It looks like I am going to need to nuke my C drive to make sure it is absolutely clean before I do this.  I think, now that I&#8217;m looking at doing an Ubuntu partition I am going to image the drive when done so I can really screw around without having to go through all this again for a while.

Over at Windows 7 Forums user Bare Foot Kid offered the following solution via a fantastic guide.  [[COLOR="RoyalBlue"]Here is the link to his response to me[/COLOR]]("http://www.sevenforums.com/installation-setup/147646-windows-7-after-clean-install-takes-up-183gb-space-whaaaa.html#post1267435"). and [the [COLOR="RoyalBlue"]link to HDD optimization pre-install via a clean install[/COLOR]]("http://www.sevenforums.com/tutorials/91339-ssd-hdd-optimize-windows-reinstallation.html").  If you have a window system I suggest you check the links in his response.  A lot of great knowledge in there.

And [[COLOR="RoyalBlue"]here is my follow up[/COLOR]]("http://www.sevenforums.com/installation-setup/147646-windows-7-after-clean-install-takes-up-183gb-space-whaaaa-2.html#post1268294").

Now the TL;DR of it all, I will be going into DISKPART at reinstallation of Win7.  Via this process I will I will be swiping the drive and setting it up with an

   *ntsf*  *System Reserved* partition at 200mb
*ntsf* Windows 7 partition at 35gb
*ext4* Ubuntu partition at +/-10gb
*ext4* Swap partition at 4gb
*ntsf* Data partition at whatever is left.



So here are the questions I have for the Ubuntu gang:

1) Do I need a Swap?  Mine is a 64 bit system with 4gb RAM and I plan on installing a 32bit 10.10 Ubuntu OS.  I understand I may not be able to have more than 4 partitions on a drive so, with the System Reserved partition, I will run out.
	[INDENT]1a) Do you guys think I need a System Reserve?  What is it for?  If there is even a chance I will need it I want it.[/INDENT]
	[INDENT]1b) When I did the Wubi install into my present Win7 OS I noticed that Ubuntu showed the system reserve in its file tree (or whatever it&#8217;s called).  Was this the same System Reserve as windows uses? Or did Wubi create a second System Reserve on top of Windows.  When I create a System Reserve in the DISKPART will that System Reserve be used by both Windows and Ubuntu?[/INDENT]

2)> **nothingspecial said:**
> 
Because, as someone has already mentioned, Ubuntu will see windows but windows will not see ubuntu, if you intend to use windows with iTunes I'd only give Ubuntu a maximum of 10 gigs (You would have to install an awful lot of apps to use more than that). Then keep all your data in your windows partition. Giving 35 gigs to Ubuntu is just wasting 25 gigs of space for your music because it will be unavailable in windows. You will be able to use all your stuff with ubuntu from your windows partition.
I plan on really checking out the apps Ubuntu offers.  I&#8217;m kind of OCD about this.  I try everything I can get my hands on then settle with what works best for me.  I have collected over 500apps since I got my iPhone, the majority during the first 6months of having it.  Now I only use about 30 regularly, half of those daily, but some are obscure little gems that fit me like a glove.  The question here is, knowing this is a 10gb Ubuntu partition really going to be enough? Now, I have my iPhone with me all the time so I had ample opportunity to download a ton of apps.  This won't be the case with my laptop.
	[INDENT]2b) This is key- all my itunes music is on a network drive at the house, same with photo&#8217;s.  I will on occasion download music to my laptop hard drive but I shoot it to an external as soon as I can.  I have close to 500gb of music, that coupled with Pandora, Soma.FM, iPod on my iPhone I don&#8217;t really need to keep anything on this drive.[/INDENT]
		 

3) I can read up on this but *Ext4* is the correct name for the format?  *Ext4* typed in the command line will work, someone said Ext without a number so I assumed that is what it was called.

4) Mountpoint means installation point?

5) I figured out that things are done a little different in Ubuntu with **/** meaning **C:\**

6)> **waynefoutz said:**
> When you go to install, you'll be greeted with a slider graphic, you simply  slide it to the percentage of your disk you want to give to Ubuntu, and it will partition the drives for you. You can do this manually if you want, but for a beginner. I'd let the installer do the task. It will even set up the swap for you as well. Ubuntu is actually easier than installing Windows. One word of caution, after you resize a Windows partition, Windows will run a scandisk the next time it boots. Let it complete the task. I hit the escape key one time, figuring  Windows could skip this and it hosed my Windows install. 

A great resource is Youtube. Go there and search for "Install Maverick Meerkat" and you'll find lots of great instructional videos.
 I know that Ubuntu will allow me to set partitions on install but I think the process [[COLOR="RoyalBlue"]Bare Foot Kid[/COLOR]]("http://www.sevenforums.com/tutorials/91339-ssd-hdd-optimize-windows-reinstallation.html") put forth is gong to be the most efficient way to do this.  I can get it all done in a few commands, install Win7 to its partition then install Ubuntu to it&#8217;s partition moving the slider to 100% and, if necessary, pointing the Ubuntu installer to the 4gb Swap partition for the swap.  It sounds like this will be easy.[-o<

**UPDATE**
Bare Foot Kid has [[COLOR="RoyalBlue"]responded[/COLOR]]("http://www.sevenforums.com/installation-setup/147646-windows-7-after-clean-install-takes-up-183gb-space-whaaaa-2.html#post1268339").  And I don't like what he had to say.

He says that due to Grub conflicts I should set up on a second HDD.  I can't do this and I know folks here have dual booted. I may have lost him and now must set up the Ubuntu partitions via it's installer. 

So I guess I give Windows the remainder of the drive then have Ubuntu set up it's partition and Swap partition.

The big question is the shared data partition.  This is key so I can access all my data, including and most importantly, DropBox in the same folders on each side.  Is that possible.

OK, I need to step away I think my eyes are starting to bleed.
  Thanks for the help, 
Dean

**UPDATE 2**
After commiserating further with BFK it looks like I am going to set a 100-150gb partition for Windows, a 200mb System Reserve for Windows and leave the rest for Ubuntu.  I will allow the Ubuntu installer to take 100% of the remaining hard drive.

I'm looking forward to getting past this process and on to playing.

---

### Post by nothingspecial on 2011-03-02
Couple of things.

1 Not ubuntu specific - go and buy a new drive and back your music up. All drives fail in the end (trust me, I know).

Space, - This is my home pc with a ton of applications

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             6.9G  5.8G  773M  89% /

```

And this is my media server

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.0G  8.1G  27% /
```

Any spare space on your / partition is wasted because you don't store data.
If you really intend on installing tons of stuff go for 15G or even 20G for overkill.

ext4 is the file system. You can use ext3 if you like which is older and some would say more stable, but I've never had any problems with ext4. Notice it's a lower case e, not Ext4 (linux is case sensetive).

You don't need swap, but you should have it. You need it to hibernate for example. Read this

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

And now I have to take my kids to school.

---

### Post by rvchari on 2011-03-02
> **GratefulDean said:**
> Hello gang!

I have been thinking about running Ubuntu to play around with on my laptop with Win7 for a while.  I am about to do my biannual OS re-install and think now is as good a time as any to do it but I have a lot of questions. 

I am neither a computer genius nor an idiot.  But there are some things which I consider rather basic that I don't understand and some I haven't thought about in a while so they have faded from my rather feeble mind: 

1. how to set up a partition,
2. dual boot vs. VM?  can I run Ubuntu and Windows side by side without rebooting or is that a huge PIA?
3. Since Windows traditional craps out yearly requiring me to reinstall can I do this just on the Win7 partition only?

I am familiar with the various online resources to answer these questions but do you have any recommendation as to where I can find some clear and concise instruction on how to go about this?

Thank you, I really hope I can get this done.

Dean

my lappy too came with windows pre-installed. i upgraded to win7 and then allocated partition to install ubuntu (it was jaunty at that time which is now upgraded to maverick).

in this case, you cant run windows and ubuntu side by side when on dual boot mode. if you have any ideas to run both OS simultaneously, think of running windows in virtualbox.
virtualization means it is taken for granted that you have ample RAM at ur disposal that should take care of both OS.

if you really have an intention of doing away with MS, then using it as a VM will be my suggestion !

ever since i installed ubuntu, i am happy using wine for some of the win executables and VM for non wine executables !!!

original win7 is idle and is used only for occasional updates in its antivirus and related work !!!

wish you long long years with ubuntu

---

### Post by rvchari on 2011-03-02
when allocating partitions have these things in mind. mount point / where ubuntu sys files will get installed will be around 25 GB (min), /home where your home directories will get installed will have around 25 gb (min), swap will be atleast twice your RAM.

if on dualboot, then keep your win7 (probably your C partition) to bare minimum required (if you dont have any more softwares to install) allocate the remaining space to say BACKUP so all your files (music / videos / personal backups) can be backed up to that partition in case of necessitiy.

---

### Post by mastablasta on 2011-03-02
> **GratefulDean said:**
> **UPDATE 2**
After commiserating further with BFK it looks like I am going to set a 100-150gb partition for Windows, a 200mb System Reserve for Windows and leave the rest for Ubuntu. I will allow the Ubuntu installer to take 100% of the remaining hard drive.
 
I'm looking forward to getting past this process and on to playing.
 
BINGO! keep it simple. 
 
and you can have more than 4 partitions. there are basically two types. Logical and extended partition. logical can really be only 4, but you can add extended. the trick her eis thta Windows needs to boot form logical partition, however Ubuntu can do just fine with extended as well ;-)
 
 
so your plan here is preety good. i had it done it similar, only on XP. you just leave the disk for ubuntu empty (no formatting) and Ubuntu will do everything for you.
 
Otherwise 2 more things:
 
to run ubuntu well you need about 25-30 GB (most of it for applications you will add later on and especially if you want to try out WINE running windows applications).
 
you can access the Ubuntu part of disk from windows as well you just need certain tools.

---

### Post by GratefulDean on 2011-03-02
I will be getting back to all these great responses when I get the disk clean and Win7 install completed. 

I think what I'm going to do is stick with 100gb for Win7 ad 20gb for Linux, 4 gb for swap* and, via the Ubuntu install, format the remainder ntfs for data.  If the Ubuntu installer won't let me format that data partition I'll do it through Disc Management in Windows.

I think 100gb for windows is too big, especially if I can figure out how to save my docs etc. to a common data partition. But I'll run like that for a while and see how it goes.

If I see that I'm not using any of the partitions efficiently, either they are too large or too small I will go to the "changing partition size while existing partitions are ext4 and ntfs" school of forum postings. 

This has been a *FANTASTIC* learning experience.  Invaluable.  

Oh, I almost forgot.  I ended up finding some DVD's last night and burned a copy of 10.10 and booted up.  It worked fine.

Gotta go, DISKPART is ready for me.

Thanks,
Dean

*according to the [[COLOR="RoyalBlue"]Swap FAQ[/COLOR]]("https://help.ubuntu.com/community/SwapFaq") my system is described as a "high RAM, high disc space". The system in their example has 2gb RAM and 100gb of hard disc space.  My system has 4gb RAM and over 175gb of hard disc space.  Keep in mind that I am running a 64 bit system so my 4gb of RAM should be adjusted accordingly. 

PS. I am not done with this thread yet as I still need to do the Ubuntu install.  See you in a bit!

---

### Post by GratefulDean on 2011-03-02
Install is stuck on Who Are You page.  I am not getting the "forward" button to light up and the bar has stopped moving. and the text above the bar said something like "ready when you are".

So I backed out, reentered all my info, the bar moved a little and the text above the bar says getting the time from the server.

HELP! I was so close!

---

### Post by inkrypted on 2011-03-02
Try removing the CD and then placing it back into the drive. That helped me once. I really recommend a WUBI install as you can add and remove Ubuntu just like a Windows program.

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

As they say it's simple and safe.

---

### Post by GratefulDean on 2011-03-02
> **inkrypted said:**
> Try removing the CD and then placing it back into the drive. That helped me once. I really recommend a WUBI install as you can add and remove Ubuntu just like a Windows program.

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

As they say it's simple and safe.

Thanks,

I ended up shutting it down then trying to reinstall.  The installer wouldn't come up so I went back into windows and deleted the partitions that Ubuntu set up.  Now it's getting stuck on the ISOLINUX screen.  I'm going to burn a new disk as read only. I think this one is R/W.

I've set up via Wubi the last two nights. I really want to learn how to dual boot and set up multiple partitions.

Thanks,
Dean

---

### Post by GratefulDean on 2011-03-02
[CENTER]:guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar:[/CENTER]  
[CENTER][SIZE="4"]!!!!!!!!!!Success!!!!!!!!!![/SIZE][/CENTER]

Wow, that was allot of work.

Everything was borked after the last aborted install.  So I reinstalled Windows but accidentally used my 32bit install disk.  So I swiped the drive again then gave Windows all but 25gb of the 320 available from disk management.  

Then I just threw the Ubuntu installer in and had it do it's stuff, splitting the drive between the two.  I have learned a bunch from this experience which was what I was setting out to do.  The diskpart knowledge has set me free really.  

This is not what I originally wanted to do but I need to get back to my life of leisure.  

Thanks for all the help!  I look forward to playing with and getting to know Linux!

Signing off....

Dean

---

### Post by Ditchdoc7893 on 2011-03-03
Hi, I too am a dual OS user, as I am still learning.  My background, as I am still learning, I have Ubuntu 10.10 installed side by side with my XP OS.  That being said, they are running on separate HDDs (as in they each can boot from their respective HDD).  I also have 10.10 on my netbook as the solo OS.  I really like Ubuntu.  I can do as much if not more with it as with Windows (I have not made the plunge into Windows 7 yet so that is unknown territory for me).   For me, Ubuntu on my netbook has been a playing ground for me, trying things, learning things, etc.  If you're not quite comfortable making the plunge just yet on your primary system and you have a secondary system that you can utilize, I would suggest giving it a shot and seeing how you like it.  I think you will be impressed with it's ease in transitioning and finding your comfort zone.  Save your important stuff, maybe get an external HDD for your important files (music, videos, docs, etc.) and install Ubuntu to your primary HDD, or give it a try on a netbook or other computer that doesn't house your important stuff so you can fiddle around with it.  I think you'll be impressed with its ease of use and versatility.  I'm addicted.

---

### Post by GratefulDean on 2011-03-03
> **Ditchdoc7893 said:**
> Hi, I too am a dual OS user, as I am still learning.  My background, as I am still learning, I have Ubuntu 10.10 installed side by side with my XP OS.  That being said, they are running on separate HDDs (as in they each can boot from their respective HDD).  I also have 10.10 on my netbook as the solo OS.  I really like Ubuntu.  I can do as much if not more with it as with Windows (I have not made the plunge into Windows 7 yet so that is unknown territory for me).   For me, Ubuntu on my netbook has been a playing ground for me, trying things, learning things, etc.  If you're not quite comfortable making the plunge just yet on your primary system and you have a secondary system that you can utilize, I would suggest giving it a shot and seeing how you like it.  I think you will be impressed with it's ease in transitioning and finding your comfort zone.  Save your important stuff, maybe get an external HDD for your important files (music, videos, docs, etc.) and install Ubuntu to your primary HDD, or give it a try on a netbook or other computer that doesn't house your important stuff so you can fiddle around with it.  I think you'll be impressed with its ease of use and versatility.  I'm addicted.

Yes, it seems you and I have the same OS agenda!  After hitting the wall for about a week I finally got it done last night. 

I really wanted to learn how to dual boot and as I didn't have the option to install Ubuntu on a separate drive my options were dual-boot, vm or run from a disc or drive.  I wan't keen on vm as I understand it limits what you can do with Linux and sometimes the two OS's don't play well together. I wanted the two OS's on separate partitions to minimize an OS smackdown.

  I did, twice, install with Wubi so I could get a feel for the file structure but I kept running into issues.  I also ran from a thumb drive once and from a disc once.  These were more do to curiosity and my lack of patience than need.   

My biggest problem was Window 7 had turned my C drive into a veritable junk yard.  The digital equivalent of rusted out pickup trucks, Cameros, and old tires  lay strewn across the whole thing.  I was fortunate enough to find someone who showed me a fantastic way to clean up the drive.  The links are above somewhere. 

I installed Win7 on a reduced partition, expanding it in Disk Management in windows when I was done.  I installed Ubunu on that partition.  

One of the things that drew me to Ubuntu was the community.   I've lurked here before but as I wasn't aware of any app names and terms it didn't do me much good.  But everyone seemed pretty cool and there were all levels of expertise.


In summary:   I'm a tinkerer and Ubuntu is my OS.

---

### Post by nothingspecial on 2011-03-03
> **GratefulDean said:**
> 

  I'm a tinkerer and Ubuntu is my OS.

Oh yes, you have found your home :P

---

