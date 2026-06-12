---
title: "Ubuntu Edgy and CNet CWD-854 Wireless-G Dongle"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by RKCole on 2007-03-01
Hello, everyone.

I just purchased a CNet CWD-854 Wireless-G Dongle which uses the RaLink Technologies RT73 chipset.  After today I plan to go wireless to cut down on the hassle of running cables in my town home.  I was able to (after updating the outdated driver) get this device to work and interact with my Linksys WRT54G wireless router in Windows XP, but I am not sure what I need to do to get this to work in Ubuntu Edgy.  I've searched the forums (well...with the best of my searching ability), and I have come across a post or two about this, but I do not believe that any of the said posts were solved.

Does anyone out there know how to go about getting wireless to work using this device in uUbuntu Edgy?

Thanks for any input/suggestions provided.

Take care.

---

### Post by RKCole on 2007-03-02
Sorry, everyone.

I don't typically like to bump topics, but I must do so in this case.  I still have not, unfortunately, come across a solution to this issue.  Still researching, though.  Wish I had more experience in this area.

Thanks in advance for any input.

Take care.

---

### Post by RKCole on 2007-03-02
Well, I've come a small step forward in this matter.  During my research I learned that the RT73 and RT2571 chipsets are pretty much the same thing.  Now on to getting this all sorted out.  I have both the source code for the Linux driver and the Windows driver saved onto a USB Flash drive, so now I'll go see if I can get this up and running.  I'll post back later.

---

