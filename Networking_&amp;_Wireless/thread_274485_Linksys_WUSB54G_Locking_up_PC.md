---
title: "Linksys WUSB54G Locking up PC"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by spacecowboy706 on 2006-10-09
I have a Linksys LNE100TX Wired Ethernet card that work sgreat with my new Ubuntu system. I also have a Linksys WMP54G wireless PCI card that is also working great, again with my new Ubuntu System.

BUT

My Linksys WUSB54G wireless USB adapter may or may not be working. Heres why... if i go to Main Menu -> System -> Administration -> Networking and then disable the other two cards and then select the rausb0 device and then click the "Activate" button... my system locks up and will do absolutly nothing. I have to press the Power button on the PC case to turn off the computer (OUCH that may hurt someday). 

Can someone please help me find out how to make this thing quit locking up everytime i select it and i may just be able to make it work, on my own?

---

### Post by wieman01 on 2006-10-10
I have got a WUSB54G as well & had the same problem initially. Then I decided to drop the native Linux driver (rtxxx) which happens to be fairly buggy, blacklist it, and install "ndiswrapper" instead. However, the current version of "nsidwrapper" that is in the repositories locks the system.

Solution was to download the latest version of "ndiswrapper" compile it deploy the native Windows driver. This works fine on the WUSB54G V4 and I even got WPA2 (RSN/AES) working.

If you need help installing the Windows driver, drop me a note.

---

### Post by spacecowboy706 on 2006-10-10
> Solution was to download the latest version of "ndiswrapper" compile it deploy the native Windows driver.

Where did u download "ndiswrapper" from and did u just use the windows drivers from the cd that came with the adapter (I still have it).

---

### Post by wieman01 on 2006-10-10
> **spacecowboy706 said:**
> .

Where did u download "ndiswrapper" from and did u just use the windows drivers from the cd that came with the adapter (I still have it).
You can try the version that's found in the repository (Synaptic) first. There is a nice little howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

The Windows driver is the one that comes on a CD normally shipped with the wireless adapter. The relevant files are *.INF and a few others. You'll see.

---

### Post by spacecowboy706 on 2006-10-10
I already have the one in the repo's and i tried using it this morning before i left for work along with the cd that came with the adapter (used the .inf) like u said and it locked up on me as well.

---

### Post by wieman01 on 2006-10-10
Alright... This is the version I am using. You need to compile it but it works great. I'll help you set it up if you have problems.

---

### Post by spacecowboy706 on 2006-10-11
Alright got it downloaded... and unzipped... what command do i enter to compile - or is that even what comes after unzipping it?

---

### Post by wieman01 on 2006-10-11
Unzip the files to:
> /usr/local
Then compile this way:
> cd /usr/local/your_version_of_ndiswrapper
> ./configure
> sudo make
> sudo make install
The follow the howto: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by spacecowboy706 on 2006-10-11
Alright I have messed this up already... here is a copy of the terminal... please tell me what i did wrong:

**myname@myname-desktop:~$** cd /usr/local

**myname@myname-desktop:/usr/local$** ls

bin  games  include  lib  man  *ndiswrapper-1.17*  sbin  share  src

**myname@myname-desktop:/usr/local$** cd /usr/local/ndiswrapper-1.17

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** ls

AUTHORS    driver   Makefile       ndiswrapper.spec  utils
ChangeLog  INSTALL  ndiswrapper.8  README            version

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** ./configure

bash: ./configure: No such file or directory

--------there doesn't seem to be a configure file in here------------
--------so i opened the other folders to see if it was in there------
------------------------ and it wasnt--------------------------------

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** cd /usr/local/ndiswrapper-1.17/utils

**myname@myname-desktop:/usr/local/ndiswrapper-1.17/utils$** ls

loadndisdriver.c  Makefile  ndiswrapper  ndiswrapper-buginfo

**myname@myname-desktop:/usr/local/ndiswrapper-1.17/utils$** ./configure 

bash: ./configure: No such file or directory

------------So i went back to the previous directory-----------------
------------and just skipped the ./configure and tried --------------
------to go straight to sudo make and that didnt work either---------

**myname@myname-desktop:/usr/local/ndiswrapper-1.17/utils$** cd /usr/local/ndiswrapper-1.17/

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** ls

AUTHORS    driver   Makefile       ndiswrapper.spec  utils
ChangeLog  INSTALL  ndiswrapper.8  README            version

