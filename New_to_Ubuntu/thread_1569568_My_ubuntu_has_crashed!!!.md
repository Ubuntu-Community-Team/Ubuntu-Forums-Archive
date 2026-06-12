---
title: "My ubuntu has crashed!!!"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-06
Ok I have a major problem. Ubuntu was giving me some issues b4 so after unchecking whatever functionality I din want, I thought why not jus uninstall localpurge(it was giving me issues in my update manager). I went to synaptic package manager, did a search for the keyword "localpurge" and uninstalled everything associated with it. Thought it would prevent any issues in the future. What I din reckon 4 was that my ubuntu would crash completely. first the update manager & synaptic manager disappeared under administration tab so I decided to restart thinking it was an ubuntu quirk. Now when I restart all I get is a blank screen.

---

### Post by DemonBob on 2010-09-06
Try to do Ctrl+ALT+F1 to see if you get a console login screen.

---

### Post by Suzanne42 on 2010-09-06
I did that jus now, nothing happens other than the comp making noise.

---

### Post by an0dos on 2010-09-06
The following is taken from the description of localepurge in synaptic:

> Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.

That is a fairly sizable disclaimer. It may be easiest for you to just boot from a live cd, copy your files to an external hard drive, and reinstall ubuntu.

---

### Post by Suzanne42 on 2010-09-06
Actually I installed Ubuntu long ago, not sure where I kept the CD. Isn't there any command I can type to resolve this mess? Why is my comp sending an alarm when I press Ctrl + Alt + F1? By the way I saw a similar post somehwere where an user had mistakenly remove all packages associated with "ALT" from synaptic package manager. Like my case, her comp also crashed but surprisingly she could get it running again through typing some commands in command line.

---

### Post by an0dos on 2010-09-07
> **Suzanne42 said:**
> Actually I installed Ubuntu long ago, not sure where I kept the CD. Isn't there any command I can type to resolve this mess? Why is my comp sending an alarm when I press Ctrl + Alt + F1? By the way I saw a similar post somehwere where an user had mistakenly remove all packages associated with "ALT" from synaptic package manager. Like my case, her comp also crashed but surprisingly she could get it running again through typing some commands in command line.

When you turn on your computer and hold down the shift key, does it give you the option to boot into the recovery console?

---

### Post by Suzanne42 on 2010-09-07
No, it doesn't. I restarted the comp & tried again, nothing happened. But now things are diff from b4. Last time it would come as normal before it showed a blank screen & hung. Now when I restart it flashes some error message which before I can read, the screen shifts to the blank one and jus waits.When I type, nothing comes on the screen but this time when I pressed the shift key @ least the comp din screech. I dun noe why I can't get recovery mode, jus 4 ur info I have Ubuntu 10.04.

---

### Post by Chris1274 on 2010-09-07
You may have uninstalled some system-critical dependent packages when you removed localpurge (did you happen to check "completely remove" in synaptic?)

I think your best bet is to find another computer so you can download a copy of 10.04 and make a live USB, which will allow you to recover your files and then do a clean install.

---

### Post by Suzanne42 on 2010-09-07
M searching for a downloadable copy of 10.04 right now. My qn though is if my comp doesn't respond to what I type or any keys pressed, will it run the CD to which I copy a downloaded Ubuntu 10.04?Btw yes, I did a complete removal of localpurge, my idiocy, had I known it would have led to so many problems I would have tot twice.

---

### Post by Chris1274 on 2010-09-07
When you start up your computer you should get a message that says something like "Hit Esc for BIOS settings" (or F8 or F12, depending on the computer). So long as you can get to the BIOS you should be able to boot from the CD.

---

