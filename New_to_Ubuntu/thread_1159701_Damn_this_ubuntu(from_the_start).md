---
title: "Damn this ubuntu(from the start)"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by daveedking on 2009-05-14
i can't believe it didnt boot for me .. i downloaded the 9.4 version/burned the .iso image/installed the cd/but it wont do anything...

 so i tryed to uninstall 2 reinstall and i get an error ..now i have these ubuntu files i cant delete to even retry...(THE ERROR)  :  OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso

tHANX and i hope some 1 can help
Da-VeeD
/\ iM ON VISTA Home premium /\

---

### Post by AndThenWhat on 2009-05-14
I'm confused. You can't remove the .iso file from your C: drive on Windows?

---

### Post by mgranet on 2009-05-14
Are you running Ubuntu in Wubi?

---

### Post by bacardiandwatermelon on 2009-05-15
Do you have the iso mounted in windows e.g. alcohol120? You will have to unmount it before you can delete the file as it is in use. What happens when you try and boot into ubuntu?

---

### Post by daveedking on 2009-05-15
i didn't mount the .iso image .. i burned a cd with nero... 
today i booted my pc after not being able 2 uninstall yesteday .and.wouldnt u know ..i was able 2 uninstall. thats 1 of those bugs in windows the file was floating around in some unwanted mannor, i hear ubuntu wont be so buggy...
  Ok its 4 pm. now and before i try 2 reinstall ubuntu ..again.. some very simple qusetions.
1. do i have 2 run ubuntu from the drive that vista is running on?(for exaple my lap top has 2 internal drives of 111 gigz each.. C: drive and D: drive ..vista is on the C: drive and nothing at all is on my D: drive i have never used it ..i want Ubuntu on my D: drive and do  i have 2 partition it before i even install Ubuntu ?..)
2.  also since i had no sucsess instaling V.9.4 sholud i try the older version 8* u have on the main site and upgrade?
---------------------------------------------------------------------------------------------------
  Im waiting for u guys before i even try .so please help ,and thanx for the quick replies..
DA-VeeD

---

### Post by neu2buntu on 2009-05-15
youy wont need to do anything to your drive to install ubuntu.... look at your bios settings and make sure you have boot from cdrom drive listed before your harddrive!!!

---

### Post by s3a on 2009-05-15
By the way, if you want stability; install Ubuntu **8.04** LTS.

---

### Post by neu2buntu on 2009-05-15
> **s3a said:**
> By the way, if you want stability; install Ubuntu **8.04** LTS.
true.....8.04 is well stable and also long term support!!!   but i always upgrade to the newest version and suffer all the bugs (especially audio)

---

### Post by chriskin on 2009-05-15
> **neu2buntu said:**
> true.....8.04 is well stable and also long term support!!!   but i always upgrade to the newest version and suffer all the bugs (especially audio)

i have to add here that audio on 8.04 was problematic for me on more than 5 computers , while on 9.04 everything works perfectly

---

