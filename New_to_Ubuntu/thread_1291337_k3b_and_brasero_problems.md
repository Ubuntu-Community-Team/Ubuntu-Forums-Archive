---
title: "k3b and brasero problems"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by natedogg23 on 2009-10-14
i cant get k3b or brasero to burn discs. k3b always says cdrecord has no permission to open device and brasero knows theres a blank disc in but says it has 0 bites free. any idea what is going on?

---

### Post by jbrown96 on 2009-10-14
Are you part of the cdrom group? In a terminal, ```
groups $USER
``` If you are not, then run this command ```
sudo usermod -aG $USER cdrom
``` You will need to logout for the changes to take affect.

---

### Post by natedogg23 on 2009-10-15
what is the cdrom group? this is my error msg; cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CD-RW GCE-8160B '
Revision       : '2.11'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
FIFO size      : 12582912 = 12288 KB

---

### Post by RichardLinx on 2009-10-15
Try run k3b in root mode. Open a terminal and type:
```
sudo k3b
```
This should eliminate the permission problem. Do you have multimedia codecs installed?

---

### Post by natedogg23 on 2009-10-15
i really dont know what those are or how to install them if they arent already

---

### Post by lavinog on 2009-10-15
> **richardlinx said:**
> try run k3b in root mode. Open a terminal and type:
```
sudo k3b
```
this should eliminate the permission problem. Do you have multimedia codecs installed?

no!!!
This is how things can get broken.

do what jbrown96 said.

---

### Post by RichardLinx on 2009-10-15
> **natedogg23 said:**
> i really dont know what those are or how to install them if they arent already

They're multimedia codecs for Ubuntu. (ie. So you can play most multimedia formats in Ubuntu.) There something you probably want. Have you found that you can;t play DVD's in Ubuntu, or MP3 files? That means you don't have multimedia codecs installed.

Open a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```

Follow this guide for the rest: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by lisati on 2009-10-15
> **natedogg23 said:**
> what is the cdrom group? 

Every user of a Unix/Linux system can belong to groups of users on a particular machine with special permissions and privileges. CDROM is such a group that you can belong to that relates to using the CD/DVD drive.

---

### Post by RichardLinx on 2009-10-15
> **lavinog said:**
> no!!!
This is how things can get broken.

do what jbrown96 said.

I don't think it's such a big deal when it comes to running a CD burning application. What's the biggest risk? Isn't the security risk the same as it is running "sudo" before an update?

---

### Post by natedogg23 on 2009-10-15
well crap how do i un root it now? and how do i know which code from jbrown to use? this is what happened in root instead of permission denied; Probably a buffer underrun occured  Please try a lower burn speed

---

### Post by natedogg23 on 2009-10-15
> **RichardLinx said:**
> They're multimedia codecs for Ubuntu. (ie. So you can play most multimedia formats in Ubuntu.) There something you probably want. Have you found that you can;t play DVD's in Ubuntu, or MP3 files? That means you don't have multimedia codecs installed.

Open a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```

Follow this guide for the rest: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

i dont have a dvd drive but i can play mp3s fine and used to be able to burn data disks as well. i used to only occasionally waste a blank disk because of the permission denied thing but havent been able to since my last updates. it says cdrecord has no permission to open the device everytime its past half way done

---

### Post by lavinog on 2009-10-15
> **RichardLinx said:**
> I don't think it's such a big deal when it comes to running a CD burning application. What's the biggest risk? Isn't the security risk the same as it is running "sudo" before an update?

The risk is that the application is ran as root with the users home folder.  Any configuration files created will have root permissions instead of user permissions.

---

### Post by RichardLinx on 2009-10-15
> **lavinog said:**
> The risk is that the application is ran as root with the users home folder.  Any configuration files created will have root permissions instead of user permissions.

But if it's just the configuration file for a disk project it shouldn't be such a big problem, right? I rarely save config files anyway so for me at least it's not an issue. I also don't understand how the configuration files created from a disk project could pose such a large threat to the computer - what is the risk caused by this?

> i dont have a dvd drive but i can play mp3s fine and used to be able to burn data disks as well. i used to only occasionally waste a blank disk because of the permission denied thing but havent been able to since my last updates. it says cdrecord has no permission to open the device everytime its past half way done

Have you tried jbrowns or my advice? (My advice may be "dangerous" it seems)
Also, if you don't have restricted codecs installed you'll find you can't play commercial DVD's as well as a few file formats. (Just a heads up).

---

### Post by natedogg23 on 2009-10-15
> **RichardLinx said:**
> But if it's just the configuration file for a disk project it shouldn't be such a big problem, right? I rarely save config files anyway so for me at least it's not an issue. I also don't understand how the configuration files created from a disk project could pose such a large threat to the computer - what is the risk caused by this?



