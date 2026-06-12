---
title: "Failing miserably at setting up Linksys USB Wireless-G Adapter"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by phayke on 2007-01-17
Hello, I have recently installed Ubuntu 6.10, Edgy on my secondary disk with the intent to gradually make the big switch. However, this is my big hurdle: Wireless.

I am not ashamed to admit that I am horribly undereducated with Linux, I've never learned much in it because I usually couldn't function enough to patiently learn, so I just went back to windows, instead of being stuck offline or unable to use my computer. I've googled most of yesterday and today trying to fix my problem, but every tutorial or forum thread has been difficult for me to use to my advantage. 

First of all, I don't know all of the things being referenced to, or how to do the tasks I need to do for the most part, or many of the other variables, so if someone could patiently help a noob, you would be converting one more person to Linux.  

I'll try to be as clear with my issue as I can be, if someone will be equally clear (dumbed down) with an answer. (I AM a windows user after all :p )

From what I've read so far on posts, hooking up this adapter seems to range from easy to impossible, but I've been reading many different posts for different distro's and adapters, and many threads were quite out of date.

I have a Linksys Wireless-G USB network adapter with SpeedBooster, and as previously stated, Ubuntu 6.10. I'm unsure what version of the adapter this is, I didn't even know there were different versions of the same one. I bought it late last spring however, and if someone can tell me how to find which version it is, I'll give that. 

Naturally it wasn't detected out of the box, and searching google brought up this page:
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

The article is nearly one and a half years old, but it promised **easy** so I was drawn to it. 

I downloaded the ndisgtk and ndiswrapper-utils packages from the first website google returned, (I suppose the main source) and installed them. It popped up with a wireless windows drivers button in my admin settings menu. I clicked it and it gave me an option to install drivers. Since I don't know how to get that stuff from an exe file and was afraid of adding more frustration to my problem, I just put in my driver cd and copied both WUSB54GS.inf and WUSB54GSv2.inf to my desktop and installed both. Now both drivers are listed in the window, but both say 'Hardware Present: no'. 

I should point out that when I plug in my adapter it is properly recognised in Device Manager even to the point of capitalizing the 'B' in 'SpeedBooster'. This is where I'm at a brick wall. I feel so close but so far. I'm unsure when in the whole process I should be restarting or unplugging/plugging the adapter, but when I DO plug in the adapter the green LED instantly blinks and then goes out, and if I look closely, both lights are on very faintly but aren't shining or blinking. So I know that the adapter is recognized and receiving power, but it seems that's not quite enough. 

I've also in my quest come across notes about voltage problems in Ubuntu, though I'm unsure if they've been corrected in the version I have or not. I found this guide on the forums here:
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

It was terribly huge and intimidating. With plenty of room for a Windows user like me to get lost, but I made a couple blind guesses as to what I was being directed to do. 

I read to this part: **Getting WUSB54GS to Work in Edgy and Feisty**
I followed the instructions and opened a terminal instance, copy pasting the lines provided to be extra careful. Though it told me not to plug in my adapter until I was told, I was unable to find a place in the guide where I was actually TOLD to plug in my adapter, so I've been plugging it in and out after changes to see if anything happens. Since I'm unsure the version of my adapter, I followed the rules for both. I created the custom.rules file with the instructions for V1, and when that did nothing, I tried it again replacing the text with the V2 line. Again no change, and I've reset my computer as well. I actually don't know what all was being done in terminal, I assumed I was making a new text file with some instructions on it. Does this text file get detected and read automatically? Usually when I make changes to things I'm used to editing an already existing file. Again, this is coming from someone who only has experience in Windows, so I could be way off. 



