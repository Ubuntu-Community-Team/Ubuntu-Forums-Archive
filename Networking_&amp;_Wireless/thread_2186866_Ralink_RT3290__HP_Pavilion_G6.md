---
title: "Ralink RT3290 / HP Pavilion G6"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by darin.hurst on 2013-11-09
I have an hp Pavillion G6 that had windows 8. I've heard a lot of good things about ubuntu, so I decided to give it a try thinking that everything would be working the way it should after installation.   It is now installed,  and I'm pretty much stuck with a broken computer unless I get some help.  

The wifi will act like it's connecting for a few seconds,  and then show a message that I'm now disconnected.  Then My wifi will disappear from the list of networks.  The screen flickers no matter what I try to do in the screens.  I don't see any kind of device manager to look at the drivers or update them.  I haven't a clue where to go from here. 

I've seen posts where users are asked to post their output.  I don't know how to do this.  I can't connect to the Internet to post this if I knew how.  Yes I'm new to everything here,  so if someone could take me by the hand and explain to me where I need to go or what I need to do I'd appreciate it.  I'm close to ordering a recovery cd from hp but I'd rather not do that.

---

### Post by elitehockey33 on 2013-11-09
I had a similar issue when using a pavilion dv6. The wireless card I was using was a BroadcomBcm 4321. I got it working finally through installing an app that i found in the software center . But in order to do that I had to use an external wireless card.

---

