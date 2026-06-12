---
title: "Confirmation of steps"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Faziri on 2011-06-01
Hiya, Ubuntuers ^^
---------- ***intro***
I've been hearing a lot about Linux distros being the best OSs around and so i've decided to give Ubuntu a try. If i don't like it, i can always just get rid of it anyway (or so i think anyway... Correct me if i'm wrong please xD).

I've been googling, reading the Ubuntu guides, reading blogs, tutorials, asking friends, etc etc so i've got a hang of the sheer basics, but not much. In this thread, i'd like to sum up what i currently believe the correct steps would be to get the system set up the way i want it to be. Being rather comfortable and experienced using my laptop in somewhat shady ways, i'm more picky than the average person about what happens on every level of my computer and the last thing i like is not knowing what something is doing when clearly it's doing something. :) Thus, i'd like to go over what i currently believe to be my desired setup and i'd like to ask to have it pointed out to me if at some point i'm missing something, i have to watch out for something, etc.

The reason i'm asking this here anyway, despite having read so much and having experienced that most of these things "just work themselves out" when you start them, i prefer being sure about everything 100% *before* i try doing anything potentially dangerous (i've already burnt the desktop iso and booted into ubuntu of course, that's all safe stuff). It's also due to the fact that much of the info is written by bloggers (whom may be right, but i wouldn't count them as reliable) or came from the official guides, which at some points just made me go crazy. Another big chunk of the info i found was potentially outdated, i could have misinterpreted some of it, etc. There's so many things that could go wrong so easily, making me feel very insecure if i can't get confirmation of the basic info from someone with experience. :/ Some of these question might very well already be covered somewhere, but either the info was just too shady for me or i don't feel comfortable blindly assuming it to be true without any background info and specifics. So, sorry if that's the case, but i only ask if i have a reason to ask, don't worry :P

And oh yes, stuff between round brackets is generally just semi-off-topic remarks, ignore it if you don't want personal yapping in my posts :P

---------- ***the real deal***
My current setup is win7 32bit on a plain laptop with no special hardware that i'm aware of, just the common average stuff with 4 (although some programs say 3) GB RAM, 2GHz processor, Nvidia gpu and that's about it. My only harddrive is divided the following way:
C: primary, holds win7 and program files
D: logical, holds my big stuff that doesn't fit the category "system"
G: logical, games, Steam and Firefox (like i said, i'm picky when it comes to this stuff and this G partition is mainly for constantly changing files, so i can defrag with more control and efficiency)
L and S: both logical, L to hold Ubuntu and S for its swap file (respectively 6gb and 2gb)
unmounted0 and inmounted1: both primary, created by Win7 for recovery purposes and stuff, always unmounted

What i'd like to do is
1) keep Win7 and all the rest as it is right now, absolutely no changes to anything in existance
2) install Ubuntu onto the 6GB L partition (i believe linux will label it sda7) with its swap on the 2GB S partition (probably labeled sda8 then)
3) have them dualboot nicely through grub without them tearing each other apart
4) be able to access each partition/usb stick/sd card through both OSs (i use an SD card to hold the music i constantly play, consider it a fixed disk :P). I am aware though that Windows cannot read Linux's ext4 disk format, but i'd be like to be able to access everything else through either OS

---------- ***the issues***
My questions are (with corresponding numbers):
1a) by installing Ubuntu, will anything be changed in my current system, other than the bootloader being replaced by grub and the partitions that i specify during the Ubuntu setup getting formatted to ext4 to fit linux onto them?
2a) L and S are currently formatted as standard NTFS. When i start the Ubuntu installation, will i be able to plainly select them and tell the setup to format both to ext4, then install ubuntu on L (sda7 probably) and put the swap on S (sda8 then)?
3a) will this just plainly work and have my good old win7 (yes, i'm a big fan of win7 despite knowing what a crappy company MS is, dito for everything related to it. And i just hate them for screwing up RareWare, the used-to-be best games developers :( Sure hope they don't go for Retro Studios next) listed in it, along with the newly installed ubuntu? Is there some known bug or somewhat often occurring situation where win7 is not recognised properly and the MBR needs fixing and whatnot?
4a) Yes, how about that? Windows can't access ext4, ok, but can linux/ubuntu access ntfs and fat32? Better formulated: is Windows -> ext* the only couple that doesn't match?