Another option I've thought is that I have Mandriva 2007's DVD install. Perhaps the wireless is recognized easier on that distro, (Though I have to admit I love Edgy's look and logo.) The problem with installing that however, was that although the DVD image checked out clean and I wrote it to two different brands of DVD-R at my slowest speed, they were only recognized while in windows, and wouldn't boot up. I checked with the dell website and I apparently have the most recent bios for my motherboard. Perhaps my computer is too old 'Dell Optiplex GX 150' and doesn't support booting from DVD. Is there perhaps another way to tackle that installation if I needed to, like installing from a live cd and then upgrading with the DVD? Or maybe some kind of trick to booting from a DVD? I feel like I'm close enough to making things work with Ubuntu that I'd prefer getting this running however. 



If someone happens to read this and has an idea what I should do next, I'll try anything. The only way I get internet access is through wireless, and the only thing to without internet (for me) is play games or media, which is more something I'd do on my windows partition anyway. 

Thank you,
Phayke

---

### Post by phayke on 2007-01-18
A couple things I've noticed today:

In XP the process used by my wireless adapter is labeled WUSB54GSv2.exe, and in my windows device manager it's listed as a v2. I'm not sure if labels are always undeniably true, but I'll run with it. 

It says the driver file is USB8023.sys, a file that I (somehow) couldn't locate on my driver cd or the downloaded drivers. All I had in my driver folders were .inf and .cat files, and I only copied the .inf files, since that's what ndiswrapper button prompted me to find. That may have been my error. I'm unsure where to put the .sys file, or whether there's anything else I need to move, but I'm sure I can find it on the forums here. Alot of the guides here use the command prompt, and I did it all with the interface, assuming that it was a more recent, user friendly way, so perhaps there was a step I missed that I should have done with the prompt?

The most difficult thing about finding your own help is comparing all of the thread dates. I wish it were easier to find what is most relevant.

---

### Post by wieman01 on 2007-01-18
I have not done this for a while, but start with this guide:

[http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g]("http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g")

Since you have already installed "ndiswrapper", you can skip the first steps. But give this one a go first. And make sure you have the right driver for your card (the version plays a role as well). I have a WUSB54G which works fine but I am not entirely sure about the WUSB54GS...  This could turn out to be a no-go. Nonetheless, try the guide first and post your problems here.

Let's see what we can do.

---

### Post by phayke on 2007-01-18
From what I've read, the adapter I have works fine for other people after the initial setup. The problem I have though is, although I can find the .inf files in my driver cd, I cannot find any kind of .sys files. Is the .inf all I would need? Windows isn't hiding any filetypes from me, but I can't find any .sys files anywhere. There are two un-openable .cab files in the driver cd's utilities folder, but I'm not sure if they're important. Maybe newer drivers don't have the .sys files? From what I've read, other people have had a WUSB20XP.sys file, but I can't find that file anywhere, even with a google search. I think the one my device manager is associating with my adapter (USB8023.sys) must be some kind of generic driver?


So far as the other guide, I've installed ndiswrapper and afterwards pointed it to my .inf file. Ubuntu recognized my device right after install, but their drivers didn't work, while now the ndiswrapper program is telling me that driver is installed but doesn't recognize my device.
I didn't use the commands sudo depmod
sudo modprobe ndiswrapper afterwards. I've been working through the GUI, would the commands still be the same or would I need to move to a ndiswrapper directory in the prompt before using them?


Edit: AH, I didn't see the part about blacklisting the default driver. Maybe that's the problem. Also heard that you shouldn't boot with the device connected.

Now to try all of this out.

---

### Post by Ritchstorm on 2007-01-18
Hello! I have a Linksys Wireless USB G version 2 and I used[ this topic!]("http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54g") At first it did not work and I later realised it was because I did not read further down where it told me a few extra things you needed to do if you are running 6.10 (usb power problems). I did exactly what it said and I used the attachment he provided however I had to connect directly through ethernet to install it. I did not plug my USB device in till I had done all of the extra things required for 6.10. Sorry if it doesn't help. Also to find out what version your device is just look on the underneath. Mine say "Model No. WUSB54GS ver.2" in a little box near the top. If yours just says WUSB54GS i'm guessing it is just ver.1

---

### Post by phayke on 2007-01-18
Ah, I read that thread actually, however I think I might have overlooked some parts, because apparently it answers alot of my questions. (Maybe it hadn't made sense earlier before I got this far?) I'm going to try that now. I actually think I ignored most of the thread because the title seemed specific and confusing.

---

### Post by phayke on 2007-01-18
I followed all of the instructions in: [http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54g](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54g)

and using the attached drivers ndiswrapper now recognizes when my adapter is plugged in or not. The only problem is that the light for my adapter still blinks once quickly and remains very dim. It is seen now in my device manager and in ndisgtk as present, but not in my network connections. My network connections shows my two disabled ethernet cards and an unconfigured dialup modem. I'm going to post on the other thread as well to see if maybe someone there knows what it could be.

---

### Post by wieman01 on 2007-01-19
Try these commands & post the results:
> iwlist scan
> route

---

### Post by phayke on 2007-01-19
phayke@FAILURE:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

phayke@FAILURE:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by javaJake on 2007-01-20
> **wieman01 said:**
> I have not done this for a while, but start with this guide:

[http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g]("http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g")

Believe it or not, but the S on the end of the model number (WUSB54G**S**) makes a big difference. So, while you may be tempted to follow instructions for a WUSB54G device, it won't work.

---

### Post by wieman01 on 2007-01-20
> **javaJake said:**
> Believe it or not, but the S on the end of the model number (WUSB54G**S**) makes a big difference. So, while you may be tempted to follow instructions for a WUSB54G device, it won't work.
That is true indeed... The Windows driver will be different as well as the native Linux driver that you have to blacklist. But that's all I can offer at this stage.

Are there any other HOWTOs around that you are aware of? I am running out of ideas here.

---

### Post by javaJake on 2007-01-20
> **wieman01 said:**
> That is true indeed... The Windows driver will be different as well as the native Linux driver that you have to blacklist. But that's all I can offer at this stage.

Are there any other HOWTOs around that you are aware of? I am running out of ideas here.

No, not besides mine. I would not have created a HOWTO myself, but would've contributed to an existing one instead if one existed that was close to being right. :D

---

### Post by wieman01 on 2007-01-20
> **javaJake said:**
> No, not besides mine. I would not have created a HOWTO myself, but would've contributed to an existing one instead if one existed that was close to being right. :D
Honestly, I even doubt a WUSB54GS with work with Linux. Anyway, if you happen to come across something, you know where to find a grateful audience. :-)

---

### Post by javaJake on 2007-01-20
> **wieman01 said:**
> Honestly, I even doubt a WUSB54GS with work with Linux. Anyway, if you happen to come across something, you know where to find a grateful audience. :-)

