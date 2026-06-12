---
title: "Questions from a soon-to-be-Ubuntu-user"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by 10011010010 on 2011-07-27
Hello,  I plan on setting up a dual boot tomorrow so that I can try (and hopefully stay with) Ubuntu. I have went to multiple sites and looked at several guides to installing it. The problem is that many of them are about different versions. This is what I have gathered from what I have read (Please point out anything that is wrong, that is, after all, why I'm here).     First I have to download it and get it on a CD (yada, yada, yada, this is well explained on the site). Next I need to boot from the the CD. From there I can try out the OS a bit before I set up the dual boot if I so please.  On the desktop there will be an "Install Ubuntu" icon which I can click on to (big surprise) install Ubuntu.  From there I will go through a relatively self explanatory setup wizard. When asked how to install Ubuntu I should select "something else" and it will allow me to partition the hard drive and set up the dual boot. From there I can fill some more things out and get Ubuntu working.  Did I get anything wrong? Also, tips on what things that I should do first with Ubuntu once I get that working would be greatly appreciated.

---

### Post by XBMC old School on 2011-07-27
[LIST=1]
[*][install restricted formats ]("https://help.ubuntu.com/community/RestrictedFormats")sudo apt-get install ubuntu-restricted-extras
[*]Then install all gStreamer formats for video playback (Synaptic package manager).
[*]Install and configure [Compiz-Fusion]("http://www.youtube.com/watch?v=SJaTA25tpMg")
[*]Install and configure Avant-windows-Navigator [AWN]("http://wiki.awn-project.org/")
[*]Install and configure [Screenlets]("http://screenlets.org/index.php/Download")
[/LIST]
 There is a start. I will add more if you like.

I would recommend using the Ubuntu 10.04 LTS (USB install is faster).

The Gnome shell 3.0 and/or unity might be a hard start.

---

### Post by XBMC old School on 2011-07-27
As well i would recommend a fully separated install, install ubuntu on it's own drive, if you can. And run the dual boot through the BIOS. If you install side by side and decide to dump ubuntu it will take the windows boot file with it. So to fix it you will have to do DOS based commands to rebuild the file. fun. Made that mistake.

---

### Post by Wim Sturkenboom on 2011-07-27
Advise:
[LIST=1]
[*]make backups of your important data before you start 'fiddling' with harddisks / partitions; a mistake is easily made
[*]defrag your windows drives (c, d etc) before resizing partitions; this can take a while so have coffee ready or do it at night
[/LIST]

Good luck

---

### Post by uRock on 2011-07-28
Hello and welcome to the forums,

Just to add to what has already been said. If you have Vista or 7, then creating the boot repair disk, which is usually found under the back up utility, can be a good thing should any problems arise during the install.

I have completed many installs and luckily have needed to restore anything, but it is good to have backups when things go south.

Cheers,
uRock

---

### Post by HermanAB on 2011-07-28
Howdy,

Backup your data and get a Windows install disk before you start, since you will probably mess everything up and will probably repeat the install 2 or 3 times before you get it to your liking.

The only way to ensure that you do not need a backup, is to carefully and laboriously make one first...

---

### Post by wildmanne39 on 2011-07-28
Hi, when you install enable update and third party software it will save you problems later.

Also here is a nice guide on installing Ubuntu it is for 11.04.

Unless you just need to set partitions manually I would just choose use half the disk for ubuntu install.

One last piece of advice if you only have on hard drive make sure you install grub boot loader to sda and not to the mbr of windows or to say sda1 or sda2 none of those numbers just to sda. 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by 10011010010 on 2011-07-28
Thanks for the input everyone. I'm going to backup my computer then I'll see what Ubuntu has to offer :)  > **XBMC old School said:**
> 
[LIST=1]
[*][install restricted formats ]("https://help.ubuntu.com/community/RestrictedFormats")sudo apt-get install ubuntu-restricted-extras
[*]Then install all gStreamer formats for video playback (Synaptic package manager).
[*]Install and configure [Compiz-Fusion]("http://www.youtube.com/watch?v=SJaTA25tpMg")
[*]Install and configure Avant-windows-Navigator [AWN]("http://wiki.awn-project.org/")
[*]Install and configure [Screenlets]("http://screenlets.org/index.php/Download")
[/LIST]
 There is a start. I will add more if you like.

I would recommend using the Ubuntu 10.04 LTS (USB install is faster).