myname@myname-desktop:/usr/local/ndiswrapper-1.17$ sudo make
Password:
make -C driver
make[1]: Entering directory `/usr/local/ndiswrapper-1.17/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/local/ndiswrapper-1.17/driver'
make: *** [all] Error 2

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$**

Help me out here please?

PS.... when i unzipped it i used: tar xvf ndiswrapper-1.17.tar.gz

---

### Post by wieman01 on 2006-10-11
Ok, no problem. The "configure" command is not required. So skip that one. Second, you need to install the "build-essential" which you have not. Hence this error message: [COLOR="Red"]"Can't find kernel build files in /lib/modules/2.6.15-27-386/build;"[/COLOR]

To install the "essentials" do this (without internet connection, so insert the CD please):
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
That will resolve this issue.

Then run these commands again:
> cd /usr/local/ndiswrapper-1.17/
> make
> sudo make install
That will do I guess.

---

### Post by wieman01 on 2006-10-11
And another thing: Make sure you uninstall the previous version of "ndiswrapper" via Synaptic.

---

### Post by spacecowboy706 on 2006-10-12
I fiugured that and did that long before i started trying to compile... trying your post now.. will post back in a second or two

---

### Post by wieman01 on 2006-10-12
> **spacecowboy706 said:**
> I fiugured that and did that long before i started trying to compile... trying your post now.. will post back in a second or two
That's actually more than a second or two... ;-) I'm on line now.

---

### Post by spacecowboy706 on 2006-10-12
Are we starting the dependency chain again :)  here is what i got:

**myname@myname-desktop:~$** [COLOR="Red"]sudo apt-cdrom add[/COLOR]
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [4d0f653xxxxxxxxxxx662bdxxxx201-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)'
This disc is called:
'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)'
Copying package lists...gpgv: Signature made Sat 05 Aug 2006 07:31:00 PM MDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.

**myname@myname-desktop:~$** [COLOR="Red"]sudo aptitude update[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:2 [http://soulmachine.net](http://soulmachine.net) unstable/ Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://soulmachine.net](http://soulmachine.net) unstable/ Release
Ign [http://soulmachine.net](http://soulmachine.net) unstable/ Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://soulmachine.net](http://soulmachine.net) unstable/ Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]
99% [8 Packages bzip2 0] [Connecting to archive.canonical.com] [Waiting for headbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]
99% [Connecting to archive.canonical.com] [Waiting for headers] [Connecting to ubzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get:10 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Fetched 12B in 26s (0B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

**myname@myname-desktop:~$** [COLOR="Red"]sudo aptitude install build-essential[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  acidrip amarok amarok-xine cpio ffmpeg gdb gnomebaker konversation kopete
  libmusicbrainz4c2a libssl-dev libssl0.9.7 libssl0.9.8 libxine-dev
  libxine-main1 openssh-client openssl python2.3 python2.4
  python2.4-examples python2.4-gdbm python2.4-minimal python2.4-tk
  readahead ssh-askpass-gnome
The following NEW packages will be installed:
  build-essential
0 packages upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B/6826B of archives. After unpacking 49.2kB will be used.
Writing extended state information... Done
Selecting previously deselected package build-essential.
(Reading database ... 195501 files and directories currently installed.)
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up build-essential (11.1) ...

**myname@myname-desktop:~$** [COLOR="Red"]cd /usr/local/ndiswrapper-1.17/[/COLOR]

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]ls[/COLOR]

AUTHORS    driver   Makefile       ndiswrapper.spec  utils
ChangeLog  INSTALL  ndiswrapper.8  README            version

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$**[COLOR="Red"] make[/COLOR]
make -C driver
make[1]: Entering directory `/usr/local/ndiswrapper-1.17/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/local/ndiswrapper-1.17/driver'
make: *** [all] Error 2

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$**

Same as last time right.... I wasnt sure what CD to put in so i first tried a blank disc and that didnt work, so i then tried the Ubuntu disc and that was how i got the above.... was i supposed to use a different disk? or am i missing some other dependency or something?

---

### Post by wieman01 on 2006-10-12
Aeh... not a blank CD please. We need the Ubuntu Live CD that you have used in the first place to install Ubuntu on your PC.

How does that command finish? Can you post the whole section please?
> sudo aptitude install build-essential

---

### Post by wieman01 on 2006-10-12
Ok, try this again. You need to install the kernel source:
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-source-`uname -r`
That will install the source files for your version of the kernel. You need those to compile "ndiswrapper". Please also post the output.

---

### Post by spacecowboy706 on 2006-10-12
Same results again... Here is the entire terminal copied from start to finish:

