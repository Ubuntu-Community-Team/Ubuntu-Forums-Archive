---
title: "Wireless and Video"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by acai32 on 2009-01-29
I just installed Ubuntu 8.10 on a desktop, dualbooting with vista. I had run the LiveCD prior to installation to check for any hardware errors. I noticed the wireless networks weren't listed and I was unable to raise the video settings for the GUI desktop. I found the hardware testing utility and ran it and it listed my Wireless Adapter but announced I was not connected to the internet (which made sense seeing it had not found any wireless networks in the network manager). It also failed to show any static or color bars in the video test. So, in summation, my main two queries are for the video card and the wireless adapter. The specs for each are as follows: 

Wireless adapter - 
Broadcom Corporation BCM4318 [AirForce One 54g]
802.11g Wireless LAN Controller 

Video Card - 
XFX GeForce 9800 GTX 

  I also went to Administration > Hardware Drivers and it lists two drivers available. "NVIDIA accelerated graphics driver (version 173)" and "NVIDIA accelerated graphics driver (version 177) [Recommended]". I tried to activate them, but nothing happened. I installed Ubuntu anyways thinking that these were minor problems that could be fixed. So... here I am.

 I checked this thread also:   [http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)  but I have no package called ndiswrapper. Any tips/advice?

---

### Post by Temposs on 2009-01-29
Ah yes. Broadcom wireless cards are known for not working out of the box in Linux. They're basically the only kind that don't these days.

If you'd like to install ndiswrapper, open System->Administration->Synaptic Package Manager and do a search for ndiswrapper by Name. Install ndiswrapper-utils-1.9. You should be able to use ndiswrapper then.

---

### Post by acai32 on 2009-01-29
I searched and no results appeared. I tried a quick search, name search, and name + description search on both ndiswrapper and ndiswrapper-utils-1.9.

---

### Post by Temposs on 2009-01-29
In Synaptic Package Manager, from the Settings menu, please choose "Repositories". Make sure in the "Ubuntu Software" tab(which is what appears immediately), that there are five(5) checkmarks and that they are all checked. Please check them if they are not. 

If there were unchecked boxes that are now check, close the Repositories settings and click the Reload button in the top left.

---

### Post by acai32 on 2009-01-29
The 5th and bottom box "source code" was unchecked and refused to be checked unless I also checked the option "Cdrom with Ubuntu 8.10 'Intrepid Ibex'" under the "Installable from CD-ROM/DVD" menu. So I checked both boxes and hit reload. An error came up, so I tried inserting the Ubuntu LiveCD and retrying, but an error also came up. The error said as follows: 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Releases.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Releases.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/il8n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/il8n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg) Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/il8n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/il8n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/il8n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/il8n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/il8n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/il8n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/il8n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/il8n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead



That took me forever to type, hehe.

EDIT: It didn't come up in the search, but I scrolled down the list and after inserting the LiveCD the option to install ndiswrapper from the CD appeared, so I did. I'll attempt to fix the wireless tomorrow as I need sleep, but thanks for the help so far. I'll check in as soon as I try the fix.

---

### Post by Temposs on 2009-01-29
OK, well you had enough boxes checked. You can put that back how it was if you like.

Next, in Synaptic, select "Sections" from the bottom right buttons and make sure "All" is selected in the left panel. Then tell me how many packages are listed. I have 26534 packages listed. I expect I have a few more that comes standard, but you should have some number on the same order of magnitude.

Also, make sure that "All" is selected when you do a search for ndiswrapper.

You might also try opening a terminal and typing:

```
sudo apt-get install ndisgtk
```

I hope you didn't type all that :-P

---

### Post by acai32 on 2009-01-29
I have 1217 packages listed and 1187 installed.

I attempted the fix I found for the wireless card which I linked a few posts up, it did not work.
edit: I was able to install the .inf file using ndiswrapper, but after a reboot, there was still no wireless detected.

Also, incase I didn't make it clear, I managed to install ndiswrapper already hehe.

 So, right now I'm back at square one. Video card not being utilized and no wireless internet connection. Now what? :)

---

### Post by avtolle on 2009-01-29
Now that you have Ubuntu installed, you can again try to activate the driver for your video card; please note that you will need to have an internet connection for this, so given your current situation with the wireless, a wired internet connection will be needed. This for the reason that the driver files, etc., will need to be downloaded.

Broadcom wireless cards continue to be problematic; there are multiple threads on that topic, as I'm sure you have learned, with many potential solutions. Generally, you will need to download the Broadcom firmware from an approved site and install. There was a thread on the Forum (sorry, don't recall the subforum) earlier today with some good detailed directions; I'll see if I can find it again.

---