### Post by sideaway on 2010-09-07
[http://ubuntu-releases.eecs.wsu.edu/10.04/ubuntu-10.04.1-desktop-i386.iso](http://ubuntu-releases.eecs.wsu.edu/10.04/ubuntu-10.04.1-desktop-i386.iso)

^ 10.04 32bit for desktop.

You've got to be careful when fiddling around under the hood, when ever you type 'sudo' or punch in the super-user password it assumes you know what you're doing.

---

### Post by Suzanne42 on 2010-09-07
Tat's the thing, some msg flashes by when I start my comp(its an Acer) but before I can read the msg, it shifts to the blank screen with a waiting indicator. Anyways I will try a reinstallation of Ubuntu 10.04 from CD. Will see if anything comes. I pressed Esc, F8, F12 jus now but the screen remains the same, no recovery option or anything pops up.

---

### Post by Chris1274 on 2010-09-07
It looks like Acer makes things more complicated. Try holding down ctrl+alt+esc.

---

### Post by Suzanne42 on 2010-09-07
I did tat jus now & the comp sent off a screech again. Now downloading the ubuntu 10.04, it takes eons. Hope it works tis time otherwise I really dunno how to resolve tis.

---

### Post by Suzanne42 on 2010-09-07
Ok, I have copied the Ubuntu file to my usb & connected the USB to the comp. However, nothing comes. The same file pops up on my Window platform to suggest installation of Ubuntu. However in the errorneous Ubuntu platform, absolutely nothing. M @ my wits end, I really dunno wat 2 do.It jus gives me the same blank screen.

---

### Post by Suzanne42 on 2010-09-07
Guys, where r u? M so sorry to take up ur time but I finally got into the BIOS setup utility, now what do I do? There's a boot option but would like some advice on how to go about things, dun want the comp to crash again. Btw it has responded to the USB I connected, it contains the Ubuntu 10.04 setup file.

---

### Post by jtarin on 2010-09-07
Do you have another computer where you can stay online and follow instructions?

---

### Post by Suzanne42 on 2010-09-07
Yes, m on a Windows platform right now. Pls help. Current status is I downloaded Ubuntu 10.04. I then copied it from my desktop to my usb. Now I connect the usb to my comp by which time after eons I had gotten the BIOS setup configuration menu. I changed the boot option to boot from USB, then I saved the new options. Right after that, I got the message saying "Operating System Not Found!". What on earth is happening I dunno, it doesn't seem to do anything other than give me errors. I will be on this forum regularly, would be great if u could help out. This is the sec day of this disaster. I seem to be getting nowhere.

---

### Post by jtarin on 2010-09-07
>  Btw it has responded to the USB I connected, it contains the Ubuntu 10.04 setup file.You downloaded the .iso file and put it on your USB? Did you do anything to prepare your USB to boot?

---

### Post by Chris1274 on 2010-09-07
Some of us need to sleep ;)

Now you're pretty much home free. Once you've got the lve USB running with the menu screen up, pick the option that says "Run a live session without making any changes to your computer" or something like that. If there's anything on your current installation that you want to keep, you can mount your hard drive and save all your files to a second thumb drive. Then click on the "Install Ubuntu" icon on the desktop. The rest should be familiar.

---

### Post by Chris1274 on 2010-09-07
You can't download the .iso directly to the USB, you have to make it a bootable device. Download the .iso to your desktop, then go to "pendrivelinux.com" and click on "Universal USB Installer". Follow the instructions they give you.

---

