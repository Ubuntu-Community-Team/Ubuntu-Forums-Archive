---
title: "belkin wirelesss-- a good laugh"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by degarb on 2009-12-30
I really know nothing, so this should give you all a good laugh.

I have a pcmcia belkin  I think drivers here [http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)

But there is no inf or exe to click to install!!!  That the Heck guys?   I am a windows user there is nothing in the documentation that makes any sense to a windows user

After 2 hours I figured out how to use the terminal and navigate to the extracted bz directory.  Then, followed the directions, but only got File couldn't something.  so no luck with the directions.  I have no idea what these file extensions are or mean.  

I don't see any ndiswrapper in the Ubuntu menus.  So cannot try that method.

I won't install until I can get vlc and the wireless working (only ethernet it has.)  So in a holding pattern.

---

### Post by halitech on 2009-12-30
to verify what driver you need, plug the device in and run
```
lspci
```
and post the output here.

Linux doesn't use exe files and typically doesn't use point and click for installs. 

As far as vlc, with the ethernet connection, open Synaptic (System - Admin - Synaptic) and search for vlc. you can also open a terminal and run
```
sudo apt-get install vlc
```
enter your password (you won't see it, just type it in and hit enter) and it will be installed.

---

### Post by SeaJayEmm on 2009-12-30
The first thing you need to do is update your ubuntu. You need to have an internet connection for this, hard wired into your router. Go to Applications > Accessories > terminal...type in sudo apt-get update. After this done post back with the make and model of your pcmcia card or the output from typing "lspci" in terminal.

---

### Post by Bucky Ball on 2009-12-30
After you have your updates from an ethernet cable connection go to System->Administration->Hardware Drivers. Anything there?

---

### Post by degarb on 2009-12-30
bcm4318 AIRFORCEONE 

i also tried  

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

but saying sudo not found ( got all files copied to cd and put on hard drive.)

I am perplexed and frankly turned off (unless I am missing something) that no one would write a batch file to do the typing, and install for the user.  Most people couldn't find the terminal window, nor navigate in it.  Most people mistype, or forget files even when well educated.  I am following directions and something is missing.

Also, I am wondering, can I even install a driver on a live cd?  Will it let me write to the /lib/ folder?

---

### Post by degarb on 2009-12-30
Looks like ndiswrapper would be far easier than installing with a standard linux means.  But on knoppix, vector, ndiswrapper is easy to find.  Seems hidden in Ubuntu.

---

### Post by Bucky Ball on 2009-12-30
> **Bucky Ball said:**
> After you have your updates from an ethernet cable connection go to System->Administration->Hardware Drivers. Anything there?

?

---

### Post by halitech on 2009-12-30
> **degarb said:**
> Looks like ndiswrapper would be far easier than installing with a standard linux means.  But on knoppix, vector, ndiswrapper is easy to find.  Seems hidden in Ubuntu.

far as I know, ndiswrapper is not installed by default and ndsiwrapper itself is a CLI app.. You can try getting it off the cd or connect a wired connection and open a terminal and run
```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
that will install ndiswrapper and the gui so you can find it in your menu

---

### Post by Bucky Ball on 2009-12-30
If bcm4318 that would indicate it is a Broadcom wireless chipset. Ndiswrapper isn't there because it is pretty well obsolete in Ubuntu and was never part of the OS by default anyway. This card should work with B43 driver and b43-fwcutter firmware after updates. 

ndiswrapper would be the last resort and the clumsiest way.

---

### Post by bkratz on 2009-12-30
> **bucky ball said:**
> if bcm4318 that would indicate it is a broadcom wireless chipset. Ndiswrapper isn't there because it is pretty well obsolete in ubuntu and was never part of the os by default anyway. This card should work with b43 driver and b43-fwcutter firmware after updates. 

Ndiswrapper would be the last resort and the clumsiest way.




+1

---

### Post by mechro on 2009-12-30
Instructions for "Installing Drivers for the bcm43xx Cards" is available from this Ubuntu Howto...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... may or may not work :|

---

### Post by degarb on 2009-12-31
> **mechro said:**
> Instructions for "Installing Drivers for the bcm43xx Cards" is available from this Ubuntu Howto...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... may or may not work :|

I tried all this and something isn't working--perhaps, persistant typos or blind spot in my linux knowledge to get this working. Can I do all this with only a live cd?  It this a problem with live cds?

I only have the wireless pcmcia for internet.  The notebook may have a built in modem, (I have 1 isp, no analog phone line, but two voip).

 I am thinking I need to tear up some storage areas to perhaps find the pcmcia wired card, but think wife threw it away and wonder if ubuntu will pick it up automatically.

Does linux do bat files to avoid typos? Beyond amazed that no bat files (what replaces exes or bat files in Linux?) are done to simplify user installs, I am wondering why ubuntu linux only looks for drivers via internet and not on a cd or harddrive folder?

---

### Post by bkratz on 2009-12-31
> **degarb said:**
> I tried all this and something isn't working--perhaps, persistant typos or blind spot in my linux knowledge to get this working. Can I do all this with only a live cd?  It this a problem with live cds?

I only have the wireless pcmcia for internet.  The notebook may have a built in modem, (I have 1 isp, no analog phone line, but two voip).

 I am thinking I need to tear up some storage areas to perhaps find the pcmcia wired card, but think wife threw it away and wonder if ubuntu will pick it up automatically.

Does linux do bat files to avoid typos? Beyond amazed that no bat files (what replaces exes or bat files in Linux?) are done to simplify user installs, I am wondering why ubuntu linux only looks for drivers via internet and not on a cd or harddrive folder?




Has anyone pointed at this one yet, a lot of people have had success.

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by darkeye123 on 2009-12-31
As much as installing drivers via Ndiswrapper can be clumsy and a last resort, IMHO it is far easier than installing drivers in the normal linux way.

My lspci:
```
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I am assuming you have the same wireless card, so here is how I got it to work:

I put in the Ubuntu Karmic Koala cd, and began to browse through it. (should be a cd on the desktop). I typed: ndis in the search box, and that returned a folder, ndisutils, ndiswrapper, and ndisgtk.

I installed ndisutils, then ndiswrapper, then ndisgtk. (just double click on the .deb and follow instructions)

Now you should see "Windows wireless drivers" in your menu. (Under administration I think) Click on that, and type in your password if necessary.

Now insert your wireless driver cd, the one that came with your card. (You could probably also find the drivers on the internet if you don't have the cd)

Click on Install New Driver, and browse through your wireless driver cd, until you locate bcmwl5.inf. Install that driver.

Now open up the terminal, and type: iwlist scanning

This should return a list of your surrounding networks.

At this point, all you have to do is configure your wireless card settings in the network manager.

---

### Post by 3rdalbum on 2009-12-31
> **degarb said:**
> Does linux do bat files to avoid typos?

We don't do "bat files". That's a Windows file type.

We do shell scripts where appropriate. Compiling a driver is not appropriate for a simple shell script, because if you don't have the dependencies (prerequisite packages) for compiling the software, then the script would simply fail.

> I am wondering why ubuntu linux only looks for drivers via internet and not on a cd or harddrive folder?

Ubuntu already comes with drivers for tens of thousands, possibly even hundreds of thousands of devices. Every one of these drivers is open-source; if they weren't, then they couldn't be distributed with Ubuntu.

Broadcom's wireless drivers are not open-source, so they must be obtained through a network connection. Usually this means plugging an Ethernet cable into your computer and router (or using a mobile broadband stick) and updating the package list, and then you can go to System > Administration > Hardware Drivers and install the driver with one click there.

How do Linux users cope with this? Well, they don't - they make sure that they buy one of the hundreds of wireless cards that are supported out-of-the-box on Ubuntu. Quite easy to find if you check out the hardware compatibility lists.

---

### Post by mechro on 2009-12-31
> **degarb said:**
> 
Does linux do bat files to avoid typos? Beyond amazed that no bat files (what replaces exes or bat files in Linux?) are done to simplify user installs, I am wondering why ubuntu linux only looks for drivers via internet and not on a cd or harddrive folder?

In most cases the hardware will just work but if the manufacturer is not bothered about or interested in supporting open source then problems will arise. In this case the Howto states *"Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) do provide the b43 drivers, but due to copyright reasons not the proprietary firmware which is required to run your card"*.

Sorry this is giving you a bad experience of Ubuntu but I'd say open source configuration of wireless networking isn't yet quite "up to speed". Personally, in order to avoid Windows, I'd look for a wired solution or perhaps change the wireless hardware.

---

### Post by degarb on 2009-12-31
> **bkratz said:**
> Has anyone pointed at this one yet, a lot of people have had success.

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

THis link got me excited. My sucess: xubuntu , no luck. With ubuntu 9.1 it looked like it worked but on reboot, nothing. I am wondering if it would work better if I had a real install.  But as I don't want a dead laptop with no functionality ( I will need to wipe off windows me to fit ubuntu.), I won't chance it.  Time: 2 hours, no luck.

I am excited to try darkeye123 solution.  Note, it will be running live; I don't see settings saved as in live Puppy linux cd, so unsure.  I will likely not be able to try this until after new year.

What are the script extensions in linux and why aren't they used more so end user don't need a 12 step to get simple things to work and risk typos?  Even in windows, if I need several complex dos lines, I alway write a batch script then click the bat script for editing reasons; these can be redistributed to save other end users time and failure. So, what replaces the exe in linux?  I hear talk of compiling, but don't see such a tool.  (In windows, usually compiling requires fileinstalls and directory structures that someone that not fluent in reading source of the language, so a typical user cannot compile for obvious of missing files. Assuming they have knowledge of a compiler in that specific language.)

---

### Post by degarb on 2009-12-31
> **mechro said:**
> In most cases the hardware will just work but if the manufacturer is not bothered about or interested in supporting open source then problems will arise. In this case the Howto states *"Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) do provide the b43 drivers, but due to copyright reasons not the proprietary firmware which is required to run your card"*.

Sorry this is giving you a bad experience of Ubuntu but I'd say open source configuration of wireless networking isn't yet quite "up to speed". Personally, in order to avoid Windows, I'd look for a wired solution or perhaps change the wireless hardware.

What is cost of a compatible wireless card. Logically, also, if I find the wired card and it works, this won't help me since the problematic card will not be present to trigger the download and install.  Would forcing the install through the snaptic manager, provide better results as any critical update would be accessible with wired card?

And why would it look like I was able to apply the install with the card off cd only but on reboot, it acts as if nothing happened.

Do I need to blacklist something, maybe?

---

### Post by degarb on 2009-12-31
Another note of my perplexity.  On snaptic installer, Ubuntu, allowed me to search cd.  Fine, but wouldn't telling it to search for a driver off jumpdrive, flash drive, or hard drive, make a ton more sense?  If I downloaded a driver on main computer, logically the easiest way to get to laptop is via jumpdrive. It just seems to me a big butt oversight.

---

### Post by degarb on 2009-12-31
> **darkeye123 said:**
> As much as installing drivers via Ndiswrapper can be clumsy and a last resort, IMHO it is far easier than installing drivers in the normal linux way.

My lspci:
```
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I am assuming you have the same wireless card, so here is how I got it to work:

I put in the Ubuntu Karmic Koala cd, and began to browse through it. (should be a cd on the desktop). I typed: ndis in the search box, and that returned a folder, ndisutils, ndiswrapper, and ndisgtk.

I installed ndisutils, then ndiswrapper, then ndisgtk. (just double click on the .deb and follow instructions)

Now you should see "Windows wireless drivers" in your menu. (Under administration I think) Click on that, and type in your password if necessary.

Now insert your wireless driver cd, the one that came with your card. (You could probably also find the drivers on the internet if you don't have the cd)

Click on Install New Driver, and browse through your wireless driver cd, until you locate bcmwl5.inf. Install that driver.

Now open up the terminal, and type: iwlist scanning

This should return a list of your surrounding networks.

At this point, all you have to do is configure your wireless card settings in the network manager.


I noticed on my live cd run, I cannot get the cd door open. Is there a trick to opening the cd tray?

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
You don't. A live environment locks the CD tray whilst it is running. This goes for any variant.... BTW, if your driver requires a reboot, you can't use it in a live situation.

---

### Post by mechro on 2009-12-31
> **degarb said:**
> What is cost of a compatible wireless card. Logically, also, if I find the wired card and it works, this won't help me since the problematic card will not be present to trigger the download and install.  Would forcing the install through the snaptic manager, provide better results as any critical update would be accessible with wired card?

And why would it look like I was able to apply the install with the card off cd only but on reboot, it acts as if nothing happened.

Do I need to blacklist something, maybe?

OK. I've re-read the thread and basically you want to make your wireless card work while using the LiveCD. Sorry, I don't think it can be done without remastering a Ubuntu LiveCD to include the configuration and drivers. Somebody may be able to do that but it ain't me.

Most of the thread replies, including mine :redface: seem to assume your trying to install your wireless drivers to a fully installed Ubuntu system... Come to think about it, even Windows assumes your sticking your drivers in a fully installed system and I'm buggered if I ever got a working internet connection from my XP disc!... j/k just defending Ubuntu :D

---

### Post by sandyd on 2009-12-31
oops
wrong thread

---

### Post by Locke_99GS on 2009-12-31
Shell scripts may or may not have extensions. When they do, it is often "*.sh*". Executable files can be anything with xattr set. A shell script can be executable, as can a python, php,or perl script. Compiled executabled usually have no extension, but many many non-executable files also have no extension. 

Most things are available as packages; "*.deb*" in our case. These are mostly available through a software repository. Some things aren't packaged and must be installed via a script or compiled manually. Compiling is very easy in Linux.


Linux isn't Windows.

---

### Post by degarb on 2010-01-03
> **Locke_99GS said:**
> Shell scripts may or may not have extensions. When they do, it is often "*.sh*". Executable files can be anything with xattr set. A shell script can be executable, as can a python, php,or perl script. Compiled executabled usually have no extension, but many many non-executable files also have no extension. 

Most things are available as packages; "*.deb*" in our case. These are mostly available through a software repository. Some things aren't packaged and must be installed via a script or compiled manually. Compiling is very easy in Linux.


Linux isn't Windows.

Thanks for these answers to one question.  These side questions are usually buried and forgotten in posts.

Compiling brings up questions.  I will research later once installed, unless someone has a favorite thread or url to post.

Now, back to installing.  I am in a catch 22.   The live xubuntu doesn't seem to be able to install the card with the steps that appear to work on the live Ubuntu (snaptic install...)  So to be safe I would install Ubuntu. But ubuntu while appearing to run fine on live cd, the specs doesn't appear to be able run on a 6 gig harddrive, like ubuntu can.   I will also need to double check cpu too (windows me is reporting 1.6 ghz while install cd reports 450 mhz. with 512 meg ram)  But no sluggishness on live ubuntu. Infact, it may be my imagination, but ubuntu seems to work more smoothly than the live xubuntu cd (thought this may be quality of the blank media.).

---

### Post by degarb on 2010-01-24
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

ME was giving me head aches and I saw you had a polite and responsive forum.  So,I thought I would wipe out my ME installation since the above thread makes sense, unlike the fwcutter solution which reads like goo.   ( I want a simple belkin-install.exe  not a 12 step program with vague parameters and steps and no clear method for getting onto stranded computer.)

I did the wipe, install, and snaptic install (verified chipset  )  rebooted, and no card showing up.   I want to throw up, since I don't understand why something so simple is so hard. (windows is never this hard to install.  Done scores and scores of them, which is why I want linux-just one that works out of box.) I got a brick. What can I do?  I don't have $40 to go out and buy a new card.

---

### Post by degarb on 2010-01-24
Is there something I need to turn on or uninstall?

---

### Post by degarb on 2010-01-24
What is procedure for buying a used pcmcia card?   Can I PLUG it in and see it light up.  Or plug in and reboot and see if it lights up.   Or do i need to print out a huge list and pray I see a match, and guess at chipset inside.

  I wiped my notebook and installed ubuntu. My belkin wireless g pcmcia card doesn't work. (no 98 to see chip set any more. )  I HAVE ONLY A CD drive or jump drive to install any drivers.  i DO NOT HAVE INTERNET NOR WILL UNTIL RESOLVED.  
 Unfortunately, installing it with snaptic manager  bcmwl-kernel-source did nothing to help.  Did I NEED TO UNinstall something first?

Has anyone a non official version of Ubuntu that will help, as I understand they could make it work from cd but choose not to because of licensing? Or compiled some exe or bat equivalent to install for us, since it is easier to fail (since the chances are most solutions WILL fail.) after 30 seconds of clicking some file than 30 minutes trying to follow 25 steps.

---

### Post by erictherev on 2010-01-24
I wish I could give you a simple solution.

I had similar issues with an old laptop of mine and a Belkin wireless card. What I can tell you is that you will most likely need to use ndiswrapper with windows drivers, unfortunately I never had a whole lot of luck with this. Eventually, I gave up on that laptop. (It was a piece of junk.) The real problem here is that Belkin doesn't make Linux drivers for their products.

The best advice I can offer is to search the forums thoroughly. Sorry I can't be of more help, but at least you know you're not alone in this predicament.

Hang in there and keep looking for an answer.

---

### Post by overdrank on 2010-01-24
Threads merged.

---

### Post by degarb on 2010-01-25
> **erictherev said:**
> I wish I could give you a simple solution.

I had similar issues with an old laptop of mine and a Belkin wireless card. What I can tell you is that you will most likely need to use ndiswrapper with windows drivers, unfortunately I never had a whole lot of luck with this. Eventually, I gave up on that laptop. (It was a piece of junk.) The real problem here is that Belkin doesn't make Linux drivers for their products.

The best advice I can offer is to search the forums thoroughly. Sorry I can't be of more help, but at least you know you're not alone in this predicament.

Hang in there and keep looking for an answer.


I think it will be easier to buy a new card.  why did you not try this?  But I really dont think it will be practical to bring a list, as chip sets are only available via command line.    

Is ubuntu plug and play?    Is there something that will happen at plugin?   Like a windows tip saying, New hardware found, installing drivers, insert installation disc in cd drive.

Else, what is the easiest find at walmart or best buy that is guaranteed to work with ubuntu.  Then how to get it installed
?

---

### Post by degarb on 2010-01-25
Where is the device manager in Ubuntu?   on hardware test is sees a airforce wireless card,  not belkin.  I am wondering if some driver installed that shouldn't , even though I installed the snaptic bcwhatever driver.    Or is there more hoops to go through to enliven the card so leds light up and it sees a wireless signal.

---

### Post by degarb on 2010-01-25
as you can see, i HAve many questions, that are unanswered,  One more,  where is the nsdiwrapper hidden in ubuntu?  Do I need to uninstall other drivers first?

---

### Post by degarb on 2010-01-25
also pages like [http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)  mean little since they dont include installers or instructions on how to install, or if this is redundant to what came on the installation disc.

---

### Post by degarb on 2010-01-25
and [http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_20060108-6build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_20060108-6build1_i386.deb)  is poorly written.  makes no sense, since if I have no isp, I cannot use snaptic to download.   A well written thing would be instructions to download using windows, burn, directory structue that is needed, and install instructions specific for ubuntu.   I don't get ubuntu folderstructures or extensions. Unlike windows that takes about 2 minutes to figure out.

---

### Post by degarb on 2010-01-25
After beating my head into a wall with the fwcutter and snaptic way, and about to smash computer and ubuntu discs, I tried the ndis.  I first installed the ndis gui.  then installed the belkin inf off windows cd for xp.  I took about zero time or difficulty.  I think you all are insane if you think there is any value installing it the linux way.  This is just driving users away.   Heck I almost spent 50 bucks on a new card.


The only issue I see now is I cannot connect to my wireless network if it is secured.   I had similar issues with windows me for a while, then once I tried again after a few months it worked.  i am not sure if this is a configuration issue or some weird bug that will work itself out.


On a side note, the latest ubuntu is not showing a device manager under sys admin.  But I see comments about it on google.  So do I need to install it or find it and put a shortcut in menu?

---

### Post by bkratz on 2010-01-25
> **degarb said:**
> After beating my head into a wall with the fwcutter and snaptic way, and about to smash computer and ubuntu discs, I tried the ndis.  I first installed the ndis gui.  then installed the belkin inf off windows cd for xp.  I took about zero time or difficulty.  I think you all are insane if you think there is any value installing it the linux way.  This is just driving users away.   Heck I almost spent 50 bucks on a new card.


The only issue I see now is I cannot connect to my wireless network if it is secured.   I had similar issues with windows me for a while, then once I tried again after a few months it worked.  i am not sure if this is a configuration issue or some weird bug that will work itself out.


On a side note, the latest ubuntu is not showing a device manager under sys admin.  But I see comments about it on google.  So do I need to install it or find it and put a shortcut in menu?


I use ndiswrapper and have not been able to use encryption on the network at all in 9.10.  I tried the next version (10.04) and it was back. But since this is not released I downgraded to 9.04 where it worked also.  Anyway, it is perfectly normal to not show up in the Hardware Drivers menu when using ndiswrapper, if this is what you mean, or are you referring to something else?

---

### Post by degarb on 2010-01-26
[QUOTE=bkratz;8724486 Anyway, it is perfectly normal to not show up in the Hardware Drivers menu when using ndiswrapper, if this is what you mean, or are you referring to something else?[/QUOTE]
Not at linux machine now,  I don't remember if hardware drivers showed anything, any driver.   I do find it disturbing no control panel is in linux,  I have seen it in other distributions but you could only see settings and not write to them.

Whenever writing a program,  allowing a user to edit the config file can break the program as certain variable settings are not compatible. In a gui you can disallow some settings when certain ticks are ticked.  Also, typos will break programs, and everyone makes typos.  They frustrate users and turn them off. Also the uptime with guis is a tiny fraction of wading through thousands of pages: first read to get what your are saying and second to understand why.  A picture is worth ten thousand words. Though I understand guis are very time consuming to write and can take focus off debugging core functions of the program.

Now, when you upgrade, do you need to reinstall any program/hardware device?   I will be anxious to resecure network. Though only my two neighbors on either side of me could log in.  I don't mind them watching one of my movies or pulling a few web pages, but not using my network to watch utube.

---

### Post by degarb on 2010-01-26
If ubuntu included the ndiswrapper gui, I would have been up and running in minutes, not 2 days.  I am not sure how they consider it clumsy.  I suspect a hatred of anything windows, or perhaps bad experiences with certain cards.   Though the loss of ability to login to personal wpa is a downside.


Speaking of hating windows, I am interested in using wine, since we have many educational kids games.  Or perhaps I can find them in the repository or on some page.

BTW.  Flash games have some weird lag.   I tried to raise priority of firefox, but don't think that priority is sticking.  I need something like bitsum's process lasso.

---

### Post by bkratz on 2010-01-26
Ndiswrapper and the GUI (ndisgtk) are on the live CD. You could simply have searched after adding the CD to software sources and found it.

---

### Post by Locke_99GS on 2010-01-26
> **degarb said:**
> and [http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_20060108-6build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_20060108-6build1_i386.deb)  is poorly written.  makes no sense, since if I have no isp, I cannot use snaptic to download.   A well written thing would be instructions to download using windows, burn, directory structue that is needed, and install instructions specific for ubuntu.   I don't get ubuntu folderstructures or extensions. Unlike windows that takes about 2 minutes to figure out.

Umm, or you could have downloaded the file you linked to in Windows, then in Ubuntu just double-click on the file and it would have installed.

You seem to be making things seem far more complicated than they really are.

---

### Post by Bucky Ball on 2010-01-27
Plug in an ethernet cable and get your updates if you haven't already. Do this with the card plugged in.

System->Administration->Hardware drivers. Anything there?

Although it is Belkin I just about guarantee it is not using a Belkin wireless chipset but one more common. This info can be found with the instruction given early on in this thread:

Open a terminal and:

```
lspci
```

Your network controller etc should be near the bottom. What is it? Sorry if I missed this info early on.

---

### Post by Ji Ruo on 2010-01-28
> **degarb said:**
> Infact, it may be my imagination, but ubuntu seems to work more smoothly than the live xubuntu cd (thought this may be quality of the blank media.).

It's not your imagination! I found the vanilla version of Ubuntu performed as well or better than Xubuntu on old hardware. It's also much easier to find information on how to use it and solve problems. 

I admire your tenacity in getting your existing hardware to work. That's really the spirit with which Linux came about - Torvalds couldn't find what he wanted, so he rolled up his sleeves and did it himself.

With regard to PCMCIA wireless cards that work out of the box, I bought the cheapest new one available here in Australia which was a D-link AirPlus G (DWL-G630), for the princely sum of $19AUD. It, like other cards from vendors more enlightened than Belkin, was 'plug and play' - it worked straight out of the box with the Ubuntu network manager. Same with my mobile broadband modem, too. The only hardware issues I've had is with a cheap tv tuner that no one's written a driver for yet. So what you've gone through isn't typical of hardware support these days.

---

### Post by mark bower on 2010-03-06
You can save a heap of frustration by getting the Belkin F5D7050 USB wireless adapter (on line for about $US 30).  A large number of persons have had "out of the box" success with it.  I can practically guarantee it working for you with Ubuntu 8.10, 9.04 and 9.10.  I have used the F5D7050 with the Ubu versions mentioned and on three different motherboards and one laptop - with absolutely no problems.  

Going thru 3 thick plaster walls at my residence to reach the router, the F5D7050 works just fine with a signal strength of about 30/100.    If a laptop does not have USB, I have had out of the box success with the PCMIA D-Link DWL-G630.

If you cut thru the agony and get one of these devices, please come back and post your success for others to see.

mark

---

### Post by 3rdalbum on 2010-03-06
> **mark bower said:**
> You can save a heap of frustration by getting the Belkin F5D7050 USB wireless adapter (on line for about $US 30).

Thanks for the tip, but two months have passed since the first post on this thread. The original poster has probably gotten their adapter to work or moved on since then.

---

### Post by degarb on 2010-03-07
> **3rdalbum said:**
> Thanks for the tip, but two months have passed since the first post on this thread. The original poster has probably gotten their adapter to work or moved on since then.

Yes, I did.  More command line knowledge now and understanding of the architecture (odd things like sudo) than 2 months ago.   Cheated with ndis, since fwcutter wasn't working.  And not sure if I could do it the harder linux way, or not, today with a tad more knowledge (only read handbook once, but failed to memorize everything).   Though the real knowledge is gained from the forum, with stuff that cannot be contained in a manual.

I am thinking of setting up another machine upstairs.  The usb Belkin F5D7050 suggestion is very appealing.   Can one buy this at staples or radio shack or best buy?

---

### Post by mark bower on 2010-03-08
degarb, pls see post titled "Belkin F5D7050 Wireless USB", author davester65.  while i and many others have had out of the box success with the F5D7050, chipset instances are reported where it does not work (ala coffeecat).  i bot mine at best buy, but googling shows it avail on line also.  however, if you can purchase it locally, then it can be tried out and quickly returned if it does not work.

also, note linuxemporium in the referenced post: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)
based on what is said, i believe i would also consider the D-link USB for a wifi device.  

let us know how it all turns out.

mark

---

