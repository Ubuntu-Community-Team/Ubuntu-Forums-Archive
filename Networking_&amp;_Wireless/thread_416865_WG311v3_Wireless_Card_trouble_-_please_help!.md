---
title: "WG311v3 Wireless Card trouble - please help!"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by amosharper on 2007-04-21
I'm not sure whether this should be here or in Absolute Beginner talk. I'm not an **absolute** beginner, but I'm not yet fluent in Ubuntu, but I know the basics (navigation, basic use of the terminal, package manager etc).

I'm using Feisty, and am having trouble installing the driver for my wireless card (NETGEAR WG311v3) with ndiswrapper. Could someone help?

I have the device driver, and ndiswrapper common/ndiswrapper-utils-1.9.

This worked in Edgy (eventually), so I wondered if anyone would be so kind as to walk me through installing for Feisty. Thanks **hugely** in advance,

- Amos

---

### Post by asch246 on 2007-04-21
I´m in exactly the same situation! I Have the same card and am usig fiesty too. I too am not an ´absolute´ beginner, but am still a novice. 

Could anyone please help us both??

---

### Post by SizzleBeast on 2007-04-21
I have that card and never got NDIS wrapper to work. If you are able, just use the restricted drivers manager to use the restricted Atheos (something like that) driver. That should work fine.

---

### Post by asch246 on 2007-04-21
When I try to open the restricted drivers manager, I get a pop-up window telling me:
> Your hardware does not need any restricted drivers.
Then it all closes again.

---

