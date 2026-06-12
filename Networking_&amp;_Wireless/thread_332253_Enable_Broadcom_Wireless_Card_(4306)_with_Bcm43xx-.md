---
title: "Enable Broadcom Wireless Card (4306) with Bcm43xx-Fwcutter"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by maclenin on 2007-01-05
I am still a Linux maiden (with ref. to: [http://ubuntuforums.org/showthread.php?t=328272)](http://ubuntuforums.org/showthread.php?t=328272)) and though, perhaps, now a wee less chaste - remain just as giddy....

After a few weeks of (unconnected) searching and scratching for solutions to this wireless problem, I finally plugged in my ethernet cable and (with the indispensible help of numerous sources, who I will try to recognize, al fine) pieced together the following "solution".

As I am still in the early stages of linux learning and also appreciate "guides" that don't meander, my descriptions of the various steps in this process will be brief and simple (and surely clumsy to those ubuntu magi who might stumble across this post)....

**A. STARTING CONFIGURATION**

Dell Inspiron 600m laptop
Windows XP on the hard drive 
Xubuntu 6.10 (Edgy Eft) on a LiveCD
Broadcom 4306 wireless chipset
bcmwl5.sys wireless driver
Ethernet connection


**B. LOCATE YOUR WIRELESS "DRIVER" (bcmwl5.sys) AND DOWNLOAD THE FIRMWARE CUTTER "UTILITY" (bcm43xx-fwcutter)[STEPS B. AND C. CAN, OF COURSE, BE COMPLETED VIA LINUX, IF YOU'RE HARDWIRED TO THE INTERNET]**

1. Start Windows XP and locate bcmwl5.sys in c:\windows\system32\drivers

2. Create a directory in Windows XP called c:\windows\linux

3. Download bcm43xx-fwcutter-006.tar.bz2 from [http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547) into c:\windows\linux

**C. COPY YOUR DRIVER AND UTILITY FROM WINDOWS TO LINUX**

4. Start Linux from the LiveCD

5. Open up the terminal (Applications - System - Terminal) to identify your **NTFS** Windows partition...
```
sudo fdisk -l
```
...and look for the line of output similar to:
```
**/dev/hda2**   *   7    9254    74284560   7   HPFS/**NTFS**
```
6. Mount your **NTFS** Windows partition (which happens to be labeled, **/dev/hda2**, in my example) into Linux and copy your driver and utility from Windows to Linux:
```
sudo mkdir /c
sudo mount **/dev/hda2 **/c -t ntfs
sudo mkdir /home/utilities
sudo mkdir /home/drivers
sudo cp /c/windows/linux/bcm43xx-fwcutter-006.tar.bz2 /home/utilities
sudo cp /c/windows/system32/drivers/bcmwl5.sys /home/drivers
```

**D. UNPACK AND INSTALL THE UTILITY**

7. Install the build-essential tool set:
```
sudo aptitude update 
sudo aptitude install build-essential
```
8. Identify your kernel version, using...
```
uname -r
```
...which should output something similar to:
```
**2.6.17-10-generic**
```
9. Update your linux headers, using the output from uname -r, as indicated:
```
sudo aptitude install linux-headers-**2.6.17-10-generic** 
sudo ln -s /usr/src/linux-**2.6.17-10-generic** /lib/modules/**2.6.17-10-generic**/build
```

10. Unpack and install the utility:
```
cd /home/utilities
sudo chmod a=rwx bcm43xx-fwcutter-006.tar.bz2
sudo tar -jxvf bcm43xx-fwcutter-006.tar.bz2 -C /home/utilities
cd /home/utitlities/bcm43xx-fwcutter-006
sudo make
sudo make install
```

**E. CUT THE FIRMWARE FROM YOUR DRIVER AND INSTALL THE FIRMWARE**

11. Run the utility to cut the firmware from your wireless driver and install the firmware:
```
sudo bcm43xx-fwcutter /home/drivers/bcmwl5.sys
sudo make installfw
```

That should do it!

**F. CREDITS** (in no particular order and, certainly, not exhaustive):

**Build-essential:**
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)
[http://www.linuxquestions.org/questions/showthread.php?t=514940](http://www.linuxquestions.org/questions/showthread.php?t=514940)

**Bcm43xx-fwcutter:**
[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx)
[http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)
[http://hangdog.pihl.no-ip.org/index.php?option=com_content&task=view&id=14&Itemid=34](http://hangdog.pihl.no-ip.org/index.php?option=com_content&task=view&id=14&Itemid=34)
[http://www.linuxquestions.org/questions/showthread.php?t=510440](http://www.linuxquestions.org/questions/showthread.php?t=510440)

**Chmod:**
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

**Tarballs:**
[http://ubuntuforums.org/showthread.php?t=314082&highlight=.tar.bz2](http://ubuntuforums.org/showthread.php?t=314082&highlight=.tar.bz2)

**Linux:**
[http://linux-newbie.dotsrc.org/](http://linux-newbie.dotsrc.org/)

**G. ADDENDUM: NOW THE CONNECTIVITY TROUBLESHOOTING FUN BEGINS! MORE, ANON!**

---

### Post by ingo on 2007-01-07
Excellent stuff! How about WEP and WPA? Is it capable of any of that?

---

### Post by maclenin on 2007-01-08
Thanks for the feedback. As far as WEP and WPA are concerned, I am now looking into a handful of things more related to just maintaining a consistent connection. Secure network protocols will soon follow!

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

Again, thanks for the post....

---

### Post by lukemack on 2007-01-14
i cannot mount /dev/hda1 and get the error - cant find /dev/hda1 in fstab or mtab. hda1 is the location of my windows partitions.

however, i can see it when i issue fdisk -l.

is there any way round this?

thanks,

lukemack.

---

### Post by maclenin on 2007-01-15
lukemack: I would make certain the syntax is correct - and try again - if you are still having issues, copy and paste this command into your terminal:

sudo mount /dev/hda1 /c -t ntfs

Also, you might want to confirm that "hda1" is, indeed, the NTFS partition....

Finally, take a peek at this link for additional mounting help (there is an extra step re: modifying the fstab file that might help you - I did NOT modify my fstab file):

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Good luck.

---

### Post by lukemack on 2007-01-15
thanks - i did have to modify the fstab file to get this working. not sure why though.

---

### Post by maclenin on 2007-01-15
Have you gotten your card up and running? Are you having any connectivity issues?

Take a peek at...

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

...because I am (having connectivity issues).

Glad you made some progress!

---

### Post by emeraldjay on 2007-01-16
I'll commend you for being so persistent with fwcutter. I didn't have such patience. I do remember finding a link to a repository somewhere in the forums that would have made life a little easier. I wish I had the link handy to give you.

If you don't mind I would like to offer a bit of a critique and maybe some help in the process.

You don't have to make a separate directory for fwcutter. If it helps to make one open a terminal and do:
```
mkdir ~/utilities
```
copy your tarfile to that directory or untar it to that directory. Try not to use sudo when doing "make" just for "make install", also there is no need to chmod anything, the "make install" command will do that on its own. Instead using your steps do this"
```
tar jvfx bcm43xx-fwcutter-006.tar.bz2
```
if you really want to use the "-C" option of tar do this:
cd to the directory in XP where the tar file is, then
```
tar jxvf bcm43xx-fwcutter-006.tar.bz2 -C ~/utilities
```
that will unpack the tar file into the utilities subdirectory of your home directory . Then you can "make" without the sudo, then "sudo make install".

Sorry I am a fanatic about the use of sudo/gsudo/su/root. I've heard horror stories of people really thrashing their system from improper use of root priveledges. I don't know how much success you have had so far, but my experience was good but not great. I was only able to get an 11mb connection instead of a 54mb connection, so I switched to using ndiswrapper.  I still haven't found out if I can get an 802.11a connection since while my card may be dual band, my router at home is only equipped for 802.11b/g.

---

### Post by CCBalla10 on 2007-01-16
Hey guys i too have the 4306 and Edgy....but there is a much more simple route.  I used Ndiswrapper and have had no problems in a long time.  Always works!....here is the link[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper[/HTML]

**One thing, after you blacklist the bcm43xx driver, bookmark that page and restart your computer....**

---

### Post by maclenin on 2007-01-16
Thanks guys for the critique / suggestions - much appreciated.... I  have, actually, ended up taking the ndis route, as well - and am writing this note via my newly-found wireless bliss.

For reference, see:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)

Again, thanks for the observations!

---

### Post by lukemack on 2007-01-17
i did notice the connection was a bit flaky so have tried installing the ndiswrapper driver. however, when i get to sudo modprobe ndiswrapper, i get the following error:

FATAL:Error inserting ndiswrapper (/lib/modules/2.6.17-10-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):invalid argument.

anyone got any ideas what is causing this?

thanks <L>

---

### Post by maclenin on 2007-01-17
There is a conflict related to the version numbers of the ndiswrapper utility - not really sure exactly what's up - but I think this should help you :

Take a peek at this [guide]("http://ubuntuforums.org/showthread.php?p=2027150#post2027150") - hot off the presses....

Good luck!

---

### Post by lukemack on 2007-01-17
thanks but i get the error described and so need to do this:

sudo aptitude install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper

however, nothing gets installed. the package cant be found and i dont have an internet connection. i;ve also tried installing direct off the cd but no joy.

i get 'no candidate version found for ndiswrapper-utils' (also get this error when trying utils-1.8)

never thought i would say it but drivers on windows are a piece of cake compared to this.

---

### Post by maclenin on 2007-01-17
As I start to get the hang of it (or think I'm getting it) - I am learning to love the flexibility and control in linux that windows does not provide....

I am quite certain the guide I've posted requires an internet connection - though there may be work-arounds - and I think I've come across some of them on line - just don't remember where....

How are you posting these comments? Is there any way you could plug the ethernet cable into the computer you are tying to configure to help complete the wireless install? That's what I ended up finally doing after hours of unwired toil!

---

### Post by maclenin on 2007-01-17
Folks, I have been able to get ndiswrapper installed - and [working]("http://ubuntuforums.org/showthread.php?p=2027150#post2027150").... emeraldjay, feel free to have another walkabout through my ndiswrapper guide - with the same sudo issues in mind - I think I might have strayed a bit - again.... Also, forgive my ignorance - what is the "~" symbol? I am getting ready to do a clean install of linux and want to make certain I set it up logically and securely - I appreciate the commentary....

---

### Post by ingo on 2007-01-18
the tilda usually stands for your home directory

---

### Post by maclenin on 2007-01-18
Thanks. As opposed to "/home" - are they two different locations (~ and /home)? Or just different syntax? And I am not certain I fully grasp the difference between "/" and "/root".... I am getting ready to install linux and partition the drive (mono-boot - wiping windows clean) - and want to make the setup logical and secure...still need to do more reading on the directory stucture / logic....Thanks for the help.

---

### Post by maclenin on 2007-01-31
The [**latest**]("http://ubuntuforums.org/showthread.php?t=340689")....

---