**myname@myname-desktop:~$** [COLOR="Red"]cd /usr/local/ndiswrapper-1.17/[/COLOR]

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]sudo apt-cdrom add[/COLOR]
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [4d0f65347bf45d44fc5a662bdae80201-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)'
Copying package lists...gpgv: Signature made Sat 05 Aug 2006 07:31:00 PM MDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]sudo aptitude update[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
99% [5 Packages bzip2 0] [Connecting to archive.ubuntu.com] [Connecting to archibzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:7 [http://soulmachine.net](http://soulmachine.net) unstable/ Release.gpg [189B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://soulmachine.net](http://soulmachine.net) unstable/ Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://soulmachine.net](http://soulmachine.net) unstable/ Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://soulmachine.net](http://soulmachine.net) unstable/ Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 29.8kB in 6s (4328B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]sudo aptitude install linux-source-`uname -r`[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-source-2.6.15-27-386"
The following packages have been kept back:
  acidrip amarok amarok-xine cpio ffmpeg gdb gnomebaker konversation kopete
  libmusicbrainz4c2a libssl-dev libssl0.9.7 libssl0.9.8 libxine-dev
  libxine-main1 openssh-client openssl python2.3 python2.4
  python2.4-examples python2.4-gdbm python2.4-minimal python2.4-tk
  readahead ssh-askpass-gnome
0 packages upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]ls[/COLOR]
AUTHORS    driver   Makefile       ndiswrapper.spec  utils
ChangeLog  INSTALL  ndiswrapper.8  README            version

**myname@myname-desktop:/usr/local/ndiswrapper-1.17$** [COLOR="Red"]make[/COLOR]
make -C driver
make[1]: Entering directory `/usr/local/ndiswrapper-1.17/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/local/ndiswrapper-1.17/driver'
make: *** [all] Error 2

[B]myname@myname-desktop:/usr/local/ndiswrapper-1.17$
[/B]

During the part where u have me enter: sudo aptitude install linux-source-`uname -r` <--- Sisce u didn't tell me too I left the `uname -r` exactly as u posted it... should i insert my username in here?

---

### Post by spacecowboy706 on 2006-10-12
I hate to do this to you....... I just got a new computer today (got it for free from a friend and its twice as good as this old one is, in processor speed, ram, video card, everything) and this old clunker is going to the kids room where the usb wireless isnt needed...

I will be swapping hard drives .... moving the 250 GB windows XP drive (from  my wifes pc) to the new computer and formatting it then reinstalling Ubuntu to that, moving the 80 GB Ubuntu drive (from my pc) to my wifes pc and reformatting and installing windows xp to that (she doesnt like Linux) and lastly moving the 40 GB hd from the new computer to this old computer for the kids. 

So since im reformatting and reinstalling everything that makes this thread kinda pointless... I do appreciate your help though and after i get done with all the Drive swapping and installing this weekend i am sure you probably will hear from me again. Thanks for all your help.

---

### Post by wieman01 on 2006-10-12
> **spacecowboy706 said:**
> So since im reformatting and reinstalling everything that makes this thread kinda pointless... I do appreciate your help though and after i get done with all the Drive swapping and installing this weekend i am sure you probably will hear from me again. Thanks for all your help.
Don't worry. I'll be here & see you next time.

BTW: The `uname -r` stands for your kernel version. You did exactly right in that you copied & pasted just like that. :-) However, there was an error message saying that package "linux-source-2.6.15-27-386" could not be found. This is probably due to the fact that you have a slight "source.list" issue. That's what the previous command/output has complained about. But we'll settle this after your fresh installation.

---

### Post by JawsThemeSwimming428 on 2006-10-12
How would I go about installing the Windows driver and what version of Ndiswrapper should I use?

---

### Post by wieman01 on 2006-10-13
> **JawsThemeSwimming428 said:**
> How would I go about installing the Windows driver and what version of Ndiswrapper should I use?
Try the current version of "ndiswrapper" that is found in the repositories (Synaptic). If you have the same issue as described in there (PC lockup) then we try to compile the latest version. 

Fire up Synaptic and install:

1. ndiswrapper-utils
2. ndisgtk

Let me know when you have done that.

_**EDIT:**_
Please get the right Windows drivers for your wireless adapter in the meantime. They usually come in an .EXE file which is a simple ZIP archive containing a number of other files (*.INF, *.CAB, etc.).

---

### Post by carusoswi on 2008-02-24
> **wieman01 said:**
> Ok, no problem. The "configure" command is not required. So skip that one. Second, you need to install the "build-essential" which you have not. Hence this error message: [COLOR="Red"]"Can't find kernel build files in /lib/modules/2.6.15-27-386/build;"[/COLOR]

To install the "essentials" do this (without internet connection, so insert the CD please):

That will resolve this issue.

Then run these commands again:



That will do I guess.

I see you are running Gutzy.  Are the above instructions valid for 7.10?  Also, how do I extract the .tar to the dirctory (local) that you suggest.  I can extract to the directory to which ndis is downloaded (/tmp on my machine), but I cannot copy to local as I am told I do not have permission to do that.

Your advise would be appreciated.

Thanks.

Caruso

---

### Post by wieman01 on 2008-02-24
I am running Gutsy which is version 7.10. So essentially, yes, it is valid.

If the error message says you don't have the permission you need to run the commands with 'sudo', e.g.:
> sudo cp file /destination
Enter you password when prompted. That's it. Any questions, please post here.

---