Have you tried jbrowns or my advice? (My advice may be "dangerous" it seems)
Also, if you don't have restricted codecs installed you'll find you can't play commercial DVD's as well as a few file formats. (Just a heads up).

yes i tried yours and it still didnt burn. i dont know which code of jbrowns i need to use. i also ran the codecs code

---

### Post by jbrown96 on 2009-10-15
> **natedogg23 said:**
> i dont have a dvd drive but i can play mp3s fine and used to be able to burn data disks as well. i used to only occasionally waste a blank disk because of the permission denied thing but havent been able to since my last updates. it says cdrecord has no permission to open the device everytime its past half way done

Do what I said earlier. Applications-->Accessories-->Terminal then try ```
groups $USER
``` Here's what I get when I run the command > justin : justin adm dialout cdrom plugdev lpadmin admin sambashare vboxusers Everything after the colon is a group of which I am a member. You need to be in the cdrom group. You should be in the group by default, but perhaps you were dropped from it for some reason. If you are not part of that group then run ```
sudo usermod -aG cdrom $USER
``` this will add you to the cdrom group. New group permissions do not take affect until the next login, so you need to logout. This should give you full access to the cd drive, so you won't get the permission error. 
You don't want to run k3b or brasero as root. k3b especially has quite a few settings, so you could run the risk of losing permission to access those settings files, and that will lead to other permission problems. It's also a security risk and a bad habit to get into.

Instead of launching k3b or brasero from the applications menu, try running it within a terminal. just use ```
k3b
``` or ```
brasero
``` This will output errors and various status message to the terminal. If it fails, then you can copy and paste it here, and we can go through it and see if there is another problem.

---

### Post by natedogg23 on 2009-10-15
> **jbrown96 said:**
> Do what I said earlier. Applications-->Accessories-->Terminal then try ```
groups $USER
``` Here's what I get when I run the command  Everything after the colon is a group of which I am a member. You need to be in the cdrom group. You should be in the group by default, but perhaps you were dropped from it for some reason. If you are not part of that group then run ```
sudo usermod -aG cdrom $USER
``` this will add you to the cdrom group. New group permissions do not take affect until the next login, so you need to logout. This should give you full access to the cd drive, so you won't get the permission error. 
You don't want to run k3b or brasero as root. k3b especially has quite a few settings, so you could run the risk of losing permission to access those settings files, and that will lead to other permission problems. It's also a security risk and a bad habit to get into.

Instead of launching k3b or brasero from the applications menu, try running it within a terminal. just use ```
k3b
``` or ```
brasero
``` This will output errors and various status message to the terminal. If it fails, then you can copy and paste it here, and we can go through it and see if there is another problem.

im in the cdrom group but i previously entered sudo k3b and now i have to launch it that way, the panel icon no longer works. i just tried k3b in the terminal and got this; DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Aborting. No write access to '/home/natedog/.ICEauthority'.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.

---

### Post by jbrown96 on 2009-10-15
Try this to fix .ICEauthority
```
sudo chown $USER:$USER .ICEauthority
```

you should be able to fix k3b with ```
sudo chown -R $USER:$USER .kde/share/apps/k3b
```

Try brasero in the terminal again, and if that doesn't work, try k3b. Post the output again if you have problems.

---

### Post by RichardLinx on 2009-10-15
jbrown seems pretty knowledgable so hopefully his command will fix it. Logging out and logging back in will also fix the issue.

---

### Post by mick55 on 2009-10-15
hi 

The CD burning issue is because of an update to wodim
that has changed its permissions.

open a terminal[Menu->Terminal]
and type these commands
```
cd /usr/bin/
```Then type
```
chmod +s wodim
```and you should be able to burn CD's without a problem

---

### Post by natedogg23 on 2009-10-15
k3b, failed after 8% heres where it started errors etc;(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.

(K3bDevice::Device) /dev/scd0: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.

(K3bDevice::DeviceManager) found config entry for devicetype: ASUS CD-S520/A
Devices:
------------------------------
Blockdevice:    /dev/scd1
Generic device: 

------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.

(K3bDevice::Device) /dev/scd1:  Number of supported write speeds via 2A: 0
(K3bDevice::ScsiCommand) failed:

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> hi 

The CD burning issue is because of an update to wodim
that has changed its permissions.

open a terminal[Menu->Terminal]
and type these commands
```
cd /usr/bin/
```Then type
```
chmod +s wodim
```and you should be able to burn CD's without a problem

natedog@natedog-desktop:~$ cd /usr/bin/
natedog@natedog-desktop:/usr/bin$ chmod +s wodim
chmod: changing permissions of `wodim': Operation not permitted   --    did i type that right?

