---
title: "How to start up?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Roadkill Bill on 2011-02-19
I had Ubuntu on my laptop, but have not had time to really use it. My computer was worked on, but the Ubuntu was gone. I reinstalled it, however, when my computer starts up I have a choice between Windows and Ubuntu. When I select Ubuntu it asks for a password. I don't have a password. I don't know how to get to it. What do I do?

---

### Post by vivek.pandey on 2011-02-19
this password is same as the password you entered while installing ubuntu.. when you would have installed it you would have been asked a user name and password this is that password

---

### Post by Roadkill Bill on 2011-02-19
I was never asked for one, or I would have known what to enter.

---

### Post by vivek.pandey on 2011-02-19
k try this i am not sure it will work on ubuntu but it works well on backtrack..start ubuntu in safe or console based mode.. enter user as root and password as toor.well you can try this even on gui  if trying console and if you get the permission to log in type startx on the console and you should go to the gui mode

---

### Post by uRock on 2011-02-19
The root/toor thing is a default setting for Back|Track only.

Try resetting the password as described in this link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Roadkill Bill on 2011-02-19
Well, it's getting closer.

Now I've reset the username and password. Then when I enter them I get:

Ubuntu 9.10 ttyl
doug@ubuntu:~$


What do I do next?

---

### Post by vivek.pandey on 2011-02-19
> **Roadkill Bill said:**
> Well, it's getting closer.

Now I've reset the username and password. Then when I enter them I get:

Ubuntu 9.10 ttyl
doug@ubuntu:~$


What do I do next?

well if you are in console type startx it works in ubuntu you will get into your gui

---

### Post by Roadkill Bill on 2011-02-19
gui?

When I typed in "startx" I got a whole bunch of stuff such as

"error in locking authority"
"could not create lock file"
"closing log giving up"

Should I just try loading this again and see what happens, or is there still hope?

---

### Post by Rubi1200 on 2011-02-19
How did you install Ubuntu in the first place and what version are you using?

---

### Post by Roadkill Bill on 2011-02-19
I installed it from a disk, version 8.10.

---

### Post by n-n-nebbl on 2011-02-19
> **Roadkill Bill said:**
> I installed it from a disk, version 8.10.

I would advise to use the newest version (10.10)

The errors with the lock-files is a privilege-problem
only superusers like root can start X i think.


if you can log in, in console screen, can't you use the same username/password in the Graphical User Interface (GUI) when you start it normal.

---

### Post by Roadkill Bill on 2011-02-19
I just started all over again.
Thanks to all. I'll let you know soon if it works this time.

Even if it does, I'll still need help. I'm a Mac person, and even PCs give me trouble. This is a whole new world to me. (But I'm told it's a ***better ***world!)

---

### Post by Roadkill Bill on 2011-02-20
OK, I'm back and Ubuntu is up and running.

Now my question is how do I get the internet to work. My wireless connection doesn't seem to want to connect. Nor does it work when I plug the DSL straight into the computer. Are computers always such a pain?

---

### Post by G4Oblivion on 2011-02-20
> **Roadkill Bill said:**
> OK, I'm back and Ubuntu is up and running.

Now my question is how do I get the internet to work. My wireless connection doesn't seem to want to connect. Nor does it work when I plug the DSL straight into the computer. Are computers always such a pain?

You're probably missing a driver.
If you plug your computer in directly to your modem through your computers ethernet port (the thing that looks like a phone cord)
You should be able to connect to the internet.

Go to System -> Administration -> Hardware Drivers

It should pop up a list of available drivers that you are able to install, wireless, graphics, etc.

e.g: My wireless driver is Broadcom B43

