---
title: "Setup Ethernet for Dummiies"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by shoq on 2007-04-14
This is my very first day with ANY linux, and I am completely and totally lost.

Ubuntu 6.10 (installed from LiveCD) did not recognize my ethernet hardware.  I am connected to a D-link home router, adn on XP and vista, everything is fine.  

Ubuntu is booting, but without seeing the Ethernet.  I have the Attansic driver on CD (downloaded from Asus), but i have no idea what do do next.

I see posts about kernels, packages, and all manner of things, but NOT simple tutoral on "getting ethernet networking up and running).   

I have no idea where to put the driver, or how to install it. I don't know enough about linux to know where to begin, and can't find any QUICK START HELP for this issue.   I read on these forums that others had trouble with the Attansic, and the kernel number was important. I don't even know where to find THAT

Could someone please give me a patient, step by step understand of how to approach this, or point me to a tutorial that does?  I gave this post a subject that other newbs would notice, and hopefully your response can help many. 


Thanks in advance


WHAT I HAVE NOW
  Attansic L1 ethernet on Asus P5L-VM1394 Motherboard. (and drivers for the L1 on disk)




THERE ARE THE INSTRUCTIONS FROM THE ATTANSIC.  But as I have never even seen linux before, I'm having a bit of trouble relating.  I don't even know how to launch a console window yet.

If someone could reduce this to Step 1, 2, 3 for us dummies, it would be great. They didnt' do a very good job :)



Linux* Base Driver for the Attansic(R) L1 Gigabit Ethernet Adapter
==========================================================================

Contents
========

- In This Release
- Building and Installation
- Command Line Parameters
- Additional Configurations
- Known Issues
- Support

In This Release
===============

This file describes the Linux* Base Driver for the Attansic(R) L1 Gigabit 
Ethernet Adapter, version 1.0.x. This driver supports the 2.4.x and 2.6.x kernels.

This driver is only supported as a loadable module at this time. Attansic is not 
supplying patches against the kernel source to allow for static linking of 
the driver. For questions related to hardware requirements, refer to the 
documentation supplied with your Attansic(R) adapter. All hardware 
requirements listed apply to use with Linux.

Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb 
<filename.tar.gz>'. Replace <filename.tar.gz> with the specific filename of 
the driver.

NOTE: For the build to work properly, the currently running kernel MUST match 
      the version and configuration of the installed kernel sources. If you 
      have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice. For example,
   use /home/username/atl1 or /usr/local/src/atl1.

2. Untar/unzip archive:

     tar zxf atl1-x.x.x.tar.gz

3. Change to the driver src directory:

     cd atl1-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl1.[k]o

   The install locations listed above are the default locations. They might 
   not be correct for certain Linux distributions. For more information, 
   see the ldistrib.txt file included in the driver tar.

5. Install the module:

     insmod atl1 <parameter>=<value>

6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>

7. Verify that the interface works. Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the interface 
   that is being tested:

     ping  <IP_address>	

Command Line Parameters
=======================

If the driver is built as a module, the  following optional parameters are 
used by entering them on the command line with the modprobe or insmod command
using this syntax:

     modprobe atl1 [<option>=<VAL1>,<VAL2>,...]

     insmod atl1 [<option>=<VAL1>,<VAL2>,...] 

For example, with two L001 PCIE adapters, entering:

     insmod atl1 TxDescriptors=80,128

loads the atl1 driver with 80 TX descriptors for the first adapter and 128 TX 
descriptors for the second adapter.

The default value for each parameter is generally the recommended setting,
unless otherwise noted.

    NOTES: A descriptor describes a data buffer and attributes related to the 
           data buffer. This information is accessed by the hardware.

MediaType
Valid Range: 0-5
		0    - auto-negotiate at all supported speeds
		1    - only link at 1000Mbps Full Duplex
		2    - only link at 100Mbps Full Duplex
		3    - only link at 100Mbps Half Duplex
		4    - only link at 10Mbps Full Duplex
		5    - only link at 10Mbps Half Duplex
Default Value: 0
    MediaType forces the line speed/duplex to the specified value in 
    megabits per second(Mbps). If this parameter is not specified or is set 
    to 0 and the link partner is set to auto-negotiate, the board will 
    auto-detect the correct speed. 

IntModTimer
Valid Range: 50-65000
Default Value: 100
    This value represents the minmum interval between interrupts controller 
    generated. 

RxDescriptors
Valid Range: 128-2047 
            
