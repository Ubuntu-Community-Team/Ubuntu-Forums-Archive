---
title: "Will Ubuntu Work for me?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by bc_320 on 2009-12-14
I have an older laptop, the specs are below.  A few years back, my buddy and I put XP on it.  It could barely handle it.  The machine sat for a years and we decided to put a bunch of kids games on it for my children.  So I took it out of the closet, fired it up and it hung on start up.  I tried fixing with various windows disk but no joy.  Couldn't get Windows to load.  In an attempt to make sure my HDD wasn't dead, I downloaded and installed a Linux Live CD (I don't recall which one).  that seemed to work fine, except the graphics were terrible.  I think that was because the machine is so old.   So I was thinking that if a version of Linux would work on it, I would give it a try.  I have always wanted to try it.  Please look over the specs and let me know if you think Ubuntu or some other version of Linux will run on this machine.   It had Windows 98 before XP.      

Specs: 

-Microprocessor 366 MHz AMD-K6-2 processor with 3DNow! technology 
 -Microprocessor Cache 512 KB L2 Pipeline Burst Cache 
-Memory     64 MB SyncDRAM (US)  
-Video Graphics          * High-performance 3D graphics     
-Maximum internal resolution of up to 800 x 600 x 16 M; with external monitor - 1280 x 1024 non-interlaced     *  24-bit color provides up to 16 M brilliant colors 
-Video Memory  128-bit accelerated graphics with integrated 2 MB video memory 
-Hard Drive 4.3 GB Hard Drive   
-Diskette Drive    3.5 inch, 1.44 MB Diskette Drive 
-Multimedia Drive    24X Max CD-ROM Drive  24X Max  
-Display    13.0 inch HPA Display  
-Fax/Modem    56K ITU V.90 PCI Modem  ITU V.90  Network Card    Ethernet Network  
-Compatible Sound    JBL Pro Audio System 
-Programmable function keys (F1 and F2)  Keyboard    Full-size keys and separate cursor control keys (88 keys)  101-key compatible   
-Windows operating system keys 
-Pointing Device     Touchpad pointing device PC Card Slots          
-One Type II PC Card slot with support for 32-bit CardBus  External Ports 
-One (1) USB connector     
-Serial RS-232 compatible,  DB9 connector (16550) 
-Parallel SPP/ECP standard interface (DB25 connector) 
-PS/2 Mouse or Keyboard port
-R-11 modem jack 
-Two audio ports (headphone/speaker-out and microphone-in) 
-External VGA monitor port

---

### Post by Geoff918 on 2009-12-14
You should be fine. I have a similar system that runs Ubuntu at home. It sometimes lags a moment, but it's very workable. XP hardly ran on it anymore.

You may want to try a LiveCD. AND--when installing, should you choose to, you may need to do an F6 (More Options) and do Safe Graphics Mode. That may prevent problems during installation.

****

More options: If you want a real low-spec, but not all that lovely installation that's another Distro.  Try Puppy it's around 100MB, but it flys because it's designed to be extremely lightweight. Lighter still is DSL, but it's also awfully ugly.

---

### Post by bc_320 on 2009-12-14
I have found some kids games that are set up for Linux.  They should work with any installation, correct?  Do I have anything I really need to worry about?  This machine is going to be used by kids.  Is it possible for them to easily screw up the OS?

---

### Post by running_rabbit07 on 2009-12-14
For future references, it is easier to read specs if they are in bullet form. 

What type graphics do you have? 

nVidia or Intel based?

nVidia has better support, but if you have Intel, I am sure someone else can tell you if it is supported.

---

### Post by Geoff918 on 2009-12-14
No, you should be fine. Linux is very secure. It has rights-based access. So, as long as you don't give kids root access, you're fine.

It's actually MUCH harder to mess up a Linux system than a Windows system through normal usage.

Are the kids games .DEB or .RPM for install? This may have some impact on what you choose. Although, with some wizardry you can port these things either way. (Or just build from source)

****
EDIT: Have you heard of or considered Edubuntu? There's also some kind of Christian Ubuntu I forget about what it's called, I wasn't too interested. But, it has adult content filters and such installed.

---

### Post by bc_320 on 2009-12-14
Sorry about the specs.  I had them in a easy to read form until I pressed submit.    As for the games.  I have no clue.  I found them when I was looking for free windows games.  I was going to downgrade from XP to 2000.  In the process I found games for Linux.  I am hoping they are as easy to put on a windows machine i.e. run an install program.  I do not know what "Eubuntu" is, so no, I have not considered it.  Should I?   as for filters, this machine is so old, all it has for network access is a dial up modem.

---

### Post by Temposs on 2009-12-14
If you are setting it up for your kids to use it, you might want to try the Edubuntu variant of Ubuntu. It has some extra apps included that are designed to help children learn, including games.

Also, there are a lot of games included in the Ubuntu Software Center. No need to find games through random websites with Ubuntu. You just fire up the Ubuntu Software Center(which is a list of thousands of apps vetted by Ubuntu), look through the list of games, click a couple times and Ubuntu will automatically download and install whatever you want. And it's all free!

---

### Post by running_rabbit07 on 2009-12-14
> **bc_320 said:**
> I have found some kids games that are set up for Linux.  They should work with any installation, correct?  Do I have anything I really need to worry about?  This machine is going to be used by kids.  Is it possible for them to easily screw up the OS?

I have found some great games for kids that are free in Ubuntu's add/remove. 

Supertux- which is a copy cat of super mario.

Supertuxkart- which is a copy of mario cart.

There are many more to chose from.

For learning there is Edubuntu and Childsplay (nothing like the movies) which both have great learning games for young children.

---

### Post by bc_320 on 2009-12-14
Instead of having Ubuntu download, can I download on my windows machine to a thumb drive, then plug it into the other computer?  The old one I want to Linux on has no and will have no internet access.    My other option would be to download them to my windows machine and burn them to a cd using Nero 7.  If that is possible.

---

### Post by audiomick on 2009-12-14
I had a 7.10 Ubuntu running on a machine with nearly those specs, after the xp on it wouldn't run anymore.

More RAM would help, if the machine will take it. A swap partition 2 x RAM size might be a good idea.

Ubuntu has the advantage that the root is disabled. You can of course set up a user for the kids that doesn't have admin privileges. Even if they stumble onto the computer when you have logged on and gone to get a coffee or something, Ubuntu doesn't let you do anything that might break the system without a password.

What might be your biggeest problem is the hard drive. 4.5GB is very small ( I read that right, didn't I ? ). That was the reason I got rid of my old one. By the time I tried to buy a bigger drive for it, the computer couldn't read the 40 GB HD that was the smallest one in the shop.

---

### Post by Geoff918 on 2009-12-14
Install is easier in Linux than in Windows, if you ask me.

It's a cultural change because you don't go to a website and download a program and run install. You just click a button in the OS itself.

And you can always install links to other repositories as well, such as:

[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

(Okay so it's not a repo, but it links to one)

---

### Post by Geoff918 on 2009-12-14
Your question about USB flash creation:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

That's usually a good site. Haven't followed this one specifically, but have done others in the past. A good source.

---

### Post by bc_320 on 2009-12-14
[quote=Geoff918;8500854]Install is easier in Linux than in Windows, if you ask me.

It's a cultural change because you don't go to a website and download a program and run install. You just click a button in the OS itself.

And you can always install links to other repositories as well, such as:

---

### Post by cartisdm on 2009-12-14
> **Geoff918 said:**
> Install is easier in Linux than in Windows, if you ask me.

Agreed.

Also, I've gotten away with putting Ubuntu on some pretty limited systems and was amazed by the performance

---

### Post by running_rabbit07 on 2009-12-14
> **Geoff918 said:**
> Your question about USB flash creation:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

That's usually a good site. Haven't followed this one specifically, but have done others in the past. A good source.
  You may use that or [unetbootin.com]("http://unetbootin.sourceforge.net/") to make a bootable thumb drive.

---

### Post by bc_320 on 2009-12-14
> **Geoff918 said:**
> Your question about USB flash creation:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

That's usually a good site. Haven't followed this one specifically, but have done others in the past. A good source.

 So if I understand correctly.  I can set up Linux on a thumb drive, boot Linux on my windows machine, go get the kids games, take that thumb drive to my old laptop that is running Linux, plug it in and install the games on the laptop. Correct?

---

### Post by Yvan300 on 2009-12-14
Go to getdeb and download the game as a .deb file. Then put it on your flash drive and install it from the old pc just as you would with a .exe file.

---

### Post by bc_320 on 2009-12-14
> **Yvan300 said:**
> Go to getdeb and download the game as a .deb file. Then put it on your flash drive and install it from the old pc just as you would with a .exe file.

 That seems easier.  But can I still move the file on my thumb drive or CD without having to install Linux on it?

---

### Post by Temposs on 2009-12-14
> **bc_320 said:**
> That seems easier.  But can I still move the file on my thumb drive or CD without having to install Linux on it?

If all you want to do is transfer files from one computer to another, there's no need to install linux on the thumb drive.

Installing linux on the thumb drive only serves the purpose of being able to boot linux from the thumb drive. If you don't need or want to do that, then skip that step :-)

---

### Post by Yvan300 on 2009-12-14
I don't understand what you mean. Most likely your flash drive is formated in fat. So you copy the .deb from the computer with the internet and then put it on the old pc running linux.

---

### Post by emeraldgirl08 on 2009-12-14
How about Xubuntu? I hear they have a lite version that runs well on older machines also. I also got ahold of an old IBM 600X that a friend didn't need anymore (very solid keyboard).

It has:

500mhz PIII processor
320mb SDRAM
4mb of Video RAM
and a very nice solid case!

So for the time I've been indulging in linux I have accumulated around 10 distros of LiveCDs :P I figured I'd give the old Hardy Heron a try. 

It works :D 

This is a laptop I've given my dad. He's never owned a laptop or a computer of his own at all. I wanted to make this seamless and easy to operate. I plan on letting Dad get comfortable with Heron until it doesn't get support from Canoniacal anymore. Then I'm going to go with another distro that is lighter. I just needed something that had Office programs, games, and knew that VLC would let Dad watch some AVIs that I have saved for when he gets bored. 

FYI I told my niece to get on and play one of her Flash games last night. I really wanted to see how well the old 600X could handle it. She played for a bit and the fan wasn't spinning hard at all!

The 600X came with an old 4200 20gb hard drive so I gave my dad an spare 80gb 5400rpm Western Digital to speed things up. The old hard drive has WinXP Pro on it but that won't let you watch videos. 

While it's not the best candidate for watching videos- by some miracle and programming Linux is able to play videos that I have saved in AVI and FLV (streaming is a little bit choppy, but saved FLV works)!

Sorry about rambling but just thought I'd share experiences I've had with an older laptop.

---

### Post by Geoff918 on 2009-12-14
> **emeraldgirl08 said:**
> How about Xubuntu? I hear they have a lite version that runs well on older machines also. I also got ahold of an old IBM 600X that a friend didn't need anymore (very solid keyboard).

It has:

500mhz PIII processor
320mb SDRAM
4mb of Video RAM
and a very nice solid case!

So for the time I've been indulging in linux I have accumulated around 10 distros of LiveCDs :P I figured I'd give the old Hardy Heron a try. 

It works :D 

This is a laptop I've given my dad. He's never owned a laptop or a computer of his own at all. I wanted to make this seamless and easy to operate. I plan on letting Dad get comfortable with Heron until it doesn't get support from Canoniacal anymore. Then I'm going to go with another distro that is lighter. I just needed something that had Office programs, games, and knew that VLC would let Dad watch some AVIs that I have saved for when he gets bored. 

FYI I told my niece to get on and play one of her Flash games last night. I really wanted to see how well the old 600X could handle it. She played for a bit and the fan wasn't spinning hard at all!

The 600X came with an old 4200 20gb hard drive so I gave my dad an spare 80gb 5400rpm Western Digital to speed things up. The old hard drive has WinXP Pro on it but that won't let you watch videos. 

While it's not the best candidate for watching videos- by some miracle and programming Linux is able to play videos that I have saved in AVI and FLV (streaming is a little bit choppy, but saved FLV works)!

Sorry about rambling but just thought I'd share experiences I've had with an older laptop.

Xubuntu isn't really any lighter at all. I've had mixed experiences with it. Sometimes much faster, more often much slower than GNOME (Ubuntu).

There's a new version of a lightweight release that's coming with 10.04 called LUbuntu. That promises to be excellent (LXDE + Ubuntu). It's only in testing at this time, however.

---

### Post by bc_320 on 2009-12-14
Thank you all for your assistance and advice.  I think I will give ubuntu or Xubuntu a try.  I will probably be back with questions.    I just thought of one.   When I tried my live cd the graphics completely sucked.  I could barely read the screen.  If I push F6 I should be able to select a mode for lower graphics, correct?

---

### Post by Geoff918 on 2009-12-14
> **bc_320 said:**
> Thank you all for your assistance and advice.  I think I will give ubuntu or Xubuntu a try.  I will probably be back with questions.    I just thought of one.   When I tried my live cd the graphics completely sucked.  I could barely read the screen.  If I push F6 I should be able to select a mode for lower graphics, correct?

Yes, it will come up with a menu. You can select "Safe Graphics Mode". You may also try some other options there if you have any further problems, such as, NO APCI or whatever.

When you install, you may find in the System -> Administration -> Hardware Drivers there may be some proprietary drivers that may help you out.

One note: Without internet access you may find Ubuntu to be a bit more difficult than we have described. It's extremely easy WITH internet access, but may require some additional effort without it.

---

### Post by bc_320 on 2009-12-14
Is there one that would be better with no internet access?

---

### Post by Geoff918 on 2009-12-14
> **bc_320 said:**
> Is there one that would be better with no internet access?


Well, not really. The one thing is that Linux grew up out of Unix which was for networked computers. Linux grew up in the Internet era. It's got more time connected to the internet than Windows does. So, it's pretty network dependent. It's both a strength and a weakness.

The problem becomes that you probably are going to have to be rather knowledgeable about Linux in order to operate it outside of the network environment. You will quickly find out about dependencies and all that the system takes care of automatically, but you'd have to manually copy those files, put them so that the system could find them, and then continue from there. It may prove difficult. Then again, if you're up for a challenge it could be very fun, too. :)

---

### Post by audiomick on 2009-12-14
In your specs in the first post there is an ethernet card listed. If you have a broadband connection with a router, you should be able to plug it in and off you go.

---

### Post by Temposs on 2009-12-14
It's not that you can't use Ubuntu without internet. 

It's just that Ubuntu and most of the major Linux variants have developed such that the main way to get new software(including extra codecs and support packages) is by downloading them from repositories over the internet(the Ubuntu Software Center I mentioned before).

You can't really go out and buy much Linux software off a shelf in a computer store, and you don't have a bunch of CDs with drivers for Linux that came with the computer. So, you get them over the internet(NOT from random websites, from the repository programs). And it's sort of difficult to do some of these software installations without the internet if they have a lot of other dependent software that must be installed first(we call this dependency hell).

---

### Post by emeraldgirl08 on 2009-12-14
If you want to update things you'll need to take that laptop out and do your updates. If you want to store programs to execute on your ubuntu you can download DEB packages (am I right guys?) on flash memory. All you do then is plug that flash memory into your ubuntu computer and drag that DEB file out and double click on it.

It's the Linux version of an Windows exe file.

lol I really hope someone helps me out with this but I'm pretty positive that is what you are getting at.

**Edit:**

Forgot about those dependencies! 

DOH!

---

### Post by Temposs on 2009-12-14
> **emeraldgirl08 said:**
> If you want to update things you'll need to take that laptop out and do your updates. If you want to store programs to execute on your ubuntu you can download DEB packages (am I right guys?) on flash memory. All you do then is plug that flash memory into your ubuntu computer and drag that DEB file out and double click on it.

It's the Linux version of an Windows exe file.

lol I really hope someone helps me out with this but I'm pretty positive that is what you are getting at.

**Edit:**

Forgot about those dependencies! 

DOH!

Yes, that is how you would install apps on Ubuntu without a direct internet connection, and yes, installing the dependencies one by one will be tedious if you need to install a lot of(well, any) software.

---

### Post by bc_320 on 2009-12-14
> **audiomick said:**
> In your specs in the first post there is an ethernet card listed. If you have a broadband connection with a router, you should be able to plug it in and off you go.

I think it was an option my wife did not get.  There is no port the cable, just the phone jack.  



Since I am not trying to do anything major, like run office or any major programs I am going to go for it.  Right now the laptop is just a very large paperweight.

---

### Post by Geoff918 on 2009-12-14
> **emeraldgirl08 said:**
> 

**Edit:**

Forgot about those dependencies! 

DOH!

Exactly. I LOVE Linux. But that would have been a nightmare when I first started with Linux this past January. I have learned A TON and gone pretty far with Linux. But, I can only imagine being unacquainted with the OS and then trying to figure out what "glibc...not found" could possibly mean, and once I understood--how then to resolve the issue.

Can you imagine building from source w/o a network connection?

The good thing is that you can often select the LiveCD as your repository site. That WILL probably fix MOST issues off the bat.

The next item is that the LiveCD won't have a lot of the software in the Repos because it's limited to ~700MB footprint.

With some skill, it can be navigated. Without some skill, it may be a nightmare.

---

### Post by emeraldgirl08 on 2009-12-14
> **Geoff918 said:**
> Exactly. I LOVE Linux. But that would have been a nightmare when I first started with Linux this past January. I have learned A TON and gone pretty far with Linux. But, I can only imagine being unacquainted with the OS and then trying to figure out what "glibc...not found" could possibly mean, and once I understood--how then to resolve the issue.

Can you imagine building from source w/o a network connection?

The good thing is that you can often select the LiveCD as your repository site. That WILL probably fix MOST issues off the bat.

The next item is that the LiveCD won't have a lot of the software in the Repos because it's limited to ~700MB footprint.

With some skill, it can be navigated. Without some skill, it may be a nightmare.

Wonder if you could steal the necessary codecs off of a Linux Mint Gnome or other distro that is similar to Ubuntu this way??? Or any other way without an internet connection and a mad desire to watch videos or listen to MP3's?

Or just to play with? :D

---

### Post by Geoff918 on 2009-12-14
> **bc_320 said:**
> I think it was an option my wife did not get.  There is no port the cable, just the phone jack.  



Since I am not trying to do anything major, like run office or any major programs I am going to go for it.  Right now the laptop is just a very large paperweight.


Well, after you get this installed. I can guarantee you we can tell you what your system has.

We can have you run something like:

sudo lshw -html >> hardware.html

from the Command Line and get an output of EVERYTHING on your system. That will make getting it all the way tweaked easier. I'm sure it will work almost perfectly, if not perfectly, straight "out of the box".

---

### Post by natravis on 2009-12-14
> **Geoff918 said:**
> Well, after you get this installed. I can guarantee you we can tell you what your system has.

We can have you run something like:

sudo lshw -html >> hardware.html

from the Command Line and get an output of EVERYTHING on your system. That will make getting it all the way tweaked easier. I'm sure it will work almost perfectly, if not perfectly, straight "out of the box".

Wouldn't that work even before installing? I haven't used a live CD in a while, so I don't remember.

---

### Post by Geoff918 on 2009-12-14
> **natravis said:**
> Wouldn't that work even before installing? I haven't used a live CD in a while, so I don't remember.

Yes, good point. I wasn't much thinking about it, though. Please forgive the oversight. Of course, it may be trickier because his file wouldn't be saved permanently without first mounting the harddrive and writing it there. And, then of course that might get wiped in the install depending on how it's done.

---

### Post by emeraldgirl08 on 2009-12-14
couldn't he hook up a usb drive and direct the save to it?

---

### Post by Geoff918 on 2009-12-14
> **emeraldgirl08 said:**
> couldn't he hook up a usb drive and direct the save to it?

Yes, you can do a "persistent install" with a LiveCD. Gosh, can't leave an angle untouched here, eh? ;)

For that matter he could just do a PenDrive install altogether.

---

### Post by running_rabbit07 on 2009-12-14
You can use APTonCD to back up the programs on one machine and then install them on another. Or, just plug in the RJ45 every now and then to install and update programs.

---

### Post by emeraldgirl08 on 2009-12-14
I'm a persistant girl ;)

lol. Gotta love linux :D

---

### Post by Geoff918 on 2009-12-14
> **emeraldgirl08 said:**
> I'm a persistant girl ;)

lol. Gotta love linux :D

Hmm, I'm not sure if flirting is a violation of the forums. I suppose we'll just move along now.

****

EDIT: I'm only kidding. I hope you get the humor / sarcasm.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I don't know how well Ubuntu plays with PCcards, and I realize it's an extra cost for old hardware, bu tyou could use [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16839158009&Tpk=network%20card") to solve your internet problems.
[Even better](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156133&cm_re=network_card-_-33-156-133-_-Product) and the first review confirms it working with Ubuntu Netbook remix, so Ubuntu does play well with it!

---

### Post by natravis on 2009-12-15
> **Geoff918 said:**
> Hmm, I'm not sure if flirting is a violation of the forums. I suppose we'll just move along now.

****

EDIT: I'm only kidding. I hope you get the humor / sarcasm.

I checked. It violates rule B4-845-P. Move along. I hope this thread doesn't get hijacked with love

---

### Post by 3rdalbum on 2009-12-15
1. How much RAM does this machine actually have? You need 256mb of RAM to install and run Ubuntu. This machine doesn't sound like it would have 256mb of RAM unless it had been drastically upgraded.

2. I doubt you can boot from a USB device on a machine that old.

3. If it can barely handle XP, then Ubuntu will be slower still as it's more modern.

Conclusion: Try a smaller distribution such as Slitaz, Puppy Linux or DSL.

---

### Post by bc_320 on 2009-12-15
well that is interesting.  I just tried to install Ubunutu and got the following message: [  13.569082] Kernel panic - not syncing: out of memory and no killable processes.... [  13.569123]  I assume that means I do not have enough memory.  So what now?  I want to try Linux on this machine, if nothing else to try Linux.  I think I have 64MB of RAM

---

### Post by Temposs on 2009-12-15
These are the minimum requirements for running Ubuntu:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Technically, a machine need only have 64mb to run Ubuntu. But, in order to run the **graphical installer**, you should have the recommended system requirements. If you install Ubuntu with the alternate CD, it should work just fine.

Here's a link to the alternate CD installer:
[http://ubuntu.cs.utah.edu/releases/karmic/ubuntu-9.10-alternate-i386.iso](http://ubuntu.cs.utah.edu/releases/karmic/ubuntu-9.10-alternate-i386.iso)

Make your CD or bootable USB drive just like you did before. When you boot, it will take you through the installation procedure without any graphics. This will probably let Ubuntu install without running out of memory.

---

### Post by bc_320 on 2009-12-15
hmmmm Will that work then once it is installed?    Maybe a smaller installation would work better. 

*Edit *

And do you have links to torrents of these ISOs?  I forgot how long it takes to do a straight download.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
A full install of vanilla Ubuntu only takes 2.7 GB and that's with the filesystem and home directory on the same partition... you just can't install anything after really. You might try just putting the filesystem  on the 4 Gb HDD and get an external USB HDD for your /home partition

---

### Post by Temposs on 2009-12-15
> **bc_320 said:**
> hmmmm Will that work then once it is installed?  And how about the min 4GB HDD space?  I only have 3GB available.  Maybe a smaller installation would work better

It should work once it's installed. You could just try it out and see what happens. It may work even with just a 3gb hard drive.

Alternatively, you could try the Xubuntu variant. According to the requirements page, it only requires 1.5gb of hard drive space.

You would still need to use the alternate install CD for Xubuntu, which I'm linking to here:
[http://cdimage.ubuntu.com/xubuntu/releases/karmic/release/xubuntu-9.10-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/karmic/release/xubuntu-9.10-alternate-i386.iso)

---

### Post by Temposs on 2009-12-15
> **ST3ALTHPSYCH0 said:**
> A full install of vanilla Ubuntu only takes 2.7 GB and that's with the filesystem and home directory on the same partition... you just can't install anything after really. You might try just putting the filesystem  on the 4 Gb HDD and get an external USB HDD for your /home partition

Like ST3ALTHPSYCH0 says, installing Ubuntu should work, but it will basically not leave much space left. But, I'm assuming you want to just work with what you've got there, and not have to buy extra stuff. Is that the case?

---

### Post by bc_320 on 2009-12-15
Yes.  We will not be buying anything for this machine.  I even have an old PS/2 mouse I am going to hook up to it if I can.  I am thinking of maybe trying Puppy Linux.  It sounds like it may work for what I need.  Although I need to find out if it can run the educational games that are out there.

---

### Post by bc_320 on 2009-12-15
[Temposs]("http://ubuntuforums.org/member.php?u=169222")
I have a dumb question.  What will the alternative cd install get me?  Is that so it will install?  It seems to me when I read the regs, I need 128 min ram to run the OS.

Furthermore, I was looking around on the Ubuntu site and came across Edubuntu.  I assume that it has the same regs as Ubuntu, correct?

---

### Post by Temposs on 2009-12-15
I'll give you some torrent links:

Ubuntu Alternate CD:
[http://ubuntu.cs.utah.edu/releases/karmic/ubuntu-9.10-alternate-i386.iso.torrent](http://ubuntu.cs.utah.edu/releases/karmic/ubuntu-9.10-alternate-i386.iso.torrent)

Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/karmic/release/xubuntu-9.10-alternate-i386.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/karmic/release/xubuntu-9.10-alternate-i386.iso.torrent)

---

### Post by Temposs on 2009-12-15
The Alternate CD gets you the full install. The problem is that with the regular install CD, it takes a lot more memory to run the graphical installer than is needed to run Ubuntu after it is installed.

So, you use the Alternate CD when you have a system with enough memory to run Ubuntu, but not enough memory to run the graphical installer for Ubuntu.

---

