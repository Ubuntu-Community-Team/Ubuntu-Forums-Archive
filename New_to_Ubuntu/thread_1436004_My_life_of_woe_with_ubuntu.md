---
title: "My life of woe with ubuntu"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by gaspros on 2010-03-22
Hello Ubutnu world, I am a somewhat experienced windows PC user. I have built my first PC yesterday and I wanted to load up the latest and greatest Ubuntu on it. This is a brand new machine I put together on the cheap and I plan on using it as an HTPC with XBMC or somesuch.

My specs are as follows:
Intel  Pentium Dual Core E6500 CPU, 2.93 GHz, FSB 1066MHz, Socket  LGA775
ASRock  G41C-VS M/board - Intel G41+ICH7, COMBO DDR2+DDR3, 1333 MHz FSB, PCIE,  int VGA, SATAII, 5.1Ch
2GB  DDR3 PC-10600 (1333MHz)
500GB Hitachi 7200rpm PATA HD

So I try loading up Ubuntu 9.10 64bit version  and it gets precisely nowhere. Just crap on the screen (numbers and codes) with something about end trace, then it just stops.
This is a live CD install and also tried the regular install. Get nowhere, same thing.
So I figure that maybe x64 is not such a good idea. So I burn another CD  with x86 on it. 
Same process. Live CD and the regular install.  I end up at some command prompt which I have no idea what to do with.  There is nothing on the screen that says something obvious like error or  failed to load or anything. Just some instructions on how to find help.  After hours of reading everything I can find I try typing in startx which then gives me a completely blank screen. Yeh!!! 
So maybe 9.10 is just too new and not ready for prime time. So 9.04 x86 burned and ready to go. Blow me over with a slight breeze it boots. It installs. It looks good. It does things, many things I am impressed this is what everyone is talking about. Wow.
It tells me there is a new version and that I should update, I agree lets get the latest new and improved. Sometime later after a reboot splat. Same crap. 

Lots more reading and I am guessing its got something to do with the motherboard or the onboard Video which is G41 chipset and Intel gma x4500.

So can anybody help. 
I am thinking rollback (except I dont know how) or re-install 9.04 and never update it!
Or go out and buy Windows7 but damit I dont want to let this thing beat me!

Thanks in advance for any help.

---

### Post by Alias1407 on 2010-03-22
Karmic Koala (Ubuntu 9.10) was the release that changed Ubuntu, you could say that Karmic Koala (in my opinion) was the worst Ubuntu distro ever released. Sure it looked pretty but didn't function as an OS. My suggestion is run a 32-bit 9.04 version of Ubuntu and don't upgrade to the newer OS. I'm running that right now and it's absolutely fantastic.

---

### Post by gaspros on 2010-03-22
OK, thanks for the advice. I will reload 9.04 since it worked. I will try and avoid upgrading anything related to the operating system. Last time I checked it did seem to want to upgrade a whole lot of other stuff which seem to be programs so I will have to try and see.

If anybody else has some specific help for my hardware configuration running on Ubutnu 9.10 I would like to know what you did to get it to work. If you got it to work!!

---

### Post by Alias1407 on 2010-03-22
You can upgrade the programs running on Ubuntu 9.04 without needing to upgrade to the latest version. If the update manager pops up just don't click "A new version is available, Upgrade Now"

I would avoid Ubuntu 9.10 at all costs. For some people it works great and for others (such as myself and many of my friends) it fails to function as an OS.

---

### Post by gaspros on 2010-03-22
Can you rollback or do I have to re-install? I can access Grub and select the previous version which works. Is there someway to rollback or make it so it auto selects the versions that actually boots?

---

### Post by Alias1407 on 2010-03-22
If you can access it from GRUB then you can edit the /boot/grub/menu.lst file to put the version you want at the top of the list. Otherwise you will have to re-install.

---

### Post by gaspros on 2010-03-22
I can access Grub , So I will try doing this. Will let you know how it goes. Thanks

---

