---
title: "i can't even get the disk to load!"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by pakrat1963 on 2011-02-23
My girl friend's kids have a couple of desk top machines that are running Pirate versions of XP, and they are so infected it isn't funny (kids on the net with NO anti-virus software, go figure.)i forget the name of the virus we have, but it is a nasty bugger! has the security programs tied in knots, messes with the internet connection, and keeps wanting us to send money to what i believe is a non-existing company for security soft ware.

i downloaded ubuntu 10.10 on my Vista laptop, opened the .rar to my installed dvd/cd drive and burnt the cd.

When i dropped the ubunto cd into the reader on the kids machine and tried to reboot, it would not boot from the cd. i have gone into BIOS and tried to shift boot priorities, but it still boots the pirate XP from the hard drive. 

The cd did give me what looks like an "install Wizard." But when i run it, the virus seems to be blocking it from finishing in the last steps.

It there a way to get a new OS on this machine? The XP OS that is there is a pirate copy with no support. My understanding is that Ubunto had grunch loads of support (you guys here on the forum!) The kids aren't doing rocket surgery, they just want to get on the 'net, play some games, maybe store some pictures and mp3s,and do Facebook stuff. 

i have loaded XP on an old laptop, but this one is throwing me a loop! Thanks in advance for the help!
pakrat

---

### Post by Old *ix Geek on 2011-02-23
It sounds like there's a problem with the CD. Either you didn't burn it correctly or it's incomplete/corrupted, etc.

If the CD is good and you boot up from it, you won't see any of that windoze garbage as the Ubuntu CD will be in charge.

I'd check to make sure the file is good AND that you correctly burned its image to CD.

---

### Post by pakrat1963 on 2011-02-23
Thanks Old Geek,

Could the virus that has so totally unhinged my pirated xp be blocking the boot from cd? 

i think the cd is ok, because it did try to load "inside" the pirated xp.

Just in case it makes a difference to anyone I HAVE NO LOYALTY TO THE PIRATED OS OR THE FILES ON THIS MACHINE! I WANT THE KIDS TO BE ABLE TO PLAY GAMES AND FACEBOOK! (sorry to shout) If i can wipe the whole hard drive and start from the Ubunto loaded disk, i will be a happy camper, but i have no idea how to go about clearing a hard drive (on purpose.)

Thanks again for the help,
pakrat

---

### Post by fabricator4 on 2011-02-23
> **pakrat1963 said:**
> When i dropped the ubunto cd into the reader on the kids machine and tried to reboot, it would not boot from the cd. i have gone into BIOS and tried to shift boot priorities, but it still boots the pirate XP from the hard drive. 

The cd did give me what looks like an "install Wizard." But when i run it, the virus seems to be blocking it from finishing in the last steps.

It's not booting off the CD.. But you got the installation program?

It's got to be one or the other. Did you download the full Live CD?  When you boot off the live CD it will give you two options: Try Ubuntu, running out of memory, or install Ubuntu.

If you try Ubuntu you can still install from that point by clicking on the "Install Ubuntu" launcher.

When it asks, tell it to use the whole disk.

If you can't boot at all then the problem is either the disk, or the CD drive.  See if you an boot any other type of boot disk in that drive.  If the drive is faulty it is possible to boot off a USB, as long as the BIOS supports it.

Chris.

---

### Post by arpanaut on 2011-02-23
Take a look at item #2 in this link for the proper way to burn the iso as an image,
try the "show me how" button.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Don't even try to install with the windows installer/wubi, your Windows is too corrupted to handle that.

---

### Post by Ben Page on 2011-02-23
You are mentioning downloaded .rar file, are you sure it was .rar and where did you download it from? Download Ubuntu from Ubuntu.com website and make sure you get the .iso file, then burn it in "burn image to disc" mode, not as a regular data cd.

---

### Post by pakrat1963 on 2011-02-23
> **Ben Page said:**
> You are mentioning downloaded .rar file, are you sure it was .rar and where did you download it from? Download Ubuntu from Ubuntu.com website and make sure you get the .iso file, then burn it in "burn image to disc" mode, not as a regular data cd.

Help me here Ben, i clicked the big orange box at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and i got a .rar file in my download file with the title "ubuntu-10.10-desktop-i386.iso" When i opened the rar i didn't see anything that i really recognized, so i opened the rar to my D drive (DVD/CD Burner/player) and let it fly. the same files are on the cd as in the rar.

(Aren't noobs irritating some times?)

Thanks for the help!
pakrat

---

### Post by Jack Smith on 2011-02-23
so the name of the downloaded file was ubuntu-10.10-desktop-i386.iso.rar? or ubuntu-10.10-desktop-i386.iso?

---

### Post by nothingspecial on 2011-02-23
> **pakrat1963 said:**
> 



i think the cd is ok, because it did try to load "inside" the pirated xp.



Sounds like you've downloaded the wubi version of Ubuntu. You don't want that. You want the full desktop edition.

Wubi si for trying ubuntu inside windows, and yes a nasty virus could prevent you from doing that.

Download the desktop edition from here

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

and choose to install ubuntu over the entire disk, no files, no data, no virus, no windows, just a lovely fresh Ubuntu install.

---

### Post by PratterFak on 2011-02-23
This has been an interesting thread to read...lol

I'm not sure where the .rar is coming from. I tried all the links I could find and it all wants to just download the .iso file as I've always done. Also, not sure it is the wubi as that comes up as wubi.exe when I tried to download it.

Along with burning the correct ISO file, one very important thing is to burn it at a slow speed- I recommend burning at 4x (do not burn at max). You may also need to edit the bios to boot from CD prior to HDD.

I've had several optical drives either not read the disc or fail during installation if the 4x burn is not followed.


Assuming you want the 32-bit Desktop version- If you are still having problems, try this...

[http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/maverick/ubuntu-10.10-desktop-i386.iso](http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/maverick/ubuntu-10.10-desktop-i386.iso)

---

### Post by StarZtorm on 2011-02-23
Pakrat, the file you have downloaded is not a .rar file, it is a .iso file. 

You cant open it and burn the contents to the cd, you need a image burner for that.

Just follow the steps from the ubuntu.com site. Download the tool that is linked there. (click the "show me how" boxes that appear after you have pressed the download button for the desktop version at ubuntu.com)

And when you get all this right, and you get to the install screen, select the "erase and use the entire disc" as this will wipe everything from the computer, and give a fresh install of Ubuntu :) 

