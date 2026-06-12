---
title: "new installation on desktop pc not working right"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by mrgreaper on 2009-09-03
ok i came to the conclusion that i very rarely use my pc for games and decided that i would try ubuntu on my main pc (its already on my sever pc) 

to save a load of updating (i still had to update but meh) i redownloaded the latest version two days ago (9.04 32bit desktop)

my pc specs are;

* 4 gigs of ddr2 ram (ubuntu only saw 3.2gig which is a bit wierd but can be fixed after the really important stuff lol)
* an amd phenom 8650 triple core processor
* one scsi 500 gig hd (the primary with which windows 7 is installed this is ntfs file format)
* one ide hard drive 200 gigs i told the ubuntu installer (booted from the live cd not from inside windows) to use all of this drive
* a nvidia geforce 9800 gtx+ (a beast of a card)
* a built in 5.1 sound card with opticle out (managed to get sound working through opticle out quite fast but problems below existed before i tinkered with the settings for sound)
now hopefully i have included all the details that you may need to assist but if you need anymore please ask,

now the problem,
ubuntu runs increadable slow, windows keep turning black and white and offering to be forced closed when i click them but if left the start to respond again, this includes folder windows (ie browsing the hard drives) and fire fox. I have tried enabling the nvidia driver and having it disabled both same problem with both. if it wasnt for using ubuntu on my server pc and knowing how rock solid it could be i would plain abandon ubuntu but i want to get it to work right! this pc i use for converting mkv to 720 mpg for playing on my ps3. converting divx to a format for my archos. playing swat 4 (wine can handle an old game like that im sure if not dual booting will be fine) and general surfing and burning (growiso will do the burning (i use iit on my server pc now and again and its much more reliable with media then imgburn(though imgburn is amazing) 

so i have two problems to fix 

1) get ubuntu to play nice on my pc 

2) get ubuntu to detect the right amount of ram!

any suggestions and solutions greatfully recieved

---

### Post by tomBorgia on 2009-09-03
32-bit operating systems can't address 4GB of ram properly... which is why your only seeing 3.2 gig...

---

### Post by mrgreaper on 2009-09-03
> **tomBorgia said:**
> 32-bit operating systems can't address 4GB of ram properly... which is why your only seeing 3.2 gig...

ah so i would be better using the 64bit ubuntu? for ram atleast but umm what about the main problem, ubuntu turning all my windows black and white and being very slow

there is another minor problem grub doesnt regonise my wireless keyboard so i have had to plug in a wired keyboard to change the boot selection (not a bios issue as my bios password and all setup stuff can be accessed with my wireless keyboard) as i say its a very minor inconvience but if its easierly fixed then i would be greatful

****edit****

now downloading the 64bit version, lets hope the driver support is there ! and kinda hoping that will fix my problems

i intend to install it over ubuntu 32bit (tell it to use the whole drive again) i assume this will update grub correctly but if there is a way to simply tell ubuntu 32bit to update itself to 64bit please let me know (different cd needed lends me to the conclusion thats not possible

---

### Post by tomBorgia on 2009-09-03
I'd download and install the 64-bit version (I'm assuming your processer is 64-bit capable...) - It'd certainly be faster for video recoding anyway so is probably worth it.

I suspect the graphics issues are down to the nvidia driver - I'd download and install the official linux nvidia driver for your card from their website... I've had problems in the past with the generic and restricted drivers.

---

### Post by mrgreaper on 2009-09-03
> **tomBorgia said:**
> I'd download and install the 64-bit version (I'm assuming your processer is 64-bit capable...) - It'd certainly be faster for video recoding anyway so is probably worth it.

I suspect the graphics issues are down to the nvidia driver - I'd download and install the official linux nvidia driver for your card from their website... I've had problems in the past with the generic and restricted drivers.

ah i thought it downloaded the right updated driver by default. and yes according to amd the processor is 64bit compatable

im now rebooting to do the install so will post if it makes any improvements

any advice on easy tools for ubuntu video conversion would be greatly recieved (though im sure google will help me there) currently i use mkv2vob for ps3 stuff (the other stuff divx etc i can use mencoder on ubuntu to do as i do some of it on the server pc)

---

### Post by Bucky Ball on 2009-09-03
64bit is what you want.

---

### Post by tomBorgia on 2009-09-03
I've no idea why the nvidia driver in the "restricted drivers" is different from the official nvidia website's version... but there are several versions of it for different and legacy cards (on nvidia.com) so I'm assuming it works better for less everyday hardware? Like I said not sure really just from past experience I've had to use the official version...

No idea about video conversion software... Good luck getting it working!

---