### Post by mastablasta on 2010-03-22
You could try the 10.04 beta.
There seems to be an issue in 9.10 that for some reason it doens't install on computers where 9.04 worked flawlesly. the workaround was to use alternate install. installing without graphical interface, so you can load propper drivers before starting up the GUI. not sure if it would work in your case.
 
also you could just buy an older model of video card that is compatible with Linux. they are cheap and a whole lot better than the newest intel chips (although as i know intel GPU does have Linux support).

---

### Post by quinnten83 on 2010-03-22
> **gaspros said:**
> Can you rollback or do I have to re-install? I can access Grub and select the previous version which works. Is there someway to rollback or make it so it auto selects the versions that actually boots?

<snip>
i have 9,10 installed on several computers and they all have been working like a peach. 
run a checksum on your live CD's.
<snip>
If ubuntu isn't working, try another distro. look on distrowatch.com.
check ubuntuguide.org to see if any of your problems are addressed there. Seems to me you should not be having that many problems if you are running on intel chips, altough there is an intel bug, but i thought that was with the graphics card. If you are adventurous try with lucid beta. Maybe the bug affecting you got solved in that version.

---

### Post by gaspros on 2010-03-22
Sure Ubuntu 9.10 works on many a system just not on my current config. I have really spent hours looking around in these forums and reading the newbie advice. I will try the places you suggested but I dont want to try other distros. Might give Lucid a try though probably via the live CD after I have re-installed 9.04. I did find that Intel have updated drivers on one of their sites. I seem to be running xf86-video-intel 2.9.0 and there is a 2.10.0 out but I can find out how to install this. Seems I would have to compile the source myself and I am just not upto the task.  Still trying to figure out how to edit Grub right now to save the re-install.[URL="http://lists.freedesktop.org/archives/intel-gfx/2009-September/004401.html"]
[/URL]

---

### Post by gaspros on 2010-03-22
Dont want to have to upgrade the video just to work with 9.10. Is this 9.10 beta you suggest the Lucid that was referred to in another post?

---

### Post by Alias1407 on 2010-03-22
Lucid Lynx is 10.04 the proper release date will be in April sometime and even though it is possible that it will function perfectly I would tend to stay away from betas, especially beta Operating Systems.

---

### Post by gaspros on 2010-03-22
OK finally figured out how to edit Grub. sudo gedit and then open and edit the menu.lst file, And it now boots stright into the version that works. On closer inspection its not actually 9.04 like I thought but instead its 9.10 with Kernel 2.6.28-11-generic. The version that did not work was 2.6.31.20-generic.
So now I have 9.10 with no updates needing to be applied and on preliminary inspections it seems to work. Thanks for that.

---

### Post by gaspros on 2010-03-22
On second thought, the first thing I did was try playing a movie though VLC and the GUI rebooted the screen for me. Not the whole PC mind just seemed to reboot the screen and take me back to a login screen. So I think I still have a video card issue underneath all of this. Movie player does the same thing.
Any help with the GMA X4500 on board Video would be good about now.
Whats with the reboot to login thing anyway? My guess is something crashed!

---

### Post by gaspros on 2010-03-22
OK downloading 10.4beta now and will burn to CD, especially since its release is just around the corner. I take it that there is no easy way to just upgrade to the beta instead of re-installing via CD. If there is can you explain what to do? Thanks

---

### Post by gaspros on 2010-03-22
Its alright I think I figured it out. I selected the pre release option in repositories. Now I have a stack of things to upgrade. some of them say 10.4 so away I go. Be back soon with any further info.

---

### Post by gaspros on 2010-03-22
OK, so I edited Grub and got into the system with some previous version. Seemed ok but then found that VLC rebooted GUI on running a movie. Took the suggestion to look at 10.4 Lucid. Whilst I was downloading and burning it I tried the upgrade path. It installed pre-release stuff. 
My xserver-xorg-video-intel is still 2.9.0 when I have seen 2.10.0 out on some intel site.
I have no idea what version I am now running or how to find out?
The movies all just reboot the GUI and take me back to the login.
The Grub menu.lst has not changed. If I try and select 2.6.31-20 it now crashes with a udevd-work[139] unexpected exit with status 0x0009 and then asks me to login at a command prompt.
I have noticed that it says ubuntu 9.10 and not 10.4 so I guess I did not upgrade afterall.
So what next?

