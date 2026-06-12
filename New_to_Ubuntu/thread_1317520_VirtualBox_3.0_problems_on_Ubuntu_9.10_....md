---
title: "VirtualBox 3.0 problems on Ubuntu 9.10 ..."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by ltipto1 on 2009-11-06
I installed VirtualBox and discovered that the OSE version doesn't include USB support.  I used Ubuntu Software Center to remove the program.  I then jumped through the hoops to install the right repository and installed VirtualBox 3.0 CSE which DOES support USB.  However, when I try to run it I get an error:

"Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

I'm a noobie, and don't know what to do from here...  Any suggestions...

---

### Post by ricardo.gloe on 2009-11-06
Open a terminal (Applications,Accessories).

Type: sudo /etc/init.d/vboxdrv setup

Wiat until it finishes and then you should be able to open your vm's.

Probably the next time you boot, you'll get the same error and have to repeat this process. 
 

I have the exact same problem and still haven't found the permanent solution.

---

### Post by ltipto1 on 2009-11-06
error:

sudo: /etc/init.d/vboxdrv: command not found


Now what?

---

### Post by ricardo.gloe on 2009-11-06
You typed " sudo: /etc/init.d/vboxdrv: command not found " ?

try without the colon after sudo

it's just " sudo /etc/init.d/vboxdrv "

---

### Post by Merk42 on 2009-11-06
Copy paste this to make sure you don't mistype
```
sudo /etc/init.d/vboxdrv setup
```
This is mentioned on page 23 of the [Virtualbox manual](http://download.virtualbox.org/virtualbox/3.0.10/UserManual.pdf)

---

### Post by ltipto1 on 2009-11-06
Here is a copy of my terminal session...


larry@larry-linux:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for larry: 
sudo: /etc/init.d/vboxdrv: command not found
larry@larry-linux:~$

---

### Post by howefield on 2009-11-06
When you reinstalled, did you check you were still in the vboxusers group ?

---

### Post by ricardo.gloe on 2009-11-06
Have you tried uninstalling and re-installing Virtualbox?

If you haven't, try that and then check the /etc/init.d folder for the vboxdrv file. Also check /dev for vboxdrv. 


If both these files are present, then open and check /etc/modules file if there is an entry: vboxdrv. If not, you have to include this. It's a readonly file, so there'll be some steps to change it.

I just included this and finally fixed the problem permanently. I'v rebooted three times and everytime the vm's have started ok.

---

### Post by ltipto1 on 2009-11-06
I'll try that... It might take me awhile...I'll let you know the result.

---

### Post by ltipto1 on 2009-11-06
When I uninstalled the first time, earlier tonight, I must not have done a "complete" uninstall...  Some stuff was obviously left over.  Because when I did it this time it popped up the "users" dialog, which it didn't do the first time.

VirtualBox 3.0 now works!  And when I started up the VB Windows XP Pro it found new hardware and installed the USB stuff.  I put in a USB drive and it didn't see it, but I think I can fix that with VirtualBox configuration.  It's not seeing the CD/DVD drive either.  But, that is half the fun, Right?  Right?  LOL

Thanks for the help.

---

### Post by Merk42 on 2009-11-06
Open up Virtualbox, but not the machine.
Go to Settings:
for CD/DVD Rom you can either use your host machines drive or mount an iso file.
for USB you need to add a filter, probably the plus sign.

---

### Post by aitjcize on 2009-11-08
> **ricardo.gloe said:**
> Open a terminal (Applications,Accessories).

Type: sudo /etc/init.d/vboxdrv setup

Wiat until it finishes and then you should be able to open your vm's.

Probably the next time you boot, you'll get the same error and have to repeat this process. 
 

I have the exact same problem and still haven't found the permanent solution.

I think it's because of the new Upstart
dmesg | grep VirtualBox
=> Nothing...

vboxdrv is not load at startup
just type:
sudo /etc/init.d/vboxdrv start

you don't have to compile it again...

---

### Post by ario on 2010-01-26
God bless you "aitjcize"
The command:
```
sudo /etc/init.d/vboxdrv start
```
Worked for me and saved my time a lot!
Thanks for your help:)

---