### Post by neu2buntu on 2009-05-15
> **chriskin said:**
> i have to add here that audio on 8.04 was problematic for me on more than 5 computers , while on 9.04 everything works perfectly
maybe it is because i am running pulse-module-jack through pulseaudio (so that i can record/play/layer any audio (ubuntu-studio) that is giving me audio problems. but generally before i started modifying files audio was good on all releases of ubuntu for me (8.04 8.10 9.04) i should have made this clear before postingt!!!

---

### Post by MontelEdwards on 2009-05-15
uhhh, 
are you in Windows?
and there is no reason to say "damn ubuntu"
that is kind of rude to say that on a forum that helps you. for free

---

### Post by Didius Falco on 2009-05-15
> **daveedking said:**
> i didn't mount the .iso image .. i burned a cd with nero... 
today i booted my pc after not being able 2 uninstall yesteday .and.wouldnt u know ..i was able 2 uninstall. thats 1 of those bugs in windows the file was floating around in some unwanted mannor, i hear ubuntu wont be so buggy...
  Ok its 4 pm. now and before i try 2 reinstall ubuntu ..again.. some very simple qusetions.
1. do i have 2 run ubuntu from the drive that vista is running on?(for exaple my lap top has 2 internal drives of 111 gigz each.. C: drive and D: drive ..vista is on the C: drive and nothing at all is on my D: drive i have never used it ..i want Ubuntu on my D: drive and do  i have 2 partition it before i even install Ubuntu ?..)
2.  also since i had no sucsess instaling V.9.4 sholud i try the older version 8* u have on the main site and upgrade?
---------------------------------------------------------------------------------------------------
  Im waiting for u guys before i even try .so please help ,and thanx for the quick replies..
DA-VeeD

Hi, and welcome to the Ubuntu forums.

1. No, you can install Ubuntu to the second drive and it will run quite well. You don't have to partition it yourself, but if you are comfortable working with partitions, I'd recommend it. 

If you are comfortable with doing your own partitioning, let us know when you post your system specs and you'll get plenty of advice.

Otherwise, I'd suggest you choose the **Manual (advanced) **option when the installer gets to the Partitioner. That will let you point the partitioner to
the second hard drive.

2. What version I'd recommend would largely depend on your system specs, particularly your video card. If you would post those, it would help a lot in making a recommendation.


Regards,

Didius

---

### Post by Bölvaður on 2009-05-15
Ubuntu is not installed from within windows. So you'll have to change the bios boot order in order to have cd above hard disk drives in there.

I urge you to prepare the install by making partitions either from windows with special programs or from the live cd (the cd you have).

As a beginner that is just checking things out you will only need 2 partitions.
1 Swap partition that is of equally size as your RAM and 1 partition that holds everything else.

This can be tricky without the help of Google and Ubuntu forum search ;)


Ubuntu 8.10 has become very stable and has fewer bugs than the last long term service release (8.04) I am currently using it and will recommend it over 9.04 for computers with intel graphics cards.

---

### Post by Ms_Angel_D on 2009-05-15
I suggest having a look at this [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) it will help you have a better understanding of How to install ubuntu.

---

### Post by daveedking on 2009-05-15
> **mgranet said:**
> Are you running Ubuntu in Wubi?
   i just download and burned the 8.04 version 2 a cd...what do u mean when u say if im running ubuntu in wubi... ???  dosent the cd i just burned from the main page download section automaticaly take care of the full installation ..?? 

  I just downloaded wubi.. so do i need 2 install this first before ubuntu...could this have been the problem??
----------------  AND THANX FOR THE VERY FAST REPLIES.. --------------------

---

### Post by AndThenWhat on 2009-05-15
No sorry for the confusion, but Wubi is just one of the ways you can install Ubuntu.  With Wubi you install Ubuntu like it is a Windows program so that you can easily remove it from Add/Remove Programs.  The CD you burned is also a very easy way to install Ubuntu.  Just pop in the CD, restart your computer, and select to use the D: hard drive as the place you want to install Ubuntu.

Basically, no you do not need Wubi because you have the CD.

---

### Post by Don1500 on 2009-05-15
17 Just a quicky....> "select to use the D: hard drive as the place you want to install Ubuntu." 

It will not be called "D:/" it will be called something like "sdb" or "sdc" (your C:/ should be "sda") so when you get to the partitioning section of the install you should know what you're looking for.

And when it asks for your mount point it want's to know where to put your ROOT Directory. This would be that sdb I mentioned. just put "/" (no quotes) in that box. Put a check in the format box and then use the ext3 format style. (I heard that ext4 runs faster but it is somewhat buggy right now)

---

### Post by anewguy on 2009-05-15
And another quick note:  you will want to choose the manual option for disk partitioning.  You will see both of your drives there so you know which one you are working on, but most importantly since this is a laptop you will probably need a swap size of 2 times the size of your systems' physical memory plus just a little overhead if you plan to hibernate the laptop while in Ubuntu.

If you need ANY help at all, please post back!  This is the beginner's forum, you are a beginner, and we want you to feel free to ask for any help you may need - don't worry if it seems like a "dumb" question, because there is no such thing as a dumb question.  We want to make your experience with Ubuntu as nice as ours is.

Dave :)

---

### Post by daveedking on 2009-05-16
Im in.. im looking at the wounderfull orange background...i tryed  installing the 9.04 version before and it wouldnt install .. i finally installed with wubi... im now runnin the 9.o4 version and Ubuntu seems better and faster than Windows  already... thanx....
now im trying to add vlc ...i have taken the path System/Administration/software sources/thirdparty software/ add and the codes that i use say that its out of date ..can someone give me the right Repository code for vlc so i can play vlc as my flash player in firefox..  (2days noobs R 2morrows programers) DA-VeeD
  I just dloaded this vlc 0.9.9a.tar.bz2