---

### Post by Calash on 2010-03-22
I hate to say this, but if you are having issues off of a LiveCD, and there is no error on your CD, it is likely you have a hardware issue.

Easiest thing to test first is to run the memtest option on the LiveCD.  Let it go for a bit and see if it comes up with anything.

Based on your description of the crashes I am inclined to think it is a video card problem.  Just guessing, so don't hold it to heart.

---

### Post by gaspros on 2010-03-22
OK I burnt the 10.4beta and rebooted with it and I get the udevd-work[95]: '/sbin/modprobe -b pci: gooblegoop'   unexpected exit with status 0x009 error. 

Wow how boring is this!

---

### Post by gaspros on 2010-03-22
OK running the memory test now from the 9.04 x86 CD since it was the one that worked and actually installed. When its done I will re-install 9.04 from scratch. Everyhtng else has failed for me. Its my last shinning hope of having a ubuntu HTPC with xbmc. 

Gripe time now: If that does not work well thats enough time wasted for me and I am back to M$. If its a hardware error then it should show up in windows as well and I will come back and appologise to all the good folk at ubuntu world. If not then its just my hardware and ubuntu dont mix. If thats the case its just too much trouble moving to ubuntu from windows when windows works.

---

### Post by Calash on 2010-03-22
Unfortunately that may not be the case.  Issues can show up in one OS and not the other.  I have seen issues that only effect some service packs on WinXP.  

Still, you have to find what works for you.  It may just be that there is something odd enough about your hardware that ti is throwing Ubuntu out of whack.

Ether way I hope you get a working system soon.

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> On second thought, the first thing I did was try playing a movie though VLC and the GUI rebooted the screen for me. Not the whole PC mind just seemed to reboot the screen and take me back to a login screen. So I think I still have a video card issue underneath all of this. Movie player does the same thing.
Any help with the GMA X4500 on board Video would be good about now.
Whats with the reboot to login thing anyway? My guess is something crashed!

I think what you're experiencing is X-Windows restarting. Sounds to me like (as you've mentioned) there's a video card issue causing X to crash... and when X goes down, the system automatically restarts it.

Sorry to hear you're still having issues. I hope it does work out for you, because this is definitely a far better alternative to the M$ options. Good luck.

---

### Post by gaspros on 2010-03-22
Me too. Memtest ran just fine no errors anywhere for the 25mins that I let it go for. I think the problem is the onboard video from Intel. GMA x4500 g41...Now installing re-installing 9.04.

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> Now installing re-installing 9.04.

In your original post you said "This is a live CD install"... So are you installing this to your HD? Have you tried just running off the live CD?

---

### Post by gaspros on 2010-03-22
I have tried both ways to run 9.10. Live CD will not boot for me install will not install for me.
Not in x64 nor x86 CD's. I did not try alternate ISO. 
Sucess came with 9.04 live CD and then I installed it to the hard disk and it seemed ok. 
When it told me that I could upgrade I went ahead and did this. Then it was on for young and old from there.
Currently re-installing 9.04 clean. 9.04 does boot into live CD but I need it to persist and be able to install xbmc and VLC for shows. So I am installing 9.04 again.
Any suggestions? (Other than never upgrade the little bugger if it works!)

---

### Post by Zlatan on 2010-03-22
> **Alias1407 said:**
> Karmic Koala (Ubuntu 9.10) was the release that changed Ubuntu, you could say that Karmic Koala (in my opinion) was the worst Ubuntu distro ever released. Sure it looked pretty but didn't function as an OS. My suggestion is run a 32-bit 9.04 version of Ubuntu and don't upgrade to the newer OS. I'm running that right now and it's absolutely fantastic.

karmic worst os? have you tried warthy wardog?
and are you really sure karmic does not function when it does for me?

