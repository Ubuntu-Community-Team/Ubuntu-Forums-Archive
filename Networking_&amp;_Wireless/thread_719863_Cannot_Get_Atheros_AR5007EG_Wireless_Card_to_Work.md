---
title: "Cannot Get Atheros AR5007EG Wireless Card to Work"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by narboza22 on 2008-03-09
Ok, first, this is the first time I have Linux, so I am kind wandering around in the dark trying to get my wifi to work.  I have Ubuntu 7.10 installed on an Acer Aspire 5100 that has an Atheros AR5007EG wifi card in it.  I've tried following the steps listed in other threads on this forum and in google searches, but so far, I've had no luck.  I've tried using ndiswrapper and madwifi, but I didn't know what to do with madwifi once I had downloaded it, and ndiswrapper with a winXP driver did not seem to do anything.  In my network settings window, there is no wireless connection listed.

I don't really know where to go from here.  Since I didn't really know what I was doing to start with, I think I may have made things worse by messing around with ndiswrapper and madwifi.  If anyone could guide me in the right direction to getting my wifi to work I would appreciate it.

---

### Post by spinctz on 2008-03-09
i have the same wireless card only and same problem  on a fujitsu siemens esprimo v5515 ... help pls ...also newbie ...

---

### Post by DXM31 on 2008-03-09
To me this is a real shortcoming for Ubuntu.
I have gotten Madwifi to work...twice with the atheros card

My advice is if you do get it to work DO NOT DO UBUNTU UPDATE
Because that kills it.
As of now wifi is not working.
I was not able to get ndiswrapper to work ever.
I guess if I want wifi I have to boot Vista
otherwise I get to drag an ethernet cable around

---

### Post by scottro on 2008-03-09
(Best Eric Idle voice)

Say..no more.  

Ok, here we go.  Note---THIS IS ONLY FOR 32 BIT SYSTEMS.


NOTE--there were several typos and omissions in this--I've fixed it in post #24.  So, please follow the instructions there.  

I might forget to type sudo on a command that needs it, so if you get any permission denied ones, put sudo in front of the command. However, I'll try to not make that error, but I"m sleep deprived today. (Daylight Savings in the US). 


There are several threads about this card, and what I'm posting here is more or less a repeat of some, but the threads get so long and evolve as things have changed, that it's worth posting again. 

IF YOU HAVE NDISWRAPPER INSTALLED.

First, uninstall any drivers that you installed with ndiswrapper

ndiswrapper -l

