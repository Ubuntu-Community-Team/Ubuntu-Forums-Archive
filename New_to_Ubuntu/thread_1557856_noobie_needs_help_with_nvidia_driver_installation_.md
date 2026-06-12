---
title: "noobie needs help with nvidia driver installation on 8.04 LTS"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by John Galt on 2010-08-21
Hello everyone,  I recently dual booted windows xp and ubuntu 8.04 LTS. The problem is; being a noob with linux, i am not able to figure out how to install the nvidia driver for my gforce 4 mx 4000 graphics card.  I downloaded the driver from the nvidia website and being a windows afficondo for a decade thought that double clicking the installer would work on linux too.   What happens is that a pop up wants to confirm what action needs to be taken for the file - whether to run it in a terminal or a text file or some thing of that sort. After a few minutes of click and try, the terminal window shows that the installer needs to be run as root.  I do not know how to proceed from here and any help would be welcome.  Please help me setup my graphics card as without it my screen sort of looks like a tenth of it has shifted into oblivion.  As mentioned before; I have been a windows afficondo for over a decade and now, feel that it is time that I try out the open source a try as windows no longer holds my attention for it's resource hungriness.  My system details are as follows:  asrock 845gv chipset  pentium 2.4 Ghz  512 mb ram  a 40 gb hard drive to dual boot xp and linux (xp is ntfs partioned and linux has one root in ext3 and a swap.)  an 80 gb harddisk for data (in ntfs ofcourse).  a dvd combo drive; samsung.  a gforce 4 mx 4000 graphics card.  I understand that a question like this might have been answered previously on this forum, but it would be nice if someone among this ubuntu community took time for this linux noob.  I would like to bring to your kind attention that i am in the process of learning ubuntu through an ebook but got to tell you that without a working os it is difficult to do so. Hence my pressing need that this problem be answered.  Thanking you for helping me resolve my query.

---

### Post by realzippy on 2010-08-21
Welcome!
it is not to hard to install the nvidia driver manually,but have you been at
System/Administration/Hardwaredrivers?Is there any driver offered?
if not,I suggest to add the [xswat]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") ppa to your system,since there are patched drivers available.
All you need to know is how to open a terminal...
feel free to ask,can get a step-by-step guide if you want..

BTW,why not running 10.04LTS since support will be dropped for 8.04?

---

### Post by oldsoundguy on 2010-08-21
an FYI.  "NVida Current", the driver that is in most of the hardware drivers file, will NOT work on anything older than a 6 series card. So I am replacing the boatload of 5500 cards in my Ubuntu machines.  Found that out the hard way. Either update your card or be content to run the generic drivers without all the bells and whistles.  The generics for 10.04 are VERY good, just not gaming/eye candy standards.

---

### Post by realzippy on 2010-08-21
@ oldsoundguy:

  What about alberto milone's xswat 96 driver,which I would have suggested?

---

### Post by oldsoundguy on 2010-08-21
Alberto's package (Envy) would not work on 10.04 with a 5500 card.  Tried that.  It MAY be working now, though.

Just found it easier to get a more up to date card.  (granted, some bucks involved .. but I found what I needed on eBay at a reasonable price, and updating was painless.)
And the improvement in video performance was REALLY notable.  Some issues such as slow scrolling went away!

I am NOT against attempting to use legacy stuff on Linux .. after all, that is the intent .. to not just "throw it away" .. opposite of the Windows philosophy.  But, comes a time, when some upgrading just make life easier.

---

### Post by realzippy on 2010-08-21
Not talking about alberto's envy script;the updated nvidia 96 driver(xswat PPA),which should work fine in 8.04 ...
Not everybody here in the forum can grab an old nvidiacard for "20 bucks"...since
this makes a month' food in some areas...
Ironically I own an old geForce 7950,only 256Ram,works perfectly in ubuntu and nobody I know wants it,so it is wasted in the cellar somewhere...

---

### Post by John Galt on 2010-08-22
Thanks a lot Mr realzippy, Mr oldsoundguy,