---

### Post by gaspros on 2010-03-22
Sounds like it to me as well. I just re-installed 9.04 and then installed VLC and started playing a video. It worked for about 5 seconds and then hung and then rebooted me back to the login screen. or as you say x windows restarted after a crash.
So what to do next I wonder?

---

### Post by Calash on 2010-03-22
My vote is bad video card.  If you do get Windows installed, run some tests on it before trusting the card.  

If you have another card lying around try putting that one in and see if the LiveCD is any more stable.

---

### Post by sylaryn on 2010-03-22
I think you'll have to do some tweaking for your graphics card. I'm old to linux, but have spent most of my linux life on the command-line without X-Windows, so my knowledge of vid-card tuning is limited. From what I can see, your card should work fine. There's some info here, but it may get a bit complicated for someone who hasn't been doing this for a while... [http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=3](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=3)

---

### Post by gaspros on 2010-03-22
So thats with a clean install of 9.04 The update manager was bugging me again and I took a look through the lengthy list. There is an update called xserver-xorg-video-intel. I am looking to apply that.
I have version 2.6.3-oubuntu9 and it upgrades to version 9.3. 
Is there a way to see what actually is causing the crash in some log somewhere when x server reboots?

---

### Post by Endolith on 2010-03-22
Just get Windows 7.  :)  It's expensive, but think how much you'll save in headache medicine.

---

### Post by ythe1300 on 2010-03-22
> **gaspros said:**
> Sounds like it to me as well. I just re-installed 9.04 and then installed VLC and started playing a video. It worked for about 5 seconds and then hung and then rebooted me back to the login screen. or as you say x windows restarted after a crash.
So what to do next I wonder?

Sounds like a system stability issues.

 Is the system overclocked? If so go into the BIOS and set everything to default and then try again.
I would also recommend checking the RAM / CPU voltage and frequencies / CAS  I have had ASRock motherboards do some stupid things with RAM timings. 

( Also sometimes you need to run Memtest for more that 25min to find RAM stability issues. ;) )

GoodLuck :)

---

### Post by gaspros on 2010-03-22
OK two things come to mind. With the information from the link you provided. The viseo is the HD version which has a HDMI slot. The next is they talk about the latest DDX and Mesa drivers (which I will have to go and look for) but that was back in 2008.
The journey continues for now....

---

### Post by sylaryn on 2010-03-22
> **Calash said:**
> My vote is bad video card.  If you do get Windows installed, run some tests on it before trusting the card.  

If you have another card lying around try putting that one in and see if the LiveCD is any more stable.

Or go out and buy a cheap NVidia card. They work great.

> **gaspros said:**
> So thats with a clean install of 9.04 The update manager was bugging me again and I took a look through the lengthy list. There is an update called xserver-xorg-video-intel. I am looking to apply that.
I have version 2.6.3-oubuntu9 and it upgrades to version 9.3. 
Is there a way to see what actually is causing the crash in some log somewhere when x server reboots?

I would definitely try the xserver-xorg-video-intel update. As for x-server logs, they should be in /var/logs. I'm sure there's some sort of GUI log viewer, but again, X-windows is not my strong point.

---

### Post by gaspros on 2010-03-22
ythe: System is new and not overclocked at all. Everything is as it was deleivered. I have not changed anything in the BIOS.

---

### Post by theozzlives on 2010-03-22
Hmmmmm... what I would do is probably try the Lucid Beta 1. When partitioning, I would choose "Manual". delete all partitions and partition as follows:

10-20 GB / ext4 (this is where the OS and programs will go)
2 -4 GB swap
all the rest make /home ext4 (this is your data and settings)

If you wanna play it safe, go with Jaunty (9.04) with the same partitioning scheme. That way if you do re-install you only have to format / and you get to keep all your documents and settings.

EDIT: With only 2 GB RAM, you don't need the 64 bit version. Wait til you upgrade to 4 GB.

---