Don't doubt - I use it all the time, and many others have gotten it to work as well. :D

If you need help, post your issues, and I'll see what I can do.

---

### Post by javaJake on 2007-01-20
> **phayke said:**
> I am not ashamed to admit that I am horribly undereducated with LinuxPlease don't feel ashamed about this at all! Everyone starts somewhere. The "gurus" on the forums all started out just like you. :)

> **phayke said:**
> From what I've read so far on posts, hooking up this adapter seems to range from easy to impossible, but I've been reading many different posts for different distro's and adapters, and many threads were quite out of date.This adapter ranges from easy to tricky. Impossible is not true, unless you are using a 64-bit system, in which case it is almost impossible. There are a lot of snags that'll keep this from working, which is why there are HOWTOs in the first place. :)

> **phayke said:**
> The article is nearly one and a half years old, but it promised **easy** so I was drawn to it.OK, there's a problem here. The ndiswrapper included with Ubuntu is v1.8, which is extremely outdated. When you try to use this with the WUSB54GS, **it will crash your computer's USB system**.

> **phayke said:**
> I downloaded the ndisgtk and ndiswrapper-utils packages from the first website google returned, (I suppose the main source) and installed them.Yep, you've just hit the first snag - v1.8 will crash your computer. You actually have to compile a newer version (anything above v1.21). And, no, v1.8 isn't newer then v1.21. Go figure.

> **phayke said:**
> I've also in my quest come across notes about voltage problems in Ubuntu, though I'm unsure if they've been corrected in the version I have or not. I found this guide on the forums here:
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)Another snag you've hit - this voltage thing affects all versions above Dapper. It is a new "feature" that restricts power to protect the hardware.

> **phayke said:**
> It was terribly huge and intimidating. With plenty of room for a Windows user like me to get lost, but I made a couple blind guesses as to what I was being directed to do.  Well, if you got confused anywhere, please please please let me know, and I'll try to fix it!

> **phayke said:**
> I read to this part: **Getting WUSB54GS to Work in Edgy and Feisty**
I followed the instructions and opened a terminal instance, copy pasting the lines provided to be extra careful. Though it told me not to plug in my adapter until I was told, I was unable to find a place in the guide where I was actually TOLD to plug in my adapter,At the end I say you can now enjoy your new internet connection, or something like that. Actually, you are pretty much safe after you got the new ndiswrapper version installed.

> **phayke said:**
> Does this text file get detected and read automatically? Usually when I make changes to things I'm used to editing an already existing file. Again, this is coming from someone who only has experience in Windows, so I could be way off.  It gets read next time you plug in your device. I'll see if I can make this clearer...

---