Default Value: 256
    This value is the number of RFD/RRD descriptors allocated by the driver. 
    Increasing this value allows the driver to buffer more incoming packets. 
    A receive buffer is also allocated for each descriptor and can be either 
    2048, 4096, or 8192 bytes, depending on the MTU setting. 
    The maximum MTU size is 8192.

    NOTE: MTU designates the frame size. It only needs to be set for Jumbo 
          Frames.
    NOTE: Depending on the available system resources, the request for a
    higher number of receive descriptors may be denied.  In this case,
    use a lower number.

TxDescriptors
Valid Range: 64-1023

Default Value: 512
    This value is the number of transmit descriptors allocated by the driver.
    Increasing this value allows the driver to queue more transmits. 

    NOTE: Depending on the available system resources, the request for a
    higher number of transmit descriptors may be denied.  In this case,
    use a lower number.

FlashVendor
Valid Range: 0-2

Default Value: 0
    This value standards on vendor of spi flash used by the adapter.
    0 for Atmel, 1 for SST, 2 for ST
    

Additional Configurations
=========================

  Configuring the Driver on Different Distributions
  -------------------------------------------------

  Configuring a network driver to load properly when the system is started is
  distribution dependent. Typically, the configuration process involves adding
  an alias line to /etc/modules.conf as well as editing other system startup 
  scripts and/or configuration files. Many popular Linux distributions ship 
  with tools to make these changes for you. To learn the proper way to 
  configure a network device for your system, refer to your distribution 
  documentation. If during this process you are asked for the driver or module 
  name, the name for the Linux Base Driver for the Attansic L1 is atl1
  
  As an example, if you install the atl1 driver for two L1 adapters 
  (eth0 and eth1) and set the speed and duplex to 10full and 100half, add the 
  following to modules.conf:

       alias eth0 atl1
       alias eth1 atl1
       options atl1 Speed=10,100 Duplex=2,1

  Viewing Link Messages
  ---------------------

  Link messages will not be displayed to the console if the distribution is 
  restricting system messages. In order to see network driver link messages 
  on your console, set dmesg to eight by entering the following:

       dmesg -n 8

  NOTE: This setting is not saved across reboots.

  Jumbo Frames
  ------------

  The driver supports Jumbo Frames . Jumbo Frames support is enabled by 
  changing the MTU to a value larger than the default of 1500. Use the 
  ifconfig command to increase the MTU size. For example:

       ifconfig eth<x> mtu 3000 up

  NOTE: This setting is not saved across reboots. The setting change can be 
  made permanent by adding:

       MTU=3000

  to the file /etc/sysconfig/network-scripts/ifcfg-eth<x>, with Red Hat
  distributions, for example.  Other distributions may store this setting in a
  different location.

  NOTE: MTU designates the frame size. To enable Jumbo Frames, increase the MTU 
  size on the interface beyond 1500.


Known Issues
============

NOTE: For distribution-specific information, see the ldistrib.txt file 
      included in the driver tar.

  Driver Compilation
  ------------------

  When trying to compile the driver by running make install, the following
  error may occur: 

      "Linux kernel source not configured - missing version.h"

  To solve this issue, create the version.h file by going to the Linux source 
  tree and entering:

      make include/linux/version.h.

---

### Post by chili555 on 2007-04-14
First, you will need a package called build-essential which you can get here: [http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) All those red dots indicate dependencies, so download those, too. You will also need linux-headers to match your running kernel, which you can find with the command *uname -r* [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=linux-headers&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=linux-headers&sourceid=mozilla-search)

Since you have no internet access, I assume you will download these on another computer and USB drive or CD-R them to your Ubuntu machine. When you get them moved over, you can drag-n-drop them to your Home folder. Then, open a terminal and:```
sudo dpkg -i build-essential
sudo dpkg -i next_one
etc.
```Press the TAB key and all the remainder of the filename will fill in.

Now we are ready to install Attansic. Drag-n-drop the tar.gz (affectionately known in Linux as "tarball") to your Home folder. Right-click it and select "Extract here." A folder will be created. Double-click the new folder and you will be inside. See if there is an INSTALL or README document you can open with a text editor. It will describe the process.

Generally, the process is to open a terminal and do:```
cd <new_directory_created>
./configure
make
sudo make install
```A module will be built, possibly called atl1.ko. Do:```
sudo modprobe atl1
```and eth0 should appear.```
sudo dhclient eth0
```

---

### Post by shoq on 2007-04-14
Thanks Chili

While waitn for a reply, i found me way to Terminal, and tried "make install" on the L1 driver, as it instruced.  I was told "Install: cannot create directory 'lib/modules/2.6.17-10-generic/kernel/drivers/net/atl : permission denied