### Post by gaspros on 2010-03-22
Calash: I dont happen to have any other video cards lying around that will fit the motherboard. Current video is onboard video. It sucks to have to go out and buy another video card especially when it could just need some driver update or some tweak somewhere

---

### Post by sylaryn on 2010-03-22
If you go to "System > Administration > Log File Viewer" you'll see the Xorg log there. There may be something helpful in there.

---

### Post by Calash on 2010-03-22
> **gaspros said:**
> Calash: I dont happen to have any other video cards lying around that will fit the motherboard. Current video is onboard video. It sucks to have to go out and buy another video card especially when it could just need some driver update or some tweak somewhere

In my experience the LiveCD is very stable.   I have thrown a ton of different hardware at it and the only time I run into issues is when there is a failing hardware component, or something radically different (IE, PPC hardware)

Your running an Intel board, a common one at that.  There is not much fancy about Intel video drivers.  There is no real reason it should be throwing these types of errors at you.  That is the reason I am suggesting investigating the hardware for failures.  

I would not suggest going out and buying a new card until you know what is causing the problem.  However it may be worth some time to see if there is some form of diagnostic disk you could run on the systemboard to rule out a failure.  I would check the vendor site that the board is branded to, or the Intel site if there is none.

---

### Post by gaspros on 2010-03-22
OK, I forced another crash by playing a show and these are the logs that were updated at that point. I dont know which one would be useful. Couldnt upload the logs, I think I need to zip them. So off I go to do that. Whats the linux equivalent of 7zip?

---

### Post by gaspros on 2010-03-22
Thanks Calash I will look into the hardware side later on. Cant do anything about it right now anyway.

---

### Post by gaspros on 2010-03-22
Idiot right: 7zip was sitting in the list of add programs.

---

### Post by sylaryn on 2010-03-22
You can just use 'zip' or 'gzip'... both work fine. gzip is probably the most common linux zip utility... oh, and there's also bzip. 'zip' is the same algorithm as the native 'zip' in windows xp and newer, so if you wanted to share files with windoze users, that's the way you would go.

---

### Post by gaspros on 2010-03-22
Logs are here

---

### Post by gaspros on 2010-03-22
I installed 7zip and then couldnt find it anywhere but just right clicked on the files after copying them to my document folder and created the zip that way. Information for other newbies like me in case somebody else is having this issue.

---

### Post by gaspros on 2010-03-22
[theozzlives]("http://ubuntuforums.org/member.php?u=420456"): the problem with anything above 9.04 is that they just dont even let me get to the partitioning part. The liveCD doesnt even fully bootup. 9.04 is my only choice with getting to the partition part.

---

### Post by gaspros on 2010-03-22
I may just get more RAM if I need it later on so thats why I thought x64. But not for now. Just trying to get a stable 9.04 working.

---

### Post by sylaryn on 2010-03-22
```
Mar 23 01:02:58 saspros-desktop gdm[2614]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

```This is what's causing your X to crash... investigating...

---

### Post by gaspros on 2010-03-22
Mar 23 01:37:41 saspros-desktop pulseaudio[5694]: pid.c: Stale PID file, overwriting.
Mar 23 01:37:41 saspros-desktop pulseaudio[5694]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Mar 23 01:52:24 saspros-desktop syslogd 1.5.0#5ubuntu3: restart.

Found this in messages. Does it mean anything to anyone. 1:37 is when the last crash occurred

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> Mar 23 01:37:41 saspros-desktop pulseaudio[5694]: pid.c: Stale PID file, overwriting.
Mar 23 01:37:41 saspros-desktop pulseaudio[5694]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Mar 23 01:52:24 saspros-desktop syslogd 1.5.0#5ubuntu3: restart.

Found this in messages. Does it mean anything to anyone. 1:37 is when the last crash occurred
I think those messages are just fallout from the crash... as for the gdm_slave_xioerror_handler it seems it's a generic message saying X crashed for some reason... but it could be anything!