I really appreciate your quick reply.

First of all I would like to tell you that I did go about looking for the latest version of ubuntu to install and as luck would have it the only working disk that i could pull of the streets was 8.04 LTS. Tried 9.10 (faulty disk) and two live dvds for 10.04 (both fail to even boot properly). Linux is not a very popular OS in Delhi. Had a tough time finding this one working version in itself.

You may be wondering why not download it off the internet. My internet allows me a limited amount of data to be downloaded per month and I would blow it an a matter of minutes if i were to download an os like ubuntu. Hence, my reliance on computer magazines for linux distributions.

Anyways, coming back to the point... I did check the System/Administration/Hardwaredrivers and there are no drivers offered :(

That option when you can enable a harware by clicking on it and the system wants to confirm the enable by a restart; i tried it several times but everytime i still find a part of the screen missing.

Also about this xswat ppa; please elucidate a bit more as I am confused what are these and if i need an internet connection in linux to download these updates. The web site also does not give any reference on how to install these in 8.04; it offers version upto 8.10.

Also any help with the nvidia driver (NVIDIA-Linux-x86-96.43.18-pkg1.run) already downloaded would surely be appreciated.

Um.. another query; do drivers like these (for graphic cards like nvidia); do they come bundled in the recent releases?

Also I have no clue on how to setup my internet in Linux yet so downloading anything though ubuntu is out of the question. All this communication is being done through win xp for the moment.

Please revert with your comments and helpful suggestions. I once again thank you for taking time to help me with this predicament of mine.

---

### Post by realzippy on 2010-08-22
Ok,so why not installing the nvidia-driver you already have on good old 8.04:

1.Copy your NVIDIA-96xx.run file to Desktop.Log out.
2.Press alt+ctrl+F2
3.Login at the console as your user
4.```
sudo /etc/init.d/gdm stop
```
5.```
cd Desktop
```
6.```
sudo sh NVID
```  (press "TAB" for autocomplete)

7."YES" to all questions
8.```
Sudo reboot
```

If this work,be careful with updating xserver/kernel related packages..,this
results in reinstalling the manually installed driver and may even be incompatible to that driver.That's why I thought about the 96.xx driver from xswat since this might be the most
polished version.The 8.10 driver might work in 8.04,since it is a question of linux-kernel/Xorg-server version and not of the "Ubuntu nomenclature"...

---

### Post by Zill on 2010-08-22
> **John Galt said:**
> ...I would like to tell you that I did go about looking for the latest version of ubuntu to install and as luck would have it the only working disk that i could pull of the streets was 8.04 LTS. Tried 9.10 (faulty disk) and two live dvds for 10.04 (both fail to even boot properly). Linux is not a very popular OS in Delhi. Had a tough time finding this one working version in itself...
You *should* be able to buy the latest Ubuntu CDs/DVDs in India.  For example, I had a quick look on [www.google.co.in]("www.google.co.in") and found [LinuxFlavour]("http://linuxflavour.co.in/zen/index.php?main_page=index&cPath=3") offering Ubuntu v10.04 Lucid Lynx Full Install/ Live i386 DVD for Rs100.

---

### Post by John Galt on 2010-08-23
respected mr realzippy,

as soon as I log off and hit alt+ctrl+f2 i am greeted with a lime coloured scrambled screen which occupies three quarters of the computer screen. This persistent screen refuses to change into any terminal or a command screen (tried waiting for whole 15 minutes thinking some miracle would happen in a few moments ;) ).

No other improvements so far to show in terms of driver installation; status quo maintained and await your respected and appreciated guidance.

Thanks for your patient ear and hope that the next time my problem becomes a no problem for the both of us. 

P.S I really find it uncomfortable to disturb you over and over again like a cry baby. I would not have done so if i could help it.


Respected Mr Zill,