### Post by tweedledee on 2007-04-22
ndiswrapper is seriously broken in Feisty (mutliple launchpad bugs about this).  If only I'd thought to check that before I upgraded....  Anyway, I had this card working perfectly in Edgy simply by using the default CD driver and the GTK interface to ndiswrapper.  Now I can't get it to work with either the Feisty version (1.38/1.9) or a compiled latest version (1.42/1.9).  The older version that worked on Edgy no longer compiles, suggesting that this isn't actually a problem with ndiswrapper, but is instead a kernel problem (suggested in at least one bug report).  Feisty has been a real wireless pain for me on multiple computers; I may be downgrading if I can't get this resolved soon (especially as all the "new" features such as windows migration and compiz are either useless or also don't work on my hardware).

Also, note to a previous post: this is not the WG311T, which uses the Atheros chipset (and hence restricted drivers); this is the WG311v3, which is a different chipset altogether and does not work via any means except ndiswrapper (and so with ndiswrapper down, this is a dead card).

---

### Post by asch246 on 2007-04-22
Thanks, Tweedledee! 
I guess it's off to Edgy for me!
Any tips for setting it up in Edgy? (ie- do you know of any issues I may come accross?)

Cheers

---

### Post by tweedledee on 2007-04-22
> **asch246 said:**
> Thanks, Tweedledee! 
I guess it's off to Edgy for me!
Any tips for setting it up in Edgy? (ie- do you know of any issues I may come accross?)

Cheers

Not really - I just used the WinXP driver from the CD (actually the oldest download on the linksys site) - the .sys and .inf in a single directory, fire up ndiswrapper-gtk ("window wireless driviers") and select it, and it worked (after a "modprobe ndiswrapper" and/or adding "ndiswrapper" to /etc/modules and restarting).  Some people have reported better success with the w2k driver, but I found that didn't work.  The most frustating thing for me is that it was so easy (even WPA worked), and I'd just recently purchased that as a cheap replacement for my previous card (which worked out of the box, but only with WEP and would occasionally lock up my computer), and now it's just dead.

For the moment I'm running a cable across my apartment and using my wired card, hoping the issue will get resolved in the next few days.  If not, I'll have to weigh OO.org bug fixes and the newest Thunderbird (Feisty) against a working wireless connection (Edgy).

---

### Post by asch246 on 2007-04-23
I´ve installed edgy but I cant find/install the gtk interface for ndiswrapper? I´ve tried looking in add/remove and in synaptic package manager for either ´ndisgtk´ or ´windows wireless drivers´ but cant find either in either listing. What did you use?

Thanks again for your help!

---

### Post by mwells on 2007-04-23
Hi All,

I have this card and have been able to get it working in Feisty with relative ease. I'm at work at the moment but will try and put together a little how-to tonight, although it was a fairly simple install procedure.

Basically all I did was install ndiswrapper (I compiled the latest source from the download page), then took the drivers off of the install CD and installed them with ndiswrapper, and that was enough to get it working fine.

The only problem I am now having is getting network manager to work with a static IP address, though that may be a NM specific problem.

Hope that helps

/Matt

---

### Post by tweedledee on 2007-04-23
> **asch246 said:**
> I´ve installed edgy but I cant find/install the gtk interface for ndiswrapper? I´ve tried looking in add/remove and in synaptic package manager for either ´ndisgtk´ or ´windows wireless drivers´ but cant find either in either listing. What did you use?

Thanks again for your help!

You need to have the universe respository enabled, then "ndisgtk" should show up in Synaptic.  Alternatively you can use the command line (ndiswrapper -i <full path to .inf file>), but I've found the gui to be reliable in Edgy.

mwells: I tried that procedure, didn't work for me; perhaps I have something left over somewhere from the upgrade that is interfering (did you upgrade or clean install Feisty?).  As for your static problem, NM does not play nice with static IPs; supposedly you can simply configure the devices manually and NM will ignore them, but I've not had success with that - I have actually removed NM from my computers and am either manually configuring and/or using the "network" control panel and/or using wicd instead.

---

### Post by mwells on 2007-04-23
Hi,

Yeah it was a fresh feisty install so that must be the difference.

Have you tried cleaning ndiswrapper from your system and recompiiling maybe? Also I can send you the drivers that I currently have functioning if you think that would help? Its strange because it worked really quite easily for me, literally just compile ndiswrapper, load into the modules, modprobe ndiswrapper and it was up!

The network manager thing is a bit of a pain, I'm gonig to look at configuring a static path using the router and the MAC address just as i dont really fancy playing with it, as I'm assuming they will patch NM soon, but is it easily removed? I noticed it marked Ubuntu-desktop for removal when I looked at deleting it which im not sure of the consequences of if I went ahead with it.

All the best

/Matt

---

### Post by Philistine on 2007-04-23
I get this when I try to use any of the WG33v3 V1 drivers - XP, 2000, ME or 98:

phil@phil-desktop:~/WG311v3$ sudo ndiswrapper -i WG311v3.INF
installing wg311v3 ...
couldn't open WG311v3.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.


What am I doing wrong?

Thanks,

Phil

PS Let us know what drivers you are using - and can you set out specific directions on how to compile?  I think I am using ndiswrapper 1.38 (I downloaded a .deb common and .deb utils file so that I wouldn't have to recompile), but if you are using 1.42 maybe that is the difference.

---

### Post by mwells on 2007-04-23
Hi there,

To install ndiswrapper I just followed this link (written by JavaJake) 

[click here ](http://ubuntuforums.org/showthread.php?t=225206)

> 
Step 1 - Install the essentials
If you haven't compiled anything before using "make", then you'll probably need to run this command. Open the terminal and run this:

```

sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)

```

Step 2 - Build ndiswrapper
Extract ndiswrapper from the attachment. ndiswrapper.sourceforge.net has the latest version, so if you want the latest, go there. You absolutely cannot use ndiswrapper from apt-get (repositories)! It is really outdated, unfortunately! If this writing is really old, and the version in apt-get is actually higher then 1.21 (1.8 does not count as a higher version - go figure), then go ahead and skip Step 2.

Once you have extracted ndiswrapper from the attachment, go into the ndiswrapper folder in the terminal, and run:

```

sudo make uninstall
make
sudo make install

```

    NOTE: Some have reported that sudo make uninstall reports an error about a directory that was unable to be deleted. If the directory is "/lib/modules/<numbers>/kernel/drivers/net/ndiswrapper", then run this command:

```

 sudo rm -fR /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper

```

To complete the task, and to tell the kernel to always load ndiswrapper at startup, run this command:

```

sudo ndiswrapper -m

```


Then as I say I took the drivers off of the install CD (I can check which ones when I get home later and post them up if you like)

Hope that helps

/Matt

---

### Post by tweedledee on 2007-04-23
> **mwells said:**
> Hi,

Yeah it was a fresh feisty install so that must be the difference.

Have you tried cleaning ndiswrapper from your system and recompiiling maybe? Also I can send you the drivers that I currently have functioning if you think that would help? Its strange because it worked really quite easily for me, literally just compile ndiswrapper, load into the modules, modprobe ndiswrapper and it was up!

The network manager thing is a bit of a pain, I'm gonig to look at configuring a static path using the router and the MAC address just as i dont really fancy playing with it, as I'm assuming they will patch NM soon, but is it easily removed? I noticed it marked Ubuntu-desktop for removal when I looked at deleting it which im not sure of the consequences of if I went ahead with it.

All the best

/Matt

I'm getting other indiciations that the upgrade process may not have been as smooth as it seemed - I may be wiping and trying fresh (just need the time!).  One of those is that ubuntu-desktop is NOT marked for removal when I remove NM (even though it should be).  Anyway, you have you two options to avoid removing ubuntu-desktop (which you should not do if you ever plan to upgrade rather than fresh install a new release):
1. Create the files /etc/NetworkManager and /etc/NetworkManagerDispatcher, each with just the word "exit" in them - this will shut down NM as soon as it loads.  However, I had mixed results with this approach.

2. Actually uninstall NM (and ubuntu-desktop).  In synaptic, select the two packages and go to the Packages Menu & select "Lock Version."  Then re-install ubuntu-desktop (which won't re-install NM b/c they are "locked" as not installed).  I've not tried this b/c I'm not experiencing the ubuntu-desktop removal effect myself, but I've seen it recommended elsewhere as a solution (maybe the wicd site?).

And your third option is just to remove ubuntu-desktop if you plan to not upgrade to Gutsy (i.e., clean install instead) - that package is only important for that process.

---

### Post by asch246 on 2007-04-23
mwells-
Is there any chance you would be able to post step-by step what you did, for those such as amosharper and myself who have very little/no knowledge of a lot of stuff? It seems that all guides etc for installing + using ndiswrapper assume I know how to do various bits on my own- I don't! It'd be very super-awesome of you if you could, but I understand that time is not always affordable. I can do a fresh install of fiesty or edgy, but I am using xubuntu- would that make any difference?


tweedledee- 
I tried using ndisgtk in edgy, and it appeared to work - the driver installed and it said the hardware was present- but when I went to system>network to turn off my wired connection and confgure the wireless one, I found the wireless one wasn't listed there at all! Then, I found that installing the driver had done something to the wired connection and it wasn't working any more.

---

### Post by mwells on 2007-04-24
> **tweedledee said:**
> I'm getting other indiciations that the upgrade process may not have been as smooth as it seemed - I may be wiping and trying fresh (just need the time!).  One of those is that ubuntu-desktop is NOT marked for removal when I remove NM (even though it should be).  Anyway, you have you two options to avoid removing ubuntu-desktop (which you should not do if you ever plan to upgrade rather than fresh install a new release):
1. Create the files /etc/NetworkManager and /etc/NetworkManagerDispatcher, each with just the word "exit" in them - this will shut down NM as soon as it loads.  However, I had mixed results with this approach.

2. Actually uninstall NM (and ubuntu-desktop).  In synaptic, select the two packages and go to the Packages Menu & select "Lock Version."  Then re-install ubuntu-desktop (which won't re-install NM b/c they are "locked" as not installed).  I've not tried this b/c I'm not experiencing the ubuntu-desktop removal effect myself, but I've seen it recommended elsewhere as a solution (maybe the wicd site?).

And your third option is just to remove ubuntu-desktop if you plan to not upgrade to Gutsy (i.e., clean install instead) - that package is only important for that process.

Thanks very much for the info. I'm tempted to remove NM although I spent 10 minutes looking at my router last night and am able to give the box a static IP based on the MAC address of the interface which circumnavigates my problem of the static IP. With that in mind I think I'm going to just leave the thing alone and see if there are any updates thrown at it (im assuming there will be as there are loads of people with similar problems)

Once again thanks for you info though! In terms of your problem a fresh install probably sounds like the safest option, as you say it's just having the time to do it, though the install is fairly painless and so far I dont seem to have experienced any issues (one with samba but i think that is just me being stupid!)

Let me know how you get along though as maybe once you have got the drivers working we could look at WEP or WPA?
> **asch246 said:**
> 
mwells-
Is there any chance you would be able to post step-by step what you did, for those such as amosharper and myself who have very little/no knowledge of a lot of stuff? It seems that all guides etc for installing + using ndiswrapper assume I know how to do various bits on my own- I don't! It'd be very super-awesome of you if you could, but I understand that time is not always affordable. I can do a fresh install of fiesty or edgy, but I am using xubuntu- would that make any difference?


Asch I'm going to start on this tonight, as I say it will just be splicing from other bits of allready written material but will hopefully help you to get it up and running!

Could you let me know specifically what you are having issues with though please? did you follow the info that I posted yesterday written by JavaJake in order to compile the latest version of ndiswrapper?

Cheers

Matt

---

### Post by asch246 on 2007-04-24
well, there are some bits in JavaJake's instructions that I'm not very confident on (I only started using linux at all about 3/4 days ago!) for example:
> 
Once you have extracted ndiswrapper from the attachment, go into the ndiswrapper folder in the terminal, and run: 
and also, I wasn't sure about whether it mattered what directory i did this:
> To complete the task, and to tell the kernel to always load ndiswrapper at startup, run this command:

But basically, I've just found that most guides to doing things on ubuntu are good, but assume that you know how to do the little stuff already, which isn't necessarily the case. I spent the first 4 hours after I installed ubuntu the first time trying to find a support page that explained how to change directories in terminal, because a guide (re- wireless networking which didnt work) I was trying to follow didnt tell me. 

Maybe it's just the way it is and I just need to get over it, maybe my perfectionist streak (too often agonising over detail) is coming out again...
In any case, I look forward to seeing/trying what you come up with- the other guys in my house are getting a bit itchy about the cable going across 3 rooms. :p

thanks!

---

### Post by mwells on 2007-04-24
Ah ok,

Well I will try make bits like that clear by adding them in then. In terms of stuff like that though you can go to the site, download the .tar.gz (menas it's a gzipped archive) to your desktop. You can then just double click it and the archive manager will open to alow to you extract it.

After that there will be an ndiswrapper folder on the desktop. You can then simply open a terminal and type

```

cd ~/Desktop/ndi (type ndis then hit the tab key which will autocomplete it for you)

```

Then hit enter, you are now inside the extracted ndiswrapper folder (type 'pwd' at the terminal to have it tell you where you are within the filesystem if you like)

When in this folder you can then run make uninstall, make, make install etc (run them as sudo - which means type sudo before them, this means that the action is performed as root)

As far as completing the task by ndiswrapper -m it doesnt matter where you are within the filesystem, as it is running the newly installed 'ndiswrapper' command (again make sure you run as root (sudo))

You can then pop the install cd in navigate to the drivers folder and copy all the files in the 'XP' directory into a folder on your desktop then tell ndiswrapper to use them (as per javajakes instructions)

Following that a simple;

```

sudo modprobe ndiswrapper

```

should have you wireless card recognised and functioning!

Let me know how you get along and where you get stuck!

Cheers

Matt

---

### Post by asch246 on 2007-04-24
ok first off, when I extract the files, an error message comes up saying there was a problem and offers me this command line output:
> ndiswrapper-1.42/AUTHORS
ndiswrapper-1.42/ChangeLog
ndiswrapper-1.42/INSTALL
ndiswrapper-1.42/Makefile
ndiswrapper-1.42/README
ndiswrapper-1.42/ndiswrapper.spec
ndiswrapper-1.42/ndiswrapper.8
ndiswrapper-1.42/loadndisdriver.8
ndiswrapper-1.42/utils/Makefile
ndiswrapper-1.42/utils/ndiswrapper
ndiswrapper-1.42/utils/loadndisdriver.c
ndiswrapper-1.42/utils/ndiswrapper-buginfo
ndiswrapper-1.42/driver/divdi3.c
ndiswrapper-1.42/driver/hal.c
ndiswrapper-1.42/driver/iw_ndis.c
ndiswrapper-1.42/driver/iw_ndis.h
ndiswrapper-1.42/driver/loader.c
ndiswrapper-1.42/driver/loader.h
ndiswrapper-1.42/driver/longlong.h
ndiswrapper-1.42/driver/Makefile
ndiswrapper-1.42/driver/crt.c
ndiswrapper-1.42/driver/ndis.c
ndiswrapper-1.42/driver/ndis.h
ndiswrapper-1.42/driver/ndiswrapper.h
ndiswrapper-1.42/driver/ntoskernel.c
ndiswrapper-1.42/driver/ntoskernel.h
ndiswrapper-1.42/driver/ntoskernel_io.c
ndiswrapper-1.42/driver/pe_linker.c
ndiswrapper-1.42/driver/pe_linker.h
ndiswrapper-1.42/driver/pnp.c
ndiswrapper-1.42/driver/pnp.h
ndiswrapper-1.42/driver/proc.c
ndiswrapper-1.42/driver/rtl.c
ndiswrapper-1.42/driver/usb.c
ndiswrapper-1.42/driver/usb.h
ndiswrapper-1.42/driver/winnt_types.h
ndiswrapper-1.42/driver/workqueue.c
ndiswrapper-1.42/driver/wrapmem.h
ndiswrapper-1.42/driver/wrapmem.c
ndiswrapper-1.42/driver/wrapper.c
ndiswrapper-1.42/driver/wrapndis.h
ndiswrapper-1.42/driver/wrapndis.c
ndiswrapper-1.42/driver/lin2win.h
ndiswrapper-1.42/driver/win2lin_stubs.S
mv: will not overwrite just-created `/home/team/Desktop/ndiswrapper-1.42/Makefile' with `ndiswrapper-1.42/utils/Makefile'
mv: will not overwrite just-created `/home/team/Desktop/ndiswrapper-1.42/Makefile' with `ndiswrapper-1.42/Makefile'

so, I went ahead with the next step any way, to see if it would be ok and this is what happened:
> team@xubuntu:~$ cd /home/team/Desktop/ndiswrapper-1.42/
team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make uninstall
Password:
make: *** No rule to make target `uninstall'.  Stop.
team@xubuntu:~/Desktop/ndiswrapper-1.42$ 


What does that mean? anything? so, I went on with make and make install any ways, just for kicks...
which seems to have gone ok:

> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/team/Desktop/ndiswrapper-1.42
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/team/Desktop/ndiswrapper-1.42/built-in.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/crt.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/hal.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/iw_ndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/loader.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ntoskernel.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ntoskernel_io.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/pe_linker.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/pnp.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/proc.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/rtl.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapmem.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapper.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/usb.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/divdi3.o
  LD [M]  /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.mod.o
  LD [M]  /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/team/Desktop/ndiswrapper-1.42
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
team@xubuntu:~/Desktop/ndiswrapper-1.42$ 



then I get this:

> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found


I don´t understand what happened there, but I kinda get the feeling that ¨command not found¨ wasn´t supposed to be the answer. ;)

So, what do you suggest doc?

---

### Post by mwells on 2007-04-24
Hi!

Right, not to sure whats occuring with the extracting or the uninstall there, think that possibly there is allready a version of it on your desktop maybe but we can skip that for now.

So far you have done 

```

sudo make unistall
```

then

```

sudo make
```

Then I see no output from sudo make install, did you do this part? If not that would be why the command is not found as it's not installed :P

Let me know!

Cheers

Matt

---

### Post by asch246 on 2007-04-24
> **asch246 said:**
> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/team/Desktop/ndiswrapper-1.42
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
Building modules, stage 2.
MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
team@xubuntu:~/Desktop/ndiswrapper-1.42$ 

sorry, I had make and make install in the same quote box.

---

### Post by Philistine on 2007-04-24
I managed to get 1.42 installed following your directions.  All my errors disappeared when I typed the first long command you posted (to do with linux headers?) and put the CD into the drive...

I copied all the drivers from WG311v3 v1.0 zip file, found under the XP directory, into a folder under "Desktop", which I called WG311

then I typed cd WG311

then sudo ndiswrapper -i WG311v3.INF

and it seemed to install

when you type ndiswrapper -l, it says:

driver present, device (A11:AG) present - or something like that.  I can't remember the exact bit in the brackets

....now what do I do?   I tpyped something and got:

lo  - no wireless extensions

etho - no wireless extensions


Thanks

:D

Phil

PS  Am I close, or no?

---

### Post by mwells on 2007-04-25
> **Philistine said:**
> I managed to get 1.42 installed following your directions.  All my errors disappeared when I typed the first long command you posted (to do with linux headers?) and put the CD into the drive...

I copied all the drivers from WG311v3 v1.0 zip file, found under the XP directory, into a folder under "Desktop", which I called WG311

then I typed cd WG311

then sudo ndiswrapper -i WG311v3.INF

and it seemed to install

when you type ndiswrapper -l, it says:

driver present, device (A11:AG) present - or something like that.  I can't remember the exact bit in the brackets

....now what do I do?   I tpyped something and got:

lo  - no wireless extensions

etho - no wireless extensions


Thanks

:D

Phil

PS  Am I close, or no?


Hi Philistine, it sounds like you have the drivers working so now you can type;
```

sudo modprobe ndiswrapper

```

And if alls well the card should now be recognised!

> **asch246 said:**
> sorry, I had make and make install in the same quote box.

Asch, I started putting the various bits of posts together last night, hopefully I'll get it finished tonight, though I'm meant to be out so it may not be untill friday im afraid, but the error is coming about in installing ndiswrapper for some reason.

Have you tried removing all associated files from your desktop and then downloading and attempting again from scratch?

Hope that helps

/Matt

---

### Post by asch246 on 2007-04-26
Ok, so I´ve tried again, with much the same results. I followed a combination of mwells´ and javajake´s instructions
1. completely clean install of fiesty. 
2. Downloaded and extracted ndiswrapper 1.42 from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) 
Had same error occur as before when extracting:
> mv: will not overwrite just-created `/home/team/Desktop/ndiswrapper-1.42/Makefile' with `ndiswrapper-1.42/utils/Makefile'
mv: will not overwrite just-created `/home/team/Desktop/ndiswrapper-1.42/Makefile' with `ndiswrapper-1.42/Makefile'

3. Downloaded and extracted initial release drivers from [http://kbserver.netgear.com/products/WG311v3.asp](http://kbserver.netgear.com/products/WG311v3.asp) no errors
4. deleted downloaded zip/gz files from desktop (just so there was no confusion).
5. open a terminal window and did this: 
> team@xubuntu:~$ sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpp is already the newest version.
cpp set to manual installed.
gcc is already the newest version.
linux-headers-2.6.20-15-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Xubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

Selecting previously deselected package linux-libc-dev.
(Reading database ... 80865 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...


6. changed to directory ndiswrapper was extracted to:
> team@xubuntu:~$ cd /home/team/Desktop/ndiswrapper-1.42/


7. Ran ¨sudo make uninstall¨ with same results as before:
> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.


8. Ran ¨sudo make¨ 
> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/team/Desktop/ndiswrapper-1.42
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/team/Desktop/ndiswrapper-1.42/built-in.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/crt.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/hal.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/iw_ndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/loader.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ntoskernel.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/ntoskernel_io.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/pe_linker.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/pnp.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/proc.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/rtl.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapmem.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapndis.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/wrapper.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/usb.o
  CC [M]  /home/team/Desktop/ndiswrapper-1.42/divdi3.o
  LD [M]  /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.mod.o
  LD [M]  /home/team/Desktop/ndiswrapper-1.42/ndiswrapper.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo make install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/team/Desktop/ndiswrapper-1.42
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /


9. Ran ¨sudo make install¨
> team@xubuntu:~/Desktop/ndiswrapper-1.42$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found


10. write this post to get help.

Can anyone see where I went wrong/ why it will not work? is there something else I should have done first? 
I honestly cant think of ANYTHING else I did, so even if it´s the littlest thing, feel free to suggest it.

---

### Post by tweedledee on 2007-04-28
asch246 - Did you restart before doing the "make" commands?  I think the headers install requires it to be fully recognized.  Also, you can try to to do a search in /usr/bin and /usr/sbin for nd* and manually remove any old ndiswrapper files, in the event something there is interfering.

I've finally managed to get mine working with 1.42, but for some reason it assigned it to wlan1 instead of wlan0, so I had to reconfigure my /etc/network/interfaces file manually (I discovered where it was assigned with an "iwlist scanning" and checking which card was locating networks).

---

### Post by asch246 on 2007-05-07
hey, 
no, i didnt restart after the headers. But i'm out of town for a few weeks now, so i cant try it till i get back. 
still wasnt working when i left, but i hadnt really tried anything different since last post. anyways, i'll post again when I get home and have had a chance to have a go.

---