Aside from that, i've also got some general issues but i believe i can fix those by myself, such as some confusion in my mind about mounting partitions and having them appear as dev/sdaX while they're also just in /media... If i can't fix those, i'll ask properly, just ignore that for now ^^


I'm sorry if i come across like i've been living here forever or something, but if you spend your entire day talking to all sorts of people around the globe and reading forum topic after forum topic about all sorts of stuff from economy and war to funpics and surveys, you tend to get tired of those silly introductories and being overly humble. :P Being polite is good of course and i will always be polite, but being "humble" is not part of being polite IMO :P Even if my writings don't sound like it, i really do appreciate any help people offer, as i regularly have to do it myself and i know what a pain it can be sometimes.

Either way, thanks to anyone who can give me confirmation that the steps above are the correct ones, can answer my questions regarding the setup and can point out any roadblocks i might hit along the way ^^. Also, sorry for the wall-o-text but they are a necessary evil sometimes :D

---

### Post by Faziri on 2011-06-01
I just got a PM from Jerrys, but then got an error when trying to send a reply... Supposedly he's set to not receive PMs or he's been punished :P

Jerrys, if you're reading: thanks for the offer but making a telephone call would be pretty costly and silly with the free alternatives like Skype and Steam around...

---

### Post by ashwinrao on 2011-06-01
1a) by installing Ubuntu, will anything be changed in my current system, other than the bootloader being replaced by grub and the partitions that i specify during the Ubuntu setup getting formatted to ext4 to fit linux onto them?


Ans: No, only boot loader will be replaced by Grub. You need to choose partitions manually during installation to prevent formatting of other partitions.


2a) L and S are currently formatted as standard NTFS. When i start the Ubuntu installation, will i be able to plainly select them and tell the setup to format both to ext4, then install ubuntu on L (sda7 probably) and put the swap on S (sda8 then)?

Ans:  Yes, you will get a option to format these partitions during installation if you choose manual method.

3a) will this just plainly work and have my good old win7 (yes, i'm a big fan of win7 despite knowing what a crappy company MS is, dito for everything related to it. And i just hate them for screwing up RareWare, the used-to-be best games developers Sure hope they don't go for Retro Studios next) listed in it, along with the newly installed ubuntu? Is there some known bug or somewhat often occurring situation where win7 is not recognised properly and the MBR needs fixing and whatnot?

Ans: Since you are installing Ubuntu after Windows installation, there will not be any known issues.

4a) Yes, how about that? Windows can't access ext4, ok, but can linux/ubuntu access ntfs and fat32? Better formulated: is Windows -> ext* the only couple that doesn't match?

Ans: Yes, you can access Windows drives(ntfs and fat32) using Ubuntu.

Welcome to Ubuntu family! If you came across any difficulties, post here. Large Ubuntu family members are here to help you.

---

### Post by syntr on 2011-06-01
Hi, I think you're overcomplicating things a bit. :)

You can install Ubuntu quite comfortably to a Windows Virtual Disk using Wubi (Windows Ubuntu Installer). It's the easiest method of installing Ubuntu and can be removed in Windows "Add or Remove Programs" dialog. On boot, you will get the Windows bootloader that will ask which OS you want to boot into. The Wubi installer is right on the disk, and is the disk's "AutoPlay" option.

Of course, you can still install Ubuntu to its own partition, but if you're not sure yet this is great and is a dedicated install that will not require the disk to boot and will not be hindered by optical media read speeds.

---

