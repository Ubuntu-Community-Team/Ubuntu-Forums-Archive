---
title: "CD/DVD not recognised"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Indigo340 on 2010-08-02
I have had this problem since I installed Lucid about 6 weeks ago, there was no problem with Karmic. I have also been trying Mint 9 which also shows the problem.

The CD/DVD drive _is_ showing up in Nautilus but no information is listed. I _can boot_ from the drive but no media is recognized in Linux. Using Device Manager, I can see all the relevant information about the drive and using lspci in Terminal I can see that it's correctly  installed and ready but still will not mount. I cannot access it at all with Linux.

I have been waiting and scanning the forums, blogs and other sites to see if a solution appears but nothing yet. Any suggestions ?

---

### Post by mastablasta on 2010-08-02
did you upgrade or fresh install? i upgraded and then upgraded computer and it seems some drivers needed a reinstall as they didnt' work propperly. maybe some config files are not read properly... just guessing here...

---

### Post by Indigo340 on 2010-08-02
Fresh install.

When Nautilus is open, I can view the icon for the CD/DVD drive until I insert a disc then the icon disappears, it reappears when the disc is removed.

---

### Post by Indigo340 on 2010-08-03
Surely I'm not the only person with this problem, I have read many threads from people with similar probs but not this specific one.

[CENTER]Sony Vaio VGN-SZ2HP laptop.

Matshita DVD-RW, CD-RW drive.
Model: UJ-842D
Device File: /dev/sr0
Firmware version: 1.01
Connection Type: Internal
Remevable Media: Yes (ejectable)
Media Compatibility: CD-ROM/CD-R/CD-RW/DVD-ROM/DVD+R/DVD+R DL/DVD+RW/DVD-R/DVD-RW
Max Read Speed: 28x (33.87 MBps)
Max Write Speed: 28x (33.87 MBps)
Media Capacity: -
Partitioning: -[/CENTER]

Is it possible to update firmware ? Is it possible it is on the wrong port, how do I check and change ports ?
The fact that I can boot from CD-ROM proves that the drive works at least at a basic level, it obviously can read data and is properly set-up but why does it not work in Linux ?

I have also noticed that I have no entry in the fstab file for the cdrom or dvd at all
Here it is;

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=00563ab6-53b4-4c1c-b976-87639b35f664 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=60d4582d-53b3-4ec9-ae8a-e03fae3b45a0 none            swap    sw              0       0



And here is the output from running lshw

 *-cdrom
                description: DVD writer
                product: UJ-842D
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

---

### Post by anewguy on 2010-08-03
Is it possible that somehow permissions got messed up, so when the drive is mounted perhaps you have no permissions to it?

I would try this:

- put a disk in the drive
- open a terminal window (Applications/Accessories/Terminal)
- type:

sudo nautilus <press enter>

Now look and see if you can see the drive and disk.  If so, it would indicate a permissions problem.

Post back the result.

Dave ;)

---

### Post by Indigo340 on 2010-08-03
Thanks for your response Dave. When I enter "sudo nautilus" it opens a file browser with very few files. I cannot find anything on this laptop. In the left hand pane there are 4 locations, 'Desktop, File System, Network and Trash', the only link that contains anything is 'File System' which also contains a folder called 'CDROM' but that contains nothing. I have tried Ctrl H, still nothing.

Strangely I was using terminal and entered 
ls -l /dev/sr* /dev/dvd* 

Which mounted the drive and I was able to view a DVD, but after I closed Terminal it stopped working and will not respond again

---

### Post by anivegmin on 2010-08-03
Similar problem here.

Although quite often the cd drive and dvd drive will both mount discs immediately after booting the system. But then after some random length of time they will either unmount or wont mount a newly inserted disc.

As I write this post both my drives are inaccessible.

sudo mount /dev/cdrom /media/cdrom

mount: mount point /media/cdrom does not exist

Both drives are listed in Disk Utility -

TSSTcorp CDRW/DVD TSH492B
HL-DT-ST CD-RW GCE-8320B

Both drives work fine with Windows XP.

I have had this problem since installing 10.04 in April. I have posted on various threads on this forum and still not solved it.

---

### Post by Indigo340 on 2010-08-04
Anewguy, If I click the icon for the CD/DVD drive in the 'Computer File Browser' and click on 'Properties', under the 'Permissions' tab it says, "Permissions for CD/DVD drive could not be determined"  I think this could be the cause, how do I go about changing permissions and what should I change it to ???

---

### Post by anivegmin on 2010-08-05
Sorry to butt in on this thread again but I have solved my long standing CD/DVD drive mounting problems.

A while back on another thread someone suggested installing the latest kernel (2.6.34). I tried this but no luck.

Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. This has solved my mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

---

### Post by Indigo340 on 2010-08-05
Thanks I have tried various combinations of "http://ppa:kernel-ppa.com/ppa/ubuntu lucid main" etc but it won't let me add this as a source, obviously I am missing something but don't know what to do.

Software sources/Other software/Add source/ or is there a better way with Terminal???