### Post by nyinge on 2007-03-02
If the method you're trying doesn't work, we can try ndiswrapper.  I found your card [listed here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#C").

---

### Post by RKCole on 2007-03-03
Hello, nyinge.  Thanks for your response.

I tried the compilation method to no avail.  I also tried th efollowing wiht the rt73.inf file from Windows:

```

sudo ndiswrapper -i rt73.inf
sudo modrobe ndiswrapper <-------This led to the error message "/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko; No such file or directory" Is something broken?----->

```

I had read that after doing this I could run
```

sudo ndiswrapper -m

```

Unfortunately, though, I think I did it incorrectly.  Also, what do I need to do about the ndiswrapper.ko file that is missing?

Thanks for any input you can give.  I'm doing all I can to learn how to do these things as I hope to soon just give up Windows all together...I'm getting closer and closer...Just need to get used to some things.  I wish I knew more about Networking, though.

Thanks again.

PS:  I was thinking of maybe purchasing a book on Ubuntu; would you have any recommendations?  I would like to find something which is very in-depth...something I could use maybe even across different distros, if needed.  Any ideas?  Thanks again and take care.

Take care.

---

### Post by nyinge on 2007-03-03
Which compilation method did you follow?  From the ndiswrapper site?  What I did was I downloaded the latest ndiswrapper source package from its [website]("http://sourceforge.net/projects/ndiswrapper/").  Make sure you have build-essential and linux-image-`uname -r` packages.  Also, make sure that you've removed the module bcm43xx.
```
 sudo su 
```   - to become a superuser.
```
 echo "blacklist bcm43xx >> /etc/modprobe.d/blacklist 
```   - to prevent it from loading at startup.  Reboot your computer.

Then I compiled and built the module.
```
 make uninstall 
``` - to uninstall the previous version of ndiswrapper.
```
 make 
``````
 make install 
```Now, install the wireless hardware's driver:
```
 ndiswrapper -i DRIVER.inf 
```Check if hardware and software are installed:
```
 ndiswrapper -l 
```   - should display something like "hardware present, software present"
```
 modprobe ndiswrapper 
```   - see if it still complains about "ndiswrapper.ko" not being found.

If things turn out smooth, we're good to go.  :)

---

### Post by RKCole on 2007-03-04
I'll have to try this tomorrow; hopefully I'll have some luck with it.

So, do I need the rt73.sys file as well?  I had seen on some sites that both the .sys and .inf files were needed.

Thanks for the help.  It is much appreciated.

Take care.

---

### Post by nyinge on 2007-03-04
Yes, you do.  In my case, I needed lsbcmnds.inf and bcmwl5.sys for Linksys WPC-54G card.

---

### Post by RKCole on 2007-03-15
Sorry for the delayed response...it's been hectic here.

I found the rt73.inf and rt73.sys files in Windows and copied them to a folder on my Ubuntu Desktop.  I then ran (I am sure it was the ndiswrapper graphical utility) System->Administrative (may be off on that)->Windows Wireless Device and installed the rt73.inf file.

When I went to configure my network interfaces, I found wlan0 and wmaster0 present.  The command

```

ndiswrapper -l

```

shows that the hardware and the driver are present.  I tried to ping my router, but to no avail.

My Linksys WRT54G Wireless router is set up to use WPA2 with a pre-shared key.  Could this be why my computer is not getting an Internet connection?

Do you think that just reinstalling Edgy would get things set up automatically?  I've been meaning to do that, anyhow.

Thanks for the help with this issue.

Take care.

---

### Post by nyinge on 2007-03-15
I don't think reinstalling Edgy would solve the problem at all.  Take a look at this [post]("http://ubuntuforums.org/showthread.php?p=1741197#poststop").  Although it is for a different wireless chip, you will get the general idea.  I'd suggest trying without wpa2 or any encryption first.

---

### Post by nattydread on 2007-03-17
Hi I’m just getting started on this Linux thing. Downloaded and installed latest kubuntu, dual boot w xp.
I don't really know anything on Linux, but to start I need internet. Have a wireless connection, same cnet g dongle.
How can I get this running? Need all the help I can get!!
Besides this, what’s a good method to learn Linux?, books, forums, I’m kind on my own, no friends on Linux experience.
Thanks

---

### Post by RKCole on 2007-03-18
Hello, nattydread.

Within the next few days (when I have enough "alone" time with my PC) I'm going to work on getting the wireless Internet up and running with my Cnet Dongle.  I've done a lot of reading on this subject (and have been given some pointers by nying in previous posts on this thread), and once I get it all up and running, I'll write back with instructions on how I did it.

As far as reading up on Linux goes, I've got a few good sites for you:

UbuntuGuide.org
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Psychocats Ubuntu Tutorials
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Free Online Linux Courses
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

Ubuntu Document Storage Facility (UDSF)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

Ubuntu Wiki
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Ubuntu Help Pages
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Linux Command Reference (I am sure there are better ones, but this is all that comes to mind right now)
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

I hope that these links will be fo some help.  As far as books I am unsure at this point.  I was thinking of ordering the Ubuntu Linux Bible ([http://www.amazon.com/Ubuntu-Linux-Bible-William-Hagen/dp/0470038993/ref=pd_bbs_sr_1/002-2309057-1718428?ie=UTF8&s=books&qid=1174238971&sr=8-1](http://www.amazon.com/Ubuntu-Linux-Bible-William-Hagen/dp/0470038993/ref=pd_bbs_sr_1/002-2309057-1718428?ie=UTF8&s=books&qid=1174238971&sr=8-1)) which seems like it would be a great resource.

Hope this helps.

Take care and welcome to Ubuntu.

---

### Post by RKCole on 2007-03-18
Hello, again.

I accidentally stumbled across [this link]("http://opensource.bureau-cornavin.com/belkin/index.html") which seems to have a good tutorial on getting wireless up and running.  Although it is for a Belkin device, the chipset is still the same as the Cnet CWD-854 Dongle.  I'm going to give this a try today (hopefully) as well as other suggestions.

---

### Post by nattydread on 2007-03-18
thanks for the info RK \\:D/. got some reading to do!!

---

### Post by RKCole on 2007-03-18
No problem.  Although there is quite a lot to read and learn, it's definitely fun doing.

As far as the wireless dongle situation goes...still no luck.  I've read and tried compiling code based on the tutorial I posted just a few posts ago, but to no avail.

When I run

```

sudo iwlist wlan0 scanning

```
I can see my wireless network and the others in this area.  Does this have any significance?

I used my Ubuntu Edgy Alternate install CD earlier today to see if it could detect my wireless 2)  network during the Network Configuration portion of setup (Before going into the initial Ubuntu installation setup setup I disabled wireless security on my Linksys WRT54G router, thus leaving everything open in the hope that something different would occur).  This portion of the setup detected eth0, wmaster0, and wlan0.    The setup asked me for my ESSID, so I entered it.  I did not set up a network password, so I hit enter on the screen which requested it.  The setup process then searched for my wireless network, but did not find one.  It actually gave me a Network Configuration Failure message which stated that no DHCP server could be found.

As far as the drivers I compiled/tested, there were the following:
1)  RT25USB-SRC-V2.0.8.0.tar.gz  (compiled successfully)
2)  rt73-cvs-daily.tar.gz  (compile was unsuccessful)
3)  rt2570-1.1.0-b2.tar.gz  (compiled successfully)