about the installation disks that i use for installing linux, you will find that disks of various computer magazines which bundle assortment of softwares for all major os's are dime a dozen and piled up along the streets in a flea market. This makes buying them quite cheap and it works most of the time. The only problem that you are to encounter when buying them is when the disks come corrupted from the manufacture's side themselves (which are of course an impossibility to detect.) And this is the problem that i have been facing lately. Anyways, as is quite evident i am a complete novice when it comes to linux; you got to start somewhere. let me get my feet wet with 8.04 and then when i feel that i can manage on my own; I will get myself the latest distro.

BTW thanks for the info that i could buy it through a web site. I thought you have to download it or that cannonical ships to you for free. Did not know that there were sites that sold linux too (apart from red hat linux). Maybe my research was incomplete.

---

### Post by realzippy on 2010-08-23
So have you tried to boot in recovery mode?
If this should work,drop to root shell and install it from there.
You can leave out the "sudo" in the commands,for
```
cd Desktop
```

you had to type

```
cd /home/*yourusername*/Desktop

```


P:S:
You are welcome,not disturbing.The forum is made for asking questions..


Edit:

If booting in recovery mode does not work also,you can try to boot with special parameters like:
**vga=771** or **xforcevesa**.See chapter "*Change Boot Options Temporarily For An Existing Installation*"
in [this]("https://help.ubuntu.com/community/BootOptions") guide.

---

### Post by John Galt on 2010-08-24
Respected Mr realzippy,

tried your method to install the nividia driver by logging in the recovery mode. Now some new issues have cropped up.

I trace my steps for your better understanding. 

First I copied the driver in the root folder where the desktop folder was (not inside the desktop folder.) Then I changed the long winded name of the driver into plain and simple nvidia.run. From then on, it was just the way you taught. Logged of and booted into the recovery mode stopped the gnome and sh'ed the driver. (believe me took a lot of trial and error just to get this going.)

At the time of writing this entry, the system still boots without an nvidia driver because of the following errors.

1) This error appears first as soon as the sh command is given and states the following:

" you apear to be running in run level 1; this may cause problems. For example; some distributions that use devfs do not run devfs daemon is run level 1; making it difficult for 'nvidia-installer' to correctly setup the kernel module cnfiguration files. It is recommended that you quit installation now and switch to run level 3 ('telinit 3') before installing. "

After this message the system wanted to confirm to proceed with a simple yes or a no. I still wanted to proceed just to see what happens. So I took the yes option and now i am greeted with the next error which I have illustrated in the next point.

2) "You do not appear to have libc header files installed on your system. Please install your distribution's libc development package."

After this the installer did not proceed and here I am writing again to you.

Please tell me how to proceed further.

---

### Post by realzippy on 2010-08-24
*It is recommended that you quit installation now and switch to run level 3 ('telinit 3') before installing. *

Ok,the nvidia-driver seems to need runlevel3 for building the kernel modules.
So,type:

**telinit 3**

then run the driver installation...

---

### Post by John Galt on 2010-08-24
After having logged into root and stopped gnome i gave the command telinit 3.

the system again stated the gnome and asked me to log on and hen i was greeted by the home screen. Then i opened a terminal and again gave the command to stop gnome and then started the installer again.

this time the error message was "You do not appear to have libc header files installed on your system.  Please install your distribution's libc development package."

Please advise how to proceed from here.

---

### Post by realzippy on 2010-08-24
You have still no internet with that machine?That is bad.Generally a linux system
needs it for package management.So you can try to install [packages]("http://packages.ubuntu.com/hardy/allpackages") manually (downloaded from another computer or your UbuntuCD):

libc6-dev libc6-dev-i368 libc6 linux-libc-dev

Maybe it would be more important to fix the internet first than to install the nvidia-driver!


The dev packages you need are also included in *build-essential* (what should be on your ubuntu CD,but I do not know),so open synaptic and check if your ubuntuCD is in the sources and simply install:
build-essential

---

### Post by realzippy on 2010-08-26
Mr J.Galt?
Any news?

---

### Post by John Galt on 2010-08-26
Dear Mr realzippy,