I think the contents of this thread [http://ubuntuforums.org/showthread.php?t=1545946&highlight=update+kernel   ]("http://ubuntuforums.org/showthread.php?t=1545946&highlight=update+kernel")might have the answer, I am trying it now.

---

### Post by anivegmin on 2010-08-05
Yeah - Software sources/Other software/Add

Then type "ppa:kernel-ppa/ppa" into the dialogue box (without quotes). Should work.

Otherwise in a terminal type the following -

"sudo add-apt-repository ppa:kernel-ppa/ppa"

Again without the quotes.
Good luck.

---

### Post by anivegmin on 2010-08-05
Make sure you choose the correct 3 packages for you system in Synaptic.

x86 packages for 32 bit
x86/x86_64 packages for 64 bit

---

### Post by anewguy on 2010-08-06
One of the things the newer kernel fixes is a problem with hot-mount devices, such as USB external disk drives, etc..  The current kernel won't recognize/mount correctly any of those devices unless you have them plugged in to a USB port at boot time.  It's a known bug documented on launchpad.  I tried updating to the .35 kernel but ended up with a mess, including wireless that could no longer be made to work no matter what.  That's why I just removed Ubuntu from my desktop and only have it on my netbook.  When the newer kernel is rolled out as part of standard ubuntu then I will probably install ubuntu again on my desktop.  I use an external USB connected hard drive and an external USB connected DVD/RW drive, and HATE having to reboot just because I decide to turn the device on and use it.

Dave

---

### Post by anivegmin on 2010-08-06
Sorry you're still having problems. All my external USB devices, including an external hard drive, work fine.

Not sure what else to suggest. I was 3 months without properly working internal CD/DVD drives and 2.6.35 has fixed this problem for me. Everything else is working fine.

Hop you can find some solutions.
Good luck.

---

### Post by cjack007 on 2010-08-06
this also happened to me
firstly i would recommend that you disable automatic login if you have you can use ubuntu tweak for that.

---

### Post by Indigo340 on 2010-08-06
It now appears that I have 2.6.35 installed but am still using 2.6.32, how do I enable it? There is no option in boot menu to use 2.6.35

I have searched the forums and come up with this thread [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835") but it seems a little old, is the information too old ?

---

### Post by Indigo340 on 2010-08-06
Now I have the option to boot into 2.6.35, after a couple of reboots and boots into Linux Mint 9, and it appears to function normally (external USB devices are normal) but still the DVD is not recognized.

By the way I live in Hong Kong although I am English, hence the delay in replying, but it is possible that the disc I  am using is a copy, would that make a difference ?

---

### Post by anivegmin on 2010-08-06
Have you installed "restricted-extras" and "libdvdcss" ?

I think Mint might already have restricted extras but you can install from Software Center or Synaptic.

Install "libdvdcss" (needed for DVD playback) with the following command in a terminal -

sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by rgrauer on 2010-08-06
> **anivegmin said:**
> Sorry to butt in on this thread again but I have solved my long standing CD/DVD drive mounting problems.

A while back on another thread someone suggested installing the latest kernel (2.6.34). I tried this but no luck.

Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. This has solved my mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

That worked for me.--Thank you.
IBM T23 ubuntu 10.04

---

### Post by Indigo340 on 2010-08-06
I am beginning to run out of patience on this issue, I have spent a long time trying to figure it out and ask the right questions and it seems to be getting me nowhere. 
I have Ubuntu Kernel 2.6.35-14 installed and can boot from it in Grub Boot-loader, I have all the necessary drivers and players and codecs installed, many thanks to those who helped and offered advice but still can not play CD or DVD and the drive still appears to not be recognised by the system. I am happy that this thread is helping other people with the same problems that was my intention too but why is it not helping me ?
As I said in my opening post, the problem only started when I installed 10.04, it did not happen with 9.10 so maybe that is the answer, maybe I must go back to Karmic, which I am very reluctant to do but if it means I can watch movies on DVD's or CD's then I will install a third OS on my laptop just for that purpose.
Incidentally I have the same problem with Mint 9 but that is based on Ubuntu 10.04 so that would explain it. 
I think it's time to call it a day and go to plan B, install Karmic in another partition just for watching movies.
Thanks again guys, I will leave this thread open for a while just in case anyone has a Eureka moment and I will watch it for as long as possible but it seems I have done as much as can be done and should call it a day on this issue. Thanks very much for all your help and advice. Ian

---

### Post by Indigo340 on 2010-08-07
Just an update, I have just had 3 software updates for Mint 9 and immediately after that the DVD auto mounted and I was able to watch the movie !
I don't know what the updates were but it appears to have done the trick. Linux Mint 9 is booting from Kernel 2.6.32 and I have not made any adjustments or altered anything in Terminal since I installed it.
I now don't need to install Karmic as a third OS just to watch movies and use the DVD drive !
It looks as though I will be using Mint much more that Lucid now and I only installed it as a test to see what it was like. I am not a fan of the interface and menu system of Mint, I love the simplicity of Ubuntu but Mint appears to be a much more 'complete' package that I will recommend to anyone looking for a viable alternative to Microsoft.

---

### Post by Indigo340 on 2010-08-08
I spoke too soon. It appears that I can only play DVD's at random times, in fact I have only managed it a couple of times over the past few days. (using Mint 9) so my problems are not over yet.

---