---

### Post by RichardLinx on 2009-10-15
Just put "sudo" before the command.

Edit: So: ```
sudo chmod +s wodim
```

---

### Post by mick55 on 2009-10-15
sorry about that

```
sudo chmod +s wodim
```

---

### Post by jbrown96 on 2009-10-15
Making wodim SUID should not be necessary. It's not on my system, and I can burn perfectly fine. SUID programs can be extremely dangerous. Natedog, I can understand that you just want this to work, so if chmod +s /usr/bin/wodim works and you are fine with the security implications that's fine, but I do want to warn you that this solution is ill-advised. There are very few commands that need SUID permissions, and only because there isn't a better way for them to work. 

Before you do this, try removing wodim and then resintalling it.
```
sudo apt-get purge wodim
``` This will remove brasero and k3b then reinstall with ```
sudo apt-get install k3b brasero
```

---

### Post by natedogg23 on 2009-10-15
i will do that but i just tried to open k3b thru the terminal after loging out and in and its freezing and the k3b start screen is blocking my screen. the last thing i did was the wodim code. heres the termaial;;natedog@natedog-desktop:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
natedog@natedog-desktop:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8160B to device /dev/scd1
Mapping udi /org/freedesktop/Hal/devices/storage_model_CD_S520/A to device /dev/scd0
/dev/scd1 resolved to /dev/scd1
/dev/scd1 is block device (1)
/dev/scd1 seems to be cdrom
bus: 1, id: 1, lun: 0
(K3bDevice::Device) /dev/scd1: init()

---

### Post by mick55 on 2009-10-15
hey jbrown96

I was able to burn fine on my system too, and then after running
an update a while back i started having problems.
I tried every burning software from the repositories, and nothing worked.
I tried burning from the command line and that didn't work
either.And then i tried burning from the command line as sudo
and it worked.Thats when i modified wodim so i didn't need to keep
switching to sudo.
I do all my cd burning from the command line now.In fact i got
lazy and wrote some nautilus scripts to automate the process.

I have since learned not to install every available update.

cheers
mick

---

### Post by mick55 on 2009-10-15
i just saw your post natedogg23

to restore to original config use 

```
sudo chmod a-s wodim
```but i don't think that's causing your problem

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> i just saw your post natedogg23

to restore to original config use 

```
sudo chmod a-s wodim
```but i don't think that's causing your problem

me either and i dont want to try to restore it

---

### Post by natedogg23 on 2009-10-15
> **jbrown96 said:**
> Making wodim SUID should not be necessary. It's not on my system, and I can burn perfectly fine. SUID programs can be extremely dangerous. Natedog, I can understand that you just want this to work, so if chmod +s /usr/bin/wodim works and you are fine with the security implications that's fine, but I do want to warn you that this solution is ill-advised. There are very few commands that need SUID permissions, and only because there isn't a better way for them to work. 

Before you do this, try removing wodim and then resintalling it.
```
sudo apt-get purge wodim
``` This will remove brasero and k3b then reinstall with ```
sudo apt-get install k3b brasero
```

Should i restore all of these?-The following packages will be REMOVED:
  brasero* k3b* nautilus-cd-burner* ubuntu-desktop* wodim* xfburn*

---