(That's a lower case L, like list.)
It'll tell you if you have the 5416 or 5211, the two that people use.  If so, then

sudo ndiswrapper -e net5211

(or net5416 if that's the one you have.)

Get the module removed

lsmod |grep ndis

If you see an ndiswrapper module, remove it.

sudo rmmod ndiswrapper

Uninstall ndiswrapper.   If you installed it through apt then

sudo apt-get remove ndiswrapper

If you installed from source then cd into the ndiswrapper directory that was created and 

sudo make uninstall

Do it twice just to make sure.

It probably left a file in /etc/modprobe.d and we'd like to get rid of that too.

sudo rm /etc/modprobe.d/ndiswrapper


Ok, if you installed MadWiFi through apt get rid of that too.

I never did it, so I'm not sure if it's called madwifi, MadWifi or Madwifi.  Anyway, uninstall it with apt if you installed it that way. 

If you've already downloaded the tarball and tried to install it, let's try to get a clean slate.   We'll get to that in a minute. 

If you haven't yet downloaded the recommended patched snapshot then

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007.tar.gz

Now we do the clean slate thing. 
sudo make uninstall 
sudo make clean 

sudo make
sudo make install
sudo modprobe ath_pci

Now see if you have ath0 

iwconfig

Hopefully, it will now show an ath0 card listed.  If so, we're cooking with the proverbial gas

iwlist ath0 scan

If you get results, then you should be good from here and be able to connect to your wireless network with NetworkManager or whatever method you usually use.

RE UBUNTU UPDATE

Each time your kernel is upgraded, you will have to rebuild this module.  To do that repeat some of the steps we did before

cd madwifi-ng-r2756+ar5007.tar.gz

Now we do the clean slate thing. 
sudo make uninstall 
sudo make clean 

sudo make
sudo make install

Note that at least on my Acer laptop, the LED light doesn't work with madwifi and the card, so don't let that worry you.  Also, of course, if your laptop has a button to turn wireless on and off, make sure it's on.  As my laptop just has a little button that you press, I just had to press it a few times till it worked.

---

### Post by scottro on 2008-03-09
As I said, I'm sleep deprived right now.  One more important step. 

If you haven't already done so, before running the make commands

sudo apt-get build-essential

That will give you the compiling tools. Otherwise, when you run the make commands you'll get all sorts of errors.

---

### Post by DXM31 on 2008-03-10
Thanks I hope this works
Will try tomorrow.
Like many others I am new to this whole Ubuntu thing so I am glad you explained everything.

---

### Post by kevdog on 2008-03-10
Yes you need a patched version of the madwifi drivers to work.  The key is that he provided you a link to the patched drivers.  Although not concise, the overall explanation was very good.

---

### Post by DXM31 on 2008-03-10
When I do this

wget [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)

--09:56:05--  [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)
           => `special...+ar5007.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:56:11 ERROR 404: Not Found.

I know the link exists because I can open it in another tab

Whats up?

---

### Post by kevdog on 2008-03-10
Just download the file then through the web interface -- not sure why wget isnt working.

---

### Post by DXM31 on 2008-03-10
got the patch
tar'd it then

dale@dale-laptop:~$ cd madwifi-ng-r2756+ar5007.tar.gz
bash: cd: madwifi-ng-r2756+ar5007.tar.gz: Not a directory

---

### Post by DXM31 on 2008-03-10
OK so I took the tar.gz of since that really isn't a directory
the cd worked
now

dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ sudo apt-get build-essential
E: Invalid operation build-essential

see why it is hard for some of us to get this thing going?

---

### Post by weeg on 2008-03-10
OMG you are a genius, i've been spending weeks trying to get this stuff to work. 2 minutes with your steps and bam! everything works!!!

Now if only installing the NVIDIA drivers was this easy..... eesh
I'm new but im learning!

---

### Post by kevdog on 2008-03-10
sudo aptitude install build-essential

---

### Post by DXM31 on 2008-03-10
I ran this instead

sudo apt-get update && sudo aptitude install build-essential

I don't know if it is the same as yours or not but it seemed to work

Now when I try the uninstall I get this

dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ sudo make uninstall
cd: 1: can't cd to /lib/modules/2.6.22-14-386/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-386/build is missing, please set KERNELPATH.  Stop.

Does this mean it is not installed?

So I need to install madwifi as per
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
Then reinstall the patch?
I am getting lost
Congrats to weeg
I think the last steps under RE Ubuntu Update are golden I just need to get there

---

### Post by kevdog on 2008-03-10
Are you trying to uninstall ndiswrapper??

You could probably skip this part of the tutorial since you could just blacklist the module so it wont load or simply remove reference to ndiswrapper within /etc/modules.  The module wont load into the kernel at boot with either of these two methods.  The binary may still be installed on the computer, but I don't think that is a big deal.  As long as the kernel module isn't loaded, it will not cause any problems.

---

### Post by DXM31 on 2008-03-10
I was on this step

wget [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)

tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007.tar.gz

Now we do the clean slate thing.
sudo make uninstall <----------------------------
sudo make clean

The uninstall of madwifi

---

### Post by DXM31 on 2008-03-10
either way I'm glad you told me about nidswrapper in the module
It was in there twice
gone now

So am I getting thismessage because madwifi is not installed
But the patch seemed to work
The patch has to patch something right...
Still lost

---

### Post by kevdog on 2008-03-10
ill have to get back to you later -- a patch patches the original drivers -- are you sure you dont possess a patched version of the drivers already -- so hence someone patched them for you and all you need to do is install them?

---

### Post by DXM31 on 2008-03-10
I have run the patch before.
I think the big problem is the search function
I search for fixes and try them all
The wifi has worked before, it worked well, 

I even did all this so it would connect when I booted up:
----------------------------------------------------------------------------------------------------

Code:

gksu gedit /etc/rc.local

This opens up the file in the gedit utility and allows you to make changes and save the file

Code:

ifconfig <wired network connection interface> down
ifconfig <wireless network connection interface> down
dhclient -r <wireless_interface>
iwconfig <wireless_interface> essid <router name>
iwconfig <wireless_interface> mode Managed
ifconfig <wireless_interface> up
dhclient <wireless_interface>
-------------------------------------------------------------------------------------------------

not exactly that but the same idea, and it worked like a champ
then ubuntu update, down for the count then,try this fix, try that fix,...
and were working on another fix
I do appreciate your help, but I understand people have a life

---

### Post by spratelboing on 2008-03-10
Hi everybody.
I don't know how to get this thong working. I tried many different ways but nothing seems to work!? I would be very, very happy if someone will help me out of this.
First of all I want to say sorry for my bad English. Nevertheless I hope you can understans what I am trying to say.

I'm absolutely new to linux. The OS I've got running is Ubuntu Gutsy Gibbon. I'm using this on a LG R400 notebook with an Atheros wlan card build in. 
I tried different versions of ndiswrapper with different driver versions. Nothing seems to work. Well, at least my device seems to be recognized by linux, but no a single bit was transfered via wlan. There was also no connection established to my AP.

The last thing I tested was the work around via madwifi as it was described in this thread. But it didn't work for me, too.

I did some Terminal inputs to give you guys some information about what my problem is about. These are attached to this post.

One more thing:
I also have the problen that I'm not sure if my wifi is enabled/disabled since LED doesn't seem to work. I change the status via Fn + F8. But I can not recognize any changes.

All this is really bad, because it's my first linux installation and I was really glad to set it up. But I'm not able to do so, because I not even get this wlan working :(

PLEASE HELP ME! I read many posts and tried many solutions already..

---

### Post by spratelboing on 2008-03-10
here are my terminal outputs for more information:

[http://rapidshare.com/files/98543550/terminal_ausgaben.html](http://rapidshare.com/files/98543550/terminal_ausgaben.html)

---

### Post by DXM31 on 2008-03-10
Since I don't have ath0 or wifi0 I assume madwifi is not installed anymore
So I try to install it and get this

dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
cd: 1: can't cd to /lib/modules/2.6.22-14-386/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-386/build is missing, please set KERNELPATH.  Stop.


again with the krenelpath:confused:

---

### Post by scottro on 2008-03-10
My thanks to Kevdog was because he corrected yet another typo of mine in the initial instructions.  (I left out install in the sudo apt-get install build-essential)

---

### Post by scottro on 2008-03-10
I'm redoing it because of typos and omissions.  I'm awake now.

Ok, here we go.  Note---THIS IS ONLY FOR 32 BIT SYSTEMS.


IF YOU HAVE NDISWRAPPER INSTALLED.

First, uninstall any drivers that you installed with ndiswrapper

ndiswrapper -l

(That's a lower case L, like list.)
It'll tell you if you have the 5416 or 5211, the two that people use.  If so, then

sudo ndiswrapper -e net5211

(or net5416 if that's the one you have.)

Get the module removed

lsmod |grep ndis

If you see an ndiswrapper module, remove it.

sudo rmmod ndiswrapper

Uninstall ndiswrapper.   If you installed it through apt then

sudo apt-get remove ndiswrapper

If you installed from source then cd into the ndiswrapper directory that was created and 

sudo make uninstall

Do it twice just to make sure.

It probably left a file in /etc/modprobe.d and we'd like to get rid of that too.

sudo rm /etc/modprobe.d/ndiswrapper


Ok, if you installed MadWiFi through apt get rid of that too.

I never did it, so I'm not sure if it's called madwifi, MadWifi or Madwifi.  Anyway, uninstall it with apt if you installed it that way.  

If you've already downloaded the tarball and tried to install it, let's try to get a clean slate.   We'll get to that in a minute. 

If you haven't yet downloaded the recommended patched snapshot then

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

You will need the build-essential package to do the compiling, so if you haven't installed it previously then

sudo apt-get install build-essential

(EDIT--thanks again to kevdog.)

Make sure you have the kernel headers for your kernel as well
apt-get install linux-headers-`uname -r`

tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007

Now we do the clean slate thing. 
sudo make uninstall 
sudo make clean 

sudo make
sudo make install
sudo modprobe ath_pci

Now see if you have ath0 

iwconfig

Hopefully, it will now show an ath0 card listed.  If so, we're cooking with the proverbial gas

iwlist ath0 scan

If you get results, then you should be good from here and be able to connect to your wireless network with NetworkManager or whatever method you usually use.

RE UBUNTU UPDATE

Each time your kernel is upgraded, you will have to rebuild this module.  To do that repeat some of the steps we did before

cd madwifi-ng-r2756+ar5007
Now we do the clean slate thing. 
sudo make uninstall 
sudo make clean 

sudo make
sudo make install

Note that at least on my Acer laptop, the LED light doesn't work with madwifi and the card, so don't let that worry you.  Also, of course, if your laptop has a button to turn wireless on and off, make sure it's on.  As my laptop just has a little button that you press, I just had to press it a few times till it worked.

---

### Post by DXM31 on 2008-03-10
I think your instructions are great but
Does the patch contain everything you need to run Madwifi?
We don't need to install Madwifi?
Because this worked:
sudo apt-get install build-essential

tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007

the rest didn't

Now we do the clean slate thing.
sudo make uninstall

---

### Post by scottro on 2008-03-10
You shouldn't need anything else--that is a patched snapshot, as opposed to just being a patch.  So, that's just a different version of Madwifi, that includes a patch, supplied by Atheros, for the card to work on 32 bit machines.  

cd madwifi (heh, I keep mistyping it as mad wife, hope she doesn't look over my shoulder.)

sudo make uninstall might or might not give a result.

The same with make clean. 
However, I believe you said that you'd had it installed before and lost it when you upgraded.  In that case, you should have seen something when you ran those commands.  

If not, does make and make install complete without errors?
When you say make uninstall and make clean didn't work, what happened?

Did you install build-essential?

---

### Post by kevdog on 2008-03-10
Just to confirm since this should be included in the original instructions, that you have the linux headers installed for your kernel version.  If you have an internet connection already then skip the following step, if you do not you need the installation cd and you need to do the following:

sudo apt-cdrom add

For all versions:
sudo aptitude install linux-headers-`uname -r`

If you added the cdrom to the apt sources, I would then recommend you remove the cd rom as a list of possible repositories.
gksu get /etc/apt/sources.list

Remove or comment out the line referring to the cdrom as a repository.  If someone can provide me the exact syntax of the line, I will edit my instructions that will bypass opening on the manual editor to do this and instead write a one line command using sed.

---

### Post by scottro on 2008-03-10
Thanks Kevdog--I've added that to post 24. 

(Actually, I just found out about that one tonight, as another thread indicated that the very latest updates might actually include support for this card.  Unfortunately, they didn't and when I went to rebuild madwifi, it turned out I didn't have the /lib/modules/<kernel>/build.  I'd been laboring under the impression that build-essential included that for you..

(I'm more Fedora and Arch--Arch includes most build tools by default and with Fedora, one actually installs several packages to ensure that things can be compiled, so I'd assumed build-essential would take care of that. )

---

### Post by DXM31 on 2008-03-10
Ok so I figure I have to install madwifi

dale@dale-laptop:~$ cd madwifi-ng-r2756+ar5007
dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ sudo make
cd: 1: can't cd to /lib/modules/2.6.22-14-386/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-386/build is missing, please set KERNELPATH.  Stop.
dale@dale-laptop:~/madwifi-ng-r2756+ar5007$

This is what is in my madwifi...
dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ dir
ath            COPYRIGHT        Makefile         patch-kernel  SNAPSHOT
ath_hal        hal              Makefile.inc     README        svnversion.h
ath_rate       include          Makefile.kernel  regression    THANKS
BuildCaps.inc  INSTALL          Module.symvers   release.h     tools
contrib        kernelversion.c  net80211         scripts
dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ 

So I guess I am still missing something?

---

### Post by DXM31 on 2008-03-10
> **scottro said:**
> You shouldn't need anything else--that is a patched snapshot, as opposed to just being a patch.  So, that's just a different version of Madwifi, that includes a patch, supplied by Atheros, for the card to work on 32 bit machines.  

cd madwifi (heh, I keep mistyping it as mad wife, hope she doesn't look over my shoulder.)

sudo make uninstall might or might not give a result.

The same with make clean. 
However, I believe you said that you'd had it installed before and lost it when you upgraded.  In that case, you should have seen something when you ran those commands.  

If not, does make and make install complete without errors?
When you say make uninstall and make clean didn't work, what happened?

Did you install build-essential?

Yes I ran build-essential
I ran this
sudo apt-get update && sudo aptitude install build-essential

Maybe I used the wrong format
I don't recall seeing any errors

---

### Post by kevdog on 2008-03-10
I see this:
cd: 1: can't cd to /lib/modules/2.6.22-14-386/build

What kernel version are you using?  You can find this by type uname -r at the command line.

---

### Post by scottro on 2008-03-10
I believe that this is the issue that will be fixed by Kevdog's earlier post.  

sudo aptitude install linux-headers-`uname -r`

Or sudo apt-get install linux-headers-`uname -r`
I think that will give you that missing build directory. 

Note that those are backticks, the one that share a key with the tilde ~, usually to the left of the 1 (as in numeral one) key and not single quotes. 

That was missing from my earlier instructions, though I edited it after reading Kevdog's post, because I had thought that build-essential takes care of it.  However, <sob> I was wrong. 

So, one can justifiably say that you weren't missing something, I was.

---

### Post by DXM31 on 2008-03-10
:guitar: this is what was missing 
apt-get install linux-headers-`uname -r`
I got ath0
now on with the show
Thanks guys

---

### Post by DXM31 on 2008-03-11
I am so wireless now:biggrin:

---

### Post by kevdog on 2008-03-11
scottro

You should formally write this up as a HowTo and submit it to the Tutorials and Tips section.  Dont go into detail about removing ndiswrapper -- just mention it, but just a short how-to for the patched madwifi driver, the location and the install procedure.  Most importantly mention the requirements of the chipset, 32 bit not 64 bit, and any other piece of info you think is important.

---

### Post by spratelboing on 2008-03-11
It just doesn't work for me :mad: :(

I did all the stuff:
uninstalled all ndiswrapper stuff (driver and package), deleted ndiswrapper line in /etc/modules, deleted blacklist ath_pci in /etc/modprobe.d/blacklist, installed build-essentials, installed linux-headers, uninstalled and cleaned and installed madwifi again (and modprobed ath_pci). But my iwconfig doesn't show me an ath0 device, but a wlan0 and a wifi0. The wifi0 has no wireless extensions, the wlan0 does have.

I changed my AP not to be keyd (not wpa nor wep), activated ssid broadcast, deactivated the MAC filter and turned my wireless connection in system -> operation control -> network (which is shown there!) to roaming modus.

What did I wrong. I'm still counting on you, since I really ran out of ideas now!

---

### Post by scottro on 2008-03-11
@Kevdog

Someone has alread done it, I believe--there are howtos that are variations of mine all over htese forums.  As I said in one of my first posts in these threads, I would have just directed the OP to one of them, but couldn't find the one I liked.  Also, I maintain my own pages, and the trouble with writing any sort of howto is that it has to be maintained.  

It's mostly a matter of tme.  However, if I get a chance by the weekend, and see there's nothing in there, I"ll give it a shot.  

@spratelboing

About the only thing I can think of (I'm assuming that doing iwlist wlan0 scan brings you no joy--in Fedora 8 I was finding that the card was being seen as wlan0 but still worked) is to make sure, in the System menu, that you have disabled the Atheros hardware.  In the latest kernel I have (in Hardy, 2.6.24.12, I think--I'm writing this from FreeBSD, so can't check right now), 
if I left things at their various defaults, and went into System, Administration, Hardware, there were two Atheros things, including a wireless, showing up.  Unfortunately, although the wireless showed up, it didn't work.  (I was hoping that perhaps the kernel folks had taken care of it and one no longer had to worry about this. whole thing.)

Sometimes, it has just worked for me after I did all this, other times I've had to reboot. 

Did lsmod |grep ath show ath_pci in there? 

I should add that this method doesn't seem to work on some AMD machines, judging from Fedora forums.  


After disabling them, everything worked as detailed above.

---

### Post by spratelboing on 2008-03-11
thank you very much for your help scottro!

I think I'm getting closer:

i did a completely new installation of gutsy gibbon, I uninstalled the limited drivers for atheros card, installed the build-essential (the linux-headers were already there), installed and modprobed madwifi and rebooted the system. Until now everything seems to work fine!
There's no wlan0 anymore, but a ath0 device. 

But nevertheless iwlist ath0 scan brings no results.

As I already mentioned I'm a absolutely linux newby, but nevertheless there are two things which attracted my interest. Probably they are connected to my problem?

1. if I do a dmesg in terminal there is somewhere written:
    "ath_pci: switching rfkill capability off"  
    well, what is rfkill at all?

2. When I boot the system there is an error shown like:
    ".. PCI: BIOS BUG #81..."
    There is no way to read the whole line, since it cannot be freezed.
    I went to bios, but there are no settings about PCI or about my network cards.

I'm also not sure if this damn Fn + F6 wireless button is turned on or off at the moment? But I switched it so many times that this shouldn't be the problem. Is it possible that I had wifi switched off when I uninstalled windows and now it can't be switched on using linux??

You see, I don't know how to go further. Please help!

By the way, to eliminate stupid reasons I restarted my modem without being keyd, without MAC filter and turned SSID broadcast on. The device in Ubuntu is set to roaming mode.

---

### Post by spratelboing on 2008-03-11
I finally made it!

I had to reset the bios default values. Jipieee!!!!!!!!!!
(the bios-bug error message is still there, but who cares ;)

Thank you very much for your help and instructions!

---

### Post by DXM31 on 2008-03-11
So I sit down fire up my laptop.
No wifi, no ath0
Where did it go?
It was working last night
I didn't do any updates:confused:

---

### Post by DXM31 on 2008-03-11
I do these steps to see if it fixes the problem

cd madwifi-ng-r2756+ar5007
Now we do the clean slate thing. 
sudo make uninstall 
sudo make clean 

sudo make
sudo make install

everything worked then:

dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dale@dale-laptop:~/madwifi-ng-r2756+ar5007$ 
:(

---

### Post by kevdog on 2008-03-11
Likely the module isnt getting loaded at boot.

Do the following:

Reload the module like you did yesterday:
sudo modprobe ath_pci

Then to make the module load at boot time:
echo ath_pci | sudo tee -a /etc/modules

---

### Post by DXM31 on 2008-03-11
> **kevdog said:**
> Likely the module isnt getting loaded at boot.

Do the following:

Reload the module like you did yesterday:
sudo modprobe ath_pci

Then to make the module load at boot time:
echo ath_pci | sudo tee -a /etc/modules

Thanks once again
I will give that a shot
Right now I'm on Vista because while trying to fix my no sound issue I lost wired connection:(

---

### Post by DXM31 on 2008-03-11
worked like a charm

adding it to my Ubunto notes file

Thanks

on a side note, I was at Best Buy yesterday getting a loptop for my kid and every laptop I check had the Atheros wifi, and I checked four of the from four different manufactures.

I don't know but it would be nice in the next release of Ubunto all of this would be in there

---

### Post by scottro on 2008-03-11
spratelboing, glad you got it working. 

DXM31, sometimes, I've had to redo the modprobe ath_pci upon reboot.  It's not something that I've investigated very thoroughly, though.

---

### Post by scottro on 2008-03-13
I should have said this, but anyone who feels they want to make a howto out of information I've given in this thread is more than welcome to do so. As I said, I have my own page about it, at [http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007) but most of the information I've given here comes from other threads on the forum. 

One point on which I would repectfully disagree with Kevdog is being concise.   I think it's being concise that makes it necessary for people to search for two days to find information that should have been in some original documentation.   The Linux man pages used to make me think I was stupid.  Then, I used FreeBSD for several years, and realized that I wasn't stupid, many of the people who write man pages for Linux are simply very poor at conveying information.  

One reason for my current irritation is that I just spent three days that were unnecessary because some documentation was incomplete.  Two sentences of explanation would have saved me several hours of googling.

As a friend once wrote, 

With cryptic tutorials on the net with phrases like "enable SMTP AUTH for
Postfix", as if that is supposed to be a self standing instruction, this is
beyond both my ability and the scope of my endeavors. I'm just trying to get
PHP to send an email, not become an sendmail protocol administrator.

Of the people who view this thread, figure that at least 25 % might have already tried ndiswrapper.  They might see the information on uninstalling it, but figure half of them don't know how.  It probably took me two minutes to write the instructions and if I saved 10 people 5 minutes of googling, that means it was two minutes vs. 50 minutes, a reasonable trade off.  :)

---