### Post by phayke on 2007-01-21
I may have mis-worded that, I meant that I downloaded my version of ndiswrapper from the first page google returned (the sourceforge page) and it was version 1.34. But I installed the package with the package installer program, if that makes a difference. Also I don't think I've blacklisted so far, I could never change any of the text files because of no root permissions, and not being able to login as root. I don't know any of that sudo jabberwocky either, I just cut and paste this stuff. I also used the correct drivers for my device, as listed on the forums and wiki, so I know the problem wasn't caused by following the guides for a wrong device. The voltage rule I DID add, and it associates correctly with my USB ID. (I think device manager said 0x14 and the rule said 0014) I'll try installing ubuntu from scratch and reinstalling ndiswrapper using the make command though. Probably tomorrow, since it will require moving my computer and the things attached to it next door to get wired access.

---

### Post by ButteBlues on 2007-01-21
Stop the phones!

You don't NEED TO USE NDISWRAPPER.


I have the same USB adapter - there is a WORKING native Linux version. Follow [these instructions](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)) with the following changes:

Rather than using the driver the guide suggests, use [this](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) one. All that SHOULD need doing is the make and make install inside the /Module folder for installing the driver.


Other than that change, follow the guide as specified.

---

### Post by javaJake on 2007-01-21
Wow! Thanks!! :D

I'll test out that guide, since I'd be super happy to be able to drop ndiswrapper!

---

### Post by javaJake on 2007-01-21
> **phayke said:**
> I may have mis-worded that, I meant that I downloaded my version of ndiswrapper from the first page google returned (the sourceforge page) and it was version 1.34. But I installed the package with the package installer program, if that makes a difference.

Yes, it does. You want to go through the make junk, which it looks like you figured a little ways down in your post...

> **phayke said:**
> I'll try installing ubuntu from scratch and reinstalling ndiswrapper using the make command though.

---

### Post by ButteBlues on 2007-01-21
> **javaJake said:**
> Wow! Thanks!! :D

I'll test out that guide, since I'd be super happy to be able to drop ndiswrapper!
If you have any questions regarding the guide, just hit me up. =)

---

### Post by phayke on 2007-01-23
> **ButteBlues said:**
> Stop the phones!

You don't NEED TO USE NDISWRAPPER.


I have the same USB adapter - there is a WORKING native Linux version. Follow [these instructions](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)) with the following changes:

Rather than using the driver the guide suggests, use [this](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) one. All that SHOULD need doing is the make and make install inside the /Module folder for installing the driver.


Other than that change, follow the guide as specified.

Sound's great! I'll try this right away, I have a couple quick questions however.

Since I will be using a different driver, will all of the commands stay the same? In which cases would they differ? For example, would I be blacklisting the same driver at the beginning, or a seperate one for my card? 

> All that SHOULD need doing is the make and make install inside the /Module folder for installing the driver. Other than that change, follow the guide as specified.


Am I correct in assuming that you mean in step 5 I only need to follow up to the: "Verify that the driver was installed correctly using the list short command" bit before skipping to the next step? So I do make clean, make, make install, and sl to check afterwards, and the bit about the firmware directory I ignore?

"The rt73 device requires the use of the "ifconfig rausb0 up" command to wake the device for configuration." This applies to my device as well? I guess using the command wouldn't hurt anything even if my device is already 'woken up'.

Thank you for the help everyone, I'm going to carry my tower to the wired connection and work on this until it's fixed.


Edit: I've gotten without a problem to the point where I have to *Copy the Makefile.6 file into the Makefile to prepare for a 2.6 Linux kernel build:* Since there is no makefile.6, I'm going to assume the package you told me to use is already good for the 2.6 kernel. So if I was supposed to do something else, you know where I went wrong.

---