It looks like i am screwed for good this time. :(

Installed the build-essential from the package website. Then followed the usual method to a T.

The nvidia installer worked this time and after a reboot. All that happens is that I stare at a lifeless screen. 

Nothing happens..nada, zilch.....if the power button led did not work, you would take the screen as switched off.

Now what should I do.......

---

### Post by realzippy on 2010-08-26
During the nvidia-driver install you should have been asked if "nvidia-xconfig" 
should create a xorg.conf for you (or similar).Have you answered "YES" ?

To be sure,you could run ```
nvidia-xconfig
``` in recovery mode again...
Another idea:
Can you change the monitor for testing?

---

### Post by diacad on 2010-08-26
This is a reply to "oldsoundguy" msg #3 on this thread:  5XXX series nVidia cards not supported by Ubuntu? Are you sure? If true, that seems outrageous; this series is not prehistoric, by any means. Even picky Windows 7 can support such cards with device-specific drivers that make use of the card features. One of the advantages for going with Ubuntu is its purported ability to run on less (and older) hardware than Windows, and that it doesn't try to gratuitously promote hardware upgrades. Frankly, efficiency in exploiting existing hardware is a significant reason (besides economy and reliability) why I am interested in Ubuntu. Or Linux for that matter. With all due respect to their obvious technical abilities, Ubuntu developers should be spending less time on eye-candy, and more time on legacy support.

---

### Post by realzippy on 2010-08-26
@ diacad:

Oldsoundguy never said this:"*5XXX series nVidia cards not supported by Ubuntu*"
He was talking about the nvidia "*current*" driver which does not work on 5xxx cards.For older cards you use the NVIDIA 96.xx driver,so calm down.
BTW,a thread -unless it is in the community cafe- is no off-topic chat ;-)

---

### Post by diacad on 2010-08-27
Oldsoundguy felt compelled to replace his 5xxx cards due to a driver support problem, so I concluded the 96.xx drivers did not fully exploit the capabilities of the cards to his satisfaction.  I expressed chagrin that the "current" nVidia driver did not support 5xxx - is it "off topic chat" to comment about that situation?  I am new here and do not understand some apparently unwritten rules.  Thanks for the correction, please bear with me.

---

### Post by Zill on 2010-08-27
> **diacad said:**
> ...I am new here and do not understand some apparently unwritten rules...
By registering and participating in Ubuntu Forums discussions you *did* agree to the written rules:
"...Please keep discussions on topic. Non-technical and non-3rd party project discussions belong in the Cafe..."

[http://ubuntuforums.org/index.php?page=policy]("http://ubuntuforums.org/index.php?page=policy")

It just helps to keep discussions separated out into different topics when users search the forums for info in the future.

---

### Post by diacad on 2010-08-30
Zill, I read that.  You and others here seem to have pretty narrow interpretations in my opinion.  You are right, I don't belong here.

---

### Post by Elfy on 2010-08-30
Support forums are for that.

There is a place for off-topic chat.

---

### Post by realzippy on 2010-08-30
*"Ubuntu developers should be spending less time on eye-candy, and more time on legacy support."*
is -sorry- kind of insolent statement,or a good (provoking) title for a new thread in the cafe.
**But** to jump in a thread with this where someone needs help is nothing
but "ranting"...
Can you see this?
So,welcome to the forum!

---

### Post by John Galt on 2010-09-01
Respected Mr realzippy,

coming back to my query, while dropping down to the root in recovery mode; i typed nvidia-xconfig and the then the prompt was to revert to the xconfig file or something like that. (do not rememeber now :) .)

the normal boot is still the same with a scrambled screen and no activity what so ever....any ideas ??

---