(1 was obtained [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").  2 and 3 were obtained [here]("http://opensource.bureau-cornavin.com/belkin/index.html"))

I was unsure fo which one to use as I had read that the rt2571 chipset was also the rt73 chipset.

I'm stumped.  Should I try to reinstall Edgy tomorrow and start off from scratch as [this post]("http://ubuntuforums.org/showthread.php?p=1741197#poststop") that nyinge directed me to recommended?

Thanks for any suggestions.

---

### Post by RKCole on 2007-03-18
I have a few questions/information which has just aroused my curiosity regarding this issue.

1.  When I installed Ubuntu Edgy (last October when it first came out) I lived in Ohio and had a different ISP.  Back then I used an Ethernet connection without a router.  I am now in California under a different ISP and I now use the router.  (I do not think this makes too much of a difference, though, as everything works perfectly via an Ethernet connection to the router.)  I would use an Ethernet cable connection, but my PC is too far away from the router and I do not have the option of moving it.

2.  I tested a USB version of PCLinuxOS MiniMe just a couple of minutes ago and ti detected my wireless dongle (as rausb0) on the initial boot-up.  The command
```

#  iwlist rausb0 scanning

```
showed all of the same wireless networks in the area as it did in Edgy earlier today, but it could not connect to mine.
I know that this may be an ignorant question (but I am here to learn), but could my router possibly be the cause of this issue?  The wireless dongle is obviously working if the wireless networks are shown when using iwlist (and I do not have a wired connection available right now).  Is there something which I need to do with my wireless router configuration/router firewall?

Thanks for reading and for all of the input.  I think that I am getting closer to resolving this issue.

Take care.

---

### Post by nyinge on 2007-03-19
Since we're seeing the router with iwlist, we're close I guess :).

Try:
```
 iwconfig rausb0 essid YOUR_ESSID 
```
Then, check if it has been associated:
```
 iwconfig rausb0 
```
This should show the status.  More importantly, check the "Link Quality".  It should be something like (some numbers) / 100 instead of just 0.

If things go well, issue
```
 # dhclient rausb0 
``` to get IP.  Could you also post the output of those, so that we can all try to troubleshoot.  crossing fingers...  :)

---

### Post by RKCole on 2007-03-19
Well...I hate to say it...but I broke something yesterday, apparently. :)  It's alright, though.  I am going to do a fresh install today and start from scratch.

As far as the rausb0 went, I received that interface on the PCLinuxOS system I put onto my USB drive...but never saw it in Ubuntu.  All I had in Ubuntu as wireless interfaces were wlan0 and wmaster0.

I did some more reading this morning and found [this link]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73#head-cfea35eda750890a23c58873b4183271cc3a650c") which has more information about getting wireless cards with this chipset to work.  Apparently Edgy comes preinstalled with a driver for the chipset (module rt73usb), but from what I have read the driver does not work.  I'm going to give this one a shot once the installation is complete.  Before that, however, I am going to update the firmware on my router..in case that is what is causing the problem.  I'll post back as soon as I find out anything new.  Sorry for the delay on this.

Take care.

---

### Post by nyinge on 2007-03-19
Make sure you blacklist the module rt73usb(one that came preinstalled) when you want to use other alternatives such ndiswrapper.  Good luck.

---