Hope this helps!

---

### Post by 4Orbs on 2011-02-23
> The cd did give me what looks like an "install Wizard." But when i run it, the virus seems to be blocking it from finishing in the last steps.
It sounds like your original install disc may be ok. If it asked you to create a username and password, then actually began copying the Ubuntu files to the hard drive... you were almost finished installing. When the Ubuntu installer reaches approx. 80% it will begin downloading the language packs for installation (unless you click the "Skip this Step" button). Often, the installer will seem to hang at this point with no indication of progress. The language packs usually require several minutes to download and install. If you are patient and wait out the suspense... the installation should complete.

---

### Post by 3rdalbum on 2011-02-23
> **StarZtorm said:**
> Pakrat, the file you have downloaded is not a .rar file, it is a .iso file. 

You cant open it and burn the contents to the cd, you need a image burner for that.

Just follow the steps from the ubuntu.com site. Download the tool that is linked there. (click the "show me how" boxes that appear after you have pressed the download button for the desktop version at ubuntu.com)

And when you get all this right, and you get to the install screen, select the "erase and use the entire disc" as this will wipe everything from the computer, and give a fresh install of Ubuntu :) 

Hope this helps!

+1. The ISO image needs to be burned as an image, NOT as an individual file - and don't "extract" it either.

---

### Post by Ben Page on 2011-02-23
The WinRAR application installed in the "pirated XP" is acting as a default application for handling .iso files, that is why WinRAR opens the .iso file by default. You don't need to open the .iso file, just burn it onto a CD as it is. The .iso file is a container file type, same as the archive file type, but .iso file type is used to store virtual CD images, while .rar is used to store archived/compressed files.

You should get the Ubuntu installer only when installing Ubuntu inside XP (Windows). This is called the WUBI installer. WUBI will install Ubuntu inside XP as an application and will function similarly to virtual OS giving you the option to boot XP and Ubuntu simultaneously (dualboot).

If you want to install Ubuntu as an standalone OS, you need to shut down your PC and boot from the Ubuntu Live CD, then XP doesn't play any role in this installation. You need to set up your boot priority in BIOS to boot from th CD/DVD drive first and then wait for Ubuntu to load. You'll get a prompt shortly whether you want to try or to install Ubuntu - naturally, choose to install it.

---

### Post by pakrat1963 on 2011-02-23
Thank you all for your interest and advice. It looks like i did down load the "wubi", and to be honest, i would be happy for with that if i could get it to load on the xp machine and get on to the net, then i think the Wonderful World of Linux would take me where i need to go.

So i am now downloading that InfraRecorder from the download page (do i really need another cd burner program on my laptop? i guess so...) and i think i am downloading the write version of Desktop Ubunto.

Let me clarify again, i am downloading on my Vista laptop, and trying to load the disk/Ubunto OS into an old celeron powered and highly virus infected desk top that belongs to my GF's kids. 

When i tried the wubi disk again a couple hours ago it tried to load in windows, got past the login window, and at the 1 sec remaining point i got a window with "An error occured...Invalid Argument... For more information please see the log file C:\docu~..." i opened the file indicated (a bigger step than you probably imagine for a caveman like me!) and the third to the last line said: "exception, Cannot download the Metalink and therefore the ISO"

i'm not sure what that means, but i think the nasty Security Virus is up to its tricks blocking any attempt to get around it. 

Hopefully the Desktop Ubunto will be done downloading by morning.

Thanks again for all your help and advice,
pakrat

---

### Post by oldos2er on 2011-02-23
Since your WinXP is so badly messed up, I would urge you to install Ubuntu to its own partition rather than Wubi.

---

### Post by pakrat1963 on 2011-02-23
Thanks for the advice, Ann

That's the point of the exercise! i have the ubuntu-10.10-desktop and the new disk-writer, will try again after brekkie and i'll let you know how it goes!
pakrat

---

### Post by NightwishFan on 2011-02-23
I know the issue. Windows tends to have 3rd party programs associate files, and never show the real file types. In this case the iso is being seen as an archive (by winrar probably). It is most certainly a cd image, and needs to be burned as such. Here is a nice howto! :)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Once you get to the burning step ensure you burn at the slowest possible speed to prevent errors.

---

### Post by pakrat1963 on 2011-02-23
thank you NightWish,
i hit the burn button just before i opened your post, so haven't read the thread you send, but wish me luck! it looks like it is going OK, will keep you informed.
The slowest speed available on the burner i downloaded is 10x, so that is what i am using.
Thanks All,
pakrat

---

### Post by pakrat1963 on 2011-02-23
i guess i gotta mark this thread solved! It loaded this time! 

The next question: does anyone know a forum like this in Visayan (Cebuano/Philippino) so that my teenage step daughter can start learning? 
i need to go to work so i can find time to play with my new Linux Machine!:guitar:

Thanks again for the help and support,
pakrat

---