---

### Post by cariboo on 2009-05-16
I would suggest you use System-->Administration-->Synaptic Package Manager to install packages. That way all the dependencies are met and programs install properly.

---

### Post by daveedking on 2009-05-16
> **cariboo907 said:**
> I would suggest you use System-->Administration-->Synaptic Package Manager to install packages. That way all the dependencies are met and programs install properly.
   Synaptic Package Manager shows me a big list of packages do i check them all 1 by 1 ..i cant seem 2 see a select all tool ?.. and if i press that little arrow down it fills in all the check boxes in green ..what does that mean?

---

### Post by neu2buntu on 2009-05-16
> **daveedking said:**
> Im in.. im looking at the wounderfull orange background...i tryed  installing the 9.04 version before and it wouldnt install .. i finally installed with wubi... im now runnin the 9.o4 version and Ubuntu seems better and faster than Windows  already... thanx....
now im trying to add vlc ...i have taken the path System/Administration/software sources/thirdparty software/ add and the codes that i use say that its out of date ..can someone give me the right Repository code for vlc so i can play vlc as my flash player in firefox..  (2days noobs R 2morrows programers) DA-VeeD
  I just dloaded this vlc 0.9.9a.tar.bz2
how did you get your problem sorted....for future users? what worked for you?

---

### Post by daveedking on 2009-05-16
> **neu2buntu said:**
> how did you get your problem sorted....for future users? What worked for you?
"installing using wubi worked for me"

---

### Post by cariboo on 2009-05-16
Use the search button to find packages that you need for instance if you were looking for a backup program, click the search button and type backup in the search box and click search. Synaptic will list all the backup programs for you. 

I wouldn't install everything listed in synaptic, as there are over 40,000 packages listed. Not all of them are programs, but a large majority are.

---

### Post by daveedking on 2009-05-16
ok i just installed 4 packets ...Videolan-doc ,vls,vlc-dbg and vlc data ..i still cant see flash on youtube and still no vlc icon in my applicatios video tab ?? what 2 do?? it sais im missing a public key when i go 2 update manager for videolan  and what is the sudo menu where is it ..am i looking right at it ??.............ok i added the vlc media player 2 my apps i just had to add it 2 the application menu after i installed the 4 packets..and now i can open my videos in vlc but i still cant stream in firefox.... help !!

---

### Post by anewguy on 2009-05-16
As Cariboo907 mentioned, the recommended way of installing anything in Ubuntu is going through the package manager first.  It "knows" the other things that the package depends on to run (called dependencies) and automatically flags those for installation with the package.  Flash is in synaptic package manager, and your best bet is to install it from there.

VLC is also in synaptic, and should be installed from there if not already installed.  One of the things you will see (if I remember correctly) is a package that shows in the list with VLC (always use the search function and review all that are returned) is one to work with Firefox.

I tried swf and had no luck.  I had to uninstall it (via the package manager) and install flash (via the package manager) instead.  I have also installed VLC and a bunch of things to go with it, and all of the gstreamer stuff (good, bad, ugly).  I don't have a problem with any videos now (except ABC.COM, which for some reason wants us to use a player that is MS-specific).

So, as a newbie, remember -> always install from synaptic package manager unless the package isn't found.  Sometimes you need to add a repository source (a collection of programs) in order to install via package manager - this is still the preferred method.  At some point you may use apt-get at the command line - just remember that with it you can use build-dep to include the packages dependencies.

Dave :)

---

### Post by lisati on 2009-05-16
An alternative to "synaptic" that is sometimes easier to use for new Ubuntu users is "Add/Remove Software": it can be found on the "Applications" menu. I find myself using it more often than Synaptic, even though I've been using Ubuntu for something like two years!

Don't worry too much if this seems confusing: the advice so far is still good.

---