### Post by realzippy on 2010-09-01
..you tried boot options as suggested in post [# 11]("http://ubuntuforums.org/showpost.php?p=9755353&postcount=11")?



...btw,"*(do not rememeber now :)  )*"
might have been interesting...

---

### Post by John Galt on 2010-09-02
Sir, tried every boot option to my knowledge ( took me some time to understand.....even after reading the post no. 11) .... still the same.....may be it is the computer's way of sayin' it feels at home with winxp.....

anyways .... let me get my hands on the latest version of ubuntu and then i will come back to this post .... untill then i guess i have had my share of fun with this version of ubuntu ( i am officially surrendering...got to know when to fall back for a good second wave attack.)

Please advise on how to restore the windows bootloader back rather than grub.

Thanks again for your help.

btw please let me

---

### Post by realzippy on 2010-09-02
Hello,
it may depend on the windows version..
e.g.

[XP]("http://ubuntuforums.org/showthread.php?t=381993")

[Vista]("http://arstechnica.com/civis/viewtopic.php?f=16&t=158228")

---

### Post by John Galt on 2010-09-03
thank you mr realzippy, you have been a a great help and according to me the star of this forum.

you are free to do whatever you like this thread.

take care and keep up the good work.

---

### Post by John Galt on 2010-12-19
Hello to everyone.

I am reopening this thread for discussions and finding a solution to my problems.

Please visit the link mentioned below:

[FONT=&quot][/FONT]http://mepislovers.org/forums/archive/index.php/t-6487.html

This forum talks about a person using the same motherboard as I am and having the same difficulties as I do.

His system configuration and the choice of distro may be different but the problem is very much alike.

My request to the very helpful ubuntu community is to give me a very precise step by step account of what the person did to get his linux working (which he ultimately did, by blacklisting something....). I am a noobie; haven't even learned the commands on the terminal yet.

I want to install the latest version of ubuntu linux namely 10.10.

Please help.

Thanks as always.

---

### Post by Zill on 2010-12-19
> **John Galt said:**
> ...I am reopening this thread for discussions and finding a solution to my problems...
Your "new" link refers to a Mepis thread with the last entry made in 2007 and many things have changed since then with *all* Linux distros!

I am pleased to see that you "want to install the latest version of ubuntu linux namely 10.10".  This is an excellent idea as you may well find that "it just works"!

Once you have obtained an 10.10 CD, I suggest that the *first* thing to do is to check the disk for defects.  This is a menu option you should see when you first start up the PC with the disk in the drive.  Do not try to run or install the OS at this stage - just run the check utility (this will take some time).

When the check is completed (hopefully with no errors) take the option to reboot the machine.  This time, select the "Try Ubuntu without installing" option.  This will load the OS, running from from the "live" CD.  Note that this is slow but does not make *any* changes to your PC hard drive.

This will ensure that your hardware is basically compatible and you should see the normal Ubuntu desktop and default applications.  If you ensure that your DSL router is correctly configured and online when you boot up, then Ubuntu should *automatically* connect to the internet.  Note that it is best to use an ethernet wired connection for this rather than wireless.

I suggest it is not necessary to install NVidia drivers at this stage as you are simply testing Ubuntu with the live CD and any changes will be lost on reboot.  However, if everything else seems to be working then I suggest you click the "Install Ubuntu" icon on the Desktop and proceed with a full installation to your HDD.

With Ubuntu installed on your HDD, you should again find your internet connects automatically via a wired connection.  Wireless can be configured later if required.  However, to install NVidia drivers, I suggest you simply click on the following menu option:
System, Administration, Hardware Drivers
and this should identify the available drivers (you must remain connected to the internet).
Select the appropriate driver, then reboot.

Hopefully, the appropriate NVidia driver will now be installed and your new OS will be up and running :-)

If you have any problems then I suggest you start a new thread, clearly listing *exactly* what hardware you are using, what you have done and what seems to be wrong.  (Referencing old Mepis threads just adds confusion IMHO)

---

### Post by John Galt on 2010-12-21
Thank you for the update Mr. Zill.

I will try out the method mentioned asap and post the result obtained in a new thread as per your kind advise. I will also put my hardware specifications.

---

### Post by John Galt on 2011-01-05
The issue has been resolved and the thread is to be considered closed. :)

---