So I know this has been asked already, but have you tried the 10.04 beta? If not, please try it Live (don't install to HD) and see what happens.

---

### Post by Chris_cur on 2010-03-22
I could not get 9.10 working for me, and I tried many different work arounds. I had the exact issue that you posted originally then once I got it "fixed", I couldn't change the brightness and it was stuck at DIM AS HECK. I nearly tor my eyes out. I went back to 9.04 and am happy.

Glad every one is trying to help you out.

---

### Post by sylaryn on 2010-03-22
So I know this has been asked already, but have you tried the 10.04 beta? If not, please try it Live (don't install to HD) and see what happens.[/QUOTE]
Did you try the xserver-xorg-video-intel update? If not, please try it.

Also, do you see any xserver updates in the update list? If so, please install just those and see what happens.

---

### Post by gaspros on 2010-03-22
Thanks for all of your help people: [sylaryn]("http://ubuntuforums.org/member.php?u=1040701"): I have tried 10.04beta the desktop x86 version, tried as a liveCD. I will do it again now if you think it will help? I can tell you exactly whats happenning as it goes.
I have a windows PC next to the newbie. So I can post and boot together

---

### Post by sylaryn on 2010-03-22
sorry for going in multiple directions here, but if you haven't rebooted already, try the updates i mentioned in the previous post first please.

---

### Post by Calash on 2010-03-22
> **sylaryn said:**
> ```
Mar 23 01:02:58 saspros-desktop gdm[2614]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

```This is what's causing your X to crash... investigating...


Here is a bug report that seems to match what we are seeing here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306)

The Intel drivers are also talked about.

---

### Post by gaspros on 2010-03-22
OK updates first. Perhaps this will help in the meantime. Its the post from when I tried 10.04

Post19 from way back on page 2 
OK I burnt the 10.4beta and rebooted with it and I get the  udevd-work[95]: '/sbin/modprobe -b pci: gooblegoop'   unexpected exit  with status 0x009 error. 

Wow how boring is this!

---

### Post by gaspros on 2010-03-22
Just to confirm: The updates were to the xserver-xorg-video-intel anything else.
Sorry it took so long to respond I was reading the bug report calash linked to.

---

### Post by sylaryn on 2010-03-22
> **Calash said:**
> Here is a bug report that seems to match what we are seeing here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306)

The Intel drivers are also talked about.

I think you may be on to something here Calash...

gaspros, I recommend you turn on Backtraces and cause the crash again. Then submit the data to bug #350306 (linked above). To turn on backtraces, run the following command from a terminal window:
```
sudo service apport start force_start=1
```Once it's done, it will prompt you to submit it and take you to the bug forum where you can choose the bug to report it against.

---

### Post by gaspros on 2010-03-22
From the bug report it looks like the 9.3 version of the xserver-xorg-video-intel has not solved the problem.

So should I update or not?

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> Just to confirm: The updates were to the xserver-xorg-video-intel anything else.
Sorry it took so long to respond I was reading the bug report calash linked to.

No problem... I was suggesting you do any xserver updates listed. I think it may still be a good idea to do so before submitting the bug report. The last thing the developer community needs is reports on bugs already fixed ;)

---

### Post by gaspros on 2010-03-22
ok backtraces now one,  now just waiting for the crash, takes longer in some shows.

---

### Post by gaspros on 2010-03-22
It crashed and it did not prompt me to do anything. I did type in the sudo command
????

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> It crashed and it did not prompt me to do anything. I did type in the sudo command
????
sorry. Do you see a little orange splash with an exclamation mark in it on the top bar on the right? If you do, please click it.

---

### Post by gaspros on 2010-03-22
Trying it all again. I have applied the xserver update and the intel one was the only one in the update manager list. Lots more in synaptic though.

---

### Post by gaspros on 2010-03-22
Nope, no orange anything on the right. Just the shutdown button.
The whole x system reboots after the crash would that make it go away?

---

### Post by sylaryn on 2010-03-22
> **gaspros said:**
> Nope, no orange anything on the right. Just the shutdown button.
The whole x system reboots after the crash would that make it go away?
It shouldn't make it go away... in fact, you may have to log out and log back in to get the crash report. More info here: [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by gaspros on 2010-03-22
OK I definately do not get that symbol described in the link and I have just checked /var/crash and there is nothing in there. I am going to go back and read the link more thoroughly shortly but is there any chance of a typo or something in the command you provided to me?