### Post by Quackers on 2011-06-01
Ubuntu will not install to a NTFS partition and swap will not use a NTFS partition. In that regard I would advise that you delete the L and S partitions on your system from inside Windows, using the Disk Management console.

During installation of Ubuntu you can choose the manual partitioning option (called "something else" in 11.04) and create the partitions for Ubuntu (ext4 for root - mount point " / " and swap) out of that free space that you just created.
As a word of caution I would say that my actual Ubuntu root partition does not have many programs installed and it still takes up more than 4GB of space. So 6GB for the Ubuntu root partition will work, but it doesn't leave masses of space available.

Another word of caution, as I am not absolutely certain how many primary partitions you currently have in use. Please do not exceed 4 at any time. This figure of 4 must include an extended partition as one of them. Any system reserved partition (usually for Windows 7 boot files) is often another.

Ubuntu can access Windows file system but it is not recommended that you write to those files.
A separate NTFS "shared data" partition can be created so that both OSes can read/write data in that partition, if required.

---

### Post by Faziri on 2011-06-01
Syntr ->
one of my linux pals recommended not to use the wubi and i personally also am not in the mood for having a system running on a virtual disk... It's just one of my quirks and i got a few reasons not to want to use it. I was going to at first, but a slightly cleaner install seems better to me... There's also some hard drive space issues and such that i need to keep in mind... My laptop is sometimes very weak in extreme scenarios due to the many personalisations/basic setup changes i make to it, but in the everyday scenarios it runs a dozen times better than the average one :P

Quackers ->
-Ok, so erase L and S to turn them into plain unallocated space, then run the installation and... I guess i will just see the menu with the input fields and everything i need to re-create the partitions then.
-That's ok, i'm not planning to make heavy use of it in the near future and go install truckloads of stuff on it. Although it does raise the question how a nearly 4GB OS fits on a 700MB disc as well (since it comes from that disc...). Obviously file compression would do the trick, but... seriously? That's around 570% compression...
-Yes, i know of the limit of 3 primaries + 1 extended... That is why i spent a lot of time googling if Linux distros have to be installed on a primary or not, since i wouldn't be able to make one if it was needed.
-Ubuntu writing to those files triggers the windows checkdisk, right? Is there any real chance of damaging stuff by writing to it or is that just windows being careful/paranoid/dumb?
-By that extra partition, do you mean just a plain partition like my current D, reserved for shared files or are you talking about a special kind of file management system that prevents the potential mess?


Ashwinrao ->
Ok, thank you, exactly the answers i was hoping to hear :)

So, with my computer prepared as it is at the moment (iso burned to disc, 6gb L: for ubuntu and 2gb S: for the swap, the bootable iso working fine with my stuff) i should have no problems setting it up tomorrow morning, exactly the way i described it above :D

Cool, i'll check back here tomorrow morning and then get started on it. Hope i can get a hang of it and overcome the differences soon enough :popcorn:

I'm going offline now, i've been trying to shift my natural sleeping rhytm from "going to sleep somewhere around 2am" back to a somewhat normal hour to prepare for the upcoming exams, so spending the night till 1:30 on a forum is not the smartest thing to do xD. Thanks for the (very sudden O_o) load of help, guys :D

---

### Post by syntr on 2011-06-01
> 
4a) Yes, how about that? Windows can't access ext4, ok, but can linux/ubuntu access ntfs and fat32? Better formulated: is Windows -> ext* the only couple that doesn't match?

I forgot to mention, Windows can indeed access ext4 disks.
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

---

### Post by jerrrys on 2011-06-01
yep, my mailbox is closed, but you got plenty of help.  so good luck

---

### Post by Quackers on 2011-06-01
Faziri, it might be worth reading through it again.

---

### Post by Faziri on 2011-06-01
> **Quackers said:**
> Faziri, it might be worth reading through it again.
Sorry, through what exactly? A certain chapter of the guides? And related to what exactly?

And now i'm really off, i tried replying 10 minutes ago but i got my usual thrice-a-week bluescreen again, so i made an exception... Something to do with the ZoneAlarm firewall, apparently...