### Post by squakie on 2013-11-09
Please use a terminal window and post back the output of the following:
[COLOR=#0000ff]EDIT:  to open a termina window, click the unity dash (upmost button on the left hand menu) and type terminal - then click the result:
[/COLOR]
lspci <press enter>

[COLOR=#0000ff]EDIT:  Select the output on the terminal window, then right-click and copy, then paste in a reply here.[/COLOR]

Normally we would restrict just how much of the output we need, but since you are also apparently having video problems we might as well get it all.

Also - have you checked restricted/additional drivers to see if there is a video driver waiting to be installed.  [COLOR=#0000ff]EDIT:  you can do this by going to the unity dash again and typing Software & Updates - then click on the result.  There is a tab there for Additional Drivers.[/COLOR]

Something to keep in mind:  when you buy a name brand PC the vendor has already installed all of the drivers for your model, otherwise you would have to do so your self.  Ubuntu does it's best at installation time to get the drivers you need, but that doesn't mean it gets them all.  Video and wireless are the 2 main ones.  Normally what is required is the installation or activation of a Linux driver.  For your wireless, we won't know where to look until we get the above output.  It will also show your video adapter so we can try to help with that as well.

Linux isn't Windows - don't expect to see things like the Windows device manager.

---

### Post by darin.hurst on 2013-11-09
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7420G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

I really do appreciate the help.  To get this information I had to save the file and transfer to my phone so I can post it.  If I plug into ethernet will I be able to connect?

Edit: there are no additional drivers available.

---

### Post by monkeybrain20122 on 2013-11-10
Your card is  RT3290 It appears to be a bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/+index?comments=all)

There are several work arounds in the thread, but the easiest seems to be just install kernel 3.12 (post 142)
You can find the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2013-11-07-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2013-11-07-saucy/)
You need 3 packages :linux-headers-generic (32or 64 bit depending on your machine), linux-headers-all and linux-image-generic(32/64bit)
Download all three and put them into a folder: say right click on your desktop and create a new folder, name it "kernel" (without quotations) and move all three downloaded files into it, then open a terminal and type
```
cd Desktop/kernel
sudo dpkg -i *.deb
```

---

### Post by darin.hurst on 2013-11-10
I installed those kernels. I still get screen flickering,  kind of like a lightning bolt across the screen.  Error messages pop up saying "system program problem detected, do you want to report the problem now? " Then the wifi.  Networks aren't even visible now.

---

### Post by darin.hurst on 2013-11-10
Do I need to update the drivers?

---

### Post by darin.hurst on 2013-11-10
This thread was moved,  but the mobile version doesn't show me where.  I realize it's my fault for buying an hp product,  but it appears Linux may just not be compatible with my system, or I'm just not smart enough to figure it out.  If I don't figure it out by tomorrow,  I'm going to have to order a recovery cd from hp.  I hate memory hog windows.  Any help I can get would be greatly appreciated.

---

### Post by squakie on 2013-11-10
I would suggest you follow [this thread]("http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working"), specifically the first set of instructions for downloading and building the driver you need.

---

### Post by darin.hurst on 2013-11-11
I followed that step by step and got errors during the install.  I'll try one more time tonight,  but this is getting frustrating.  I Did seem to get my video working.  Did a fresh install wire connected to the Internet and it downloaded those drivers.

---

### Post by cssvb94 on 2013-11-11
@darin.hurst

Just download the 3.12 kernel from kernel.org, unpack it to /usr/src, get into the folder and compile it to debian package (headers and image).
Steps in terminal:

sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 build-essential
sudo -s
cd /usr/src
wget -vc [https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.12.tar.xz](https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.12.tar.xz)
tar -Jxvf linux-3.12.tar.xz
cd linux-3.12
fakeroot make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Sit back or go for a coffee, it will take a while ...
The new deb packages will be at /usr/src

Install them and reboot the system into the new kernel by choosing the apropriate option from the bootloader menu.
Test everything and if it is good then you can put that kernel package as held by using aptitude, so not to get overwritten by future updates.

That helped me after 3 days of struggling.

---

### Post by darin.hurst on 2013-11-11
I apologize for being so clueless to all of this but I do appreciate the help.  Could someone explain the following 2 paragraphs for me?  Thanks again. 

 and get into the folder and compile it to debian package (headers and image).

Install them and reboot the system into the new kernel by choosing the apropriate option from the bootloader menu.
Test everything and if it is good then you can put that kernel package as held by using aptitude, so not to get overwritten by future updates.

---

### Post by squakie on 2013-11-11
you may want to read further in that page (if you haven't already) as there are more things there for errors during the build.  Remember that most of the terminal commands given will require sudo to avoid permissions errors.

could you post back a screenshot showing the errors?  (the tool is aptly named "Screenshot).

---

### Post by squakie on 2013-11-11
I missed [**[COLOR=#000000]cssvb94[/COLOR]**]("http://ubuntuforums.org/member.php?u=87099") reply above, so I would suggest following it.  What I don't know is how much was already done in your trying to get this to work, and if you'd be better off with a fresh re-install and then doing as they suggest.  It's hard to know where some little thing may have been changed that has a large impact.  So - just my suggestion only - if you have any data you need to back up, do so, then use the install media and reinstall, being sure to mark your ubuntu partition(s) for reformatting first.  Then:

[COLOR=#0000ff]EDIT:  Connect your PC via a hardwire to your internet access point, then:

[/COLOR]
[COLOR=#0000ff][/COLOR]sudo apt-get update
sudo apt-get upgrade

then follow [**[COLOR=#000000]cssvb94[/COLOR]**]("http://ubuntuforums.org/member.php?u=87099") post from above - that way you know you are starting at a "clean slate".

---

### Post by darin.hurst on 2013-11-12
Thanks.  I'm going to give i ta try. What I don't understand is the line that says compile it to a debian package. 

Also, the last step says reboot system into kernel from bootloader menu. 

Could someone explain that? I've never had any knowledge of linux, but eager to learn.

---

### Post by squakie on 2013-11-12
I haven't ever done what  				 				 					 						 	[**[COLOR=#000000]cssvb94[/COLOR]**]("http://ubuntuforums.org/member.php?u=87099") has given instructions for, but this is my interprettation to answer you questions - I could be wrong.

> Sit back or go for a coffee, it will take a while ...
The new deb packages will be at /usr/src

At the end of the process it apparently creates new .deb packages in /usr/src.  You would need to search that folder to see the new ones, then just click on each and it should start up the process (perhaps software center, perhaps something else) to install each - you will probably only need to acknowldege with an ok or install or some such thing.

> reboot the system into the new kernel by choosing the apropriate option from the bootloader menu.

This would be the grub menu you get at boot time. [COLOR=#ff0000]EDIT: Select the "Advance Options" ( or some such wording) and press enter, then on the next menu select[/COLOR]  the 3.12 kernel option and press enter.


Hopefully this is correct.  You may want to wait and see if anyone else posts back with an answer.  I'm just posting what I would try.

---

### Post by cssvb94 on 2013-11-12
@squakie
Hi, that's exactly what I meant.

@darin.hurst
When the compilation is over and without errors, two deb packages with names slimilar to:
linux-headers-3.12.0-custom.deb
linux-image-3.12.0-custom.deb
will be in /usr/src
Go to that folder using the file browser and just double click on each of them, the associated application will start and propmpt for credentials and installs it.
Reboot the system and as **squakie **said, use "Advanced options" on the grub bootloader menu to select it.
If you don't see the menu, at system start press shift key just before the system starts loading.

---

### Post by darin.hurst on 2013-11-12
This is getting to be quite entertaining trying to get this going.  I can't even find a way to gain access to /usr/src. If kernel 3.12 will solve the problem, wouldn't it be easier to write it in to the installation script?

---

### Post by squakie on 2013-11-12
Tyr this from a terminal window:

sudo nautilus <press enter>

It will ask for a password - just enter your normal password - it won't show on the screen.

This will start the file manager in super user mode.  Just click on "Computer" then click on "usr" then click on "src".  You should see the file structure there as mentioned.  Since you are acting as super user you can double-click on each of those files mentioned.

---

### Post by darin.hurst on 2013-11-13
> **cssvb94 said:**
> @darin.hurst

Just download the 3.12 kernel from kernel.org, unpack it to /usr/src, get into the folder and compile it to debian package (headers and image).
Steps in terminal:

sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 build-essential
sudo -s
cd /usr/src
wget -vc [https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.12.tar.xz](https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.12.tar.xz)
tar -Jxvf linux-3.12.tar.xz
cd linux-3.12
fakeroot make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Sit back or go for a coffee, it will take a while ...
The new deb packages will be at /usr/src

Install them and reboot the system into the new kernel by choosing the apropriate option from the bootloader menu.
Test everything and if it is good then you can put that kernel package as held by using aptitude, so not to get overwritten by future updates.

That helped me after 3 days of struggling.
I went through everything in this post.  Everything seemed to be gong smoothly.  I installed the 2 deb packages and restated.  It now restarts in terminal mode.  Any ideas?

---

### Post by squakie on 2013-11-13
Is it possible you selected the right kernel version but the "recovery" option instead of just a normal boot with it?

Sounds like you need to reinstall your video driver, or perhaps the driver doesn't work with that version of the kernel.  I'm sorry to say that is something I just can't help you with.  Perhaps someone with that knowledge will be able to help you.

---

### Post by darin.hurst on 2013-11-13
Is there anyone who had the answer to this or am I best off going back to windows?

Edit: 
Let me ask a question as I think I may no why it did this. When I ran this command (fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers), there was a period of pauses where it gave options to input y, n or m. I just entered through those with a y or m. Am I supposed to answer those questions or just let the script run not answering anything?

---

### Post by squakie on 2013-11-13
I haven't ever done that so I can't answer that.  Might want to wait for [**[COLOR=#000000]cssvb94[/COLOR]**]("http://ubuntuforums.org/member.php?u=87099") to answer that for you.  As far as going back to Windows, here are my thoughts:

I am no Operating System biggot.  I say just to use what ever works best for you.  If you have an interest in pursuing linux further but keeping Windows, might I suggest that you install windows, then defrag a couple of times right away, then install linux for dual-boot.  this will allow you to continue as you need with Windows but with the ability to select ubuntu at boot if you want to occasionally try to get ubuntu working.  It's the best of both worlds.  Normally I would suggest running one as a virtual machine in the other,  but with your current problems with linux it would (in my opinion) be best to keep virtualized hardware until we can get your hardware working as is in linux.  I'm a little busy on something right now, but i suppose I could try to go through these steps here (I don't have your hardware) just to see what it's like and if there any step-by-step instructions we might be able to come up with.

In the mean time, if it were me, I would reinstall Windows, then follow above for creating a dual-boot system - it will allow you to choose Windows or Ubuntu at the boot menu.  That way you can get back to what you need to do, but also keep trying with linux and post back at this thread and I'll see what I can come up with in the mean time.  Keep in mind this building the kernel stuff is all new to me as well.

If you need any help setting up dual boot, or any questions at all on that, please post back so we can help guide you.

---

### Post by squakie on 2013-11-13
Well, I just tried copy/paste of the steps 1 by 1 into terminal.  I had to manually download the tar'd file, move it /usr/src and use nautilus (as su) to click and extract the files - just copying/pasting the wget fails as there are "."'s in place of actual content in the string.  After download, trying un-tar the file with the given options didn't work - it said it wasn't a bzip2 file, that's why I just manually downloaded and unpacked.

When I got to the longer fakeroot statement, I also got a LOT of  N/Y or N/M/Y prompts.  I tried going through them, and not knowing what they did I finally just exited the process and never continued.  Some of the options appear to be just for debugging purposes.  Others, and I guessing here, where they said "n/m/y", I suspected meant "no", such as no built in support, "m" for something like a loadable module (like you would do with modprobe or the /etc/modules file) or "yes" for built-in kernel support.

The thing is, not knowing what any of those things do I thought was a little dangerous to just guess at an answer for.  I know one of the early ones had something to do with video - perhaps that one caused some of your resulting problems.

In order to actually test this all the way through, I'm going to need to do a LOT more research and ask a lot of questions in the forums to find out what the heck everything is and what/how I should reply.  Considering how much of the build seems to have automatic answering to the prompts, I suspect that some of the new options just haven't been automated yet.

It's also possible you may want to try a different "flavor" of linux - perhaps Mint (based on Debian (and Ubuntu, I *think*) or some other distrubution.  I am not knowledgable enough to point you to good options there.

---

### Post by darin.hurst on 2013-11-13
What I'm wondering is If by answering y or m to everything,   did I install just about every driver out there?  That would definitely cause conflicts.

I've come to realize that ubuntu is not for the average person.  It takes a lot of computer knowledge just to set it up.

---

### Post by squakie on 2013-11-13
Normally these types of problems are not encountered by people installing Ubuntu.  Indeed, I would say there are a lot of long-time users out there that have never had the need to compile a kernel.  The 2 areas that pop up the most often are video and wireless, and usually that's just a simpe matter of installing a driver, just as you would if you installed Windows from scratch (not by a manufacturers' recovery disk set).

Your problems are rather unique, and to be honest, I'd rather go back to a fresh install, try the link I posted again and post back exactly what the errors are, since there are additional instructions there for some problems.  I currently have an open thread asking for some on the kernel building, but no replies (I don't get many replies anymore - long story).

Indeed, building the kernel by answering all of those question could have made a mess.  Some of those were for debugging purposes, some for who knows what.  As i mentioned, there was one very close to the start about video, and your answer to that may have caused your current video problem, but I simply don't know.

The link I initially posted I can at least follow along on and know pretty much what is happening.  If you wouldn't mind trying that again (fresh install first - and have your PC hard-wired so it has internet access during and after the installation) I can see if I can help on that or not.  It's completely up to you.  I understand your frustration - before things improved wireless used to be an "adventure" to get working for certain chipsets - go back far enough and for all chipsets.  Between that and video  many people trying linux for the first time bowed out.  Things have gotten MUCH better - it's just a shame you've run into what appears to be an exception to the norm.

Let us know what you decide.

---

### Post by cssvb94 on 2013-11-14
I can post later direct download links to the pre-compiled packages if you want.
Going back to window$ is bad option.

---

### Post by darin.hurst on 2013-11-14
I appreciate the help. I did get the file downloaded ok. It was just not knowing to enter y n or m. Anyway,  whoever will help me with something that works,  I'll try it. Seems to me I'm back to square 1.

---

### Post by cssvb94 on 2013-11-14
> **darin.hurst said:**
> I appreciate the help. I did get the file downloaded ok. It was just not knowing to enter y n or m. Anyway,  whoever will help me with something that works,  I'll try it. Seems to me I'm back to square 1.

[linux-headers-3.12.0_3.12.0-2_amd64.deb]("https://dl.dropboxusercontent.com/u/10645004/Ubuntu/linux-headers-3.12.0_3.12.0-2_amd64.deb")
[linux-image-3.12.0_3.12.0-2_amd64.deb]("https://dl.dropboxusercontent.com/u/10645004/Ubuntu/linux-image-3.12.0_3.12.0-2_amd64.deb")

Just download the files from the links above, they are for the 64-bit version of Ubuntu.
Double click 1st on the linux-headers-3.12.0_3.12.0-2_amd64.deb and follow the instructions on the screen to install it, then do the same for linux-image-3.12.0_3.12.0-2_amd64.deb

These are the binary packages for the 3.12 kernel, meaning you don't have to download the source and compiled as I suggested earlier.
Let us know the result after rebooting the system, again by choosing 3.12 kernel from grub boot menu.

---

### Post by squakie on 2013-11-14
Thanks cssvb94 - I'mw WAY out of my element here!  Someone also did answer my thread about looking for help on compiling the kernel, so I thought I'd paste that in here - it will supposedly get rid of all those questions I don't have a clue how to answer:

> 
 		                                                                                                                                                    5 Hours Ago                                                                                                                                                                                                     [#2]("http://ubuntuforums.org/showthread.php?t=2187802&p=12847772#post12847772")                                                                                                                                                                                      		
  		 			 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1245983_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1245983") 				 				 					 						 	[**[COLOR=#DD4814][B]Doug S**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1245983") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						Ubuntu Member 					 					 						[IMG]http://ubuntuforums.org/images/rank_ubuntumember_2013-02.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateFeb 2011LocationCoquitlam, B.C. CanadaBeans1,170DistroUbuntu 12.04 Precise Pangolin 					 					 				
 			 		
 	
  	 		 		 		 		[h=2]Re: help building kernel image[/h] 		 				 				 					 				 		 			 				[INDENT] 					I never know how I should set all of the config options either, so I  cheat. First, I would install the Ubuntu 3.12 kernel from the [kernel PPA]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/").  Then I copy the config file from /boot to my kernel build location,  thus setting most if not all of the config options. The last time I did  this, was 3.11RC2 	Code:
 	cp /boot/config-3.11.0-031100rc2-generic .config 

Maybe that might help someone else as well.

 				[/INDENT]

---

### Post by squakie on 2013-11-15
It has also been recommended that you just buy a cheap USB wireless adapter that is iknown to work.  I myself have used Tenda 300-Mbps model W322U for a long time on several Linux systems and it has always worked just "out of the box" - no fuss, no muss.  Our local Micro Center has had these on sale at $12.99 - marked down from the $29.99 I've paid in the past.  I bought a couple of spares at that price, as they also work "out of the box" on my Raspberry Pi's.

---

### Post by darin.hurst on 2013-11-15
> **cssvb94 said:**
> [linux-headers-3.12.0_3.12.0-2_amd64.deb]("https://dl.dropboxusercontent.com/u/10645004/Ubuntu/linux-headers-3.12.0_3.12.0-2_amd64.deb")
[linux-image-3.12.0_3.12.0-2_amd64.deb]("https://dl.dropboxusercontent.com/u/10645004/Ubuntu/linux-image-3.12.0_3.12.0-2_amd64.deb")

Just download the files from the links above, they are for the 64-bit version of Ubuntu.
Double click 1st on the linux-headers-3.12.0_3.12.0-2_amd64.deb and follow the instructions on the screen to install it, then do the same for linux-image-3.12.0_3.12.0-2_amd64.deb

These are the binary packages for the 3.12 kernel, meaning you don't have to download the source and compiled as I suggested earlier.
Let us know the result after rebooting the system, again by choosing 3.12 kernel from grub boot menu.

Thank you cssvb94!  I don't exactly know what the answer was, but so far my wireless appears to be stable. And thank you squakie as well for all of your input. You both have been great.

---

### Post by squakie on 2013-11-15
I didn't do much - cssvb94 solved your problem.  I'm just glad it's working for you.  Truely, this is a very big exception to how the vast majority of installs go.

---

### Post by cssvb94 on 2013-11-15
That's why we are here, to help. Just don't give up. In a time you'll understand the beauty of freedom Linux provides.
I'm glad that worked, you may as well change the thread title as resolved, so to help somebody else who is looking for solution.
This kernel package I gave to you is plain vanilla kernel - no patches, not even the configuration was touched, just downloaded, unpacked and compiled to deb.
I'm trying to say that that kernel should resolve theoretically other issues caused after the upgrade to 13.10. 
I'll post later today how to put this kernel on hold so next kernel update wont override it.

---

### Post by darin.hurst on 2013-11-15
There are a couple other things I want to resolve. 
1. Computer doesn't wake when I've been away.  Sounds like it does but no video. 
2. Can't play any dvd movies
3. Message pops up periodically about an error in the system.

Don't know if I start a new thread or even where.  Or what information is needed to track it down.

---

### Post by squakie on 2013-11-15
I don't know about the others, but for DVD playback you will need libdvdcss2.  This is something you have to take note of:  This package decrypts DVDs, and it may not be legal in your country due to copyright laws.  You have been forwarned.

I don't know if we're allowed to post the actual instructions here (at one time we were not), so please follow [this link]("http://www.gaggl.com/2013/10/installing-libdvdcss-on-ubuntu-13-10/").

---

### Post by squakie on 2013-11-15
For you r video problem - this is pretty common.  I've been looking for solutions, and found something I thought I'd pass along now - I have no idea if it will work:

hold down FN and press the up arrow.  This supposedly restores the brithness on a screen that has gone to sleep.


EDIT:  Forgot you have AMD.  Did you install the open source driver or the proprietary one?  If proprietary - do you have a watermark in the lower left saying "hardware not supported?  If so, use synaptic and install the updates-flgrx package - it should also ask you to confirm you will be installing updated-catalyst as well.

If you did not use a proprietary driver, then use the above steps to install updates-fglrx.

Try hibernation and wake up again.  This has been reported to solve the problem on many AMD based laptops.

---

### Post by squakie on 2013-11-15
When the error pops up about the system error, click on "details" and post back what package it occured in.

---

### Post by cssvb94 on 2013-11-17
You could try to install Ubuntu's mainline 3.12 kernel builds.
Download the following 3 files:
[linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb")
[linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb")
[linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb")

Install them following the order above and reboot in the new kernel.

If you still expirence crashes try to get more details as squakie suggested.

---

### Post by wildmanne39 on 2013-11-17
Please start a new thread for each issue and do not bunch them together.

Also each time you install or upgrade to a new kernel you may fix one thing and break another.
Thanks

---

### Post by squakie on 2013-11-18
BTW - the libdvdcss instructions will still apply no matter what kernel image you use.  I suspect the video will also remain the same.  About the only a different kernel might get you is away from the error message - though I still get that occasionally myself but from other packages - not the kernel.

---