### Post by RKCole on 2007-03-20
Well, everyone..the suspense is finally over.  Wireless now works on my Edgy distro.  It was actually pretty easy this time around...I guess I just made things harder than what they were.  I'm going to write out, step-by-step, how I did this.  I don't know if this would be material for a HOW-TO, but I will try to make this as detailed as I can.

**NOTE:**  To insure that the compilation of this driver source is successful, you must have the latest linux-kernel headers installed on your system.  I believe that if you always let the Update Manager do its work when new updates are available that this should already be done for you. (It was for me today after reinstalling Edgy and getting all available updates)  You must also insure that you have build-essential installed.  If you do not have this installed, simply use the command
```

sudo apt-get install build-essential

```

[SIZE="4"]**STEP 1--GET THE RT73 DRIVER**[/SIZE]
Through all of my research, I found that the RT73 driver is constantly "in the works".  You can get the latest version of the driver source from the RT73 link on [this page]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads").  The name of the driver source file is **rt73-cvs-daily.tar.gz**. I do not think it really matters where you save the file, but I saved it in /usr/src for my memory's sake.

There is a default RT73 driver in Ubuntu Edgy, but from what I have read ti does not work very well.  As nyinge mentioned in earlier posts, this driver must be blacklisted.  To do this, simply do:
```

sudo echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist

```
This should tell the kernel not to use the default rt73usb driver.

[SIZE="4"]**STEP 2--EXTRACT AND COMPILE THE DRIVER**[/SIZE]
**cd** to the directory where you saved the driver source file and use
```

sudo tar -zxvf rt73-cvs-daily.tar.gz

```
to unzip/untar the file into a directory named **rt73-cvs-daily-<date>**.  Now, use the command
```

cd /<directory containing driver source>/rt73-cvs-daily-<date>/Module/

```
to change to the directory containing the driver source.

**HINT:**  In cases like this where there is a lot to type, the tab-autocomplete feature of the Linux terminal is very nice.  Just type in part of a directory name, hit tab, and, in most cases, the system will fill in the blanks for you.  If you hit tab and hear a system "beep", it usually means that one or more directory/file names begin with the characters typed in.  Hit tab again to see a list of these directories/files or type in a few more characters and hit tab again.

Now, execute the following commands to create teh driver:
```

sudo make
sudo make install

```

The driver should now be compiled...but this isn't the end.  There is some configuration which must be carried out.

[SIZE="4"]**STEP 4--SYSTEM CONFIGURATION**[/SIZE]
The following actions must be taken in order for the system to see/activate the USB dongle on startup.

1.  Open /etc/modules in gedit 
```

gksudo gedit /etc/modules

```
and add the line "rt73" at the end of the file, on its own line.

2.  Check to see fi the installation added a rt73 file (text file) to your /etc/modprobe.d/ directory.
```

ls /etc/modprobe.d/ | grep rt73

```
If this file does not exist (it did not exist on my PC), create it.
```

sudo touch rt73

```
Now, put the line "alias rausb0 rt73" inot the file.
```

sudo echo "alias rausb0 rt73" >> /etc/modprobe.d/rt73

```

3.  The driver installation (make, make install) creates a modprobe.conf file located in /etc/modprobe.conf.  This file has no use and should be removed.
```

sudo rm /etc/modprobe.conf

```

4.  Make a backup of /etc/network/interfaces.
```

sudo cp /etc/network/interfaces ~/interfaces.backup

```

5.  Use gedit (using gksudo), open the file /etc/network/interfaces
```

gksudo gedit /etc/network/interfaces

```
Delete the information that was automatically generated for the rausb0 (or ra0) device.  Add the following (just copy and paste) underneath the section about wireless devices (where the just deleted information was located).
```

auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid ""
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=
        pre-up iwpriv rausb0 set EncrypType=
        pre-up iwpriv rausb0 set WPAPSK=
"
        pre-up ifconfig rausb0 up

```

Set the values for essid, AuthMode, EncrypType, and WPAPSK (your WPA key if you use WPA)  I would like to use WPA2, but I have not tested i tout yet.

6.  Reboot.