---

### Post by dFlyer on 2011-06-01
All I can say is 6 gigs is not much room for linux. Sure it will fit, but what are you going to use linux for? The more full the partition is will increase the likely hood of linux problems. You might want to ask someone about this. I've never had that problem as I only run linux and never use more than 75% of my disk before replacing it with a larger drive.

---

### Post by larrypg on 2011-06-01
Not sure if this has been suggested....but why not try it from the livecd before you install.  That way you can decide if it is something you want to use.

---

### Post by Faziri on 2011-06-02
> **larrypg said:**
> Not sure if this has been suggested....but why not try it from the livecd before you install.  That way you can decide if it is something you want to use.
I've already done that and i've decided that i want to install it for real [IMG]http://static.pardus.at/img/stdhq/chat/rolleyes.gif[/IMG]

dFlyer -> how many gigs do you suggest then if i'll only use the linux partition for linux itself and its programs, which will only be the sheer basics (firefox, skype, video editor and 1 or 2 more programs)... If it turns out to be too little space, i can always shrink one of the neighboring partitions and increase the size of the linux one. Done it before, i'm comfortable with it. I've also just noticed my windows partitioning program supportd ext3 formatting, but the latest standard is ext4, isn't it?

---

### Post by ashwinrao on 2011-06-02
In my case, it is 10 GB --- /, 15 GB --/home and 2 GB--swap. It is good to have separate /home partition. It helps you to re-install the new Ubuntu version without loosing your contents.

---

### Post by Faziri on 2011-06-14
So, to go over it again... I have 8GB of free space now. I'm only gonna use Ubuntu limitedly so i doubt i'll need much more than that.

Out of the 8GB free space make
-2GB swap partition. Do Ubuntu and the installation itself take care of labeling that partition as the swap partition or do i need to manually do stuff later on?
-4GB root ( " / " ), which is where i suppose ubuntu itself will be installed, along with everything else system-related like programs and all that. I take it the installation will call this your "main" partition?
-2GB home partition for my personal files, which would be the /home folder. How do i go about making that one during the installation (AFAIK the installation only tells you to make the 2 above) and how do i get the installer to pre-define it as my /home?

Once i know that, i can move on to actually doing it, i was hoping to get it done today after studying and changing my windows antivirus :) Thanks for the help so far

---

### Post by jerrrys on 2011-06-14
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+partition&as_qdr=all&sa=Google+Search&lang=en#926](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+partition&as_qdr=all&sa=Google+Search&lang=en#926)

---

### Post by Faziri on 2011-06-14
Ok, i've got it installed succesfully now :) The many negative messages (this not found, that not located, can't install such and so) kinda made me freak a bit but all of it worked fine after all... The sudden change in interface when i installed the nvidia driver (i think it's called Unity) is a pretty big downside since the default interface was much handier to me, but i'll guess i'll get that worked out when i start using it for serious stuff... I also got that weird keyring issue where suddenly no password will do and i had to delete the ring, but whatever... Worries for later, back to Win7 for the moment anyway

Thanks for the help and patience :)

---

### Post by Quackers on 2011-06-14
If you login to Classic gnome you'll get the old desktop back.
Glad you got things working ok :-)

---

### Post by Faziri on 2011-06-28
I've got a new question related to my current setup, hence why i'm posting it here... I've already tried googling it but it seems that my setup is rather rare and nobody has bothered writing a page with the info i need (as far as google can tell anyway) :o

A few days ago, i experienced the hard way that the grub bootloader doesn't quite like Windows changing partitions (had to reinstall grub from the live cd after getting the grub rescue mode). So, that of course means that i'll have to do all my partitioning via GParted and then make sure to run an updategrub. I'm just wondering: will that have any effect on Windows? I can't quite imagine Windows freaking out just cause there's a new partition that was created while it wasn't active, but you never know in situations like these... Especially not with Windows, lol

---