### Post by phayke on 2007-01-23
```
phayke@FAILURE:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]           
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://us.archive.ubuntu.com edgy Release  
Hit http://us.archive.ubuntu.com edgy-updates Release               
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Fetched 3B in 23s (0B/s)
Reading package lists... Done
phayke@FAILURE:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6 libc6-dev libc6-i686 libstdc++6-4.1-dev
  linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 7 newly installed, 0 to remove and 102 not upgraded.
Need to get 13.2MB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com edgy-security/main linux-libc-dev 2.6.17.1-10.34 [1770kB]
Get:2 http://us.archive.ubuntu.com edgy-updates/main libc6 2.4-1ubuntu12.2 [4129kB]
Get:3 http://us.archive.ubuntu.com edgy-updates/main libc6-i686 2.4-1ubuntu12.2 [1124kB]
Get:4 http://us.archive.ubuntu.com edgy-updates/main libc6-dev 2.4-1ubuntu12.2 [1852kB]
Get:5 http://us.archive.ubuntu.com edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5 [1619kB]
Get:6 http://us.archive.ubuntu.com edgy/main g++-4.1 4.1.1-13ubuntu5 [2573kB]  
Get:7 http://us.archive.ubuntu.com edgy/main g++ 4:4.1.1-6ubuntu3 [1434B]      
Get:8 http://us.archive.ubuntu.com edgy/main dpkg-dev 1.13.22ubuntu7 [110kB]   
Get:9 http://us.archive.ubuntu.com edgy/main build-essential 11.3 [6974B]      
Fetched 13.2MB in 6m49s (32.2kB/s)                                             
(Reading database ... 88191 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.4-1ubuntu12.2) ...

(Reading database ... 88191 files and directories currently installed.)
Preparing to replace libc6-i686 2.4-1ubuntu12 (using .../libc6-i686_2.4-1ubuntu12.2_i386.deb) ...
Unpacking replacement libc6-i686 ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.17.1-10.34_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.2_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.1-6ubuntu3_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up libc6-i686 (2.4-1ubuntu12.2) ...

Setting up linux-libc-dev (2.6.17.1-10.34) ...
Setting up libc6-dev (2.4-1ubuntu12.2) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...
phayke@FAILURE:~$ sudo apt-get install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.17-10-generic
1 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.
Need to get 909kB of archives.
After unpacking 28.7kB of additional disk space will be used.
Get:1 http://security.ubuntu.com edgy-security/main linux-headers-2.6.17-10-generic 2.6.17.1-10.34 [909kB]
Fetched 909kB in 48s (18.9kB/s)                                                
(Reading database ... 89939 files and directories currently installed.)
Preparing to replace linux-headers-2.6.17-10-generic 2.6.17-10.33 (using .../linux-headers-2.6.17-10-generic_2.6.17.1-10.34_i386.deb) ...
Unpacking replacement linux-headers-2.6.17-10-generic ...
Setting up linux-headers-2.6.17-10-generic (2.6.17.1-10.34) ...
phayke@FAILURE:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
phayke@FAILURE:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
ln: creating symbolic link `/lib/modules/2.6.17-10-generic/build/linux-headers-2.6.17-10-generic' to `/usr/src/linux-headers-2.6.17-10-generic': File exists
phayke@FAILURE:~$ sudo apt-get install tofrodos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tofrodos
0 upgraded, 1 newly installed, 0 to remove and 101 not upgraded.
Need to get 16.6kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com edgy/main tofrodos 1.7.6-2 [16.6kB]
Fetched 16.6kB in 21s (779B/s)   
Selecting previously deselected package tofrodos.
(Reading database ... 89946 files and directories currently installed.)
Unpacking tofrodos (from .../tofrodos_1.7.6-2_i386.deb) ...
Setting up tofrodos (1.7.6-2) ...
phayke@FAILURE:~$ dir
Desktop  Examples
phayke@FAILURE:~$ cd Desktop
phayke@FAILURE:~/Desktop$ dir
rt73-cvs-daily.tar.gz
phayke@FAILURE:~/Desktop$ tar xvzf rt73-cvs-daily.tar.gz
rt73-cvs-2007012311/
rt73-cvs-2007012311/FAQ
rt73-cvs-2007012311/THANKS
rt73-cvs-2007012311/CHANGELOG
rt73-cvs-2007012311/CVS/
rt73-cvs-2007012311/CVS/Root
rt73-cvs-2007012311/CVS/Repository
rt73-cvs-2007012311/CVS/Entries.Log
rt73-cvs-2007012311/CVS/Entries
rt73-cvs-2007012311/TESTING
rt73-cvs-2007012311/LICENSE
rt73-cvs-2007012311/Module/
rt73-cvs-2007012311/Module/auth.c
rt73-cvs-2007012311/Module/rt73.h
rt73-cvs-2007012311/Module/rt73.bin
rt73-cvs-2007012311/Module/md5.c
rt73-cvs-2007012311/Module/rtusb_data.c
rt73-cvs-2007012311/Module/rtmp_main.c
rt73-cvs-2007012311/Module/unload
rt73-cvs-2007012311/Module/rt_config.h
rt73-cvs-2007012311/Module/assoc.c
rt73-cvs-2007012311/Module/CVS/
rt73-cvs-2007012311/Module/CVS/Root
rt73-cvs-2007012311/Module/CVS/Repository
rt73-cvs-2007012311/Module/CVS/Entries
rt73-cvs-2007012311/Module/ifcfg-rausb0
rt73-cvs-2007012311/Module/wpa.c
rt73-cvs-2007012311/Module/sync.c
rt73-cvs-2007012311/Module/rtmp_info.c
rt73-cvs-2007012311/Module/iwpriv_usage.txt
rt73-cvs-2007012311/Module/rtusb_bulk.c
rt73-cvs-2007012311/Module/mlme.h
rt73-cvs-2007012311/Module/connect.c
rt73-cvs-2007012311/Module/rtmp_tkip.c
rt73-cvs-2007012311/Module/auth_rsp.c
rt73-cvs-2007012311/Module/oid.h
rt73-cvs-2007012311/Module/rtmp_init.c
rt73-cvs-2007012311/Module/rtusb_io.c
rt73-cvs-2007012311/Module/rt73sta.dat
rt73-cvs-2007012311/Module/rtmp.h
rt73-cvs-2007012311/Module/load
rt73-cvs-2007012311/Module/mlme.c
rt73-cvs-2007012311/Module/md5.h
rt73-cvs-2007012311/Module/wpa.h
rt73-cvs-2007012311/Module/rtmp_wep.c
rt73-cvs-2007012311/Module/rtmp_def.h
rt73-cvs-2007012311/Module/Makefile
rt73-cvs-2007012311/Module/rtmp_type.h
rt73-cvs-2007012311/Module/sanity.c
rt73-cvs-2007012311/README
phayke@FAILURE:~/Desktop$ cd rt73-cvs-2007012311
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ dir
CHANGELOG  CVS  FAQ  LICENSE  Module  README  TESTING  THANKS
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ cd Module
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ chmod -R 775 *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ fromdos *
fromdos: File read/write error while converting CVS.
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ chmod -R 775 *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ chmod -r 775 *
chmod: cannot access `775': No such file or directory
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ chmod -R 775 *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ f
bash: f: command not found
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ fromdos *
fromdos: File read/write error while converting CVS.
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ chmod -R 775 *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ dir
assoc.c     CVS               Makefile  mlme.h    rt73sta.dat  rtmp_info.c  rtmp_type.h   rtusb_io.c  wpa.c
auth.c      ifcfg-rausb0      md5.c     oid.h     rt_config.h  rtmp_init.c  rtmp_wep.c    sanity.c    wpa.h
auth_rsp.c  iwpriv_usage.txt  md5.h     rt73.bin  rtmp_def.h   rtmp_main.c  rtusb_bulk.c  sync.c
connect.c   load              mlme.c    rt73.h    rtmp.h       rtmp_tkip.c  rtusb_data.c  unload
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ cd /
phayke@FAILURE:/$ cd ~
phayke@FAILURE:~$ fromdos *
fromdos: File read/write error while converting Desktop.
fromdos: Unable to create temporary file for converting /usr/share/example-content.
phayke@FAILURE:~$ dir
Desktop  Examples
phayke@FAILURE:~$ cd Desktop
phayke@FAILURE:~/Desktop$ fromdos *
fromdos: File read/write error while converting rt73-cvs-2007012311.
phayke@FAILURE:~/Desktop$ dir
rt73-cvs-2007012311  rt73-cvs-daily.tar.gz
phayke@FAILURE:~/Desktop$ cd rt73-cvs-2007012311
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ dir
CHANGELOG  CVS  FAQ  LICENSE  Module  README  TESTING  THANKS
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ fromdos *
fromdos: File read/write error while converting CVS.
fromdos: File read/write error while converting Module.
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ cd Module
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ fromdos *
fromdos: File read/write error while converting CVS.
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ fromdos *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ cd CVS
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module/CVS$ fromdos *
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module/CVS$ cp Makefile.6 Makefile
cp: cannot stat `Makefile.6': No such file or directory
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module/CVS$ cd .
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module/CVS$ cd
phayke@FAILURE:~$ cd Desktop re73-cvs-2007012311
phayke@FAILURE:~/Desktop$ cd rt73-cvs-2007012311
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ dir
CHANGELOG  CVS  FAQ  LICENSE  Module  README  TESTING  THANKS
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311$ cd Module
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ cp Makefile.6 Makefile
cp: cannot stat `Makefile.6': No such file or directory
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ gedit rtmp_def.h
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ make clean
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtmp_main.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/mlme.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/connect.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtusb_bulk.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtusb_io.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/sync.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/assoc.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/auth.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/auth_rsp.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtusb_data.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtmp_init.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/sanity.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtmp_wep.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtmp_info.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rtmp_tkip.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/wpa.o
  CC [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/md5.o
  LD [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rt73.o
  Building modules, stage 2.
  MODPOST
  CC      /home/phayke/Desktop/rt73-cvs-2007012311/Module/rt73.mod.o
  LD [M]  /home/phayke/Desktop/rt73-cvs-2007012311/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ sudo make install
Password:
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/phayke/Desktop/rt73-cvs-2007012311/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  INSTALL /home/phayke/Desktop/rt73-cvs-2007012311/Module/rt73.ko
  DEPMOD  2.6.17-10-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
/sbin/depmod -a
grep: /etc/modprobe.conf: No such file or directory
append 'alias ra0 rt73' to /etc/modprobe.conf
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ ls /lib/modules/`uname -r`/extra
rt73.ko
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ sudo gedit /etc/network/interfaces
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ sudo modprobe rt73
Password:
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ sudo modprobe rt73
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ cd~
bash: cd~: command not found
phayke@FAILURE:~/Desktop/rt73-cvs-2007012311/Module$ cd ~
phayke@FAILURE:~$ sudo modprobe rt73
phayke@FAILURE:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

phayke@FAILURE:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
phayke@FAILURE:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

phayke@FAILURE:~$ sudo gedit /etc/network/interfaces


```