(I'm new to Ubuntu, so I could be wrong)

Just about all ethernet cards should work. Can you post what card you have?

To check your ethernet card, open up terminal and enter this:
```
$ lspci | grep -i eth
```

---

### Post by Roadkill Bill on 2011-02-20
Did the System>Administration>Hardware Drivers thing, and neither of my choices will load. After half an hour the loading indicator bar has not appeared yet. Does it usually take this long?

---

### Post by G4Oblivion on 2011-02-20
> **Roadkill Bill said:**
> Did the System>Administration>Hardware Drivers thing, and neither of my choices will load. After half an hour the loading indicator bar has not appeared yet. Does it usually take this long?

You need internet access first, so it can check for hardware drivers.
Once you are connected to the internet it should only take ~1min.

To connect to the internet you need to plug your computer directly into your modem.

Please post what ethernet & wireless cards you have.

To check what cards you have enter this into the terminal:
```
lspci | grep -i eth
lspci | grep -i network
```

---

### Post by Roadkill Bill on 2011-02-20
OK, dumb rookie question here. How do you type it into the "terminal"?

I tried the line up top and got a Google search.

---

### Post by Roadkill Bill on 2011-02-20
Got it.

Ethernet controller: Broadcom Corporation BCM4401-B0 100Base -TX (rev 02)
Network controller: Broadcom Corporation BCM4312 Bo2.11b/g (rev 01)

I don't know what that means, so what do I do now?

---

### Post by vivek.pandey on 2011-02-20
> **Roadkill Bill said:**
> OK, dumb rookie question here. How do you type it into the "terminal"?

I tried the line up top and got a Google search.

to type anything in applications->terminal and then type the given command

also you should tell a bit more about your modem for us to try to help

---

### Post by thefasterblueone on 2011-02-20
@Roadkill Bill, check this thread for possible solution.

   [http://ubuntuforums.org/showthread.php?t=1604868]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by G4Oblivion on 2011-02-22
Step by step with pictures:

Open up terminal
[http://i53.tinypic.com/5y7vah.jpg](http://i53.tinypic.com/5y7vah.jpg)

Type ```
lspci
```
[http://i52.tinypic.com/wim5w6.jpg](http://i52.tinypic.com/wim5w6.jpg)

Hit enter, and you should get something that looks like this
[http://i51.tinypic.com/105sfoj.jpg](http://i51.tinypic.com/105sfoj.jpg)

Copy everything it just printed on the terminal
[http://i55.tinypic.com/34pm7oy.jpg](http://i55.tinypic.com/34pm7oy.jpg)

Post what you just copied here.

---

### Post by Roadkill Bill on 2011-02-23
What I copied was:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by G4Oblivion on 2011-02-24
Looks like your Ethernet card is supported.
You have to download the STA driver to get wireless.

STA Driver download:
Select your Ubuntu version

Ubuntu 9.10 Karmic STA Driver download:
32Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb")
64Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_amd64.deb")

Ubuntu 10.04 Lucid:
32Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb")
64Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb")

Ubuntu 10.10 Maverick:
32Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb")
64Bit: [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")

Put that on a flash drive or something and install it.

---

### Post by Roadkill Bill on 2011-02-24
It didn't work from a flash drive, and then when I tried to use it from a package I got:

An error occurred
E: Could not get lock/var/cache/apt/archives/lock-open (11:Resource temporarily unavailable)
E: Unable to lock the download directory

I think the second one is what I got when trying to load from the flash drive.


(Gosh, how do you guys know all this stuff??!!?)

---

### Post by G4Oblivion on 2011-02-25
I haven't tested it, so I don't know if the driver can be installed offline. I don't see why not.
EDIT: I tested it and it installed offline. I can't be 100% sure though, since it was already installed.

Open terminal again and type
```
sudo apt-get clean && sudo apt-get autoclean
```

**Make sure no package manager is open e.g: Synaptic Package Manager, Ubuntu Software Center, etc.**

Open up the terminal again and type this:
```
cd Desktop
``` (Be sure to use an upper-case D)
I assume the .deb (package) is on your Desktop. If not, put it there.
Now enter this in terminal:
```
sudo dpkg -i FILE_NAME.deb
```

Where "FILE_NAME.deb" is put the name of the package.
To get the packages file name easily, right click it and select properties.
Under "NAME: " is the files full name, copy that.
Screenshot: [http://i54.tinypic.com/2nathqt.png]("http://i54.tinypic.com/2nathqt.png")

Paste the file name into the terminal once you've followed the steps above.
Should look like this: [http://i54.tinypic.com/2nathqt.png]("http://i54.tinypic.com/2nathqt.png")

If the error still appears you probably need to connect your computer directly to your router/modem using an Ethernet cord.
(Looks like a phone cord, but slightly bigger.)
[INTERNET NEEDED]
And open System -> Administration -> Hardware Drivers
Select the STA driver.
If Hardware Drivers freezes or doesn't work for some reason open up synaptic.
System -> Administration -> Synaptic Package Manager
Seach "bcmwl" without the quotes.
Two packages should appear:
bcmwl-kernel-source
bcmwl-modaliases

Install both of them. To install a package, right click it and select "Mark for installation"
[INTERNET NEEDED END]

I looked up your Ethernet card and it looks like Ubuntu supports it. Ubuntu 8.04 LTS, 10.04 LTS and 10.10 support it.
I suggest using 10.04+ if you're not already, unless theres a specific reason you're using an older version.

What I meant by:
> Put that on a flash drive or something and install it.
Was to download the driver on another computer and put it on a flash drive to transfer it.

I'm out of ideas if none of the above work.

---

### Post by Roadkill Bill on 2011-02-26
I entered:

doug@ubuntu:~$ sudo apt-get clean && sudo apt-get autoclean

and got

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
doug@ubuntu:~$ ^C
doug@ubuntu:~$

Also when I tried to install the two bcmwl packages I got:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by G4Oblivion on 2011-02-26
> **Roadkill Bill said:**
> I entered:

doug@ubuntu:~$ sudo apt-get clean && sudo apt-get autoclean

and got

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
doug@ubuntu:~$ ^C
doug@ubuntu:~$

Also when I tried to install the two bcmwl packages I got:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Try deleting the lock file (It is safe to delete this file. Be sure to recreate the file later, though. This is just an empty file)

To delete the file open terminal and enter
> sudo rm -rf /var/cache/apt/archives/lock

Try it again and see if it works.

To recreate the file, enter this:
> sudo touch /var/cache/apt/archives/lock

---

### Post by Roadkill Bill on 2011-02-26
I tried this and it keeps coming back to the prompt.

doug@ubuntu:~$ sudo rm -rf /var/cache/apt/archives/lock
[sudo] password for doug: 
doug@ubuntu:~$ sudo rm -rf /var/cache/apt/archives/lock 
doug@ubuntu:~$ sudo rm -rf /var/cache/apt/archives/lock
doug@ubuntu:~$

---

### Post by vivek.pandey on 2011-02-26
BUDDY are you running two sudo simultaneously. i mean two processes which need your password , if yes stop one and then retry

---

### Post by Roadkill Bill on 2011-02-27
I tried to load the two bcmwl packages. They appeared to load, but then I got the message:

Please insert the disk labled:
Ubuntu 9.10_Karmic Koala_-Release amd64(20091027)
in drive/cdrom/

I have no such disk. What do I do now?

(Man, if DOS and Mac had been this much trouble I would never have gotten into computers!)

---

### Post by nm_geo on 2011-02-27
> **neo_aryan said:**
> BUDDY are you running two sudo simultaneously. i mean two processes which need your password , if yes stop one and then retry

+1 Synaptic or Update Manager or Additional Drivers.  Something else is running.. Been there done that..

---

### Post by Roadkill Bill on 2011-02-27
Thanks for all your help folks, but I am punting.
I just don't don't have time for all of this crap. Not exactly user friendly. Too much "insider information" required. Linux/Ubuntu may be great, but I guess I'm going to just stick to Mac and Windows right now. Maybe this summer I'll download it again and try once more, but even then it may just be a waste of time.

Thanks again.

---

### Post by vivek.pandey on 2011-02-27
> **Roadkill Bill said:**
> Thanks for all your help folks, but I am punting.
I just don't don't have time for all of this crap. Not exactly user friendly. Too much "insider information" required. Linux/Ubuntu may be great, but I guess I'm going to just stick to Mac and Windows right now. Maybe this summer I'll download it again and try once more, but even then it may just be a waste of time.

Thanks again.

surprised to see you gave up so soon.... and i guess it wasnt waste of time . for learning any new thing you need patience and a lot of hard work . did you go through ubuntu's documentation. nobody said ubuntu would be easy but its worth the hard work you put into because you didnt pay a single penny for it. dont think that whatever i am saying is in fit of anger or to promote ubuntu. its only to let you know what i feel about it. i hope i am not rude. all the best. hope you will be back again :-)

---