### Post by daveedking on 2009-05-16
I couldn't get the VLC flash player plugin for Firefox to work so i installed the Adobe flash player plugin for Firefox and sure enough it worked... now i can look at all these apps and packets that are provided (love that open source) 
anyway .... Ubuntu is running great ,flash in mozilla is fine now time 2 customize right..
/any Dj program like ableton live or virtual dj for ubuntu ??
----------------------------------------------------------------------------------------------------------------------------------- 
Last beginner questions...
1. how 2 raise the screen brightness?( my screen goes dark sometimes ,not black it just dims by itself..is this a bug?
2. i have an older Toshiba Satelite 1 gig Ram and it had xp Pro on it..but wait..the thing is that it wont boot , infected with viruses and it wont boot past the xp splash screen...So can i just put the .iso image that i burned with nero 2 the CD , into disc drive and boot like that ? even with  corrupted windows ..??

  Please answer these 2 questions are critical 2 me.......thanx and thanx .....DA-VeeD

---

### Post by anewguy on 2009-05-16
If your screen sometimes dims, perhaps to a grey tint, it is because the system is busy - it should come back on its own in a short time.

The LiveCd you used for installing should work fine on your laptop.  I would make a couple of suggestions before you start:

since you know the model number, etc., check the support site for Toshiba and see what the video is and what the wireless is.  Then using the search function on the forum search for things with your model and wireless and your model and video to see if there are any special things you may need to do to make it all work.  

Doing this homework ahead of time can have you prepared for knowing there will be some problems, so you don't feel frustrated, and you can hopefully already have a game plan for fixing those problems.  So much easier than going into it "blind".

Dave :)

---

### Post by daveedking on 2009-05-16
i cant get compiz configure to add the effects i want... im trying to get the infamous wobbly windows effect ... i have 3 gig ram and intel core 2 duo  acer aspire 5720 laptop...
since i couldnt figgure out the compiz  configure manager out i went ahead and installed compiz-fusion..and still no new effects... also since i installed fussion after compiz-configure manager will there be some type of conflict ?

---

### Post by mikewhatever on 2009-05-16
>  Damn this ubuntu(from the start)

Where is my troll picture?

Edit: This one will do. [http://upload.wikimedia.org/wikipedia/commons/8/8b/Troll1.JPG](http://upload.wikimedia.org/wikipedia/commons/8/8b/Troll1.JPG)

---

### Post by neu2buntu on 2009-05-16
> **daveedking said:**
> I couldn't get the VLC flash player plugin for Firefox to work so i installed the Adobe flash player plugin for Firefox and sure enough it worked... now i can look at all these apps and packets that are provided (love that open source) 
anyway .... Ubuntu is running great ,flash in mozilla is fine now time 2 customize right..
/any Dj program like ableton live or virtual dj for ubuntu ??
----------------------------------------------------------------------------------------------------------------------------------- 
Last beginner questions...
1. how 2 raise the screen brightness?( my screen goes dark sometimes ,not black it just dims by itself..is this a bug?
2. i have an older Toshiba Satelite 1 gig Ram and it had xp Pro on it..but wait..the thing is that it wont boot , infected with viruses and it wont boot past the xp splash screen...So can i just put the .iso image that i burned with nero 2 the CD , into disc drive and boot like that ? even with  corrupted windows ..??

  Please answer these 2 questions are critical 2 me.......thanx and thanx .....DA-VeeD


there are 2 programs that i know of for djing.... mixxx and djplay...there are probably more...and if you are creative you can install ubuntu-studio inside your normal ubuntu install.... look for "lmms" "ardour" "hydrogen" "rosegarden" "audacity" "rezound"    ubuntu is well set up for audio applications ,you can even install the demo of flstudio8 through wine!!!!

---

### Post by daveedking on 2009-05-16
cant find any driver in system /administration/hardware (no proprietary drives) ..i see alot of people have the very same problem .. im trying 2 get those wobbly windows..

---

### Post by waspbr on 2009-05-17
what is you video card? 
if u don't know, type this code into a terminal window (Applications>Acessories>Terminal)

```
lspci
```

copy the output and paste it here

---

### Post by daveedking on 2009-05-17
> **waspbr said:**
> what is you video card? 
if u don't know, type this code into a terminal window (Applications>Acessories>Terminal)

```
lspci
```copy the output and paste it here
daveedking@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
daveedking@ubuntu:~$ 
...Thanx for responding i was starting to feel abandoned,,,lol...........thanx

---

### Post by anewguy on 2009-05-17
You have the Intel 965 - there are posts in the forum for something about the Intel driver with 9.04 not working correctly, and that there was a notice about it in the 9.04 release notes.

Dave :)

---

### Post by mojolobo on 2009-05-17
9.04 works much better for , and my pc runs an AMD sempron (that old). No problems .
Firstly is the iso file corrupted , try downloading a new one. Or the cd.

Im new to this as well  , but no problems so far

---

### Post by daveedking on 2009-05-17
> **mojolobo said:**
> 9.04 works much better for , and my pc runs an AMD sempron (that old). No problems .
Firstly is the iso file corrupted , try downloading a new one. Or the cd.

Im new to this as well  , but no problems so far
   It not  appearing  2 be corrupted , im trying 2 load to sources list with repositories this line :[http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) and [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu)
and i get  this error  (   W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CE90D8983E731F79  )
  I removed the  removed xserver-xorg-video-i740 and actualy it was allredy and it was uninstalled by default...
---------------------------Y am i getting this error? where can i get the public key?--------------------------------
(DA-VeeD)

---

### Post by goldblattster on 2009-05-17
Like I say, I just don't understand those microsoft people anymore.

---

### Post by bonkadventure2 on 2009-05-17
I don't understand what you mean.

---

### Post by sandyd on 2009-05-17
ableton can run in a program called WINE

```

sudo apt-get install wine ubuntu-restricted-extras
 [wget http://winezeug.googlecode.com/svn/trunk/winetricks]("http://winezeug.googlecode.com/svn/trunk/winetricks")
sudo mv winetricks /usr/bin
sudo chmod 777 /usr/bin/winetricks
winetricks allfonts allcodecs fontfix

```then just run the ableton live installer....

p.s. forgot you were a newbie. Enter all of the stuff into Applications -> Accessories -> Terminal

EDIT: AHHHhhh.... wait a minute.... it actually doesn't work so well in WINE :(.... nvm.....
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113)