---

### Post by sylaryn on 2010-03-22
i copied and pasted from that same link!

---

### Post by gaspros on 2010-03-22
Dammit, not my day today. I redid it all again. 
Went into terminal:
sudo service apport start force_start=1

Then typed quit to get out of terminal
Then ran the show with VLC 

X server crashed and logged me back in.

No symbol and no crash report.

What now. It talks about permanently enabling it.

---

### Post by gaspros on 2010-03-22
I just did the same thing. I copied and pasted it from the link

sudo service apport start force_start=1

Nothing after the crash!

---

### Post by sylaryn on 2010-03-22
Not quite sure. You can just leave the terminal open and minimize it or something. But i doubt that closing it turned off Apport... it's a service after all. Maybe try the 10.4 Live CD and see how that goes :) (sometimes it helps to change it up a bit!)

---

### Post by gaspros on 2010-03-22
OK I am going to use the perminent command

---

### Post by gaspros on 2010-03-22
Yep tried it leaving the terminal open as well.
Now tried it with the permanent command as well and again nothing.

whats a guy gotta do to get a crash report.

---

### Post by gaspros on 2010-03-22
Livecd in and booting

---

### Post by gaspros on 2010-03-22
purple flash screen

---

### Post by gaspros on 2010-03-22
udevd-work[92]: '/sbin/modprobe -b pci: v00008086d.......' unexpected exit with status error

---

### Post by sylaryn on 2010-03-22
I admire your persistence :)

---

### Post by gaspros on 2010-03-22
Seems to have moved on a bit and is now on a 134.220502 call trace:

---

### Post by gaspros on 2010-03-22
Damn thing wont beat me.

---

### Post by gaspros on 2010-03-22
199.7165021 call trace

Its taking forever but it seems to be doing something just so imperceptably slowly that I normally would not have noticed the change?

It just keeps stalling

---

### Post by gaspros on 2010-03-22
396.212502 call trace:

---

### Post by gaspros on 2010-03-22
do you think its looping slowly?

---

### Post by gaspros on 2010-03-22
? i915_driver_open
mutex_lock
drm_open_helper
drm_open
? cdev_get
drm_stub_open
chrdev_open
__dentry_open
?security_inode_permission

Only halfway down the list: Is this stuff crapola or uselful in someway?

---

### Post by gaspros on 2010-03-22
I think its getting nowhere.
Any final suggestions
Its 3:18 in the morning here and I have work tomorrow

---

### Post by sylaryn on 2010-03-22
I have no idea. It sounds to me like it's having some serious issues with one of your hardware components. Unfortunately, this is wayyy beyond my abilities. :(

---

### Post by sylaryn on 2010-03-22
Oh lord! Get some sleep! I guess this means back to Windoze for you? Perhaps the final release of 10.4 may prove more successful for you. Whichever way you, good luck!

---

### Post by gaspros on 2010-03-22
Great, Well thanks for your help and time. Much appreciated.
I am off to bed now.

Belated thanks to evryone lese as well.

Man what a maraton. 

Thanks again

---

### Post by gaspros on 2010-03-24
Well 2 days later after the 5 hour marathon and I have some spare time to try to sort out this problem.
Can anybody out there help me?

---

### Post by gaspros on 2010-03-28
I still have this as an error but once I managed to load up Karmic it turns out that this error relates to the onboard sound. At least now I have Karmic loading.

---

### Post by gaspros on 2010-03-28
The way I got Karmic to load much about with my BIOS settings. There were various settings in there for setting the primary graphics adapter and there was a setting to change the DRAM frequency as well.
Dont know what did it but once it started to work I stopped fiddling in there.

---