Everythign worked perfectly after rebooting.  I did a test (pinged a DNS server), and everything worked normally.  iwconfig rausb0 now shows information for Link Quality and everything else.

I hope that this will help others in this situation.  It actually did not take long at all to set everything up, and it was much easier than I would have expected.

It is late here, and I am sure I have made some typos in this.  I will come back tomorrow to make any edits.

Take care, everyone.  Marking this as solved (if I can remember how...haha).

---

### Post by nyinge on 2007-03-20
I'm glad it's working, and that's an awesome detailed guide.  I'll bookmark it to refer to anyone who needs it.  Thanks RKCole!

---

### Post by RKCole on 2007-03-20
Thanks, nyinge.  And I appreciate you sticking with me through this whole thing.  You definitely were a great help.  And thanks for the compliment on the guide.  I have always loved writing.

Take care.

---

### Post by RKCole on 2007-03-20
PS:  Dumb question, I know...but this one's a lot easier to answer.  I really cannot remember how to mark a thread as SOLVED.  How do I do this again?  Sorry...

---

### Post by nyinge on 2007-03-20
> **RKCole said:**
> PS:  Dumb question, I know...but this one's a lot easier to answer.  I really cannot remember how to mark a thread as SOLVED.  How do I do this again?  Sorry...

Click "edit" on your very first post in this thread, and you'll find a checkbox in the beginning for marking it as resolved.  :)

---

### Post by RKCole on 2007-03-20
Thanks, nyinge.  You're a life saver. :)  I looked through all of the other options and the User CP, but found nothing about marking threads as solved.

Thanks and take care.

---

### Post by nattydread on 2007-03-23
RK thats great!!=D> 
congratulations i didn't understand a thing but hey it works!!! 
ill try it on my kubuntu (of course ill just copy paste, can i do this with kubuntu?)
that guide is sweet, do you think it will work on my system, remember i dont know what i'm doing, but maybe after this i might be surfing on Linux rather than microsoft!! so i can begin to understand Ubuntu!! 
great work

---

### Post by nyinge on 2007-03-23
> **nattydread said:**
> RK thats great!!=D> 
congratulations i didn't understand a thing but hey it works!!! 
ill try it on my kubuntu (of course ill just copy paste, can i do this with kubuntu?)
that guide is sweet, do you think it will work on my system, remember i dont know what i'm doing, but maybe after this i might be surfing on Linux rather than microsoft!! so i can begin to understand Ubuntu!! 
great work

Yes, it should.  Make sure you use "kate" (or kwrite) instead of "gedit", since gedit is native to GNOME.  Good luck!  :KS

---

### Post by RKCole on 2007-03-23
I"m not too familiar with Kubuntu/KDE as I've only used GNOME since I began using Ubuntu.  I would think, however, that everything (with an exception to the text editor in use, as nyinge had mentioned) should be the same.  Please, someone, correct me if I am wrong, but I believe that KDE is just a graphical desktop environment, but the underlying system is the same.  The only differences lie in what graphical applications are in use and the actual desktop itself.

I hope that you'll have yours working soon, nattydread.  Please let me know the outcome.

Take care.

PS:  I was thinking about improving this tutorial some by working on wording and [trying to] give more explanations of what is being done.  I just really wish I had more knowledge in networking/network security/Linux...I think I'm getting a bit better, though.

---

### Post by RKCole on 2007-03-23
Hello again, everyone.

I just installed Ubuntu 7.04 (Feisty Fawn) beta a few minutes ago.  Unfortunately it did not detect my wireless dongle, but I am happy to inform you that the method for getting it to work on Edgy also works on Feisty.  I am writing you from my Feisty desktop at this moment.  I just wanted to leave this update as I wanted to see if I could get this working on Feisty...and needless to say...it does...and well.

Take care.

---

### Post by nattydread on 2007-03-25
hi hows it going.
couldn't make a thing on my kubuntu, i don't know what i'm doing wrong :confused: .
first i cant copy paste using the console or kate, nothing happens when i click paste.
so i typed the commands and attached is what i got
downloaded the rt73 file but save it on a fat 32 partition, to use it on ubuntu and windows, then i couldn't move it to usr/.... (the folder you suggested), it just didn't gave me the option.
remember i'm a complete rookie, so any help is appreciated.
Thanks