### Post by jbrown96 on 2009-10-15
This is really stumping me. Is this a laptop? Have you used a program called powertop? Can you read disks without any permission errors? Is this ruining a disk each time you try to burn? If you look carefully at the disk, can you tell if it wrote anything to it? What are you burning, data files, DVD movie, audio cd, etc.? 
Here's what I would do:
1) try the remove and reinstall procedure that I wrote in an earlier post. I just saw your last post about how it wants to remove some extra applications. Is xfburn another burning app that you tried? If so, don't reinstall it, but add nautilus-cd-burner and ubuntu-desktop to the end of the install command. ```
sudo apt-get install k3b brasero ubuntu-desktop nautilus-cd-burner
```
2) undo the chmod +s wodim command with ```
sudo chmod -s /usr/bin/wodim
``` then try to run brasero again. 

What version of Ubuntu are you running? If you are not sure, ```
lsb_release -a
``` Do you have any non-standard software repositories activated? Backports, testing, etc.? If you don't know what that means, then you don't.

Mick55 you seem to understand wodim and I would imagine genisoimage as well. I'm not familiar with them, but I looked through the manpage for wodim, and I found that there is an option to simulate writing to disk. Could you create a command for natedogg to simulate burning if he's wasting disks each time?

---

### Post by natedogg23 on 2009-10-15
not a lap top, no powertop, i can play music fine but cant burn since the last update and it does burn on and waste the disk. simulation will complete fine and still not burn correctly (in k3b). i burn audio and mp3s. xfburn i found today in synaptic. its for data cds. im on 8.04

---

### Post by natedogg23 on 2009-10-15
i opened k3b thru the terminal again after i purged and this was there again;;kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
i have no idea what that is

---

### Post by jbrown96 on 2009-10-15
When you are burning in K3b there are two buffer bars for software (?) and device. Do they drop to zero when it fails, or does it just fail all at once? 

Did you try running ```
sudo brasero
``` or ```
sudo k3b
``` and still get the permission error?

I'm at the point now where I would say that it is a hardware problem. Then again, you said it worked until the last update. I really can't think of anything else to try. I imagine you are using 8.04 for a reason, but would it be possible to get you to upgrade to 9.04 or 9.10 (when it is released at the end of October)? I'm using 9.10 beta, so 8.04 is several releases old for me; it's pretty amazing how much Linux and Ubuntu have progressed, so I'm having trouble remembering 8.04s idiosyncrasies.

EDIT: I just found something on the Fedora forums that might fix this problem. Check the permissions on your cd drive. ```
ls -l /dev/cdrom
``` Mine looks like > lrwxrwxrwx 1 root root 3 2009-10-14 15:40 /dev/cdrom -> sr0 Make sure that the permissions are rwxrwxrwx. If they are not then run this ```
sudo chmod 777 /dev/cdrom
``` and ```
sudo chmod 777 /dev/sr0
``` just to be safe, but don't be surprised if the second command complains about the file not existing.

---

### Post by lavinog on 2009-10-15
> **natedogg23 said:**
> i opened k3b thru the terminal again after i purged and this was there again;;kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
i have no idea what that is

I believe it is a warning saying that the software is using a program function that is no longer supported.  If this is the case, you can ignore it because it is a reminder for the developers to use a new function.

---

### Post by lavinog on 2009-10-15
> **jbrown96 said:**
> 
I'm at the point now where I would say that it is a hardware problem. 

This is a possibility.
I am guessing since the drive cannot read dvd's it is pretty old.
My 4 year old dvd burner seemed to work fine with an occasional coaster...i thought the coasters were ubuntu issues...it turned out that the drive was near the end of its life.  I bought a new dvd burner for $25 on newegg, and my first reaction was that I should have done that much earlier.

---

### Post by natedogg23 on 2009-10-15
when i ran sudo k3b it failed from a buffer overrun instead of the permisson error. it is rwxrwxrwx. k3b just crashed during a simulation and locked the cd drive closed and in max buffer

---

### Post by natedogg23 on 2009-10-15
but would i get permission errors just because the drive is old?

---

### Post by jbrown96 on 2009-10-15
That's the thing: permission errors would be unlikely for a hardware problem. It would be more likely to be "device /dev/cdrom could not be opened" repeated many times. 
I'm done for the night. Maybe fresh eyes will give me some new ideas tomorrow.

---

### Post by oboedad55 on 2009-10-15
> **natedogg23 said:**
> well crap how do i un root it now? and how do i know which code from jbrown to use? this is what happened in root instead of permission denied; Probably a buffer underrun occured  Please try a lower burn speed

Follow Richard's notes above for installing restricted extras and the medibuntu repo. That's what I would do first.

---

### Post by mick55 on 2009-10-15
hey dogg

Let's try this from CLI
that way we can deal more directly with the CD drive

run this from a command prompt

```
wodim --devices
```this will give you your device name

now let's burn from the CLI

run this from a command prompt, this will blank a CD

```
cdrecord -v speed=4 blank=fast dev=/dev/scdx
```run this from a command prompt,this will burn an ISO

```
cdrecord -v speed=4 driveropts=burnfree dev=/dev/scdx xxxx.iso
```(cdrecord is a symbolic link to wodim)

Change the x to your CD drive letter/number

If there  are permission errors put "sudo" infront of the commands,
although you shouldn't need to since you modified the permissions 
for wodim.

let me know what happens.

---

### Post by natedogg23 on 2009-10-15
i have installed the extras and still no luck. mick, havent tried from command line yet but i just opened brasero thru terminal checked disc integrity since it still says 0 bites free on any blank cd and got;;GConf Error: Bad key or directory name: "/system/storage/default_options/(null)/fstype_override": `(' is an invalid character in key/directory names
GConf Error: Bad key or directory name: "/system/storage/default_options/(null)/fstype_override": `(' is an invalid character in key/directory names
(brasero:5301): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: the drive could not be mounted

(brasero:5301): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: the disc could not be mounted (max attemps reached)

---

### Post by natedogg23 on 2009-10-15
i havent changed permissions of wodim i dont think, the last thing i did was purge it. unless that does change them. i did the usr/bin chmod command posted earlier but that was before the purge

---

### Post by natedogg23 on 2009-10-15
> **natedogg23 said:**
> i havent changed permissions of wodim i dont think, the last thing i did was purge it. unless that does change them. i did the usr/bin chmod command posted earlier but that was before the purge

should i get this warning;;; natedog@natedog-desktop:~$ wodim --devices
wodim: Warning: controller returns wrong size for CD capabilities page.
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'ASUS' 'CD-S520/A'
 1  dev='/dev/scd1'	rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8160B'

---

### Post by natedogg23 on 2009-10-15
mick, 2nd command;;;natedog@natedog-desktop:~$ cdrecord -v speed=4 blank=fast dev=/dev/scdx
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scdx'
devname: '/dev/scdx'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
-----and the 3rd;;;~$ cdrecord -v speed=4 driveropts=burnfree dev=/dev/scd1 xxxx.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CD-RW GCE-8160B '
Revision       : '2.11'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 4194304 = 4096 KB
wodim: No such file or directory. Cannot open 'xxxx.iso'.----the RLIMIT MRMLOCK and most of this looks like the same output i get after wasting a disk in k3b but k3b wastes the disk before it tells me this

---

### Post by natedogg23 on 2009-10-15
k3b again;;; cdrecord has no permission to open the device- this was in the terminal ;;;;;(K3bDevice::Device) /dev/scd0: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/scd0: modeSense 0x05 failed!
(K3bDevice::Device) /dev/scd0: Cannot check write modes.                      Launched ok, pid = 6461
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8160B
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8160B

---

### Post by natedogg23 on 2009-10-15
> **natedogg23 said:**
> k3b again;;; cdrecord has no permission to open the device- this was in the terminal ;;;;;(K3bDevice::Device) /dev/scd0: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/scd0: modeSense 0x05 failed!
(K3bDevice::Device) /dev/scd0: Cannot check write modes.                      Launched ok, pid = 6461
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8160B
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8160B

right now it appears im right back where i started

---

### Post by lavinog on 2009-10-15
How old is this drive?  I am finding that this model came out in 2001.
Does this drive work in other computers or OSes?

---

### Post by natedogg23 on 2009-10-15
it used to be in another pc i believe. it was given to me and used to work fine. i saw an error msg on there that said wodim wasnt permitted and another that said no such file but i did purge it

---

### Post by jbrown96 on 2009-10-15
I think that this is a kernel problem, so all the userland modifications won't fix it. When you boot the computer, you should get a GRUB screen where there are many kernels (since 8.04 has been out for so long). Try choosing The third from the top. you should have two entries per kernel; the first is the regular version and the second is the recovery version. The third entry should be the regular version of the previous kernel. Perhaps this was the update that hosed your burning capabilities. You may also want to try an even older version. Obviously the problem with trying many different versions is that you will waste a CDR each time.

Have you tried running updates since this problem started occuring. Perhaps it has been fixed, although I would imagine other users would have the same problem, but I haven't seen anything related in the forums. 

1) Run update manager and apply all updates
2) then try an older kernel

---

### Post by mick55 on 2009-10-15
hi natedogg23 

Read my posts again.
I said if wodim gave permission errors to put sudo in front of the commands.
I also said replace x with your own information.

I stick with my original suggestion
run this command in terminal
```
sudo chmod +s wodim
```the error message
"Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev"
Specifically means you need administrator rights to use wodim.

All your CD burning programs are front ends for wodim.
Fix wodim and try burning from the CLI again.

Remember i can't see what you can, and an "X" means fill
in your own details, i dont know them.

cheers
mick

---

### Post by mick55 on 2009-10-15
For a test you could download the linux version of Nero.
It works really well and doesn't use wodim.
It's trial ware but at least you could use it to prove
to yourself that your hardware is good and your whole
system isn't borked.

[html]http://www.nero.com/enu/support-linux4.html[/html]good luck
mick

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> For a test you could download the linux version of Nero.
It works really well and doesn't use wodim.
It's trial ware but at least you could use it to prove
to yourself that your hardware is good and your whole
system isn't borked.

[html]http://www.nero.com/enu/support-linux4.html[/html]good luck
mick

nerolinux! i used to have it before i upgraded to 8.04 and it got deleted. it was great. when i upgrade to 9.10 will this wodim ever be a problem again? iheard 9.10 is a long term one which is why im still on 8.04.

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> hi natedogg23 

Read my posts again.
I said if wodim gave permission errors to put sudo in front of the commands.
I also said replace x with your own information.

I stick with my original suggestion
run this command in terminal
```
sudo chmod +s wodim
```the error message
"Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev"
Specifically means you need administrator rights to use wodim.

All your CD burning programs are front ends for wodim.
Fix wodim and try burning from the CLI again.

Remember i can't see what you can, and an "X" means fill
in your own details, i dont know them.

cheers
mick

i thought that made it SUID which i shouldnt need to do and i should have admin rights already and dont know why i dont. what do i put in the xxxx.iso?

---

### Post by natedogg23 on 2009-10-15
there was 1 update and it was for audio files. is there some reason i dont have admin rights or should i not even need them? if wodim is the only problem and it isnt on newer versions, and ill be just fine ill upgrade now. is that the case?

---

### Post by mick55 on 2009-10-15
read my message #40 again.

It quite clearly states how to find out your Cd drives name.
It also shows you how to blank a CD.
As far as an iso name, if you have any ISO file on your computer use that name , or make your own ISO from a directory.
But first run that command on wodim otherwise none of your programs will be able to burn a CD.

---

### Post by mick55 on 2009-10-15
Ubuntu 9.10 is not the next LTS.
Ubuntu 10.04 LTS Lucid Lynx is.

Don't upgrade to a beta version though, people have been having huge problems with it.

No guarantee wodim will be any different in 9.10

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> read my message #40 again.

It quite clearly states how to find out your Cd drives name.
It also shows you how to blank a CD.
As far as an iso name, if you have any ISO file on your computer use that name , or make your own ISO from a directory.
But first run that command on wodim otherwise none of your programs will be able to burn a CD.

i know i did find the names. i was asking what i put in there because i didnt know thats what u meant. i also dont know what iso is.

---

### Post by natedogg23 on 2009-10-15
> **mick55 said:**
> Ubuntu 9.10 is not the next LTS.
Ubuntu 10.04 LTS Lucid Lynx is.

Don't upgrade to a beta version though, people have been having huge problems with it.

No guarantee wodim will be any different in 9.10

so if wodim wasnt or rarely was a problem before, why is it so much of one now? ive tried everything posted in the terminal with no success and posted results of everything that has happened. so after i purged wodim, do i need do do everything again, like the codecs etc...

---

### Post by natedogg23 on 2009-10-15
hopefully i can check in tomorrow but ill be at a wedding this weekend and ill read and try everything thats here when i get home

---

### Post by jbrown96 on 2009-10-16
You do not need root privileges to run wodim. Your cd drive has permissions rwxrwxrwx and is owned by root. This means that the owner (first three values) has Read, Write, and eXecute permissions, members of the group (which is root) have read, write, and execute permissions, and others have read, write, and execute permissions. You fall into the others category. Wodim doesn't need any special permissions to write to the cd drive. Making wodim SUID (or even running it sudo) is just a security nightmare and has no possibility of making the situation any better.
And as for running brasero and k3b as root, you found out that it will mess up your config files. 

The burning programs and low-level cli tools (wodim) have been completely purged; all of their settings have been removed, and then reinstalled. Perhaps, there's some kind of bug in these programs, but they obviously exist in the version that Ubuntu is distributing. Re-installing them isn't going to do any good because it will just get the same buggy version. 
There's no doubt in my mind that the problem is not in userland. Mucking around with wodim, k3b, or brasero isn't going to improve anything. It's got to be a hardware problem that just happened to occur when you did updates, or it's something with the kernel. There's not really anything else that it can be. 
Here's a rough example of how a cd is burned.
Brasero/K3b---->wodim--->kernel--->vfs--->cd drive firmware--->cd
We have done about everything to fix the first two steps. A kernel problem could affect the next two, and a hardware problem would affect the last two. I think it's to try to fix something at a lower level.

---

### Post by natedogg23 on 2009-10-16
jbrown i agree with you completely that i shouldnt have to burn thru root at all especially since ive done it so many times with out it. but i really dont understand this;;the error message
"Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev"
Specifically means you need administrator rights to use wodim.;; ive seen that a few times in k3b before but it would still burn way more than not. i went to the 3rd from the top on the grub screen and im going to try again. also i did the sudo chmod a-s wodim, dont no if it matters since i purged but it said wodim doesnt exsist. before i switched kernals i tried to burn with nero and the disc plays but is not complete. the error msg doesnt tell me anything, maybe one of u will get something out of it;;;09:51:28 AM	#36 SCSI -1135 File SCSIInterface.cpp, Line 624
	SCSI Exec, HA 1, TA 1, LUN 0, buffer 0x0x95ae5c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x03 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x03 (KEY_MEDIUM_ERROR)
	Sense Code: 0x0C
	Sense Qual: 0x00
	CDB Data:   0x2A 0x00 0x00 0x02 0x64 0x0D 0x00 0x00 0x1B 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x03 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x0C 0x00 
	
09:51:28 AM	#37 CDR -1135 File Writer.cpp, Line 306
	Write error
	HL-DT-ST CD-RW GCE-8160B (H:1 T:1)
	
09:51:31 AM	#38 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 16x (2400 KB/s)

---

### Post by natedogg23 on 2009-10-16
i also dont think its hardware because why would i get permission errors from wodim if it is? im beyond lost and dont want to resort to doing burns thru root however im not opposed to burning thru the command line though i shouldnt need to. also i can run simulations in k3b and they almost always are successful and then the disc gets ruined in the burn thanks to the wodim error msg

---

### Post by mick55 on 2009-10-16
You know instead of everyone argueing about whether it's
a hardware ,software or permissions issue,why not just install
Nero as i suggested.

If you can burn OK with Nero then it's obviously not a hardware
issue.

--and then we can move ahead with a resolution for you.

Let's argue about wodim later:^)

cheers
mick

---

### Post by natedogg23 on 2009-10-17
msg 61 is the error from nero. ive tried data and audio and got that same error msg. maybe you re right jbrown, could be hardware but i want to try from the cl. would that solve the issue that its hardware if it wont burn from the cl?

---

### Post by natedogg23 on 2009-10-17
> **mick55 said:**
> You know instead of everyone argueing about whether it's
a hardware ,software or permissions issue,why not just install
Nero as i suggested.

If you can burn OK with Nero then it's obviously not a hardware
issue.

--and then we can move ahead with a resolution for you.

Let's argue about wodim later:^)

cheers
mick

mick heres my device;; 1 dev='/dev/scd1' rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8160B. which part of that goes in the xxxx.iso? everything after rwrw?

---

### Post by mick55 on 2009-10-17
hi dogg

Hey, an ISO is an image file.
Your Ubuntu Cd was made from an ISO.

Now i know your device name i can give you specific commands to input.

First let's blank a CDRW

run this command in terminal

```
sudo cdrecord -v speed=4 blank=fast dev=/dev/scd1
```You can make an ISO of a CD for a test.
Put any data CD into your CD drive.
Next unmount it

```
sudo umount /dev/cdrom
```then to make the ISO run this command

```
sudo dd if=/dev/scd1 of=dogg.iso bs=1024
```This will create an image file called dogg.iso in your home directory.

to burn the image you created to a cd 
run this command

```
sudo cdrecord -v speed=4 driveropts=burnfree -dao dev=/dev/scd1 dogg.iso
```let me know the results.

cheers
mick

---

### Post by natedogg23 on 2009-10-18
ill just post the terminal for you mick;;-desktop:~$ sudo cdrecord -v speed=4 blank=fast dev=/dev/scd1
[sudo] password for natedog: 
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CD-RW GCE-8160B '
Revision       : '2.11'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Speed set to 704 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Performing OPC...
Blanking PMA, TOC, pregap
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.
natedog@natedog-desktop:~$ sudo umount /dev/cdrom
umount: /dev/cdrom: not mounted

---

### Post by natedogg23 on 2009-10-18
sudo dd if=/dev/scd1 of=dogg.iso bs=1024
dd: reading `/dev/scd1': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00651191 s, 0.0 kB/s
natedog@natedog-desktop:~$ sudo cdrecord -v speed=4 driveropts=burnfree -dao dev=/dev/scd1 dogg.iso
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CD-RW GCE-8160B '
Revision       : '2.11'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 4194304 = 4096 KB
Track 01: data     0 MB        
Total size:        0 MB (00:04.00) = 300 sectors
Lout start:        1 MB (00:06/00) = 300 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 359546
Speed set to 704 KB/s
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 MB written.
Track 01: writing 600 KB of pad data.
Track 01: Total bytes read/written: 0/614400 (300 sectors).
Writing  time:   10.641s
-----the disk does not mount when i put it in either drive

---

### Post by mick55 on 2009-10-18
Umm...you can't blank a CDR .
It needs to be a CDRW. 
Not CD Recordable, CD Re-Writeable

sudo cdrecord -v speed=4 blank=fast dev=/dev/scd1 means
erase a Re-Writable CD.

You can't make an ISO of a blank disk.

Read what i wrote again, i thought it was quite clearly written.

sudo dd if=/dev/scd1 of=dogg.iso bs=1024  means
make an ISO copy of the CD in scd1 and name the Iso dogg.iso.
In otherwords put in a Data CD.For example a Windows XP CD or
a Linux Mint CD.

I can't help you if you don't follow the directions exactly

cheers
mick

---

### Post by natedogg23 on 2009-10-19
so its not possible to burn thru cl with cdrs? i dont have any cdrws

---

### Post by mick55 on 2009-10-19
No you cannot erase/blank a CDR period.

It is a CD Recordable not Re-Writable.

You obviously don't fully read or comprehend anything I post.

The second part has nothing to do with CDR or CDRW.

It says to put a DATA CD in your drive and create an ISO from it.

All the terminology I use is industry standard.There is nothing
oblique or esoteric about anything i have posted.

You can google "ISO" if you don't know what it is.

If you want to burn CD's in Brasero or K3b then do what i said in
the first place.

open a terminal[Menu->Terminal]
and type these commands
Code:
```
cd /usr/bin/
```Then type
```
sudo chmod +s wodim
```After you exeecute the commands above
burn a cd in k3b or brasero.

And please, this time actually READ what is written.

I am glad to help, but i need a little co-operation

cheers 
mick

---

### Post by natedogg23 on 2009-10-20
actually i have, i was asking if you can use cdrs thru the cl. ive done chmod wodim command and it also didnt work. this is the third time ive said it didnt work. all i have are cdrs, so obviously i cant burn from the cl and im just gonna mark this as solved. when i get a new drive and if i have the same problems ill repost this issue. thanks to everyone for trying to help me thru this

---

### Post by Typhoeus on 2009-11-02
Been having the same probs and been pulling my hair out for hours. tried an external usb dvd writer and managed to get 76% overall progress before it failed with the same error "cdrecord can not write to device" even though the disk has been wrote to. Tried again at 8X speed and had success. 

the thing thats bugging me is that I have used the original writer in the past (maybe 4-8 weeks ago before I reinstalled hardy) and if I remember rightly I had probs then which were resolved by chmod ing either the whole /media folder or the /dev folder to 777 but I dont think that thats a good idea.

I will try the original writer in another OS to confirm that it is ok.

---

### Post by lavinog on 2009-11-02
> **Typhoeus said:**
> Been having the same probs and been pulling my hair out for hours. tried an external usb dvd writer and managed to get 76% overall progress before it failed with the same error "cdrecord can not write to device" even though the disk has been wrote to. Tried again at 8X speed and had success. 

the thing thats bugging me is that I have used the original writer in the past (maybe 4-8 weeks ago before I reinstalled hardy) and if I remember rightly I had probs then which were resolved by chmod ing either the whole /media folder or the /dev folder to 777 but I dont think that thats a good idea.

I will try the original writer in another OS to confirm that it is ok.

You should start a new thread for your issue.  It may not be the same issue, and chmoding the media folder to 777 shouldn't really help the issue.  Chmoding the /dev folder to 777 is ** A REALLY BAD IDEA**.

---

### Post by Typhoeus on 2009-11-02
tried my original internal writer with knoppix 5.3 live cd using kernel 2.6.24.4 and k3b 1.0.4 and burnt a disk at auto speed 24X.

rebooted back into xubuntu 8.04 hardy heron using kernel 2.6.24.25 but with an edited /etc/fstab file with the 2 lines relating to my internal dvd rom and internal cd writer commented out. brasero now works no prob, k3b failed on auto speed but works fine at 4X, will increase the speed to find whats ok for me.

is there any reason why I need my cd drives mounted in fstab. I have my removable media settings set to auto mount. deselecting auto mount removable media before commenting /etc/fstab made no difference to cd burning.

---

### Post by bclarky12 on 2010-04-02
i'm sorry, but i'm having the same problem, I'm new to ubuntu, I didn't want to mess with wodim settings so i downloaded the nero trial, I'm still getting an error, I attached the log, if someone has any ideas i would really appreciate it. Thank you so much. Right now, can't burn anything at any speed

---

### Post by bclarky12 on 2010-04-02
here's a log error at 4x

---

### Post by orkyahaalhai on 2010-04-06
is there any new cd/dvd buring app like pburn or burn2iso slated in ubuntu 10.04?? well these 2 works perfectly well in puppy linux , while ubuntu has always given me headache!

---

### Post by pwebster25 on 2010-08-10
Did anyone really solve this problem.  It just popped up for me.  I did an upgrade in "9.10" and it started throwing errors when burning.  So, I updated to "10.04" but same deal.

I have read through this post as well as several others with similar problems.  I have tried most reasonable solutions but so far NOTHING has worked.

Interestingly, this burner is connected by USB cable, as it is used for burning from itunes in winxp inside virtualbox.  Itunes won't burn in virtualbox unless it is connected by usb.  It has worked great for at least a year without a problem.

If you have solved this burning problem, I would appreciate your help a lot.

---

### Post by sbubba on 2010-11-07
Hello
I had this problem with k3b 1.91.0 on ubuntu 10.04.
I've had to purge and reinstall some packages: 
```
hal libhal1 libhal-storage1 k3b wodim
```
(apt-get wants to remove many packages in addition to these, you have to reinstall all of them)

---

