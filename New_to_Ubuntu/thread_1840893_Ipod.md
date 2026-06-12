---
title: "Ipod"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by cstambaugh on 2011-09-08
Is there any way to Install my IPOD touch using Ubuntu? Many of the forums I have searched say no, But since you guys helped me a few minutes ago I figured Id ask here.

---

### Post by Johnb0y on 2011-09-08
see: [http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by Johnb0y on 2011-09-08
top 10 alternatives: [http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/](http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/)

---

### Post by Johnb0y on 2011-09-08
could also try using WINE with itunes... some people have said they can.. but some say they cant...

---

### Post by cstambaugh on 2011-09-08
I cannot even get my ipod to be reckognized by the system much less do anything else.
How do I mount the IPOD ? It is an IPOD touch think it is version 2.

---

### Post by ubudog on 2011-09-08
> **cstambaugh said:**
> I cannot even get my ipod to be reckognized by the system much less do anything else.
How do I mount the IPOD ? It is an IPOD touch think it is version 2.

Can you plug in the iPod, and then post the output of:
```
lsusb
```?

---

### Post by Johnb0y on 2011-09-09
could try this: [http://ostatic.com/blog/linux-and-your-iphone-ipod-touch](http://ostatic.com/blog/linux-and-your-iphone-ipod-touch)

---

### Post by switch10 on 2011-09-09
> **cstambaugh said:**
> Is there any way to Install my IPOD touch using Ubuntu? Many of the forums I have searched say no, But since you guys helped me a few minutes ago I figured Id ask here.

What do you mean by "install your Ipod"? 

If it is a brand new device, never connected to Itunes, you will have to connect it to Itunes, I don't think there is any way of getting around that.  You can forget about Itunes via wine since wine does not support USB.  Borrow a friends windows or mac system.

After that, your ipod will be usable with banshee or rhythmbox.

---

### Post by nns2006 on 2011-09-09
> **cstambaugh said:**
> I cannot even get my ipod to be reckognized by the system much less do anything else.
How do I mount the IPOD ? It is an IPOD touch think it is version 2.

for the first time you will need a windows/mac system. However, if this is not the first time you can use Gtkpod from synaptic. It recognises my ipod and you can manage your songs in here. 
Good Luck.

---

### Post by cstambaugh on 2011-09-09
@UBUDOG

Sorry for the delay I had classes last night. Im in school for IT but they do not teach Linux so I am trying to self teach with help of a few forums and google. Been a few months now on it and have specific laptop just for Ubuntu.
Here is the result of the command:

chris@chris-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1299 Apple, Inc. 
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-laptop:~$ 

I have GTKpod  but for some reason nothing "sees" the IPOD. It says Unable to mount IPOD device does not exist in the only place it ever showed up, under places menu, but thats there even when the IPOD is not attached.
Thanks in advance
Chris

---

### Post by ubudog on 2011-09-09
Well, it looks like your computer sees the iPod (Apple Inc.)

Have you tried Banshee?  It's not iTunes, but it does support syncing.

Alternatively, you could install KVM or VirtualBox, and create a virtual machine for Windows.  You could then run Windows (which supports iTunes) inside of Ubuntu (in a window).  Here is a good guide:

[http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux](http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux)

;-)

---

### Post by cstambaugh on 2011-09-09
it sees it but I get this error 

mount: special device /dev/sdc2 does not exist 
Any program, (banshee included) gives this same error
Is there a code I need to edit to make it mount?

---

### Post by ubudog on 2011-09-09
Have you tried this:
[http://ubuntuforums.org/showthread.php?t=411364](http://ubuntuforums.org/showthread.php?t=411364)
?  

Also, make sure the device is unlocked if it requires a password before mounting.

---

### Post by cstambaugh on 2011-09-09
Tried opening the FSTAB file and this is what mine says.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5fbb5813-f0d2-4782-ab18-f83aa81cef53 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=afdea240-698c-4360-9a92-055ab95d7030 none            swap    sw              0       0




/dev/sdc2    /media/iPod vfat    nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8    0 0


There is no password needed, it is unlocked
I came across this once before searching and his fix was to have power to his external USB hub. I am directly plugging in to a usb port on my laptop
mine has never mounted so I didnt think this applied to me.

---

### Post by nns2006 on 2011-09-09
> **cstambaugh said:**
> @UBUDOG

I have GTKpod  but for some reason nothing "sees" the IPOD. It says Unable to mount IPOD device does not exist in the only place it ever showed up, under places menu, but thats there even when the IPOD is not attached.
Thanks in advance
Chris

Install usbmuxd
it is in synaptic. Hope this helps.

---

### Post by cstambaugh on 2011-09-09
Usbmuxd is already installed. :confused:

---

### Post by cstambaugh on 2011-09-09
So does anyone know the code or what file needs to be changed to allow this to be mounted?

---

### Post by ubudog on 2011-09-09
Try this:
Plug in the iPod, then post here the output of:
```
ls /media
```

and:

```
mount
```

---

### Post by cstambaugh on 2011-09-09
chris@chris-laptop:~$ ls /media
iPod
chris@chris-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
chris@chris-laptop:~$

---

### Post by ubudog on 2011-09-09
That looks good so far.  Try:
```
ls /media/iPod
```

Do you see anything?  Did it give an error?

---

### Post by cstambaugh on 2011-09-09
chris@chris-laptop:~$ ls /media.ipod
ls: cannot access /media.ipod: No such file or directory
chris@chris-laptop:~$

---

### Post by ubudog on 2011-09-09
It appears you made a typo.

```
ls /media/iPod
```

---

### Post by cstambaugh on 2011-09-09
sorry... here is the right post

chris@chris-laptop:~$ ls /media/ipod
ls: cannot access /media/ipod: No such file or directory
chris@chris-laptop:~$ ls /media/Ipod
ls: cannot access /media/Ipod: No such file or directory
chris@chris-laptop:~$

---

### Post by ubudog on 2011-09-09
Still made a typo.  

Just copy and paste the following:
```
ls /media/iPod
```

Happens to the best of us.  :P

---

### Post by cstambaugh on 2011-09-09
it didnt do anything but go to another command line

---

### Post by ubudog on 2011-09-09
Can you post a screenshot of the window after you typed:
```
ls /media/iPod
```
please?

---

### Post by cstambaugh on 2011-09-09
ls /media/iPod

---

### Post by cstambaugh on 2011-09-09
[FONT=monospace]I cant paste the screenshot for some reason... 


bash: ls/media/Ipod: No such file or directory
chris@chris-laptop:~$ ls /media/iPod
chris@chris-laptop:~$ ls /media/iPod
chris@chris-laptop:~$ 

[/FONT]

---

### Post by ixtok on 2011-09-09
I am happy running Itunes through VirtualBox. I use the virtual box available through the virtualbox.org web site and I installed the guest additions and the extension packages. I run windows xp as the guest system and find it runs almost as well as a native windows installation.I am running Ubuntu 10.10 and find Windows XP runs better in virtual box than ubuntu 11.04 does.

---

### Post by cstambaugh on 2011-09-09
my issue isnt with running itunes it is with mounting the IPOD with the USB. It isnt even reckognized by the computer to run with any of the Itunes alternatives, and I tried using the virtual box route and it didnt work as well. My computer sees the Ipod, but does not mount the volume, like it does when i hook a flash drive or external hard drive. 
Thanks for the try.

---

### Post by ubudog on 2011-09-09
Give this a try and see if it helps:
[http://blog.christinaoutlay.com/2008/05/28/ipod-wont-mount-in-ubuntu-did-you-try-to-set-a-mount-point-and-instead-screwed-up-something-try-this-fix.aspx](http://blog.christinaoutlay.com/2008/05/28/ipod-wont-mount-in-ubuntu-did-you-try-to-set-a-mount-point-and-instead-screwed-up-something-try-this-fix.aspx)

Sorry this is taking so long...

---

### Post by cstambaugh on 2011-09-10
Its ok I just want to get it taken care of, and learn along the way.
I tried this and I do not have the storage listed. 
I trued using sudo, and gksudo to open this and no listing on either one for storage. I cannot log in as administrator on log in screen, I do not know why, but thought sudo and gksudo were admin priveleges for temp usage.

---

### Post by cstambaugh on 2011-09-11
Im still not able to find my Ipod. Is there a etc file or mount file that I manually have to see if has been altered, or needs to be altered to allow access to my Ipod? I tried alot so far, I do not understand why this is so difficult, ready to throw the Ipod away and get a generic Mp3 player instead.... Damn apple!

Please any other suggestions feel free to submit, Im willing to try anything still.

thanks

---

### Post by ubudog on 2011-09-11
Running out of suggestions here... 

Have you tried iFuse?
[http://www.ghabuntu.com/2009/09/ifuse-mount-your-iphoneipod-touch-in.html](http://www.ghabuntu.com/2009/09/ifuse-mount-your-iphoneipod-touch-in.html)

---

### Post by fdrake on 2011-09-11
i think the issue here that the ipod's filesystem is not mounted even if the lsusb recognizes the device in the port. The ipod's OS is still using the filesystem so that it cannot be mounted on you pc. Check your ipod connection options.

(Un)fortunately i do not have an iPod so i cannot test this. Make sure that before plugging the ipod you do not have any file/song in use, and make sure it's not looked. second plug the ipod and run:
```

sudo fdisk -lu
sudo lsusb -vvvs 001:003

```

post here the results here. Also can you give us a detailed description of the model/generation of your iPod?

---

### Post by cstambaugh on 2011-09-11
@ Ubudog 
I feel this would work, except that I have a entry that is already called Ipod, whether its mounted or not, listed under places in the menu, and I cannot delete it. I feel this may work, if I can delete these entries, because whenI click on them , i get my original eror that the special device does not exist.
How can I delete this I beleve it may be the etc file, I may be wrong, throwing a guess out there.

---

### Post by cstambaugh on 2011-09-11
@ Fdrake

chris@chris-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006aed4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   470450175   235224064   83  Linux
/dev/sda2       470452222   488396799     8972289    5  Extended
/dev/sda5       470452224   488396799     8972288   82  Linux swap / Solaris
chris@chris-laptop:~$ sudo lsusb -vvvs 001:003
chris@chris-laptop:~$

---

### Post by ubudog on 2011-09-11
> **cstambaugh said:**
> @ Ubudog 
I feel this would work, except that I have a entry that is already called Ipod, whether its mounted or not, listed under places in the menu, and I cannot delete it. I feel this may work, if I can delete these entries, because whenI click on them , i get my original eror that the special device does not exist.
How can I delete this I beleve it may be the etc file, I may be wrong, throwing a guess out there.

Unplug your iPod, then restart your computer, and follow that guide.

Also, try what fdrake said.

---

### Post by cstambaugh on 2011-09-11
I did, and it is still there. Ipod is not plugged in, computer restarted, still listed. I believe somewhere along the lines someone told me to change a line somewhere and that may be why it is listed, but I cannot remember what line and what page.or what file. In linux, what controls the file listings on the places menu?

it wasnt in this posting thread that someone told me to add the line, so I cant go back and see it. I have to go out and cut the grass now.. :-( Ill be back in to check this later. Thanks again for your help

---

### Post by fdrake on 2011-09-11
> **cstambaugh said:**
> I did, and it is still there. Ipod is not plugged in, computer restarted, still listed. I believe somewhere along the lines someone told me to change a line somewhere and that may be why it is listed, but I cannot remember what line and what page.or what file. In linux, what controls the file listings on the places menu?

that's not really a problem. ipod folder is just the mount-point for your ipod filesystem. 
do:
```
 nautilus ~/
``` and you should see on the left a side bar (if not press f9 ). you can right click the list and delete/add the entries.
But that's not the issue. Make sure when you follow that guide to change the release name to yours.

to find the name do
```

less /etc/lsb-release

```
and use the "code-name"

---

### Post by cstambaugh on 2011-09-11
Didnt work either, and when I open Nautilus I cant remove the Ipod listing, the option is not lighted. I dunno, I guess maybe ill just keep windows dual booted on my other machine unfortunately, and use it that way. I guess this wont work on this for some reason. thanks for the help, im at the point where Im done trying things for now, I want to throw this through the window!!! Why does apple have to be such a prick!! Thanks for all your help guys, I appreciate it

---