---

### Post by RKCole on 2007-03-25
Hello again, nattydread.

I read through your text file and noticed that the installation of build-essential was unsuccessful.  If you do not have a wired connection to your Ubuntu system, this may be the cause of the problem.  Basically, when you type

```

sudo apt-get install program-name

```

apt (the apt program is a program used to install/remove/update/etc applications) will try to look in the online repositories for the package(s) specified.  If you do not have an Internet connection established, apt-get will typically return an error stating that it couldn't find the package.  Don't worry though.  If you have the CD which you used for your installation, build-essential should be on the CD (it was on my Ubuntu installation CDs).  I read, just a minute ago while I was looking up a way to help you solve your problem, that if apt is not set to search your CD-ROM drive that you can use the following commands in a terminal to get build-essential from your Ubuntu CD.

```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

```

This should get build-essential and install it from your Kubuntu installation CD.

Now, as far as blacklisting rt73usb, I ran into the same error you did when attempting to do so.  nyinge actually posted earlier (I think on page 1) that you must do
```

sudo su

```
and enter your password for your current user account.  This will give you root/superuser access.  I found that doing the blacklist operation worked just fine under those stipulations.

Now onto your problem with moving the rt73file to /usr/src.

You mentioned that the file was saved onto a FAT32 partition.  If you (in a terminal) execute the command
```

cd /media

```
(I'm pretty sure it's the same on Kubuntu) you will be in the /media directory.  This directory contains devices which are mounted (accessible) on your system, such as cdrom (your CD-R/RW/ROM drive).

Your FAT32 drive/partition should be listed there under (depending on your setup) a category of hdb<partition number> (if the FAT32 partition is on your secondary hard drive (if you have it set up that way)).

To list the contents of the hd<letter><number of partition> drive, just do 
```

ls /media/hd<dletter><partition number>

```
If you see your rt73 file listed on whichever drive you test, you know that's the drive you want to copy from.  So you would then execute the command
```

sudo cp /media/hd<letter><partition number> /usr/src

```
This will copy the file from your FAT32 drive to /usr/src on your Linux system.

Now, just execute the command
```

cd /usr/src

```
to change to your /usr/src directory.

Now you should be able to extract the driver source and complete the rest of the steps listed in the instructions I gave earlier.

if you need any help whatsoever, please let me know...and if my instructions are not completely clear, please let me know.  I'm always glad to get construction criticism.  I'll do what I can to help you get this up and running.  If you'd like I could try to write out an OpenOffice document with step-by-step instructions.

I know that all of this is a lot for being a new Linux user, but it definitely gives more understanding on how the system works and also gives a great deal of experience with the command-line.  Don't feel like you're the only new one here, though, as I'm still quite new to Linux.  I'm **nowhere** near the status of "Linux Guru", but I'm working my way there.

Take care and write back with any questions you may have.

PS:  It may take me a day or so to write up an OpenOffice tutorial (as I like to add pictures and all that "flashy stuff"), but if it woudl be of help, I'd be more than willing to do so.  Just let me know and I'll do what I can.

---

### Post by nattydread on 2007-03-28
Hi buddys hows it going.
i started to install my wireless conection and here is what i got.
first of all this was not attached i typed 

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

every thing was great :)
then 
sudo su, so i got to the directory.
then when changing the directory, didnt know what to do with
ls /media/hd<dletter><partition number>, especially with <dletter><partition number>
didnt know what is my <dletter>, i have 1 120Gb drive with 4 partitions, didnt know the partition number, finishing with i didnt know if i should type the <> symbols

so i managed to place the rt73 file on the desktop and worked my self to use... what is typed on the attachment. 
as you see, i came close but again, what should i do with the <> symbols on <date> (refer to  the attachment)

sorry for the pain in the @%# but hey i typed my first commands and some worked!!!:guitar: 
thanks for any help and for your time

---

### Post by RKCole on 2007-03-28
I'm very sorry, nattydread.  I didn't specify things well enough.  I sincerely apologize for that.