Now, i have two users.  Admin and my name (matte) and seem to have ALL permissions.  yet I could not write to the usr/ folder earlier.  Is this because I have not done as you instruct above, and nothing is configured property yet?

This is all pretty confusing.  Can't see who this is ever going to take on windows, if it's this much trouble just installing a network,.. but I will patiently keep learning.  I just keep wondering how my mom would have even gotten this far. She wouldn't have.

Anyway.. onward. Let me not read your instructions

Just went to first link.  You said to move to "home folder"   Do i need a particuar subfolder for all of these?  Am I to just drove each file  into the home folder under my user name?  Very unclear here

---

### Post by shoq on 2007-04-14
You said "red dots" are dependencies. There are like 6-8 of them, and then each of THOSE has dependencies, and each of those do too.  Are you suggesting I have to traverse all those packages and dependences, and install them all?  It's very confusing

Regardless of what I download, Do ALL of these files go to my home folder? Or do i create one like

home/shoq/driveABC?

I am sorry to be such a dolt, but as you might imagine, downloading about a 75 files (at least) under all those red dot paths seems an awful lot of effort to make a driver. Am I missing something?  Is there one archive that contains them all, or is this just what any builder has to go through to assemble linux for this sort of work?

I just looked again. There are hundreds of files.  Each dependency had dependcies which have dependencies. This just cannot be what you meant for me to do, is it?  If it is,  there must be an archive with all of them included, or perhaps another Ubuntu disk that has them all?  I am just completely confused here. It would take all day to traverse and download all these dependencies.

---

### Post by chili555 on 2007-04-14
Permission denied usually means you need to preface the command with sudo and give your password when prompted. > Are you suggesting I have to traverse all those packages and dependences, and install them all?Yessir.> do ALL of these files go to my home folder?Yessir, and when you have installed them all, you can move the packages to Trash and empty it.

The short version is:
#download dependencies and install
#extract tarball
#cd atl1.../src
I notice their instructions do not call for 'make', so:
#sudo make install
#sudo modprobe atl1
#sudo dhclient eth0> I just keep wondering how my mom would have even gotten this far. She wouldn't have.Mom probably uses a Dell/Gateway?HP/Compac/IBM where a guy no smarter than you sorted all this at the factory, burned a CD and cloned 5,000 harddrives to pre-install in computers for sale. You wouldn't hand a home-built computer and a Vista disk to Mom and expect success, would you? My wife, who is probably as old as your Mom, uses Kubuntu every day and could not be happier. Of course, she is sleeping with a pretty decent 'sort-it-out' guy! In Linux, you are the 'sort-it-out' guy.> Can't see who this is ever going to take on windows,It probably won't until pre-installed systems are widespread. Then, I will shed a tear, because when everybody can do it, it will have lost it's cool.

---

### Post by shoq on 2007-04-14
The short version is:
#download dependencies and install
#extract tarball
#cd atl1.../src


Short version of WHAT?  I have looked at each dependency,  Each one begans level upon level of dependency. Perl, and a bazillion others.  IT would take days to download them all.

What am I missing here? Is there not one archive or repository I can download all at once?

I found this about the Attlansic on the net. It seems to imply a built driver of some kind, but perhaps you can interpret for me? Can this save some time?
[http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html)


ALTERNATIVE

I go out and buy a cheap network card guaranteed to work
1) Can you recommend such a slam dunk card? (PCI)
2) Can i set it up, sort of plug and play, without reinstalling everything? If so, what is the procedure for just "detecting new hardware," (to use a WinXP paradigm)

I hate to do this, as I have a card that works fine in windows. I just can't believe I am the only one to go through this, and there msut be somethign I can build without sending a full day downloading all these files :)

Regards to your wife.  Bet she had a card that was recognized, right?

---

### Post by shoq on 2007-04-14
Found this thread. He has my save NIC and Motherboard.  I dont' understand why he's not going through all this download drama to build.  Does this threat assume he had all these build tools already?  I just dont' get this.  I have never seen tools require separate downloads like this in any evironment ever.  I must be stuck on stupid here.