### Post by mrgreaper on 2009-09-03
> **tomBorgia said:**
> I've no idea why the nvidia driver in the "restricted drivers" is different from the official nvidia website's version... but there are several versions of it for different and legacy cards (on nvidia.com) so I'm assuming it works better for less everyday hardware? Like I said not sure really just from past experience I've had to use the official version...

No idea about video conversion software... Good luck getting it working!

well its been an utter disaster, the computer if left alone for more then 10 minutes or so crashes (num lock and scroll lock flash screen is frozen) 

the official drivers wont install as x server is running, multiple guides on the net to get around this dont seem to work

i tried envyng to install drivers they downloaded but on boot up it said that the nvidia kernal couldnt load and loaded into low settings on display 1

i went to synaptic package manager to install nvidia kernal and it wont load (starting authentication apears at the bottom and then vanishes) ubuntu is good for server pcs but for a desktop its just way to much work to be useful 

when i get home later im gonna kill the partition with extreme prejeduce its wasted 90% of my day! 

though i did find out if i press ctr+alt+f2 i get a pure text screen terminal, could be very useful on my server pc must look into that at a less angry date

---

### Post by mrgreaper on 2009-09-03
> **Bucky Ball said:**
> 64bit is what you want.

64 bit is what i installed 2nd time around but as i say above its been a disaster

---

### Post by Bucky Ball on 2009-09-04
> **mrgreaper said:**
> ubuntu is good for server pcs but for a desktop its just way to much work to be useful

Brash generalisation, made out of frustration, disproved by millions.  [-(

---

### Post by Jazzy_Jeff on 2009-09-04
Did you install using the live cd or the alternate install cd? I always have problems with the live cd. I always use the alternate install cd now. It is all text based but easy to follow. Don't know if this will fix anything for you or not.

---

### Post by tomBorgia on 2009-09-04
> **mrgreaper said:**
> well its been an utter disaster, the computer if left alone for more then 10 minutes or so crashes (num lock and scroll lock flash screen is frozen) 

the official drivers wont install as x server is running, multiple guides on the net to get around this dont seem to work

i tried envyng to install drivers they downloaded but on boot up it said that the nvidia kernal couldnt load and loaded into low settings on display 1

i went to synaptic package manager to install nvidia kernal and it wont load (starting authentication apears at the bottom and then vanishes) ubuntu is good for server pcs but for a desktop its just way to much work to be useful 

when i get home later im gonna kill the partition with extreme prejeduce its wasted 90% of my day! 

though i did find out if i press ctr+alt+f2 i get a pure text screen terminal, could be very useful on my server pc must look into that at a less angry date

You need to kill off the X server to install the drivers... I'm suprised you couldn't find out how to do it - 

from the ctrl-alt-f2 screen log in and type -

```
sudo killall gdm
```

or ```
ps -ef | grep X
```

and look for the line 

```
root      2849  2845  6 08:30 tty7     00:04:00 /usr/X11R6/bin/X
```

type ```
sudo kill 
``` then the first number after root (i.e. 2849)

This will kill the X server. Then you run the nvidia installer... something like ```
sudo sh NVIDIA-PKG-WHATEVER-ITS-CALLED
```

You could just leave the PC for 10 - 20 mins with the X server disabled... this could at least determine what's causing your crashes / system hangs...

Anyway... isn't wasting 90% of your day is what computers are for!!!

---

### Post by mrgreaper on 2009-09-04
> **tomBorgia said:**
> You need to kill off the X server to install the drivers... I'm suprised you couldn't find out how to do it - 

from the ctrl-alt-f2 screen log in and type -

```
sudo killall gdm
```

or ```
ps -ef | grep X
```

and look for the line 

```
root      2849  2845  6 08:30 tty7     00:04:00 /usr/X11R6/bin/X
```

type ```
sudo kill 
``` then the first number after root (i.e. 2849)

This will kill the X server. Then you run the nvidia installer... something like ```
sudo sh NVIDIA-PKG-WHATEVER-ITS-CALLED
```

You could just leave the PC for 10 - 20 mins with the X server disabled... this could at least determine what's causing your crashes / system hangs...

Anyway... isn't wasting 90% of your day is what computers are for!!!

thats a different method to the ones i found, they all said to type /etc/init.d/gdm stop (i think thats right typing from memory) 

the 32bit i installed from the live cd
the 63bit i installed from the install menu from booting my computer from cd if that sense makes 

installing linux was suposed to take me no more then an hour (thats how long it takes for me to setup my server) i hadnt really set aside any more time then that, it took as you can see from the time stamps a lot longer. i may try again but not till i have a full day to spare (so not untill november atleast) but your help was greatly appreciated

---

### Post by mrgreaper on 2009-09-04
> **Bucky Ball said:**
> Brash generalisation, made out of frustration, disproved by millions.  [-(

Maybe but its my opinion formed on the basis that my server pc runs ubuntu perfectly and i wouldnt dream of using another os on it ubuntu is very stable. however for the main pc ubuntu just didnt work right, maybe with better experience in linux or better google skills i could of got it working but it should work straight from the disk in my opinion and then only need tweaking to the users needs like windows, sadly this is not the case and thus my opinion that server yes desktop no, im entitled to that openion the same as you are entitled to disgree though mayhap you could be politer next time

---

### Post by fuzzyllama on 2009-09-04
Did you specify a swap partition?  What size did you specify?

---

### Post by tomBorgia on 2009-09-04
> installing linux was suposed to take me no more then an hour (thats how long it takes for me to setup my server) i hadnt really set aside any more time then that, it took as you can see from the time stamps a lot longer. i may try again but not till i have a full day to spare (so not untill november atleast) but your help was greatly appreciated - Your welcome :-)

---

### Post by mrgreaper on 2009-09-04
> **fuzzyllama said:**
> Did you specify a swap partition?  What size did you specify?

both times i told it to use all of my second drive, it did the partitioning automaticly but i do renember in the ram screen it said 7gig swap

---

### Post by mrgreaper on 2009-09-05
last night upon loading windows 7 to check on an auction bid, i right clicked computer choose manage, i then removed both the ubuntu partition and its swap partition and made the drive a ntfs drive, now this is a drive that was added to my pc a couple of days ago it is not the main drive and certainly not the boot drive. i figured grub would still load but give me the option of windows 7 and not ubuntu. I was wrong, i got an error 17 when i rebooted my pc in the middle of the night and needed to use the pc. i had three ideas to fix
1) redownload the windows 7 rc disk from microsoft (my one is with a mate with a slow connection) on my server pc *would of taken over an hour special since i have no idea where its monitier is ( i use tight vnc)*
2) find my vista disc and install vista *NO*
3)reinstall ubuntu

