---
title: "Installing kernel 2.6.35 from official repositories?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by legolas_w on 2010-08-06
Hi,

Can someone please confirm whether the 2.6.35 kernel will be available for ubuntu 10.4 from the official repos or we should use some PPA to install it.

I read the related news at [http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html](http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html)


Thanks,

Masoud.

---

### Post by Bachstelze on 2010-08-06
I don't know what Ryan has been smoking, it seems very unlikely to me that the kernel team would make such a big leap in a current stable release.  AFAIK, you have to get it from git or a PPA.

---

### Post by Vincentlaborant on 2010-08-06
Ubuntu 10.04 LTS will stay on 2.6.32-xx for the full length of the support term as it is a LTS release.

If you need the 2.6.35 kernel because it gives you better functionality of hardware (e.g. wireless networking) then you could get the new kernel from [http://kernel.org]("http://kernel.org/") , or get it via a Debian repro (don't know the last one for sure).

On Ubuntugeek a simple manual is posted on  how to update your kernel (if you wish).

---

### Post by inameiname on 2010-08-06
The official repos will not go any farther than 2.6.32. 

However, you can install the latest, 2.6.35, simply by typing the following into the terminal:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

And whenever a new kernel update comes out, just type "2.6.35" or whatever into the Synaptic Package Manager and installing (for the current kernel for example):

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic 
linux-image-2.6.35-14-generic

Sadly, unlike the official repos kernels, they won't automatically update. You have to do a search occasionally, such as in Synaptic, and do the same to see if a later version has been added into the PPA.

---

### Post by Elfy on 2010-08-06
> **Bachstelze said:**
> I don't know what Ryan has been smoking, it seems very unlikely to me that the kernel team would make such a big leap in a current stable release.  AFAIK, you have to get it from git or a PPA.

Not as far as I know related to u-g here.

---

### Post by legolas_w on 2010-08-06
> **inameiname said:**
> The official repos will not go any farther than 2.6.32. 

However, you can install the latest, 2.6.35, simply by typing the following into the terminal:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

And whenever a new kernel update comes out, just type "2.6.35" or whatever into the Synaptic Package Manager and installing (for the current kernel for example):

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic 
linux-image-2.6.35-14-generic

Sadly, unlike the official repos kernels, they won't automatically update. You have to do a search occasionally, such as in Synaptic, and do the same to see if a later version has been added into the PPA.

Hi,

When I try these commands it shows the following output:

```
The following NEW packages will be installed:
  linux-headers-2.6.35-14{a} linux-headers-2.6.35-14-generic 
  linux-image-2.6.35-14-generic 
The following packages will be REMOVED:
  libparted0{u} libwebkit1.1-cil{u} 
0 packages upgraded, 3 newly installed, 2 to remove and 1 not upgraded.
```

Is this output ok? My OS is 10.04 64 bit.

Thanks.

---

### Post by inameiname on 2010-08-06
Yeah, that looks just fine. It will install those three and remove those two. And if you want that one that needs upgraded, you can either use the Update Manager as normal, or after those three terminal commands are done that I gave you, use:

sudo apt-get upgrade

Just remember you won't be using the latest kernel until you restart. After that, you can remove the old one if you desire. Of course, make sure the latest one seems to work alright for you. It's just it's an extra 200mb, so I often remove the older ones when I'm sure the newest works.

---

### Post by slooksterpsv on 2010-08-06
I'm in, there's a lot of updates in the 2.6.35 kernel that I want to have on my system. So I'm installing the kernel as well.

Let's hope it works, and works well.

Rebooting to see how my hardware handles the new kernel.

EDIT: Nope it horribly did not work well, I have to go back to the previous kernel and install my graphic drivers again, it killed them.

---

### Post by inameiname on 2010-08-06
Really? Wow..sorry to hear that. I've been using the newest one for a few days now and have found no problems at all on my 3-year-old Gateway laptop.

---

### Post by slooksterpsv on 2010-08-06
> **inameiname said:**
> Really? Wow..sorry to hear that. I've been using the newest one for a few days now and have found no problems at all on my 3-year-old Gateway laptop.

Oh here's how I had to get it working:
1. Remove the 2.6.35 kernel, as fglrx crashed during the installation of the kernel
2. Restart and boot to the normal 2.6.32 kernel
3. Remove fglrx, fglrx-amdcce (some name like that) and one other package, automatically removed with fglrx
4. Tried running /usr/share/ati/fglrx-uninstall.sh - it would error out, so I had to remove /usr/share/ati
5. Reboot in safe graphics mode
6. Remove /etc/X11/Xorg.conf*
7. Reinstall fglrx, which ran dkms to update the kernel
8. Run sudo aticonfig --initial
9. Reboot
10. Enable composition - System -> Preferences -> Appearance -> Visual Effects -> Normal

Talk about a lot.

EDIT:
With BURG, I also had to run update-burg after removing (and installing) kernel 2.6.35

---

### Post by inameiname on 2010-08-06
That's is a lot. Glad though you were able to figure out the issues and repair yourself. It could've been even more disastrous.

---

### Post by slooksterpsv on 2010-08-10
> **inameiname said:**
> That's is a lot. Glad though you were able to figure out the issues and repair yourself. It could've been even more disastrous.

BOOYA! I got it to work, here's how.

Installed the kernel 2.6.35, as previously mentioned on post 2 or 3. Next it removed all my fglrx, fglrx-amdcccle, etc. I updated grub and burg, restarted the computer.

I tried to install fglrx, but it failed, same issue as last time, so I told it to remove fglrx, now it removed that so I downloaded the ati catalyst 10.7 driver and installed it from there, 8.753, after that I ran in a terminal, aticonfig --initial - restarted the computer and it works.

Hardware drivers doesn't show that one's installed, but composition is working, and it's not tearing or showing artifacts.

Testing a 3d game... ut2004, give me a few... it works.

The whole system feels new, its so fast!

---

### Post by inameiname on 2010-08-10
Woohoo! Faster is better! I like the new kernel as well.

---

### Post by sls54 on 2010-08-16
I have the newer kernels in two different formats & don't know what to do with them.  I want to install one of these kernels on my netbook.
 
linux-2.6.35.2.tar.bz2 or
 
linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
linux-source-2.6.34_2.6.34-020634_all.deb
 
I put them on my LinuxLive usb Key (Ubuntu netbook remix 10.04) in a folder. I can run from virtual box on my desktop online or from my netbook with no network. Either of these kernels should have the driver to make the netbook ethernet work. I have no CD drive on the netbook so it's usb or nothing except the netbook is dual boot with windows7 & the network is good in windows.
 
Can I update the kernel on the usb key from the virtual box & then install onto my netbook or try updating the kernel on the netbook without network support? I'm a Linux newbie so I barely know how to run virtual box or find what I need. Am I automatically the virtual box administrator? None of the sudo apt-get commands etc. seem to do what I expect. They can't find files or seem to fail in some manner.

---

### Post by malikkabanis on 2010-09-02
hi friends,

i m new to ubuntu 10.04 (lucid) 32 bit operating system
kernel linux 2.6.32-24-generic

but i use dell 1564 64 bit computer.

now i want to upgrade ubuntu 10.04 (lucid) 32 bit operating system
kernel linux 2.6.32-24-generic to kernel 2.6.35-19 with below procedure because i have suspend/resume problem

"""----However, you can install the latest, 2.6.35, simply by typing the following into the terminal:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

And whenever a new kernel update comes out, just type "2.6.35" or  whatever into the Synaptic Package Manager and installing (for the  current kernel for example):

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic 
linux-image-2.6.35-14-generic -----""""

from synaptic package manger 

i have chosen 

linux-headers-2.6.35-19
 linux-headers-2.6.35-19-generic 
 linux-image-2.6.35-19-generic

should i go ahead?
will break my system?

anad what is again "linux-generic meta-package" i didnt fine it in synaptic package manager..
from where can i get it??
please help me.

---

### Post by inameiname on 2010-09-02
As I said in your private message, you should be fine. Just do this and you'll install it:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-19-generic linux-image-2.6.35-19-generic

FYI, if it doesn't work well for you, you can always go back to your old kernel.

---

### Post by malikkabanis on 2010-09-03
> **inameiname said:**
> As I said in your private message, you should be fine. Just do this and you'll install it:
 
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-19-generic linux-image-2.6.35-19-generic
 
FYI, if it doesn't work well for you, you can always go back to your old kernel.
--
Oops, I'm sorry. Not:
 
sudo apt-cache search linux-generic
 
but:
 
sudo apt-cache policy linux-generic
 
It will output this:
 
linux-generic:
Installed: (none)
Candidate: 2.6.32.25.27
Version table:
2.6.32.25.27 0
500 [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") lucid-proposed/main Packages
2.6.32.24.25 0
500 [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") lucid-updates/main Packages
500 [[COLOR=#444444]http://security.ubuntu.com/ubuntu/[/COLOR]]("http://security.ubuntu.com/ubuntu/") lucid-security/main Packages
2.6.32.21.22 0
500 [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") lucid/main Packages
 
As you can see from mine, it's not installed. It was removed when I removed the old kernel.
--
 
OMG!
i installed new kernel yesterday.... and i was not having that software... now????
but after installing kernel 2.6.35-19 i didnt see it anywhere...
boot screen was not showing any new options 
 
it like this only all old options
 
ubuntu 64 bit
ubuntu 64 bit written something else with it
memory test
memory test written something else with it
windows 7
ubuntu 32 bit 2.6.32-24
recovery ubuntu 32 bit 2.6.32-24
ubuntu 32 bit 2.6.32-23
and many more like this 22 and 21 and all 
 
and there was no 2.6.35-19,,, why???
 
more info:
i bought dell 1564 with and installed windows 7 and dan friend gave me fully loaded with all softwares ubuntu 32 bit lucid with 2.6.32-24. and dan i installed ubuntu lucid 64 bit recently..
dose it meter ???

---

### Post by malikkabanis on 2010-09-03
thanx

---

### Post by inameiname on 2010-09-03
Once the newest kernel is installed, you need to reboot for the computer to boot with it. If it isn't booting with 2.6.35-19 but the 2.6.32 one, then something went wrong. I'm afraid I don't really know what could have happen if you followed the directions I put above. Uhm, how about 'sudo apt-cache policy linux-image-2.6.35-19-generic'? Is should say that it's installed. If not, then the problem lies in it not have been installed. 

And as far as your 64-bit question, I'm afraid I don't understand. Do you mean it was previously installed with a 32-bit version of Ubuntu Lucid, but was installed over by a 64-bit one? If your computer can run 64-bit, you should have no issues. Not sure if it'd even work if you installed a 64-bit version and your computer was merely 32-bit. Software-wise though, you can install all the 32-bit software you want on a 64-bit Ubuntu Lucid if you'd like. Not sure about the other way around as I've never had a 64-bit computer before.

---

### Post by malikkabanis on 2010-09-03
> **inameiname said:**
> Once the newest kernel is installed, you need to reboot for the computer to boot with it. If it isn't booting with 2.6.35-19 but the 2.6.32 one, then something went wrong. I'm afraid I don't really know what could have happen if you followed the directions I put above. Uhm, how about 'sudo apt-cache policy linux-image-2.6.35-19-generic'? Is should say that it's installed. If not, then the problem lies in it not have been installed. 
 
And as far as your 64-bit question, I'm afraid I don't understand. Do you mean it was previously installed with a 32-bit version of Ubuntu Lucid, but was installed over by a 64-bit one? If your computer can run 64-bit, you should have no issues. Not sure if it'd even work if you installed a 64-bit version and your computer was merely 32-bit. Software-wise though, you can install all the 32-bit software you want on a 64-bit Ubuntu Lucid if you'd like. Not sure about the other way around as I've never had a 64-bit computer before.
 
1st i installed windows 7 
2dn i installed ubuntu lucid 32 bit
3rd i installed ubuntu lucid 64 bit
 
ok i informed you becuase since i installed ubuntu lucid 64 bit it was default selection in boot screen of grub..
 
and i wanted to make ubuntu lucid 32 bit defaul selection which is on 6th row of boot screen..
 
so i tried to change grub in ubuntu 32 bit and i edited grup.cnf to make ubuntu lucid default selection and updated grub.. but it didnt work..
 
dan i restarted computer and changed grup in ubuntu lucid 64 bit made ubuntu lucid 32 bit default by changing grub of ubuntu 64 bit and dan it worked..
 
so i m not sure but i think tht grub of ubuntu 64 bit has taken over and therefore i dont see my new installed kernel in ubuntu lucid 32 bit..
 
and soon i will be sending out put of 'sudo apt-cache policy linux-image-2.6.35-19-generic'
 
so i can know it ws installed or not..
 
once again thank you very much.

---

### Post by inameiname on 2010-09-03
Oh I see. Well, perhaps an easier way to make the 32-bit Lucid default would be to install startupmanager rather than manually tweaking what boots:

sudo apt-get install startupmanager

I'm curious, why have a 32-bit and a 64-bit Ubuntu Lucid on the same computer? Is there a reason for that?

---

### Post by malikkabanis on 2010-09-03
> **inameiname said:**
> Oh I see. Well, perhaps an easier way to make the 32-bit Lucid default would be to install startupmanager rather than manually tweaking what boots:

sudo apt-get install startupmanager

I'm curious, why have a 32-bit and a 64-bit Ubuntu Lucid on the same computer? Is there a reason for that?

i have installed 64 bit bcoz i have 64 bit laptop.
and my friend gave me ubuntu lucid 32 bit with many preinstalled softwares and to install all those software on my 64 bit at speed of 10KBPS it will take months to download all there.. therefore i have installed it and downloading softwares slowly slowly on it..

is there any way to migrate all my software to 64 bit from my 32 bit??

and btw thank you for your help.. when i installed kernel it was installed properly and i was not seeing in grub list but when i updated grub of lucid 64 bit with sudo update-grub and restarted computer i saw my 2.6.35-19 there . yahoooo.. i did it.. thank you..
and now i new karnel broken my broadcom wireless :( . 
plz help me to for my broadcom wireless work on kernel 2.6.35-19

---

### Post by beloved88 on 2010-09-06
yes, i had a similar issue.  You have to patch and rebuild that driver.  This is where you can get the driver, [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
it's a hybrid driver, meaning it's compiled, but not built (i think), but it needs some patches for 2.6.35, download the driver and patches, and extract them all to the same folder.  Then run the following from that folder's directory
$ patch -p0 < patch
$ patch -p0 < patch_hybrid_multicast
$ make
and your driver is built
now you have to install it.
run this as root
# cp wl.ko /lib/modules/2.6.35-19-generic/kernel/net/wireless/wl.ko
# depmod
# modprobe wl
and that should do it

---

### Post by malikkabanis on 2010-09-24
> **beloved88 said:**
> yes, i had a similar issue.  You have to patch and rebuild that driver.  This is where you can get the driver, [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
it's a hybrid driver, meaning it's compiled, but not built (i think), but it needs some patches for 2.6.35, download the driver and patches, and extract them all to the same folder.  Then run the following from that folder's directory
$ patch -p0 < patch
$ patch -p0 < patch_hybrid_multicast
$ make
and your driver is built
now you have to install it.
run this as root
# cp wl.ko /lib/modules/2.6.35-19-generic/kernel/net/wireless/wl.ko
# depmod
# modprobe wl
and that should do it

i had removed 2.6.35-19 generic from ubuntu because it created some problem with BCMWL-KERNEL-GENERIC and all .DEB packages i was installing ws showing install fail message.

now i want to  upgrade kernel but i m confuse about which .deb i have to install on dell 1564 - OS ubuntu 10.04 32bit?? i386.deb or amd64.deb??? :(

---

### Post by snowpine on 2010-09-24
> **malikkabanis said:**
> now i want to  upgrade kernel but i m confuse about which .deb i have to install on dell 1564 - OS ubuntu 10.04 32bit?? i386.deb or amd64.deb??? :(

Use the terminal command 'uname -a' to figure out which is the correct architecture for your system. :)

---

### Post by slooksterpsv on 2010-09-27
Ok so I can verify the following - if you take the steps I did to install the ATI Graphics drivers for 2.6.35-14, you can use Catalyst 10.9.

Here's what you do:
Following post #2 or #3 add the PPA's and then install Kernel 2.6.35-14.
Reboot
Open a terminal and remove fglrx via: sudo apt-get remove fglrx
Now download ATI Catalyst drivers and install via terminal:
sudo ./ati-driver-installer-10-9-x86.x86_64.run
Go through the installation taking the defaults, when it shows exit, click on Exit.
Now in terminal type in: sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup.conf
Now in terminal type: sudo aticonfig --initial
Reboot =D

And you're done!

---