The Gnome shell 3.0 and/or unity might be a hard start.

 Thanks, I'll clean out a 4G USB stick

---

### Post by 10011010010 on 2011-07-28
Quick question, to manually choose the partition sizes and have my computer ask me what OS to use when I turn it on, I do "something else," not "alongside windows," right?

---

### Post by fractalman on 2011-07-28
My advice would be to save any data you want to keep (media,documents, etc) to a disc/usb/ext hdd .

Then download a copy of dariks Boot and nuke (DBAN) and burn to disc

then boot your pc from the dban disc and totally nuke your hard drive, this will write the whole drive as 0's or 1's and the end result is a totally blank drive, as good as a brand new one!

then install Ubuntu and never look back!!! :)

if you choose 'alongside windows' it will just put it alongside windows automatically

if you choose 'something else' it will give you a partition table, from here you can fromat the whole drive and remove windows or reduce the windows partition.

Doing it this way you will need to
set a mount point  select the symbol  ./
then set the size of the partition you want and choose 'home'  (i think thats what it's called)
then set another small (2-8g should suffice)partition for swap  

then continue, it is really simple to install, i've done about a dozen installs now with absolutely no probs, dual boot and solo

you wil get a grub menu when you boot the pc and you just select the o/s you want, windows or linux.  it is really easy, i was apprehensive at first but seriously don't worry!

---

### Post by mastablasta on 2011-07-28
> **10011010010 said:**
> Quick question, to manually choose the partition sizes and have my computer ask me what OS to use when I turn it on, I do "something else," not "alongside windows," right?
 
 
yes. it's also better to partition disk before instalation with windows disk manager.
 
also you need to defragment the disk about 2 times before attempting repartitioning. failing to do that increases the chances of data loss and corrupt files.
 
also you can create just single empty space and let the Ubuntu parition it automaticly. if you want you can always add partition later on. 
 
seriously oyu should tryi it out in live session first to see if you hardware is supported.

---

### Post by 10011010010 on 2011-07-28
Thanks for the info, I'm getting it on a USB stick now...

---

### Post by gigenieks on 2011-07-28
[QUOTE=XBMC old School]
Install and configure Compiz-Fusion
[/QUOTE]
Why? It **don't** enable basic "average" user needs (getting mp3 working, flash in browser). Things like that.
Compiz is just "eye candy".
I am new to Kubuntu too, which is Ubuntu but with KDE instead of Gnome desktop.

And I _haven't_ even enabled my (ATI) video card's drivers. :biggrin:
And have no need yet (everything is smooth)!


As uRock said:

> 
If you have Vista or 7, then creating the boot [COLOR="Purple"]**repair disk**[/COLOR], which is usually found under the back up utility, can be a good thing should any problems arise during the install.

It's simply a must! 

As for --->

[QUOTE=wildmanne39]
Hi, when you install enable update and third party software it will save you problems later.
[/QUOTE]
Judging from my experience with Kubuntu 11.04, **I recommend not to enable it. **
It probably caused major crash for me (had to reinstall Kubuntu :( )
Codecs to install - easy
Flash to install - easy (had to do some research)

[SIZE="3"]Ahh you didn't mention your hardware and will you install 32bit OR 64bit OS?[/SIZE]


[QUOTE=fractalman]
then set another small [SIZE="2"]**(2-8g should suffice)**[/SIZE]partition for swap
[/QUOTE]
:shock: OMG!
Why SOO much? 
[COLOR="DarkRed"]**I installed 64bit Kubuntu on 1GB system.**[/COLOR] And I did set only 1GB swap. And everything is fine! 
Kubuntu uses from 400-750MB of RAM. And from 200 to 400MB swap (mostly 0 swap).
Everything works.
So the question is: why in the world should he use 2GB - 8GB swap??

---

### Post by 10011010010 on 2011-07-28
Little problem.

At the "Allocate drive space" menu I selected "something else." The menu turned out not to look like what I had seen in guides and I don't understand it. I looked online and found the guide here [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) . It was very helpful as it told me if I select that option "you don't need a tutorial telling you what to do. " Fair enough, I went back to choose "Install Ubuntu alongside Windows 7," which the guide told me would allow me to choose which OS to use when I turn on the computer and would allow me to partition the hard drive, which is what I wanted in the first place. Little problem, the only options I have are "Replace Windows 7 with Ubuntu" (not happening) and the "Something else" that I had already tried. There is no "Install Ubuntu alongside Windows 7." Everything about the Install menu's look the same, other than that missing option. Could I either have an explanation and a way to get to that option, or a little help getting through the "Something else" menu?

Thanks in advance

In reply to a previous post: I chose the 64 bit version and my computer should be able to handle it (I have a SONY VAIO VPCF115FM Laptop)

Edit: Would screenshots help?

---

### Post by 10011010010 on 2011-07-28
Presumably /dev/sda is the partition that would be made (it has nothing listed for type mount point format size and used) and /dev/sda3 is the one with windows on it (it is  the size of my hard drive). If so, should I reduce the size of  /dev/sda3 and increase that of /dev/sda? One thing that makes me think  that that is wrong is that the default selection for boot loader  installation is /dev/sda ATA blahblah... (500.1 GB), making me think  that that might refer to the entire hard drive. I guess I could quit from the installer and make a partition through windows then select that one. Any reccomendations?

---

### Post by XBMC old School on 2011-07-28
I'm no expert but the problem maybe that there is no available partition. 

Please tell me you have backed up all your data (usb harddrive) and have a windows disk (as stated above). It's balzzy to do what your doing, for sure. i had separate OSs on separate drives before i decided to dump the big piece of sh*t they call Windows.

Wait for more responses but if you are in the liveCD (usb). I think you need to use the disk manager to re-size your windows partition. MAKE NOTE OF WHICH PARTITION IS WHICH!!! sda1 or sda2. 

Though the same disk manager should be in the installer. Which version of ubuntu are you installing? 10.04 or 11.0x?  Find an appropriate tutorial.

Wait for more information from the above commentors

---

### Post by 10011010010 on 2011-07-28
> **XBMC old School said:**
> I'm no expert but the problem maybe that there is no available partition. 

Please tell me you have backed up all your data (usb harddrive) and have a windows disk (as stated above). It's balzzy to do what your doing, for sure. i had separate OSs on separate drives before i decided to dump the big piece of sh*t they call Windows.

Wait for more responses but if you are in the liveCD (usb). I think you need to use the disk manager to re-size your windows partition. MAKE NOTE OF WHICH PARTITION IS WHICH!!! sda1 or sda2. 

Though the same disk manager should be in the installer. Which version of ubuntu are you installing? 10.04 or 11.0x?  Find an appropriate tutorial.

Wait for more information from the above commentors
11.04. I backed everything up (and even if I didn't I haven't changed anything yet as I am waiting for answers).
If I'm not told otherwise within around 20 mins, I'll cancel the installation (it's not too late yet) go back to windows, make a partition there then come back to the liveCD and select it.

Edit: Also: [http://i564.photobucket.com/albums/ss90/Titanium_Crusher/Screenshot-Install.png?t=1311871575](http://i564.photobucket.com/albums/ss90/Titanium_Crusher/Screenshot-Install.png?t=1311871575)
I was expecting [http://www.psychocats.net/ubuntu/images/installingnatty06.png](http://www.psychocats.net/ubuntu/images/installingnatty06.png)

---

### Post by Miljet on 2011-07-28
Sda refers to your entire hard drive. Sda1 or sda2 and so forth will refer to any partitions on that hard drive. You will want to install GRUB (boot loader) to sda (the hard drive itself), not to any partition.

---

### Post by sanderd17 on 2011-07-28
In Linux, /dev/sdX is refering to hard drive letter X, and /dev/sdXY is referring to partition number Y on that hard drive. So /dev/sda is your primary hard drive.

If you don't have the "next to windows", you should best go back to Windows, shrink  the Windows partition and do nothing with the empry space. Than you would see a new option to use the "empty space".

The OS Ubuntu can run on 4GB (without files), but I would at least advise 25GB if you don't want to get in trouble with the space.

---

### Post by 10011010010 on 2011-07-28
> **Miljet said:**
> Sda refers to your entire hard drive. Sda1 or sda2 and so forth will refer to any partitions on that hard drive. You will want to install GRUB (boot loader) to sda (the hard drive itself), not to any partition.
So I would want to make another partition (/dev/sda4 it would be). I know how to do that in windows so I'll boot into that, create one then come back here and install Ubuntu on it.

---

### Post by Miljet on 2011-07-28
No, don't use Windows to create another partition. Just shrink the Windows partition and leave the space created as unformatted. Ubuntu will create what it needs in the unallocated space. Windows is unable to create the type partition that Linux uses anyway.

---

### Post by gigenieks on 2011-07-28
In few minutes here will be answer. Be patient.

---

### Post by XBMC old School on 2011-07-28
I concur not a pro. As well, it is a general consensus that unity is kind of "funky" so running as classic might be beneficial.

As for doing things with ubuntu, and getting responses through the forum. 20mins might be to small a window. Especially when it is not ideal to rush things. I don't know where you live but posters come from all over the world. So people can't respond while they are at work or sleeping.

In this thread alone, we got, Latvia, Texas, New Mexico, British Columbia, Flanders & (the MoJAve?)

I would like to reinforce the idea that the 10.04 LTS (Long Term Support) is a better version. As well 32bit is a much better way to go for running software. But if you insist you should install the 32bit libraries.

sudo apt-get install ia32-libs in terminal

---

### Post by 10011010010 on 2011-07-28
Alright, I'll try to be patient, but it's a little stressful. So everything was fine I had just hit install now when it prompted me about swap space, which I had forgotten, I went back and then it froze. I am writing this on my phone right now as while the cursor moves, nothing, as a windows user would say, responds. What should I do?

---

### Post by XBMC old School on 2011-07-28
> **gigenieks said:**
> Why? It **don't** enable basic "average" user needs (getting mp3 working, flash in browser). Things like that.
 Compiz is just "eye candy".
 I am new to Kubuntu too, which is Ubuntu but with KDE instead of Gnome desktop.
 
 
 OK punchy chill out. I never said my response was a definitive answer  (it's a forum). i said restricted formats w/ gstreamer. Eye candy is  what some people come to linux for. 
 
 i to am leaning towards Kubuntu. Much better eyecandy and workspace manager. But everthing else, *eh*.
 
 As for swap? Why make it so tight? The last time i looked online laptops had 500GB HDDs. Is there a standard size? %?

0101010100101 - one of the reasons for swap is the hibernation function requires it.

---

### Post by XBMC old School on 2011-07-28
> **10011010010 said:**
>  I am writing this on my phone right now as  while the cursor moves, nothing, as a windows user would say, responds.  What should I do?

A second computer w/ internet access would be good. You got to explain more. Be back in two hours.

Shouldn't have jumped the gun on [gigenieks]("http://ubuntuforums.org/member.php?u=537072")

---

### Post by 10011010010 on 2011-07-28
> **XBMC old School said:**
> A second computer w/ internet access would be good. You got to explain more. Be back in two hours.

Shouldn't have jumped the gun on [gigenieks]("http://ubuntuforums.org/member.php?u=537072")
I posted everything that happened; at the aforementioned swap prompt I pressed back and now Ubuntu is frozen.

Edit: though I did just notice that the light on my USB drive is no longer flashing. Whether this means that the problem is with the USB stick or that that was caused by another problem, I don't know.

---

### Post by XBMC old School on 2011-07-28
are you in the liveCD can you printscreen it?

Not a big issue right now but i use my signature to show all my information easily.

---

### Post by 10011010010 on 2011-07-28
> **XBMC old School said:**
> are you in the liveCD can you printscreen it?

Not a big issue right now but i use my signature to show all my information easily.

All that I can do is move the cursor around the screen. And yes, I'm at the allocate disk space menu in the liveCD

---

### Post by XBMC old School on 2011-07-28
Is the install running? If it is fully frozen then maybe the only thing you can go is restart and prey that you can get into windows. But the cursor should be frozen.

i would restart. You can't do anything now soooo....

[SIZE=1]*_Not liable._*[/SIZE]

If you restart into windows then reboot into the liveCD (try ubuntu), setup your partitions and then printscreen & post.

---

### Post by gigenieks on 2011-07-28
> **10011010010]
There is no "Install Ubuntu alongside Windows 7.
a little help getting through the "Something else" menu?
[/QUOTE]
No worries. We will help you. Just be patient and **calm** :biggrin:



[QUOTE=Miljet said:**
> 
Sda refers to your entire hard drive. Sda1 or sda2 and so forth will refer to any partitions on that hard drive. You will want to install GRUB (boot loader) to sda (the hard drive itself), not to any partition.

I couldn't explain better. Read this post at least 3 times!


> **10011010010]
So I would want to make another partition (/dev/sda4 it would be). I know how to do that in windows so I'll boot into that, create one then come back here and install Ubuntu on it.
[/QUOTE]

Some posts on the forums --->

[QUOTE=westie457 said:**
> 
After you have reinstalled Vista the best thing to do is Start-button > Right click on Computer > Select manage. In the next window in the left-hand pane **Storage > Disc Management.**

Depending on you PC maker you will see 1 partition may be more upto 4. If you have four partitions come back here for advice. If only one Right-click and select [COLOR="Purple"]**shrink volume to whatever size you want**[/COLOR]. 

Okay to all questions and wait. [COLOR="DarkRed"]**When it has finished leave the new space unformatted.**[/COLOR] The LiveCD will be able to make proper use of it.

_Sometimes_ Windows can be very picky when its partitions are adjusted from another operating system.

> **JASONFUSARO said:**
> 
You might want to shrink the windows partition after it is installed using windows partition manager, this way windows will manage **_it's own partitioning scheme_** and you [COLOR="DarkGreen"]**will steer clear of problems**[/COLOR] that may arise using Gparted or any that are supplied in Linux, it will be the safest route. 

I re-installed my windows and shrunk it to about 1oo GiB on my 500 GiB hard drive and then created the other partitions using windows partition manager and when I installed Ubuntu I just pointed to the already partitioned partition.




> **Blasphemist said:**
> 

I to recommend starting in windows. Run defrag in windows to try and get that done as best you can. 

[COLOR="DarkSlateGray"]I'd then use ubuntu to shrink the windows partition. Use GParted to look at your partitions. As oldfred said, you may already have the maximum of 4 primary partitions. If so, likely at least one of them is a waste. For instance I had a partition that would have recovered my windows to it's original vista, as if I'd want that. :)[/COLOR]

 In the end you want to be able to [COLOR="DarkRed"]**have an extended partition that can have both ubuntu and a swap in it**[/COLOR]. Swap should be a little more than your memory. 


I edited them a bit (colors) so you start to have some understandings how & why.

Also [Ubuntu Guide says following:]("http://ubuntuguide.org/wiki/Ubuntu:Natty#Installing_Ubuntu")

> 
After shrinking a Windows partition, you should reboot once into Windows prior to installing Ubuntu or further manipulating the partitions. 

This allows the Windows system to automatically rescan the newly-resized partition (using chkdsk in XP or other utilities in more recent versions of Windows) and write changes to its own bootup files. (If you forget to do this, **you may later have to repair the Windows partition bootup files manually using the Windows Recovery Console.**)

Newer installations of Windows use two primary partitions (a small Windows boot partition and a large Windows OS partition). 

An Ubuntu Linux installation also requires two partitions -- a **linux-swap partition and the OS partition.** 

The Linux partitions can either be two primary partitions or can be **two logical partitions within an extended partition**. 

[COLOR="Sienna"]**Some computer retailers use all four partitions on a hard drive.**[/COLOR] Unless there are two free partitions available (either primary or logical) in which to install Ubuntu, however, it will appear as if there is no available free space. If only one partition on a hard drive can be made available, it must be used as an extended partition (in which multiple logical partitions can then be created). Partition management can be done using the GParted utility.


So I gave some links and quotes for better understanding (english is not my native language..)

Anyway how shoud you continue:



[SIZE="4"][CENTER]Step 1 [/CENTER][/SIZE]

Note, if you want dual-boot (recommended for starters) with Windows on same hard drive.

1. Defragment your hard drive and preferably do CHKDSK on restart (just to be sure that everything is fine with windows filesystem)

2. Then go My Computer (right click) > Manage > Disc Management.
I am assuming you are using ALL hard drive (that is, it isn't partitioned, right?)

If so continue as follows:

3. Right click on Windows 7 partition > Shrink volume > (give Ubuntu as much space as needed)
a. If it don't give you enough space, come back and say how much it is giving..

So, now you have shrinked space for Ubuntu and it IS UNFORMATED, meaning it says "unalocated space" This is what you want.

You have prepared for installing Ubuntu!


[SIZE="4"][CENTER]Step 2[/CENTER][/SIZE]

1. Boot Live CD and use install Ubuntu.

2. In [Your install screen]("http://i564.photobucket.com/albums/ss90/Titanium_Crusher/Screenshot-Install.png?t=1311871575")
choose "Something else".

Then you have to make 2 partions root with Ext3 filesystem and mount point / (this is your Ubuntu) AND swap partion filesystem swap. Give it at least as much space you have RAM in your computer. Maybe more if you planning to use "hibernation" function.

3. If your windows is on sda hard drive. Install GRUB 2 bootloader to sda!


[SIZE="4"][CENTER]Step 3[/CENTER][/SIZE]

1. Install. And when it is installed --->
2. Boot first to Windows first, so it could changes needed.
3. Boot Ubuntu if everything works --->

CONGRATS!


[COLOR="Navy"]**Any questions?? Feel free to ask.**[/COLOR]

---

### Post by 10011010010 on 2011-07-28
> **XBMC old School said:**
> Is the install running? If it is fully frozen then maybe the only thing you can go is restart and prey that you can get into windows. But the cursor should be frozen.

i would restart. You can't do anything now soooo....

[SIZE=1]*_Not liable._*[/SIZE]

If you restart into windows then reboot into the liveCD (try ubuntu), setup your partitions and then printscreen & post.

Sounds like the only thing I can do, I did back everything up first so even if the worst happens...

---

### Post by 10011010010 on 2011-07-28
I'm in windows right now looking at the disk manager. Nothing's broken :) . I'll try again...

---

### Post by gigenieks on 2011-07-28
> 
All that I can do is move the cursor around the screen. And yes, I'm at the allocate disk space menu in the liveCD


Ahh... I see you have problems which you **could** avoided if was just a little patient and did a little research! (just advice)


[QUOTE=XBMC old School]
OK punchy chill out. I never said my response was a definitive answer (it's a forum). 

As for swap? Why make it so tight? The last time i looked online laptops had 500GB HDDs. Is there a standard size? %?

0101010100101 - one of the reasons for swap is the hibernation function requires it.
[/QUOTE]
I think you misunderstand me! Goal of my note about compiz was to help **0101010100101**. **_First_** lets configure and make work basic things. If you try to do all at once (especially if you are new to linux or whatever else) information can "overload" you... 

I guess I am used to have restricted hard drive space, while others have already 500GB or 1TB hard drives, so **for me** every GB is important :biggrin:
Sorry.

As for hibernation, if he have a laptop and _will_ use hibernation (autor?) then yes - make bigger swap. If not, judging from my own experience (a week or so) you DON'T need more than 1GB swap.

Now offtopic --->

[QUOTE=XBMC old School]
Eye candy is what some people come to linux for. 

i to am leaning towards Kubuntu. Much better eyecandy and workspace manager. But everthing else, eh.
[/QUOTE]
I think most people come to linux for 3 reasons --->
[LIST]
[*]It's free!
[*]You don't have to worry about viruses etc
[*]Community is awesome and very organized.
[/LIST]
"Eye candy" stuff is very nice bonus.

Great to hear, that you are going toward Kubuntu. Come and help me with "eye candy" stuff :biggrin:

---

### Post by gigenieks on 2011-07-28
> 
I'm in windows right now looking at the disk manager. Nothing's broken  . I'll try again...

[COLOR="DarkGreen"]**Follow my steps in post #31  and everything will be fine, fast and easy!**[/COLOR]
I did install Kubuntu that way. And I am new too.

---

### Post by 10011010010 on 2011-07-28
Installed everything looks good and I'm looking forward to getting to know Ubuntu. Thanks for your help everyone.

---

### Post by XubuRoxMySox on 2011-07-28
> **10011010010 said:**
> Installed everything looks good and I'm looking forward to getting to know Ubuntu. Thanks for your help everyone.

Congratulations! Let us know how it goes. And be sure to mark this thread as **[COLOR="Purple"]SOLVED[/COLOR]**, so others can read it and benefit from it as you have.

To mark it as SOLVED, Edit your original post, choose Advanced Options, and change the Subject line adding the tag SOLVED at the beginning of the Subject line.

---

### Post by XBMC old School on 2011-07-28
I assumed that 0101101001 had passed the install stage. Awesome complete post "#31". It's been a while since i have done a fresh install.

> **gigenieks said:**
> 

Great to hear, that you are going toward Kubuntu. Come and help me with "eye candy" stuff :biggrin:

I would be glad to help if i can. It is self explanitory. Just gotta mess with it.

I like Kubuntu because the workspaces are separate (active window panels, desktop icons, wallpapers, even tasks (games, word processing, internet). And all the eyecandy is built into the install no software installs ect.  i just like the traditional setup of the panel (home, applications & system). maybe i should look at a tut for getting kubuntu to look like ubuntu. The screenlet widgets are week in ubuntu too.

I've been on ubuntu (winFree) for a year and don't miss it. i got windows at work. If Civil3d worked on linux i would kiss windows goodbye.

---