so i went for option 3 gave it a mere 3 gig of hd space but i have to keep a wired keyboard in to my machine to operate the grub menu as it always wants to load ubuntu, and my pc now has 3gigs of , to me, worthless os. oh and i lost the auction. im starting to dislike ubuntu if i cant remove it with out scewing up my pc the term virus springs to mind,harsh i know but thats how its acting.

---

### Post by 3rdalbum on 2009-09-05
> **mrgreaper said:**
> ubuntu is good for server pcs but for a desktop its just way to much work to be useful 

It's only a lot of work if you don't know how to use it. Setting up any operating system is a lot of work if you don't know how to use it. I just reinstalled Ubuntu and it's a cakewalk to get everything running, as long as you're not trying to do things the same way that you did them on Windows.

Your kernel panic problem is probably due to bad RAM; I just had this problem and (it seems like) I solved it by removing two RAM sticks.

GRUB installs a part of itself to the master boot record in order to intercept the boot process before Windows takes it over. That part is too small to be able to boot anything except the main body of GRUB, which is stored on the Ubuntu partition. Delete the Ubuntu partition and you've deleted the ability to boot anything.

What you should have done is run the "fixmbr" utility on your Windows disc, which reinstalls the Windows bootloader into the Master Boot Record. I believe the Vista disc would have worked to recreate the MBR.

---

### Post by twright on 2009-09-05
Hi,
I think most of the difficulties experienced came from how you tried to install the driver so I will try and run through a few points on how that can be done correctly and also (if you want) how to restore window 7's bootloader:

[LIST=1]
[*]If you want good performance with an nvidia graphics card the only way to get that is using their official driver. This cannot be included by default in Ubuntu for licensing reasons.
[*]The only way to install this in Ubuntu which is easy and works is through hardware drives - all of the other ways that have been suggested were mostly used before this was included and are likely to break your system. Hardware drivers will install the same thing anyway but without the breakage so there is really no reason not to do it this way.
[*]If set up correctly (whist should not take more than 1/2 hour from inserting the CD) Ubuntu is very fast (especially the 64bit edition) and would perfect for converting videos. I run it on my eeepc with much lower specs than your machine and it absolutely flys along.
[*]You can restore the Windows 7 bootloader from within Windows by typing fixmbr in a command line launched as admin but I suggest giving Ubuntu a second try first. The only reasons why you can remove it more easily are technical and would apply to any OS - infact you cannot ***install*** Windows without messing up any other OSs on the disk let alone remove it. If this is to change first hardware vendors will have to start switching to efi.
[*]I myself have converted a lot of videos on Ubuntu and found that 64bit is significantly faster (10fps ish) and you should try out both handbreak and winFF as excellent video conversion programs. You will also want to install a load of codecs first by going into Add/remove programs and searching for/installing ubuntu-restricted-extras.
[/LIST]
Good luck and I hope you have a better experience in the future :)

---

