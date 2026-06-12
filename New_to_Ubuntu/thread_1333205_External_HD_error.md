---
title: "External HD error"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by cm06mrs on 2009-11-21
Just installed ubuntu. When I plug in my external hard drive I get the following error:


Unable to mount 640 GB Filesystem

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details

Its a Maxtor Basics Desktop storage 640GB and Im running the latest version of ubuntu.

Thanks.

---

### Post by cm06mrs on 2009-11-21
anyone?

---

### Post by Cowboybebop79 on 2009-11-22
Hi having the same problem I think it has something to do with the drive not being removed safely or unmounted doing some searching to find solution. Will post a reply if I find one. MFT is the master file table which is updated when you unmount or safely remove the disk if you just yank the disk out the MFT will not be updated eventialy this will slow down the disk, corruption blah blah. Ubuntu deals with this in a different way than Windows.

---

### Post by shantiq on 2009-12-17
[COLOR=Blue][B]yes got the same with Free agent drive 

[/B][/COLOR]Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


[COLOR=Blue]**anyone knows what to do??   thanx    shan:):):)**[/COLOR]

---

### Post by shantiq on 2009-12-17
[COLOR=Blue][B]guys looking around and going through an italian link i found this by a guy called zeex

[http://ubuntuforums.org/showthread.php?t=1144175](http://ubuntuforums.org/showthread.php?t=1144175)

he says


[/B][/COLOR]I have seen this error usually when computer is switched of either in the middle of startup or shutdown. Then it doesn't mount NTFS drives in ubuntu. Going back to windows and running chkdsk <drive> /f (example chkdsk e: /f) solves all the problem. Since you don't 've windows anymore. You need to install ntfs tools in ubuntu

     Code:
   ```
  $ sudo apt-get install ntfsprogs 
```This package has a nice collection of tool for ntfs drives. To fix your problem let's say your drive is /dev/sda2 

     Code:
     ```
$ sudo ntfsfix /dev/sda2 
```This should fix the disk. Reboot after this. 

[COLOR=DarkRed]i shall add make sure your extension is the right one you can find this on the original error message you got[/COLOR]

If it still doesn't work use a Live CD like Hiren's boot CD mainly for DOS or there are a lot of other here is a [wiki list]("http://en.wikipedia.org/wiki/List_of_LiveDistros#Rescue_and_Repair_LiveDistros") of rescue n repair live CDs. Try the one you like :) Hiren's boot CD has chkdsk utility. System Rescue CD is another nice rescue CD.[COLOR=Blue][B]

the original italian page that got me to zeex was     [http://forum.ubuntu-it.org]("http://forum.ubuntu-it.org/index.php?topic=346982.0")[/index.php?topic=346982.0     ]("http://forum.ubuntu-it.org/index.php?topic=346982.0")

i genuinely feel grateful to the guys who help here  it makes this community a cool place


hope this helps you too         shan[/B][/COLOR]:):):)

---

### Post by teward on 2009-12-17
One thought I may put out there.  I saw an issue with external HDs, where they're unsafely removed, and it causes damage to the devices.  If the links above don't help, it might be an issue with the drive's I/O streams (input/output), where it got damaged and doesn't recognize commands from the system.

---

### Post by indianlinuxuser on 2009-12-20
Thanks a lot [shantiq]("http://art.ubuntuforums.org/member.php?u=870500")!! This fixed my issues to mount my external hard disk. Ubuntu Rocks!!!

---

### Post by c-lou on 2009-12-21
Thanks shantiq!!! I had the same problem, and your solution was perfect :)

---

### Post by Cardale on 2010-01-07
Worked great! Thanks dude.

---

### Post by alesssia on 2010-01-18
Hi, 
I installed Ubuntu 9-10 (Karmic Koala) and I was mounting my external HD (previuosly   unsafely removed) when I obtained the same error of cm06mrs.

I tried to follow the solution proposed by shantiq, but this was my output:

```

$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libntfs-gnomevfs
E: Package ntfsprogs has no installation candidate

```

Then I tried to install the suggested package and I obtained:

```

sudo apt-get install libntfs-gnomevfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libntfs-gnomevfs: Depends: libntfs10 (>= 2.0.0) but it is not installable
E: Broken packages

```

Obviously I also tried to force the installation of  libntfs10, but it didn't work.

Anyone can help me?
Thanks, Alessia

---

### Post by groperofeuropa on 2010-05-05
shantiq, you are an absolute king/queen of likewise gender specific royalty. This happened to me once before and i had to do a raw recovery and lost 300G of data.. you just saved me losing another terabyte...

alesssia :
sorry if this doesnt help, but my problem occurred in 10.04 Lucid Lynx and ntfsprogs was already present on the system (this was the netbook edition. im sure the desktop ver would be the same) so it might be worth giving a try in the unlikely event that you're still with the same problem.

---

### Post by Ahmedmb on 2010-05-07
ntfsfix resolve the error 

THX a lot

---

### Post by indigoanalysis on 2010-06-11
ntfsfix didn't work for me I was so scared but. First i din't read the chkdsk...then went to another comp to chk it on windows. was working...did chkdsk like shantiq advised Thanks to you Shantiq the chkdsk i: with the /f command did the trich....thanks man!!

---

### Post by mylittletom on 2010-08-08
I had the same problem with 500G/7200rpm . 
Shantig's tip save much my time .

Thanks shantiq !

---

### Post by akendrick451 on 2010-10-08
Thanks shantiq, worked a treat on my western digital drive.

---

### Post by wilsonandyb on 2010-10-14
ubuntu forums you truely are a marvel

shantiq and the bloke zeex before him, truely you are princes/princesses among men

worked perfectly for an iomega HD which I now realise I must have messed up somehow when my laptop battery went dead while transfering files.

---

### Post by balaji31d on 2010-11-09
Great Help! Thanks dude!

---

### Post by Ta0RX on 2011-02-18
> **shantiq said:**
> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.



I have the latest version of Ubuntu and just had this same problem myself with an external TB disk because a power cut this afternoon.  After turning off the box for a couple of minutes and back to on again, have followed [shantiq]("http://ubuntuforums.org/member.php?u=870500")'s instructions step by step; everything worked perfectly for me.  

Thank you [shantiq]("http://ubuntuforums.org/member.php?u=870500") for your time and great help, and thanks to the original poster of this extremely useful solution,.  :KS

alesssia, sorry this isn't working in your particular case, really wish you'd briefly find the right solution.

---

### Post by Horeb on 2011-11-18
thanks shantiq it worked for me. :)

---

### Post by oldos2er on 2011-11-19
Closed, please don't bump old threads.

---