---

### Post by daveedking on 2009-05-17
I wanna give myself a full restart.. i avet put alot of codes in but i just wanna star new ...
How do i reset to factory default .. as if i just opened it for the first time / ??

---

### Post by sandyd on 2009-05-17
> **daveedking said:**
> I wanna give myself a full restart.. i avet put alot of codes in but i just wanna star new ...
How do i reset to factory default .. as if i just opened it for the first time / ??

reinstall is the fastest way
and don't worry. Everyone who starts using ubuntu reinstalls 3-4 times at the begnning...
i reinstalled 6 times....

---

### Post by daveedking on 2009-05-17
i uninstalled 9.04 and am now running the older 8 .version and everything looks  amazeing ..wow. great effects.. wobbl windows everything enabled ..now i can use this system... i think i love ubuntu ..

---

### Post by daveedking on 2009-05-17
> **carlee said:**
> ableton can run in a program called WINE

```

sudo apt-get install wine ubuntu-restricted-extras
 [wget http://winezeug.googlecode.com/svn/trunk/winetricks]("http://winezeug.googlecode.com/svn/trunk/winetricks")
sudo mv winetricks /usr/bin
sudo chmod 777 /usr/bin/winetricks
winetricks allfonts allcodecs fontfix

```then just run the ableton live installer....

p.s. forgot you were a newbie. Enter all of the stuff into Applications -> Accessories -> Terminal

EDIT: AHHHhhh.... wait a minute.... it actually doesn't work so well in WINE :(.... nvm.....
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113)

 so are u saying with those suddo codes i can install wine..?? i want 2 run  and work with wine since i  have so much windows stuff..

---

### Post by anewguy on 2009-05-17
as I mentioned in my previous post, the wobbly windows, etc., weren't working because of a bug in support of the Intel 965 in 9.04.  Going back to a previous version works because the bug is not there.

Dave :)

---

### Post by anewguy on 2009-05-17
Why don't you just install wine through the package manager??

dave :)

---

### Post by daveedking on 2009-05-18
I like Ubuntu better than windows.... i want 2 remove all Vista from my internal hard drive...actually another reason is because windows
[B]XXX
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/help-partitions.png[/IMG]
XXX
\/[would the Admins please erase this i posted in a new topic : [http://ubuntuforums.org/showthread.php?t=1163086]/\](http://ubuntuforums.org/showthread.php?t=1163086]/\)
[/B]

---