### Post by jtarin on 2010-09-07
[Here's the link for detailed instructions of what you need to do to accomplish booting and installing from USB.]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") Any difficulties from this point post back and we will help where we can.

---

### Post by Suzanne42 on 2010-09-07
Sorry Chris, I have been so tense over this matter. Jtarin, I will try that then get back to u guys.

---

### Post by jtarin on 2010-09-07
Stay calm its only an operating system that will eventually get installed. It's a learning process like anything in life. Your not going to break anything. Just stay focused on what you need to do and follow the instructions. If you have a question about a step...ask before you do it. I don't want to push you out of the mud for you to drive into the ditch. LOL

---

### Post by Silent Warrior on 2010-09-07
And, today's moral lesson: When removing something through Synaptic/apt-get/<insert utility here> (... Uh, well, I hope you know what I mean, regardless... :o) and you get a list of things that will also be removed, make sure to read up on each package to see if you actually need some of them. :)

Suzanne: When you were asked if you could boot into recovery-mode, they meant the option present in Grub. To enter Grub (the ubiquitous bootloader), you need to hold down the right shift-key after BIOS loads (and before Ubuntu would take over). Just for future reference. It looked like you didn't know how to get to this screen - knowing how to get to the recovery-console is a good thing, for newbies, the intermediate, and old vets alike.
And if you weren't using separate partitions for / and /home, take this opportunity to change that. Advice on how much space should be allocated for / and swap (saving the rest for /home) can be found in several places, and there's no shortage of good advice on that subject.

---

### Post by gauravj on 2010-09-07
I would suggest, take a live cd. Ubuntu, knopix, any will do.
Take time to back up your data.
Do the fresh install.

Simple and easy.

---

### Post by an0dos on 2010-09-07
> **Silent Warrior said:**
> And, today's moral lesson: When removing something through Synaptic/apt-get/<insert utility here> (... Uh, well, I hope you know what I mean, regardless... :o) and you get a list of things that will also be removed, make sure to read up on each package to see if you actually need some of them. :)


You should also avoid packages that explicitly state that they are for developers and experienced users who don't mind fixing broken systems that may result from using said package. :)

---

### Post by Suzanne42 on 2010-09-07
Hey frenz, I want 2 thank all of u 4 ur wonderful help. Had it not been 4 u ppl, I would have been @ my wits end.:D

---

### Post by jtarin on 2010-09-07
Are you installed?

---

### Post by Suzanne42 on 2010-09-08
Actually I installed it yday then disconnected the usb but today it turns out that it wasn't properly installed, dunno why. M repeating the process. Yday aft installing I realized that I can't restore my Internet connection though I had an active connection before the comp crashed so I dunno yet how to restore the Internet via Network Tools. Some post suggested installing Gnome Network Manager, I checked yday, it was already installed but I need to find out how to restore via Network Tools since the Network Manager doesn't show up as an option despite being installed.

---

### Post by Suzanne42 on 2010-09-08
I realise there's still a prob, ubuntu hasn't been installed on the comp hard drive yet despite going through the installation process, it still depends on the USB bcose whenever I remove the USB the error Operating System Not Found comes.

---

### Post by an0dos on 2010-09-08
> **Suzanne42 said:**
> I realise there's still a prob, ubuntu hasn't been installed on the comp hard drive yet despite going through the installation process, it still depends on the USB bcose whenever I remove the USB the error Operating System Not Found comes.

Well, since you haven't gotten it working yet there is no harm in trying the install process one more time. :)

When you reinstall the OS, make sure that it is installing it to your internal hard drive and select the option to completely erase the hard drive and install a fresh copy of ubuntu on it.

---

### Post by jtarin on 2010-09-08
Are you properly installed to the hard drive now? Can you boot as you want? is everything as you need it but internet connection? How do you normally connect to the internet? Dial-up, DSL modem, Wireless etc;?

---

### Post by Suzanne42 on 2010-09-08
How do I do that? The Ubuntu 10.04 installation icon is no more seen on my desktop nor under system-admin. Is there any command I can type under command line?

---

### Post by Suzanne42 on 2010-09-08
Jtarin, Internet is no longer an issue now. I can see the available wireless options., will connect later but what do I do about this dependency on the USB for booting? the icon for installation no longer pops up anywhere.All my settings are seen as long as I have connected my USB otherwise the error Operating System Not Found comes.

---

### Post by jtarin on 2010-09-08
With the USB plugged in boot up and then open a terminal and issue the command ```
df -h
```post it. You might have to prepare your USB again for installation.

---

### Post by Suzanne42 on 2010-09-08
When I give the command, this is my output:
 
[FONT=Times New Roman][SIZE=3]Filesystem            Size  Used Avail Use% Mounted on[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sdb1              72G  2.1G   66G   4% /[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]none                  371M  296K  370M   1% /dev[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]none                  375M  1.2M  374M   1% /dev/shm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]none                  375M   76K  375M   1% /var/run[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]none                  375M     0  375M   0% /var/lock[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]none                  375M     0  375M   0% /lib/init/rw[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda1             1.9G  686M  1.2G  36% /media/PENDRIVE[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I really don't wish to repeat the entire process. Isn't there an alternative? ACER is hopeless, it seems.[/SIZE][/FONT]

---

### Post by jtarin on 2010-09-08
It seems you have installed Grub2 to the USB and not the MBR of the internal hard drive.You need to install Grub to drive that is 72G in size. Your booting from the USB now and it knows where the operating system is because you installed Grub to it, but when you take it out and there is no Grub to find an operating system with so you get that message.

---

### Post by Suzanne42 on 2010-09-08
Tta's jus great, nvm I will reinstall then get back to u. Hopefully no issues this time round. It must be bcose I din select the option install to hard drive fast enough.

---

### Post by jtarin on 2010-09-08
You've installed Grub to the USB and it should have been installed to the 72G hard drive. Here's a [link ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")to reinstalling Grub. Scroll down to the "METHOD 3 - CHROOT" and follow the instructions. When you do get to the desktop and open the terminal...run the command "df -h" once again to make sureyou know the partiton you should install too. Grub will complain about being installed there but use the option -force as they tell you and ignore all warnings. Run the "update-grub" command, steps 9 and 10 you will have to do the opposite of what they tell you.I have written them as you need to follow below.
```
9.Reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. 
[COLOR="Red"]_Do specify a partition number_[/COLOR].
grub-install /dev/sdXX (in your case the 72G)
10. [COLOR="red"]Do _not_ verify the install [/COLOR]
Skip to step 11.
```

---

### Post by jtarin on 2010-09-08
If you decide to reinstall watch for this screen this is the one to choose Grub location.

---

### Post by Suzanne42 on 2010-09-08
I was busy so hven got down to reinstalling, btw I had to remove the files in the usb bcose I needed to use it for something else. Hope I can format the USB again & make a successful reinstallation.In the link provided, I dun rmb they suggesting wat option to select under Advanced, perhaps that's why I missed it.I will try to correct it when I get time today.This time round hopefully won't have any issues. Will get back to u guys if it doesn't work. No issues if I try reformatting the USB again no?

---

### Post by jtarin on 2010-09-08
Format away!

---

### Post by Suzanne42 on 2010-09-08
Under Advanced Tab what do I choose? 
/dev/sda ATA HITACHI something(80.0GB) I think this refers to my USB
/dev/sda1 Ubuntu 10.4.1 LTS

---

### Post by Suzanne42 on 2010-09-08
I tried both options under the Advanced Tab but all I get is an error msg aft I reboot when installation is completed.

---

### Post by Silent Warrior on 2010-09-08
Suzanne: Is your USB-memory 80 Gb in size? I don't think so. ;) If you're at the Grub-screen, only check one. You really only need to have Grub in one place. /dev/sda will install Grub to the disk's master boot record, which is the recommended approach. Installing it to /dev/sda1 will install it to the first partition you made on your disk. Also valid, but not recommended.
I would recommend that you make a separate partition for /home, though. Take a look at some recommendations that have been posted in the past.

(ATA is an I/O-interface, common to mechanical harddrives of today.)

---

### Post by Suzanne42 on 2010-09-08
Nope, my USB is only 2 GB. I installed to dev/sda last time but tat caused the OS to be dependednt on my USB.dev/sda is the default booting option. When I try othr options an error occurs when the comp restarts after reinstallation, I jus checked its an error associated with dev/sda which I din select either times. I hve no clue wat 2 do. See no pt hving other options if they give errors.Bcose I din select dev/sda I hve errors but if I select dev/sda, I hve to forever connect my USB to use Ubuntu 10.04.

---

### Post by Suzanne42 on 2010-09-08
I can't seem to get it working. I followed the entire process again, went tot the extent of formatting the USB again but now the msg comes cannot find directive to boot from. boot: followed by cursor waiting for user input. I tried presiing F1,F2,F8,F12,Esc,Del to enter BIOS setup but that also is not coming. Now all I get is a black screen with a cursor waiting for user input when I connect the USB. I follow the same steps each time but no use.

---

### Post by jtarin on 2010-09-09
> **Suzanne42 said:**
>  but now the msg comes cannot find directive to boot from. boot: 
This means Grub cannot find the directions it needs to be able to boot from. Can you boot Ubuntu Live CD (usb) and get to the screen where it says "Install" or "Try" ?

---

### Post by Suzanne42 on 2010-09-09
No, I dun see tat option now, all I get is a msg which states as specified before. I think it expects me to provide the boot location after the command boot but I dunno what input to give.

---

### Post by jtarin on 2010-09-09
> **Suzanne42 said:**
> No, I dun see tat option now, all I get is a msg which states as specified before. I think it expects me to provide the boot location after the command boot but I dunno what input to give.
Your USB will not boot now? If it will boot and your getting these error messages something is wrong with your USB Flash. I would suggest going into Windows and then right-click on MY Computer in the menu and then when the window opens that shows all your drives you right-click on the USB flash drive and select format and from the dialog choose FAT32 if it is available. When finished reinstall the Ubuntu.iso to the USB Flash drive as you did the first time. Then you will need to designate it as the first boot device when your computer boots.  Do you know how to do that selection? The USB should boot into the Ubuntu install there is no reason you should be getting the message you are getting if it is actually booting from the USB with a good install of Ubuntu on it.When you get it it to boot and you get to the screen wher it says....Where do you want to install Ubuntu...stop and then post back here for help...do not go further.

---

### Post by Suzanne42 on 2010-09-09
Yes, m supposed to do the selection in the BIOS set up no? Selecting the USB device as the 1st option to boot from. I hope Ubuntu comes automatically, ACER seems to be really pesky.

---

### Post by jtarin on 2010-09-09
If you know how to do it in the BIOS by all means please do it there.

---

### Post by Suzanne42 on 2010-09-09
I can't get into BIOS set up. I tried pressing F2,F8,F10,F12,Esc,Del. It jus refuses to go, seems stuck at the message on cannot find a directive.

---

### Post by jtarin on 2010-09-09
Give me the make and model number of your computer

---

### Post by Suzanne42 on 2010-09-09
Model: ACER
ASPIRE 4520
S/N: LXAHS0Y0958120AF372534

---

### Post by jtarin on 2010-09-09
The 11-character value located next to the bar codes on the bottom of your product label. Or your 22 character serial number.

---

### Post by Suzanne42 on 2010-09-09
Yea, look @ my post above urs. Isn't tat the no?

---

### Post by jtarin on 2010-09-09
Consult your computer owner's manual, if you have it available, and look to see if the precise key combination needed for BIOS setup access is found there. If you don't have your manual, proceed to the following steps.
2
Ensure that your computer is turned off completely, then turn it back on by pressing the power button to the "On" position. Within the first 10 seconds, press the "Control" key and hold it without letting up. Then press the "Alt" key and hold it also without letting up. Finally, press the "Esc" key and hold it without letting up. You should be pressing and holding all three buttons down at the same time. Hold them for about two seconds and then release them. If your system is an older Acer Aspire model, you should then see the BIOS setup screen. If not, your system is of the newer Aspire model and you should continue to the following step.
3
Shut down your computer again completely. Once it has been turned off, press the power button to the "On" position to restart the system. Within the first 10 seconds, press down and hold the F2 button for about three seconds and then release it. Within five to 10 seconds after pressing and holding this button, you should see the BIOS setup screen on the monitor.


Read more: How to Enter Setup on an Acer Aspire | eHow.com [http://www.ehow.com/how_5802568_enter-setup-acer-aspire.html#ixzz0z1RMplye](http://www.ehow.com/how_5802568_enter-setup-acer-aspire.html#ixzz0z1RMplye)

---

### Post by jtarin on 2010-09-09
> **Suzanne42 said:**
> Yea, look @ my post above urs. Isn't tat the no?

Yea that is "A" number but ACER says its not a valid number. Nevermind.......try the instructions above and let me know.

---

### Post by jtarin on 2010-09-09
Fn+F2....is the combination

---

### Post by Suzanne42 on 2010-09-09
By Fn u mean press the letter f followed by the letter n before pressing the button F2?I tried that all I get is the letter f being repeated printed after the boot keywod foloowed by n.
 
boot>ffffffnnnnnn

---

### Post by jtarin on 2010-09-09
Maybe not exact location on your laptop....it has the letters "F and n" on one key.

---

### Post by Suzanne42 on 2010-09-09
Yup got it. I pressed F2 before comp booted. Now, I have the BIOS Utility. Kindly go through the process on what I should do. I should jus go & slect the first device as my USB no for booting. Last time, I did that & removed other options also.Anything else I should do?

---

### Post by jtarin on 2010-09-09
Just select the USB for the first boot device and save that setting in the bios and reboot with your USB already in the drive...when you get to the part of the install where it ask "Prepare disk space" stop and post back.

---

### Post by Suzanne42 on 2010-09-09
Currently, under boot Tab these are the devices in the priority list.
1.USB HDD: TOSHIBA TRANS MEMORY(That's my USB already)
2.IDE CDROM
3.PCI BEV
4.USB FDC
5.USB KEY
6.USB CD ROM
 
Last tym I removed all options to the non-important list except the first option.

---

### Post by jtarin on 2010-09-09
> **Suzanne42 said:**
> Currently, under boot Tab these are the devices in the priority list.
1.USB HDD: TOSHIBA TRANS MEMORY(That's my USB already)
2.IDE CDROM
3.PCI BEV
4.USB FDC
5.USB KEY
6.USB CD ROM
 
Last tym I removed all options to the non-important list except the first option.Good can you disable them? If so do so...then after install enable them in the correct order. Save your setting and exit. There should be a menu to tell how to do that at the bottom or side

---

### Post by jtarin on 2010-09-09
I suggest you have [this page]("http://www.unixmen.com/linux-tutorials/973-ubuntu-1004-lucid-lynx-step-by-step-installation-for-newbies-howto") open in a tab of your browser to refer to during installation. Refer to the picture number when asking questions.

---

### Post by Suzanne42 on 2010-09-09
Hey, a frnd was looking @ how to fix my comp. He got an older version of Ubuntu installed. So now I have Ubuntu but not version 10.04. Can I jus upgrade to version 10.04 via Update Manager? Plus there's a busy box error which always comes when I had version 10.04. I hven figured out how to fix that error. The error is- tired of waiting for root device, intrafms then I have to keep typing exit to get to my desktop. Do u noe the solution for this error?Thanx for everything, I think this settles the matter of reinstalling Ubuntu. Now, I jus need to noe how to upgrade 2 10.04 & fix the intrafms error.

---

### Post by jtarin on 2010-09-09
What version of Ubuntu do you have now? Are you getting the Busybox error with the version you have installed now?

---

### Post by Suzanne42 on 2010-09-09
Not sure, think its version 9 something. Nope, now I dun get it but later I plan to upgrade 2 10.04 then I want to noe how to resolve the Busybox error.

---

### Post by Silent Warrior on 2010-09-09
There's a few options for upgrading. You can either use the Update Manager - I think it'll give you the option of upgrading to a new release without intervention - or apt-get update && apt-get dist-upgrade (I think that's the invocation, at least). You can find several methods in the Wiki, and probably the official Canonical-made documentation.

What exactly is the busybox error-message, then? Error code?

---

### Post by jtarin on 2010-09-09
Well I would be careful upgrading and only do it a little at a time and track what you upgrade every time. As to [BusyBox]("http://linux.die.net/man/1/busybox")....its there to help if you can't boot for some reason....it's the Swiss Army knife of Linux. It can help you if you need it. It would be worthwhile to look it over. I doubt it will return if your install is good.

---

### Post by Suzanne42 on 2010-09-09
Thanx 4 the explanation. Yea, I will upgrade slowly or will do it via Update Manager. Dun want another nightmare. I think lots of ppl with ver 10.04 got Busybox, hope I dun face it again aft upgrade. Else,will get back 2 u guys, tired of the earlier method of typing exit each tym until it decides 2 go 2 the desktop.

---

### Post by Suzanne42 on 2010-09-11
I have been trying the upgrade to Ubuntu 10.04 for the past few hrs. It was working initially but now the update manager process has hung after getting all packages. So, I cancelled & retried but then it says it will do a partial upgrade bcose I cancelled the prev upgrade so I allowed it to do that but the process again hangs. I tried via the terminal, I get error messages so currently I have been waiting 4 almost 2 hrs for the upgrade 2 complete.

---

### Post by jtarin on 2010-09-11
You should upgrade through the Synaptic package manager.
System>Administration>Synaptic. You have already started it though and you shouldn't interrupt. It is a lengthy down if your re-versioning.Just my new installation of 10.04 took well over an hour and a half on my slow connection as it had to download everything that had been upgraded to that day.

---

### Post by Suzanne42 on 2010-09-11
I left it 4 an hr & went off but it stopped where I had last left it.It doesn't seem to upgrade,dunno how to resolve. I got broken packages fixed under the Synaptic option but tat made no diff.

---

### Post by jtarin on 2010-09-11
Did you try to update your installed version first? What I mean is bring all the packages in the installed version to their newest state before trying to do an upgrade? There are too many variables going from a new install and jumping immediately to an upgrade because when a version is released it is updated almost constantly before the next version is released. The only thing that i can suggest to keep this from becoming a recurring nightmare is to install the version again that you were successful with then update it little by little. When it is fully updated and then if you want, do the upgrade and don't interrupt.I will say there are plenty of people completely happy running 9.

---

### Post by Suzanne42 on 2010-09-11
Yea, I can update my installed version. What do u mean install this version again, do a clean install?The version 9 is working perfectly but I prefer version 10.04 which is why m trying 2 upgrade, there's an upgrade option in Update Manager but it refuses to complete.

---

### Post by Suzanne42 on 2010-09-11
By the way, how do I change permissions in ubuntu? I have set a password for Ubuntu yet in the terminal when I wish to update, the message comes "Permission Denied", where can I set permissions?

---

### Post by jtarin on 2010-09-11
You must use sudo to preface your commands.

---

### Post by jtarin on 2010-09-11
[Not the same version but same procedure....read carefully each dialog. This process takes hours of attended upgrading]("http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/")

---

### Post by Suzanne42 on 2010-09-11
Why shud I do this? This suggests upgrading Ubuntu 2 version 7.10, mine is version 9.10. Anyways the upgrade to Ubuntu 10.04 has resumed again after what seemed like eons. I fixed broken packages bcose that earlier was an issue, trying to see now if the upgrade completes successfully for a change.If not,will get back again.

---

### Post by Suzanne42 on 2010-09-12
For the past half an hr, the upgrade process has been stuck @ "Getting new packages" process no. 1318 of 1344, I have no clue what to do, my Internet connection is working fine but the process won't proceed.

---

### Post by Silent Warrior on 2010-09-13
I suppose this is why some people take exception's to Ubuntu's updater... If you can start System Monitor you can see if there is any network activity. If so, that probably just means it's dealing with a really big package - like kernel headers or image. Otherwise, I recommend you hit cancel and try the upgrading-method that involves using the terminal - you'll get output that would help in troubleshooting that way.

---

### Post by Suzanne42 on 2010-09-13
Anyway my ubuntu has again crashed, same problem as last time-can't login(aft login it doesn't go to the desktop).I really dunno wat caused the error this time, I fdin do anything except follow some examples to try upgrading to 10.04. Lokks like I have 2 boot from USB & repeat the entire process, this is really crazy, I din remove anything yet the problem repeats.

---

### Post by jtarin on 2010-09-13
> **Suzanne42 said:**
> Why shud I do this? This suggests upgrading Ubuntu 2 version 7.10, mine is version 9.10. Anyways the upgrade to Ubuntu 10.04 has resumed again after what seemed like eons. I fixed broken packages bcose that earlier was an issue, trying to see now if the upgrade completes successfully for a change.If not,will get back again.
If you will look at the post I made about this it says....NOT THE SAME VERSION BUT SAME PROCEDURE.

---

### Post by jtarin on 2010-09-13
> **Suzanne42 said:**
> Anyway my ubuntu has again crashed, same problem as last time-can't login(aft login it doesn't go to the desktop).I really dunno wat caused the error this time, I fdin do anything except follow some examples to try upgrading to 10.04. Lokks like I have 2 boot from USB & repeat the entire process, this is really crazy, I din remove anything yet the problem repeats.
If you just reboot and try the upgrade process again I think your just making a bigger mess out of it. I would try a new install then just do an UPDATE NOT UPGRADE. Then try the upgrade. There might not be so many packages to contend with.....not all packages require an upgrade between versions.To be honest I wouldjust update what I had until I could find a way to boot the 10.04 .iso. What you have is perfectly acceptable.

---

### Post by amjjawad on 2010-09-13
> **jtarin said:**
> If you just reboot and try the upgrade process again I think your just making a bigger mess out of it. I would try a new install then just do an UPDATE NOT UPGRADE. Then try the upgrade. There might not be so many packages to contend with.....not all packages require an upgrade between versions.To be honest I wouldjust update what I had until I could find a way to boot the 10.04 .iso. What you have is perfectly acceptable.

I agree with jtrain.
Even in Windows, when you try to upgrade your OS (Windows) while you have lots of errors/problems, same will happen after "the upgrade". Logically, same could happen with Ubuntu.

I guess new installation would be better in your case than just upgrading, regardless what version of Ubuntu do you have :)

---

### Post by Suzanne42 on 2010-09-13
Yes, I presume some1 wld say tat Jtarin but I really din screw anything this tym yet it conked out again. Now what should I do?Try to reinstall via the USB?I can't get into the desktop, is there something I can do through BIOS utility setup?Btw I dun want to try installing via USB again, it din work properly last tym, dun want 2 use that method except as a last resort, so how best 2 go forward?

---

### Post by amjjawad on 2010-09-13
> **Suzanne42 said:**
> Yes, I presume some1 wld say tat Jtarin but I really din screw anything this tym yet it conked out again. Now what should I do?Try to reinstall via the USB?I can't get into the desktop, is there something I can do through BIOS utility setup?Btw I dun want to try installing via USB again, it din work properly last tym, dun want 2 use that method except as a last resort, so how best 2 go forward?

Just do what jtarin told you :) he knows better than me!

If you failed last time to boot or install form USB, it doesn't mean you'll fail now ;)

Try to create a Live USB (check Ubuntu's wbesite - it's explained there how to do that) and if you can't access your desktop, I suppose you have your Live USB ready. If so, try to insert it, reboot your PC/Laptop, go to BIOS, change the priority sequence so that your USB-HDD will be first, save and reboot.

If you don't have Live USB, then try to create it from another PC. I hope you don't have to do so.

Clean new installation is much better than upgrading a current one with tons of issues ;)

---

### Post by Suzanne42 on 2010-09-13
It refuses to boot from USB, dunno why. I have set the USB as my first booting device yet it doesn't boot.

---

### Post by amjjawad on 2010-09-13
> **Suzanne42 said:**
> It refuses to boot from USB, dunno why. I have set the USB as my first booting device yet it doesn't boot.

I think there are 2 options
A- you need to choose which device you want to boot from (CD, HDD, FLOPPY, etc)
B- then there is another option to set the priority of HDD booting just like this on: [http://i53.tinypic.com/2lcfns.jpg](http://i53.tinypic.com/2lcfns.jpg)

You need to choose USB as your bootable device then change the HDD priority.

---

### Post by Suzanne42 on 2010-09-13
Of course, I noe tat, I have alr given 1st priority 4 booting to my USB. jtarin,where r u? M stuck.Formatting my USB & reinstalling 2 USB 4 the nth time.

---

### Post by jtarin on 2010-09-13
Just install from the source your friend had that worked.....then update...not upgrade....get that far before trying to upgrade.

---

### Post by Suzanne42 on 2010-09-13
I dunno what he did, he researched a bit then fixed it, its a working day, hven told him my Ubuntu crashed again. Tell me wat I can do?

---

### Post by Elfy on 2010-09-13
Couple of things here - are you still trying to deal with the issue caused by removing localepurge?

Why is the thread marked as solved ;)

HAve you tried simply to reinstall the desktop? That is from inside whatever you are running ```
sudo apt-get install ubuntu-desktop
```

If you can't get into the system - can you run a recovery session? If so you can run the command from there.

---

### Post by Suzanne42 on 2010-09-13
Yea, earlier the issue caused by localpurge was solved. I had Ubuntu 9.10 installed. It was working fine. Later when I tried 2 upgrade to Ubuntu 10.04, it again crashed so m back 2 square one. Right now trying 2 download the Ubuntu 10.04 iso file again, my comp is not booting frm my USB. So trying 2 redo everything.

---

### Post by Suzanne42 on 2010-09-13
I went to BIOS utility setup & put my USB as 1st priority, no use, it refuses to boot from USB. Right now m waiting 4 Ubuntu file to download, its taking eons 2 download.Need 2 get it 2 download then restart everything.

---

### Post by amjjawad on 2010-09-13
> **Suzanne42 said:**
> I went to BIOS utility setup & put my USB as 1st priority, no use, it refuses to boot from USB. Right now m waiting 4 Ubuntu file to download, its taking eons 2 download.Need 2 get it 2 download then restart everything.

Either something wrong with your USB stick on the .iso file is not working.

Yes, try to install a new copy of Ubuntu, format your USB and create new Live USB.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

then: Burn your CD or create a USB drive
Click on USB stick then show me how.
Just in case you need this.

---

### Post by Suzanne42 on 2010-09-13
Booting from USB doesn't work. It doesn't recognise my USB. I dunno wat 2 do, I reinstalled everything 2 the USB & booted no use.

---

### Post by amjjawad on 2010-09-13
> **Suzanne42 said:**
> Booting from USB doesn't work. It doesn't recognise my USB. I dunno wat 2 do, I reinstalled everything 2 the USB & booted no use.

If you're 110% sure that all the BIOS settings are correct, then do this:

1-Go to BIOS
2- Page 1 
3- Disable your HDD
4- Save and reboot
5- Try to boot from your USB
6- If it did work, it means your USB is fine and there's nothing wrong with it. You'll be able to verify whether your USB and the .iso file is fine and working.

After that, try once more to go to your BIOS settings and enable your HDD and try. Remember, the priority should be always to your USB-Stick.

---

### Post by amjjawad on 2010-09-14
I see you started a new thread but what about this one? did you fix this or what?

---

### Post by Suzanne42 on 2010-09-14
Yea, I got Ubuntu 9.10 up then upgraded to Ubuntu 10.04 Lucid via the terminal but now when I reboot, I get a blank screen. This blank screen is apparently very common when upgrading to Ubuntu 10.04, I din noe before. The issue lies with the graphics card it seems but I dunno what to change in the BIOS menu to boot correctly. So right now I have Ubuntu 10.04 installed but before it reaches the desktop, I get a blank screen. The upgrade to 10.04 took 1.5 hrs as it is now m facing this.

---

### Post by amjjawad on 2010-09-14
> **Suzanne42 said:**
> Yea, I got Ubuntu 9.10 up then upgraded to Ubuntu 10.04 Lucid via the terminal but now when I reboot, I get a blank screen. This blank screen is apparently very common when upgrading to Ubuntu 10.04, I din noe before. The issue lies with the graphics card it seems but I dunno what to change in the BIOS menu to boot correctly. So right now I have Ubuntu 10.04 installed but before it reaches the desktop, I get a blank screen. The upgrade to 10.04 took 1.5 hrs as it is now m facing this.


1-Go to BIOS

2- Page 1 

3- Enable your HDD if it's still disable. There's an option where you can press Enter for AUTO Detection. Just make sure the BIOS can read the real size of your HDD.

4- I think there's an option called: Advanced BIOS features. Make sure your First Booting Device is ... say [CDROM] and make sure the 2nd is your HDD. In the same page, there's another option called: HDD Priority. Make sure your HDD is the 1st.

5- Save and reboot


If you're getting black screen, it means you're not even seeing the booting menu, right?

Check and hope that would solve your issue!

P.S.
The above steps only for the booting issue. If you have a problem with your Graphics Card/Driver, then I'm not sure how would you login to Ubuntu. All what I would suggest is to run the Live CD to test your graphics card. If there's a problem with your Video Card's driver, you could find out when you run the Live CD.

---

### Post by Suzanne42 on 2010-09-14
I din see Advanced BIOS option but anyways I changed my priority list in the BIOS setup again & rebooted.Jus checked, its no use. I need to figure what to do abt the graphic card-Nividia, that's the one giving problems.

---

### Post by slakkie on 2010-09-14
> **Suzanne42 said:**
> Actually I installed Ubuntu long ago, not sure where I kept the CD. Isn't there any command I can type to resolve this mess? Why is my comp sending an alarm when I press Ctrl + Alt + F1? By the way I saw a similar post somehwere where an user had mistakenly remove all packages associated with "ALT" from synaptic package manager. Like my case, her comp also crashed but surprisingly she could get it running again through typing some commands in command line.

I haven't read the whole thread (just to much, sorry). But I guess/believe you can recover from your mistake by running the following:

```

$ sudo aptitude install debsums

$ mkdir tmp

# This might take a while..
$ sudo debsums -c &>$HOME/tmp/debsums-check.log
$ grep  "missing" debsums-c.log > $HOME/tmp/missing-files

# Count the missing files
$ wc -l $HOME/tmp/missing-files

$ awk '{NF=NF-1} {print $NF}'  $HOME/tmp/missing-files | \
sort -u > $HOME/tmp/missing-files-pkgs
# Count the packages
$ wc -l $HOME/tmp/missing-files-pkgs

# Install the packages missing files
sudo aptitude install $(cat $HOME/tmp/missing-files-pkgs)


# And while you are at it:
pkg=$(debsums -l)
if [ -n "$pkg" ] ; then
    sudo aptitude --download-only reinstall $pkg
    sudo debsums --generate=keep,nocheck /var/cache/apt/archive/*.deb
fi

```

---

### Post by jtarin on 2010-09-14
> **Suzanne42 said:**
> I din see Advanced BIOS option but anyways I changed my priority list in the BIOS setup again & rebooted.Jus checked, its no use. I need to figure what to do abt the graphic card-Nividia, that's the one giving problems.First step:Boot with the recovery kernel. It's usually the second item listed in Grub menu. This should get you to the desktop in low-graphics mode.When you get to the desktop post back.Do not change any configurations until you post back.

---

### Post by jtarin on 2010-09-14
If you get to the Desktop:From the menu

Press System &#9656; Administration &#9656; Hardware Drivers.
		
Find the driver which you would like to enable and read the description

Press Activate to enable the driver. You may be asked to enter your password.

The proprietary driver may have to be downloaded and installed.

You may need to restart your computer to finish enabling the driver.

---

### Post by Suzanne42 on 2010-09-14
jtarin, sorry how do I boot into recovery kernal? I only noe press F2 to get into BIOS utility setup.

---

### Post by jtarin on 2010-09-14
> **Suzanne42 said:**
> jtarin, sorry how do I boot into recovery kernal? I only noe press F2 to get into BIOS utility setup.

I posted this> First step:Boot with the recovery kernel. It's usually the second item listed in [COLOR="Red"]_Grub menu_[/COLOR]

---

### Post by Suzanne42 on 2010-09-14
How do I get to the GRUB menu? Some post suggested press ESC, i dun see any menu.

---

### Post by Suzanne42 on 2010-09-14
Ok, jtarin I got into grub menu & selected the sec option(recovery mode), now I will see wat happens then post back.

---