[http://ubuntuforums.org/showthread.php?p=2438730](http://ubuntuforums.org/showthread.php?p=2438730)

---

### Post by chili555 on 2007-04-14
No! Do not download hundreds or even 50! The needed packages may, in fact, be on your install CD! Put it in the tray and let's do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build essential linux-headers-`uname -r`
```That's back-tick there, over left of 1 on your keyboard. Ignore any errors about not being able to reach the repositories.

Try it.> I dont' understand why he's not going through all thisEither he has installed the requirements or he's going to come right back with a showstopper. "I tried to compile, but I got all these errors..." But it costs you nothing to try *without* the dependencies, go ahead, see for yourself.

---

### Post by shoq on 2007-04-14
Ah..so there was a better way. Does it matter where i type these commands? Should I be in a folder I create first?

If so, where  should it be?

home/usernname/Mydriver  ?

---

### Post by chili555 on 2007-04-14
Not at all. This will not download them to your Home folder, but install directly from the CDROM.

---

### Post by shoq on 2007-04-14
Uhh.. when I rand the first command, all seemed up
but when i ran update.. i got this


sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Temporary failiure resolving 'security" blah blah

I ASSUME these were what you warned me to ignore... BUT
Next. when i typed

        sudo apt-get install build essential linux-headers-`uname -r`

I got"Unable to lock the admin director (/var/lib/dpkg/) , is another process using it?

   I tried "n" and got bash: No command found

What now, brown cow? 


Did you mean literally `uname' or my username?  I tried both. both failed

---

### Post by chili555 on 2007-04-14
I really don't understand this: > Unable to lock the admin director (/var/lib/dpkg/) , is another process using it?Unless you have Synaptic or Update Manager or some-such open. Close every window and application except the terminal and try again.

It is 'build-essential' and not 'build essential' That little hyphen, or lack thereof, will be a showstopper.

> I tried "n" and got bash: No command foundI really, really don't understand this. What is "n" supposed to do?

To recall previous commands, press the up arrow. Keep pressing and it will go back in time for roughly 100 commands. To see a command related to a particular subject, do:```
history | grep <whatever_u_want>
```

---

### Post by shoq on 2007-04-14
Ok.. i tried it again...  closed a bunch of windows.

This time, got "Building dependency tree. Reading state info. Done

Now I go back and try the earlier effort to build?

---

### Post by chili555 on 2007-04-14
Did it install build-essential and linux-headers as far as you could see? Did it tell you new packages being installed, X MB of space required, etc.? If so, please proceed!

---

### Post by shoq on 2007-04-14
I have no way of knowing. It said nothing like that., and there is so much in this terminal window, i have no idea what is what now. 

I am now so confused again

I tried to copy the log to show you.  But now the CD-Rom will not work,after trying to write to it once, and failing.  Now, even if I try new disks, I am told there is no medium persent.

I will reboot, but generally, I really have no idea what to do now.  I saw some refernces to linux headers when i tried to "make install" on the ATTANSIC folder, as it said.. but they it failed to make the module. Ccould you please look at attansics instructions, and assume we now have the right build stuff, and take it from there?

I am really overwhelmed here. I have no idea what is rigtht and what is wrong, and no real way to orient myself now.  I will try to send the log, but let's assume i can't do that either.

I TRIED again.  The ONLY CD that is reading, is tke Live Ubunto CD.  Ever since we did those CD commands, no other media will read or autorun.  Thus, i cannot load a disk to save logs, or do much of anything
What now? This cannot be this hard, can it?

---

### Post by shoq on 2007-04-14
Now I got the CD To read, but when i try to copy the bug document to the CD. I am told that I do not have permissions to write to this folder

Clearly, permissions are a bit out of whack.  How could this happen, from a virgin Live CD instally?

Should I just start all over again?

PS
 So I go to properties > permissions, and all options are grayed out. 
At the bottom, it says "you are not the owner, so you cannot change the permissions"

There is just an admin and a user.  How do I set it up so I have "ower" rights"?   This is all very odd, for something that is supposed to be so easy.. lol

UPDATE
With a plain new bland CD-RW disk, nothing is detected. 
I type apt-cdrom ident  and get "failed to mount cdrom"



OH

The owner is who created the folder. But the folder was created under XP on my other machine. How do I break though that so I can write on this same CD, on the Ubuntu machine?

Chili? Might we coduct this via Instant message.  I have skype, AOL, googletalk, and YIM.  It would be much easier. Now sure how to exchange IDs here. My google talk is my gmail, and not wild about posting that.  My skype is cultureshoq.  I will run that, just in case.  Otherwise, I am sitting here unable to get the CD to write you the log, or do much else. Please advise.

---

### Post by chili555 on 2007-04-14
Skype: cultureshoq -- user not found.

Check PM.

---

### Post by shoq on 2007-04-14
Ooops. Sorry. Signed on the wrong skpe

I am there now. Try again

---

