---
title: "No sound on new install"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Garthhh on 2010-04-17
I'm on a PentiumIV gateway 7330 gz notebook
the cd/dvd stopped working several years ago, 
bios doesn't support boot from USB
The HDD is a brand new WD160gb
I used a HDDadapter & did a 8.04install directly to the HDD on my desktop machine
I did a update from a 9.10 cd
reinstalled HDD in the notebook

no sound
uninstalled the file as per the comprehensive sound sticky
when I go to reinstall, prompts me to put in the cd, which I can't [no player]
I have a new 8gb usb stick, won't mount [either computer]

when I check up dates I have libgnomepanel2.24-cil(new install) pending, also asking for CD...

---

### Post by Jeanke on 2010-04-17
You could try to install a disk emulation program (e.g. gmountiso, gisomount, kiso, ...) so you can mount the image of the cd virtually.

Or just mount the image ([http://www.go2linux.org/mounting-ISO-images-in-Linux]("http://www.go2linux.org/mounting-ISO-images-in-Linux")) but I'm not sure if this will be recognized as a cd.

---

### Post by Garthhh on 2010-04-17
> **Jeanke said:**
> You could try to install a disk emulation program (e.g. gmountiso, gisomount, kiso, ...) so you can mount the image of the cd virtually.

Or just mount the image ([http://www.go2linux.org/mounting-ISO-images-in-Linux](http://www.go2linux.org/mounting-ISO-images-in-Linux)) but I'm not sure if this will be recognized as a cd.


how can I bring the missing packages onboard?

gonna go poke around & see if I can get the 2 unbuntu machines talking to each other

I'm downloading the 9.10 torrent right now, since I don't have any thing to install either way

how would I tell synaptic to find them once they exist here?

---

### Post by Jeanke on 2010-04-17
Ok, so to make things clear...

You installed Ubuntu 8.04 on your hard drive while it was connected to your desktop. Then you upgraded to Ubuntu 9.10 from a cd (still using your desktop), does this mean you performed a fresh install?

After Ubuntu 9.10 was installed on the hard drive you installed the hard drive again in your notebook.
Now on your notebook Ubuntu works fine except for your sound (to me it sounds even lucky this is the only thing that is not working as the hardware you installed Ubuntu with is different from the one you are running it).

Which actions did you perform after that exactly?

---

### Post by Garthhh on 2010-04-17
> **Jeanke said:**
> Ok, so to make things clear...

You installed Ubuntu 8.04 on your hard drive while it was connected to your desktop. Then you upgraded to Ubuntu 9.10 from a cd (still using your desktop), does this mean you performed a fresh install?

After Ubuntu 9.10 was installed on the hard drive you installed the hard drive again in your notebook.
Now on your notebook Ubuntu works fine except for your sound (to me it sounds even lucky this is the only thing that is not working as the hardware you installed Ubuntu with is different from the one you are running it).

Which actions did you perform after that exactly?

yes that is the path I took

I then went to this sticky thread:
[http://ubuntuforums.org/showthread.php?t=205449]("http://http://ubuntuforums.org/showthread.php?t=205449")

I got to 

_**[SIZE=3]Getting the ALSA drivers from a *fresh* kernel[/SIZE]**_[SIZE=2]

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall **Ubuntu**. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.[/SIZE][SIZE=2]

A faster way, is to just remove the problematic packages and reinstall them cleanly.[/SIZE] [SIZE=2]

(1) Remove these packages     Code:
     sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
 [/SIZE][SIZE=2]
(2) Reinstall those same packages[/SIZE][SIZE=2]
     Code:
     sudo apt-get install linux-sound-base alsa-base alsa-utils 
 [/SIZE]when I went to reinstall, I got the prompt to insert the cd
When I checked for updates, same problem
when I go to synaptic for the missing package {libgnomepanel2.24-cil(new install)}
prompt for cd again

I have the 9.10 iso here & unpacked

I went to look for gpart in hopes of reformatting the stick, same problem...

---

### Post by Jeanke on 2010-04-18
Alright,

First of all, do you have an internet connection on your notebook?
If so, did you try to install a disk emulator (using synaptic) and mount the 9.10 iso before:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by Garthhh on 2010-04-18
> **Jeanke said:**
> Alright,

First of all, do you have an internet connection on your notebook?
If so, did you try to install a disk emulator (using synaptic) and mount the 9.10 iso before:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

I installed gisomount 
opened it, mounted the 9.10 iso
ran terminal w/above code
still asking for cd
I do have internet, I'm using the notebook right now

---

### Post by Jeanke on 2010-04-18
Try:

```
sudo gedit /etc/apt/sources.list
```

Locate the line starting with: 
deb cdrom
change this line to:
#deb cdrom
Save the file and close.

after:

```
sudo apt-get update
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by Garthhh on 2010-04-18
> **Jeanke said:**
> Try:

```
sudo gedit /etc/apt/sources.list
```Locate the line starting with: 
deb cdrom
change this line to:
#deb cdrom
Save the file and close.

after:

```
sudo apt-get update
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

[B]I got sources list, 
the output
[/B]
# added by the release upgrader
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
[B]
So I have this now[/B]?

sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Jeanke on 2010-04-18
Did you adjust the sources.list file and put a "#" in front of all lines starting with "deb cdrom" (in the output there are still 2 lines starting with "deb cdrom")?

The messages

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

usually mean there is another synaptic running.

So:
Make sure no synaptic is running.
Make sure that in the sources.list file all lines starting with "deb cdrom" are preceded with an "#".
Same as line: ***# deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted***

run:

```
sudo apt-get update
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by Garthhh on 2010-04-18
> **Jeanke said:**
> Did you adjust the sources.list file and put a "#" in front of all lines starting with "deb cdrom" (in the output there are still 2 lines starting with "deb cdrom")?

The messages

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```usually mean there is another synaptic running.

So:
Make sure no synaptic is running.
Make sure that in the sources.list file all lines starting with "deb cdrom" are preceded with an "#".
Same as line: ***# deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted***

run:

```
sudo apt-get update
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

Ok I got to run the code
failed & gave me a message like something else was running, so I did a restart
all was well
I was able to run the update manager [yea]
& when installing Gparted with synaptic
Got[IMG]file:///tmp/moz-screenshot.png[/IMG]

still no sound?
getting some where though

---

### Post by lidex on 2010-04-18
The first thing to check for sound issues in karmic is this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by d_skillz on 2010-04-18
I just tried a 10.04 install and no audio has been coming from my soundcard either. Will try these solutions though or wait till the final release on the 29th of April. This is by far the best release I have ever used.

---

### Post by Garthhh on 2010-04-18
> **lidex said:**
> The first thing to check for sound issues in karmic is this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

I get to here:

h[ttps://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")


& I get:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

same fault I get when trying to install Gparted
So I run the code:
sudo dpkg --configure -a

which yields this error:

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
cpio: ./etc/modprobe.d/blacklist-oss.dpkg-bak: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by lidex on 2010-04-18
Try this command:
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Garthhh on 2010-04-18
> **lidex said:**
> Try this command:
```
sudo aptitude update && sudo aptitude dist-upgrade
```

More progress

now the error is:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Current status: 11 updates [+9].
garthhh@garthhh-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
cpio: ./etc/modprobe.d/blacklist-oss.dpkg-bak: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by lidex on 2010-04-18
OK try:
```
sudo apt-get -f install
```

---

### Post by Garthhh on 2010-04-18
> **lidex said:**
> OK try:
```
sudo apt-get -f install
```

& the error is:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
garthhh@garthhh-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
cpio: ./etc/modprobe.d/blacklist-oss.dpkg-bak: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by lidex on 2010-04-19
Try this:
```
sudo touch /etc/modprobe.d/blacklist-oss.dpkg-bak
```
Then this:
```
sudo dpkg --configure -a
```

---

### Post by lidex on 2010-04-19
Some references:
[http://ubuntuforums.org/showthread.php?t=553861]("http://ubuntuforums.org/showthread.php?t=553861")
[http://ubuntuforums.org/showthread.php?t=252762]("http://ubuntuforums.org/showthread.php?t=252762")
[http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken]("http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken")
[http://ubuntuforums.org/showthread.php?t=186672]("http://ubuntuforums.org/showthread.php?t=186672")
[http://ubuntuforums.org/showthread.php?t=1113166]("http://ubuntuforums.org/showthread.php?t=1113166")

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> Try this:
```
sudo touch /etc/modprobe.d/blacklist-oss.dpkg-bak
```Then this:
```
sudo dpkg --configure -a
```

No such File

garthhh@garthhh-desktop:~$ sudo touch /etc/modprobe.d/blacklist-oss.dpkg-bak
touch: cannot touch `/etc/modprobe.d/blacklist-oss.dpkg-bak': No such file or directory
garthhh@garthhh-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
cpio: ./etc/modprobe.d/blacklist-oss.dpkg-bak: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> Some references:
[http://ubuntuforums.org/showthread.php?t=553861](http://ubuntuforums.org/showthread.php?t=553861)
[http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762)
[http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken](http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken)
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
[http://ubuntuforums.org/showthread.php?t=1113166](http://ubuntuforums.org/showthread.php?t=1113166)

I'm fine if I have to do a new install
I would think my chances of success would be improved if I can do it with the hard drive installed in this notebook

I don't seem to be able to get the usb stick working

the usb creator [ext1] & gparted [ext3] seem to have different ideas about what format the stick actually is.  I had the same problem on my other computer [which by the way it acts with my external hdd {very slow} isn't on usb2.0?]
the creator won't reformat at all

---

### Post by lidex on 2010-04-19
The hard way then I guess. Right click on your desktop, select "Create Document -> Empty file". Click on the icon to select file and press F2. Rename the file:
```
blacklist-oss.dpkg-bak
``` Now in a terminal:
```
cd ~/Desktop
sudo mv blacklist-oss.dpkg-bak /etc/modprobe.d/
sudo dpkg --configure -a
```

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> The hard way then I guess. Right click on your desktop, select "Create Document -> Empty file". Click on the icon to select file and press F2. Rename the file:
```
blacklist-oss.dpkg-bak
``` Now in a terminal:
```
cd ~/Desktop
sudo mv blacklist-oss.dpkg-bak /etc/modprobe.d/
sudo dpkg --configure -a
```

OK I'm guessing you meant for me to rename the 9.10 iso...
blacklist-oss.dpkg-bak

when I run terminal:

garthhh@garthhh-desktop:~/Desktop$ cd ~/Desktop
garthhh@garthhh-desktop:~/Desktop$ sudo mv blacklist-oss.dpkg-bak /etc/modprobe.d/
mv: cannot stat `blacklist-oss.dpkg-bak': No such file or directory
garthhh@garthhh-desktop:~/Desktop$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
cpio: ./etc/modprobe.d/blacklist-oss.dpkg-bak: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
dpkg: subprocess installed post-installation script returned error exit status 1
garthhh@garthhh-desktop:~/Desktop$

---

### Post by lidex on 2010-04-19
No. I wanted you to create an empty file on your desktop and rename it and move to that directory.

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> No. I wanted you to create an empty file on your desktop and rename it and move to that directory.

I get this then

mv: cannot stat `blacklist-oss.dpkg-bak': No such file or directory

---

### Post by lidex on 2010-04-19
Do you have a file on your desktop named "blacklist-oss.dpkg-bak"?

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> Do you have a file on your desktop named "blacklist-oss.dpkg-bak"?

yes
there's nothing in it
but yes there is a file named
blacklist-oss.dpkg-bak
I deleted it & did it again
terminal looks like this now:
garthhh@garthhh-desktop:~/Desktop$ sudo mv blacklist-oss.dpkg-bak /etc/modprobe.d/
mv: cannot stat `blacklist-oss.dpkg-bak': No such file or directory
garthhh@garthhh-desktop:~/Desktop$ sudo dpkg --configure -a
garthhh@garthhh-desktop:~/Desktop$

---

### Post by lidex on 2010-04-19
Gettin' messy. Open nautilus as root:
```
gksu nautilus
```
Navigate to /etc/modprobe.d/
Now drag-and-drop or copy-and-paste that file from your desktop into etc/modprobe.d/ directory

---

### Post by Garthhh on 2010-04-19
> **lidex said:**
> Gettin' messy. Open nautilus as root:
```
gksu nautilus
```Navigate to /etc/modprobe.d/
Now drag-and-drop or copy-and-paste that file from your desktop into etc/modprobe.d/ directory

ran the code again after I put the empty blacklist-oss.dpkg-bak file in the modprobe.d file
same result

I went in through the file browser afterwards, just to make sure I could find it & get some understanding of where things are
filesystem/ect/modpro.d/blacklist-oss.dpkg-bak

---

### Post by Jeanke on 2010-04-20
In my opinion you should perform a fresh install install of Ubuntu 9.10 (or wait untill 10.04 is released and then perform fresh install)
If I understand correctly you "upgraded" Ubuntu 8.04 directly to 9.10 using a cd? (in output of sources.list the hardy heron cd is still listed...)

As per upgrade notes [https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes") you should never skip a version while upgrading.

Is there a reason why you installed Ubuntu 8.04 first before goin to 9.10?

---

### Post by Garthhh on 2010-04-20
> **Jeanke said:**
> In my opinion you should perform a fresh install install of Ubuntu 9.10 (or wait untill 10.04 is released and then perform fresh install)
If I understand correctly you "upgraded" Ubuntu 8.04 directly to 9.10 using a cd? (in output of sources.list the hardy heron cd is still listed...)

As per upgrade notes [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) you should never skip a version while upgrading.

Is there a reason why you installed Ubuntu 8.04 first before goin to 9.10?

When I did a direct 9.10 install on my desktop machine, it was as if I were just using a live cd, when I remove the cd the install disappears.  I happened to have left the 9.10 cd in the drive & was prompted to do an upgrade, so I did. no weirdness on that machine at all.  since I was doing the install by using a 2.5-3.5 hdd adapter, I used the same method.

I would like to get my flash drive [USB] working as an install option.
doesn't ssem to work on either machine. I tryed reformatting with the creator & using Gparted, no go
 any suggestions?

Now that I have a working OS on the notebook, I'm not limited to installing the HDD in the desktop to do an install.

how long till 10.4 is out of beta?

---

### Post by Garthhh on 2010-04-21
> **lidex said:**
> The first thing to check for sound issues in karmic is this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

I did what I think is a clean install of 9.10, by installing my notebook HDD in my desktop machine & using a 9.10 cd I got using bit torrent,  I increased my ram [desktop] to 1gb which seemed to make the difference.

when I got to the end I reinstalled the hdd in the notebook, before the restart
did all the updates
ran the code you gave me from posts #15 & #17
& the wiki

packages are going in
but still no sound

---

### Post by lidex on 2010-04-21
> **Garthhh said:**
> I would like to get my flash drive [USB] working as an install option.
doesn't ssem to work on either machine. I tryed reformatting with the creator & using Gparted, no go
 any suggestions?

Unetbootin (in the repos) [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/"):
```
UNetbootin allows for the installation of various Linux/BSD distributions to a
partition or USB drive, so it's no different from a standard install, only it
doesn't need a CD. It can create a dual-boot install, or replace the existing
OS entirely.
```

> how long till 10.4 is out of beta?
I think it's the 28th.

---

### Post by Garthhh on 2010-04-22
> **lidex said:**
> Unetbootin (in the repos) [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/):
```
UNetbootin allows for the installation of various Linux/BSD distributions to a
partition or USB drive, so it's no different from a standard install, only it
doesn't need a CD. It can create a dual-boot install, or replace the existing
OS entirely.
```
I think it's the 28th.

Thanks
I do need to be able to do fresh installs

& another 6 months until it would be considered lts?

any hope for what I got going now?

---

### Post by ftwrobert on 2010-05-13
I've also got a Gateway 7330 gz Laptop, running 10.04. If you refer to the original page you posted here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and scroll to the '[SIZE=1]Using alsamixer[/SIZE][SIZE=3][SIZE=2]'[/SIZE] [SIZE=1]and follow the instructions there it will fix the problem. It seems as though a few things are muted there that when unmuted the sound begins to work.[/SIZE]
[/SIZE]

---

### Post by Garthhh on 2010-05-13
> **ftwrobert said:**
> I've also got a Gateway 7330 gz Laptop, running 10.04. If you refer to the original page you posted here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and scroll to the '[SIZE=1]Using alsamixer[/SIZE][SIZE=3][SIZE=2]'[/SIZE] [SIZE=1]and follow the instructions there it will fix the problem. It seems as though a few things are muted there that when unmuted the sound begins to work.[/SIZE]
[/SIZE]

Thanks good to hear there is hope
I ran through a different procedure & never got there on 9.10
does your wireless work?

if I ever get a working 10.04 install I will do that 
I'm working on this procedure
[https://help.ubuntu.com/community/Installation/FromLinux]("http://https://help.ubuntu.com/community/Installation/FromLinux")
not having a working cd certainly slows me down
I don't think I have the boot/grub file quite right....

---

### Post by ftwrobert on 2010-05-15
Yes it does, well... after a few updates. You'll need to plug in with an ethernet cable and download the proper drivers. Ubuntu prompts you do to so and finds the correct ones right off.

Everything is working the way I expect it to. That is, I only use wifi, sound, and the usb ports, and ofcourse the monitor, keyboard and touch pad works. 

Also, my dvd drive died a long time ago, not that i need it, but i suspect it should be just dandy in regards to drivers.

Good Luck!

---

### Post by Garthhh on 2010-05-15
> **ftwrobert said:**
> Yes it does, well... after a few updates. You'll need to plug in with an ethernet cable and download the proper drivers. Ubuntu prompts you do to so and finds the correct ones right off.

Everything is working the way I expect it to. That is, I only use wifi, sound, and the usb ports, and ofcourse the monitor, keyboard and touch pad works. 

Also, my dvd drive died a long time ago, not that i need it, but i suspect it should be just dandy in regards to drivers.

Good Luck!

the wireless has never worked, always used ethernet cable

I haven't been able to get a working 10.04 install yet
I just was able to get unetbootin working [understand] this morning
10.04 won't run in live mode
I'm on mint8 in live right at the moment
can't quite get it to install yet

your story does give me hope

---