### Post by acai32 on 2009-01-29
Alright, I'll try to find a cable long enough to run to the router. I'll also take a look around for more broadcom fixes, thanks for the continued help, I appreciate it.

---

### Post by avtolle on 2009-01-29
[http://ubuntuforums.org/showthread.php?t=1054127&page=2](http://ubuntuforums.org/showthread.php?t=1054127&page=2) and look at post #14 and following for some information which should help you regarding your wireless card. Good luck.

---

### Post by acai32 on 2009-01-29
I've got class soon, but I'll look it over and let you know of my results as soon as I try. Thanks for the link!

---

### Post by acai32 on 2009-01-30
Alright, I tried out the advice in post #14 of [http://ubuntuforums.org/showthread.php?t=1054127&page=2](http://ubuntuforums.org/showthread.php?t=1054127&page=2)
 and I receive an error. Here it is:


michael@michael-desktop:~$ sudo apt-get install b43-fwcutter
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.3kB of archives.
After this operation, 102kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)'
in the drive '/cdrom/' and press enter

Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 99840 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2009-01-30 09:33:32--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by acai32 on 2009-01-30
I tried connecting to the internet via ethernet cable and retrying due to the lines:
--2009-01-30 09:33:32-- [http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'

And it downloaded flawlessly. Wireless is now up and running. Now I'll try downloading the video cards drivers online. I'll let you know the results.

---

### Post by buffy^ on 2009-01-30
Good on ya!

---

### Post by acai32 on 2009-01-30
I'm so close I can taste it...

 Aaaaaaaaaaaaaaaaaaaaaaaanyways, I checked out the xfx site for the drivers.
Here's the site: [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

I followed the instructions and got the following error:

michael@michael-desktop:~$ sh NVIDIA-Linux-x86-173.08-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08-pkg1.run
 
Any ideas?

---

### Post by avtolle on 2009-01-30
Do ```
sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
```as I think you need to be root. 
Query: why not activate through System>Administration>Hardware Drivers?

---

### Post by acai32 on 2009-01-30
I received the same error message. 

As to why I do not use the system > administrator > hardware drivers utility, it doesn't allow me to activate the driver, even though it's listed. I click activate, and it does nothing.

---

### Post by avtolle on 2009-01-30
Had a thought; did you d/l the driver file to your desktop? If so, do```
cd Desktop
```and try the command again to run the driver installation file.

---

### Post by acai32 on 2009-02-08
Sorry it's been such a long time since I've responded. My time was consumed with a project.

Anyways, back to where I left off.

I have downloaded the drivers off of NVIDIA's site, but I'm having trouble installing them. The main problem is that the installation requires me to turn off the "X server" and I have absolutely no idea how to do that. 

I've tried a few methods. I tried ctrl+alt+f1, the virtual terminal (so I was told) then using the command "/etc/init.d/gdm stop" but that didn't work. I also tried "telinit 3" but that did not work either.

Any ideas?

---

### Post by Temposs on 2009-02-08
Basically, the only way I've ever been able to install them has been to boot into recovery mode and go into command line mode there.

---

### Post by kctinman on 2009-02-08
I have Broadcom I think... it did not work while using live cd, but when i installed on HD it found the drivers and now wireless works great..

---

### Post by acai32 on 2009-02-08
> **Temposs said:**
> Basically, the only way I've ever been able to install them has been to boot into recovery mode and go into command line mode there.

I just tried this, and it advises me to install in run level 3 "telinit 3" because installing in run level 1 may cause problems. I tried it in run level 3 again and it failed. Should I just go ahead and install in run level 1?

---

### Post by Temposs on 2009-02-08
yeah, it's fine :-) I just bypass that warning. Never had a problem

---

### Post by acai32 on 2009-02-08
One day! One day I shall conquer you, oh mighty driver!

So, I ran it in run level 1 as suggested and get this message:

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)

Then, no matter if I answer yes (it fails) or no ( it doesnt try) it says:

No precompiled kernel interface was found to match your kernel;this means that the installer will need to compile a new kernel interface.

Then an error message saying:

ERROR: Unable to build the NVIDIA kernel module.

And then the installation fails.  Any ideas?

---

### Post by Temposs on 2009-02-09
I believe the failure is a result of you using an old driver version...

Try one of the 173.* drivers from this page, which always shows the most recent drivers: [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by acai32 on 2009-02-09
Tried it out, same result.

---

### Post by Temposs on 2009-02-09
Try the steps in this page: [http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

He seems to have a card that's close to yours, so maybe it'll work...

I think the main difference to what we've tried so far is the linux-headers part, but try it all(replacing the kernel version with the current one, and /location/to/driver with the location to your driver, etc...

---

### Post by acai32 on 2009-04-06
I'm back from my massive break! Anywho!

I tried the method described on the page you linked, same result as my previous post.

---