That's how far I got. To the very end and it didn't show up.

> Verify that the driver was installed correctly using the list short command:
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ ls /lib/modules/`uname -r`/extra 
You should see the file rt73.ko  

That worked fine. But at the end when I did the modplug and if config it didn't show anything.

Also, the last part about adding the text to interfaces was a little confusing to me, and I'm not sure if I did it right. It said to paste that bit at the bottom and then uncomment one choice and then fill in the wireless key in the other choice. First of all I didn't have a wireless key, so I enabled encryption on my device and tried to make a wireless key, and I think it gave me a hexidecimal code at the end so I added that. I didn't want to give myself another opportunity to screw up on something so I did the automatic field. My key wasn't as many characters as the amount of x's in the guide either, if that matters.

This is what I added. 
> 
# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
wireless-key 9A9B293A87        # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0

I still didn't get any result in step 7, as you can see by my log. The guide said it might be easier to start the config in the Network Setting applet, however when I clicked the applet, only my wired and modem connections were shown. I think I remember reading that you need to disable your wired connection to use the wireless one, but I don't know if that effects it being recognized. Also since my reinstall of ubuntu I don't have that voltage rule in anymore. Would that make a difference? It's not in the guide and I think that actually had a line pointing it to ndiswrapper or something, so would I need to add that rule and add it? I don't know what I'm doing wrong, really. :(


Edit: At this point I wouldn't even reject the possibility of remote assistance, if that might be easier.

---

### Post by ButteBlues on 2007-01-23
You need to set your wireless ESSID. =)

Replace MY_ESSID with whatever yours is (eg. farrington-wireless), then restart the PC with your USB adapter plugged in. You should log in to wireless internet.

If not, run "sudo ifup rausb0" and see it should work. =)


Other than that, it appeared everything went well. =)

---

### Post by ButteBlues on 2007-01-23
edit: double post, sorry =D

---

### Post by javaJake on 2007-01-25
Well, thanks for trying this out ahead of me. That'll smooth out the kinks before I dip in. :D

Life's gotten busy, so I need to do some catching up on the weekends. I won't be able to help out here possibly until Monday.

---

### Post by ButteBlues on 2007-01-25
> **javaJake said:**
> Well, thanks for trying this out ahead of me. That'll smooth out the kinks before I dip in. :D

Life's gotten busy, so I need to do some catching up on the weekends. I won't be able to help out here possibly until Monday.
Just a side note, it turns out HIS specific usb adapter used a different chipset. I cannot recall the specific name of said chipset, but he DID eventually get it working after a few hours troubleshooting on AIM.

---

### Post by javaJake on 2007-01-26
OK, if you can figure out the details I'll link to this thread from my HOWTO.

---