When you use the command
```

ls /media

```

you should see something like
```

cdrom cdrom0 cdrom1 floppy0 hda1 had2 ...

```
This may vary depending on the hardware on yoru system.

The **hd** stands for Hard Drive (i.e. hda1, hda2, etc).  The letter (which I noted as <drive letter>) **a** would be the drive letter.  hd**a**1 would be your first hard drive, hd**b**1 would be your second hard drive.  This is if you use IDE-style drives.  If you use SATA drives you would probably see sda1, sdb1, etc.  Now for the numbers, which I labeled as <partition number>.  hda**1** would be the first partition on your hard drive, hda**2** woudl be yoru second partition (both on your first **a** drive.

So what I meant when I said to search through the hd<drive letter><partition number> was to search through hda1 and so forth (whichever one would be your FAT32 partition) to find the rt73 source file that was downloaded.  Then you coudl continue on to copying it.  Then once you would extract it using
```

sudo tar -zxvf rt73-cvs-daily.tar.gz (sorry..not exact as I cannot remember the exact name of the file)

```
you woudl have a directory called (something along the lines of) rt73-2007323.  You woudl then **cd** into that directory and into the subdirectory Modules using
```

cd rt73-2007323/Modules (the name may be different for you)

```

You could then proceed to compile the file and continue on with the other steps.

I really hope that this helps some, and I am sincerely sorry for not clarifying myself in the previous posts.

Please write back if you need any more help and I will do what I can.  It is late here at the moment, and I am unsure of how long I will be awake...but if I am online and see a new post from you I will reply.

Take care.

---

### Post by nattydread on 2007-04-01
Hi,I've tried some sudos here and there but got an error, dont know how, dont know why, but here is what i typed. i tried like 2 hours to figure out maybe what was going on, the error was on
 sudo make
sudo make install
but there was some error :confused: 
then i tried with
sudo Makefile (or something like that, it was on the same ....../Module/    file, there was no make "page" or file on Module or cvs).
attached is what i typed on kate
any help will be great. thanks

---

### Post by RKCole on 2007-04-01
Hello, nattydread.

Which version of Ubuntu are you using at this time?  I'm not sure fi your kernel version has anything to do with it or not, but I have kernel v2.6.17-10-generic on Ubuntu Edgy.

From the resources I had, the latest kernel headers are needed.  I do not know if this is an option, but are you able to (temporarily) use an Ethernet cable connection so that you can install updates to your system?  I had to do that with mine at one point.

I just hope that I can help you get this going.  I'll do what I can on my end.  Write back when you get a chance, and hopefully I'll catch it so you don't have a long wait for a response.

Take care.

---

### Post by nattydread on 2007-04-02
Hi RK.
really dont know the version on my kubuntu but what i did is downloaded the latest dapper (6.06.1 lst).
how can i check my kubuntu version?
thanks

---

### Post by RKCole on 2007-04-05
Hello, nattydread.

It sounds like you are running Uubntu Dapper (v6.06) as you had mentioned that you downloaded v6.06.1.

If possible, are you able to temporarily use a wired connection to download updates to your system?  I think that this may help things out a bit.

I know it's frustrating to keep restarting and booting into Windows/Ubuntu (if you are dual booting) as this is exactly what I had to do when I was working on getting my wireless up and running.

---

### Post by LeventO on 2007-05-20
Hello,

I also happen to be using the CNet CWD-854 Device. I've followed RKCole's instructions pretty closely.

the only place where i had a problem was the last step, the interface file. the file now looks like this:
```
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp





iface eth0 inet dhcp



auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "SSID"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=open
        pre-up iwpriv rausb0 set EncrypType=WPA
        pre-up iwpriv rausb0 set WPAPSK="mynetworkpassword"
        pre-up ifconfig rausb0 up

auto eth0
```
I wasn't sure what was supposed to be after essid, or what the authmod or encryptype or wpaPSK were exactly, but i googled around and figured, essid was supposed to be followed by the actual network name (my network name was set in my wireless router and I've used the same name here, I've just changed it to SSID for the purpose of posting it to the internet, the file  has my actual network name in it), the authmode i understood as being either open or shared, my router is set to automatic, and i don't know what the difference is so i just set it to open. the encryptype is either WEP, WPA or none (mine is WPA, again set at the router), WPAPSK, i understood to be the network password (again changed to protect my actual password for the purpose of posting it here)

so then i rebooted and i run iwconfig and see
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

at the top of my screen the wireless network icon shows only my wired connection, and not my wireless, when i go into manual configuration i see wireless connection (set on roaming), wired connection and modem connection.
before getting rid of the default drivers it showed wlan1 and wmaster1 instead of wireless connection, i could also actually see my network. (the connection just never worked, even when i tried setting the router to WEP or no encryption)

anyway, I'm not sure what I'm doing wrong,

I'm using the AMD64 version or 7.04 feisty by the way.

thanks for any help

-Levent

---

### Post by RKCole on 2007-05-20
Hello, Levent0.

I wrote a guide using OpenOffice which has more details than the walkthrough here.  I have wanted to post the guide here, but it will take a lot of editing.  I cannot upload it because the size fo the file is too large (about 20KB over the limit).  I could e-mail it to you if you'd like.  If you'd like me to do this, please just private message me here on the forums.

Please take care.

---

### Post by LeventO on 2007-05-20
Thanks RKCole,

I actually managed to figure it out.
I'm not sure exactly what the problem was, but some of the following may have been critical:
1. my wireless interface is called wlan1 not rausb0
2. WPA encryption did not work on my device
3. the device did not request an address from the DHCP server

i made the following changes:
1. changed the name in the interfaces file from rausb0 to wlan1
2. changed my router's encryption to WEP, and changed the encrypType, and add the WEP key in the interfaces file
3. added the dhclient command in the file to request an address form the DHCP server

here is the new interfaces file, the bit in tags is where my actual network information goes:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
        pre-up ifconfig wlan1 up
        pre-up ifconfig wlan1 down
        pre-up ifconfig wlan1 up
        pre-up iwconfig wlan1 essid <my network name>
        pre-up iwconfig wlan1 key <my 128bit WEP hex key>
        pre-up iwconfig wlan1 mode Managed
        pre-up iwpriv wlan1 set AuthMode=open
        pre-up iwpriv wlan1 set EncrypType=WEP
        pre-up ifconfig wlan1 up
        pre-up dhclient wlan1
```
as a point of note, the authmode is set to open here and on my router, i don't understand what the difference between open and shared is, but i think those are the only two options for the device here, and my router can also be set to automatic, though, again, i don't know what that means.

i rebooted my computer and the router, to check that it works properly, and it does, so that's one problem solved. now I have to figure out how to access the shared files of the windows computers in my network, and why the screen resolution of my shiny new 19in LCD screen isn't going above 1024x768... hmm...

---

### Post by mooser on 2007-11-09
Hi All,

Sorry to open up this thread again. I appreciate all the hard work put in by the previous poster, but it seems that I too am having problems getting the old CWD-854 wireless-g (usb) to work with ubuntu.

First some background:
Fresh install of Gutsy
Followed RKCole's instructions
No luck
Mucked around with trying to move over the windows drivers - no go either

Here's what my /etc/network/interfaces/ looks like:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
        pre-up ifconfig wlan1 up
        pre-up ifconfig wlan1 down
        pre-up ifconfig wlan1 up
        pre-up iwconfig wlan1 essid myssid
        pre-up iwconfig wlan1 key db mywepkey
        pre-up iwconfig wlan1 mode Managed
        pre-up iwpriv wlan1 set AuthMode=open
        pre-up iwpriv wlan1 set EncrypType=WEP
        pre-up ifconfig wlan1 up
        pre-up dhclient wlan1

auto eth0


```

and here's what the corresponding iwconfig looks like
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

despite repeatedly entry my ssid I can't seem to get it to pick up.

Any pointers, hints or tips would be most appreciated.

If it helps any, I have an ethernet connection going and I mostly access the machine through ssh or vnc.

thanks heaps!

---