### Post by MisFitt on 2010-03-28
> **gaspros said:**
> I have tried both ways to run 9.10. Live CD will not boot for me install will not install for me.
Not in x64 nor x86 CD's. I did not try alternate ISO. 
Sucess came with 9.04 live CD and then I installed it to the hard disk and it seemed ok. 
When it told me that I could upgrade I went ahead and did this. Then it was on for young and old from there.
Currently re-installing 9.04 clean. 9.04 does boot into live CD but I need it to persist and be able to install xbmc and VLC for shows. So I am installing 9.04 again.
Any suggestions? (Other than never upgrade the little bugger if it works!)  

Hi,sorry about your tribulations here but just wanted to let you know(though I'm having hard drive probs,worn out)
9.10 was no go for me,too many problems so I went back to 9.04 32 bit and then tried 9.04 64 bit and it's worth pursuing,it's amazing and will use your ram and resources,stick with it and by the time the fantastic 10.04's released you'll be flying.
I recommend you stick with Jaunty for the time being!Forget Karmic for now-just my opinion and I'm reasonably new-ish.
The forum's the most supportive problem solving,friendly place I've ever come across,true!:D
ps-don't go back to M$-you will miss out BIG time!
and you've probably been told to do a clean install rather than upgrade because of the 3ext/4ext differences

---

### Post by gaspros on 2010-03-28
Just remembered that I also had to select low graphics mode on the install to get Xserver to run and be displayed on the monitor. I just have a soundcard not being installed recognised now. So I am going to leave this thread alone and head off to the Hardware section for help later on after I have read everything I can on the soundcard issue.

---

### Post by viper250 on 2010-03-28
when you are building a new system the first thing I suggest is checking the hardware compatability list for the distro you are chosing ( I have found that some hardware was designed to be used with windows only)

sata drives can cause some installation issues depending on the drives mode setting in bios
I have had to set the mode to IDE on some newer laptops in order to install linux.

some of what you were describing sounds a lot like a kernel panic but you are making headway with it.
 installing a distro with new hardware can be a gamble and you are showing the dedication of a true linux user.
so don't give up hope yet
At home and work I use linux (pclinuxos)for my own systems but have to use winhosed for the plants control systems(and when you have to spend 1,200.00 for a control program linux looks a lot better when you can find a compatible driver and emulator)
there are other forums as well I am a member of a few of them

---

### Post by jaycee23 on 2010-03-28
Every respect to OP. What persistence.

Just my opinion  - stick with the distro. I am only a recent convert but way more fun than windows - still lots of things I need to try like editing my high def home vids on Ubuntu but it's a lot of fun and this place is great for help and sarcasm!

Got Ubuntu working on my laptop and new desktop (both are dual boots with Windows 7).

I have my old desktop which I will also convert to Ubuntu when I have the time. 
Always new issues with new hardware but so far I've been able to get them all sorted  :p

---

### Post by waynefoutz on 2010-03-28
gaspros, if you don't want to change the video card, which is most likely the issue, then I say just run 9.04 if that's what works. My primary laptop has ATI video integrated on the motherboard that I can't change. It ran 8.10 flawlessly with the ATI drivers, then 9.04 came out and broke everything. 9.10 with open source drivers got me back up and running, but with no Opengl. I ran that for months, patiently waiting  for 10.04 to come out. I got tired of waiting and put the beta on this weekend. I'm not impressed. So screw it. I'm back on 8.10 and that's where it's going to stay. Who says you have to run the latest version? I say stick with what works. 

The only issue you are going to have is when Jaunty, (9.04) hits the end of life date 6 months from now, then your repositories stop working and you'll stop getting updates from Canonical. A quick edit to your /etc/apt/sources.list file will get the repositories working again. [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

In my opinion, Ubuntu is a great Linux distro, but it's not so great if you want to keep things on the cutting edge without buying the latest hardware to match. On my laptop I can't upgrade the video, so I'm stuck. There are other distros out there that don't come out with a new version every six months, if you want something more stable. Debian Lenny and CentOS come to mind. I've tried both, but I keep going back to my 2 year old Ubuntu 8.10, because everything just works on my machine.

---

