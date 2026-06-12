---
title: "Linksys WUSB11 v2.6"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by e&gt;&lt;ogenic on 2009-05-14
Hi all :)

I was hoping someone might be able to help me get my wireless internet access up and running in Ubuntu 9.04.

I did a fresh install from the CD yesterday but can't get any internet access. My wireless adapter is the Linksys WUSB11 v2.6. My network uses WEP encryption (not so great, I know, but it's the only option supported my my router). I assigned my computer a static IP address in Windows and believe I have all the pertinent information (although I trip up a little on the difference between SSID and BSSID, and am not really sure what MAC address I need or how to find it, or even if I need it at all).

I am currently dual-booting with Windows XP Home SP3 and have internet access (which works perfectly) via my Windows install.

I'm still pretty new to Linux, so 'Instructions for Dummies' would be appreciated :)

I tried following through this article:
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)
...on the community documentation pages, but apparently cvs  is not on the Ubuntu CD I have (I successfully installed the build-essential package and dependencies from the same CD). I also got an error message when trying to run the 'make' command inside the extracted cvs snapshot folders from that article.

From my limited knowledge of Linux so far I understand that the driver for my wireless adapter is part of the Linux Kernel. I've also heard that some people are experiencing problems configuring wireless connections via Network Manager.

Any help would be greatly appreciated!

---

### Post by mapes12 on 2009-05-14
You may be able to configure a fix using the howto you referred to or by setting up ndiswrapper but it all boils down to how much time you want to fiddle about. I had similar problems with a Linksys adaptor and eventually had to give way to a native supported wifi device which I got from these guys: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by e&gt;&lt;ogenic on 2009-05-14
I'd love to upgrade my network hardware, but it's not an option at the moment.

It was my understanding that my adapter was natively supported by the Linux kernel, but I'm new to Linux so I could be wrong.

I've been trying to get a Linux distro installed for a while now and Ubuntu is the first to actually install so I'm determined to stick with it and figure things out. Tinkering about is something I enjoy doing (although I must admit it would be nice to get past this initial hurdle and tinker with something different :D )

---

### Post by unutbu on 2009-05-14
Please post the terminal commands you have tried and the subsequent output.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
I have no clue what terminal commands I should be trying - I'm completely new to Linux :(

---

### Post by unutbu on 2009-05-14
The instructions in [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)
ask you to issue some terminal commands. Perhaps try them again, and cut-and-paste the complete terminal output into a post here so we can see where you are and maybe what went wrong.

Posting the output in [code tags](" http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") would be appreciated.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
OK, the output below takes me up to step 14 in the tutorial. I have the Ubuntu CD in and mounted during the process (that's where I installed the 'build-essential' packages from).

```
exogenic@deadbox:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for exogenic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.28-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
exogenic@deadbox:~$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cvs
exogenic@deadbox:~$
```

---

### Post by unutbu on 2009-05-14
I think you can safely follow those instructions without installing CVS. 
Try skipping steps 14,15,19,20

Post back with more terminal output if you get stuck.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
OK, the output below takes me up to step 22 in the tutorial. I skipped the steps you recommended skipping.

```
exogenic@deadbox:~$ cd /home/exogenic/Desktop
exogenic@deadbox:~/Desktop$ tar xzvf at76c503a-cvsroot.tar.gz
at76c503a/
at76c503a/CVSROOT/
at76c503a/CVSROOT/verifymsg,v
at76c503a/CVSROOT/editinfo
at76c503a/CVSROOT/rcsinfo
at76c503a/CVSROOT/readers
at76c503a/CVSROOT/Emptydir/
at76c503a/CVSROOT/notify,v
at76c503a/CVSROOT/commitlog
at76c503a/CVSROOT/taginfo
at76c503a/CVSROOT/loginfo
at76c503a/CVSROOT/loginfo,v
at76c503a/CVSROOT/cvswrappers,v
at76c503a/CVSROOT/rcsinfo,v
at76c503a/CVSROOT/config
at76c503a/CVSROOT/config,v
at76c503a/CVSROOT/modules
at76c503a/CVSROOT/checkoutlist
at76c503a/CVSROOT/checkoutlist,v
at76c503a/CVSROOT/notify
at76c503a/CVSROOT/passwd
at76c503a/CVSROOT/taginfo,v
at76c503a/CVSROOT/modules,v
at76c503a/CVSROOT/history
at76c503a/CVSROOT/editinfo,v
at76c503a/CVSROOT/verifymsg
at76c503a/CVSROOT/commitinfo,v
at76c503a/CVSROOT/val-tags
at76c503a/CVSROOT/commitinfo
at76c503a/CVSROOT/cvswrappers
at76c503a/at76c503a/
at76c503a/at76c503a/at76_usb.spec,v
at76c503a/at76c503a/at76_usb.c,v
at76c503a/at76c503a/at76_usb.h,v
at76c503a/at76c503a/Attic/
at76c503a/at76c503a/Attic/fw-pkg-505a-rfmd2958.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/Attic/at76c503-rfmd-acc.c,v
at76c503a/at76c503a/Attic/at76c503-i3861.c,v
at76c503a/at76c503a/Attic/at76c503-i3863.c,v
at76c503a/at76c503a/Attic/fw-empty.h,v
at76c503a/at76c503a/Attic/fw-pkg-505-rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/Attic/fw-rfmd-0.100.4-16.h,v
at76c503a/at76c503a/Attic/at76c505-rfmd2958.c,v
at76c503a/at76c503a/Attic/fw-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/Attic/at76c503-fw_skel.c,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-acc.h,v
at76c503a/at76c503a/Attic/at76c505-rfmd.c,v
at76c503a/at76c503a/Attic/fw-pkg-505a-rfmd2958-1.102.0-113.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/Attic/at76c503fw.c,v
at76c503a/at76c503a/Attic/at76c503.c,v
at76c503a/at76c503a/Attic/at76c503.h,v
at76c503a/at76c503a/Attic/internalr.h,v
at76c503a/at76c503a/Attic/fw-i3861.h,v
at76c503a/at76c503a/Attic/fw-i3863.h,v
at76c503a/at76c503a/Attic/at76_usb_ids.h,v
at76c503a/at76c503a/Attic/vnet505-rfmd.c,v
at76c503a/at76c503a/Attic/kernel_patch.diff,v
at76c503a/at76c503a/Attic/.indent.pro,v
at76c503a/at76c503a/Attic/ieee802_11.h,v
at76c503a/at76c503a/Attic/readme.filenames,v
at76c503a/at76c503a/Attic/at76c503a.spec,v
at76c503a/at76c503a/Attic/fw-r505.h,v
at76c503a/at76c503a/Attic/fw-pkg-505-rfmd2958.h,v
at76c503a/at76c503a/Attic/ChangeLog,v
at76c503a/at76c503a/Attic/fw-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/Attic/fw-pkg-r505.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/Attic/at76c503-rfmd.c,v
at76c503a/at76c503a/Attic/gen_fw.c,v
at76c503a/at76c503a/Attic/at76fw.c,v
at76c503a/at76c503a/Attic/CHANGELOG,v
at76c503a/at76c503a/Attic/at76_usbdfu.c,v
at76c503a/at76c503a/Attic/at76_usbdfu.h,v
at76c503a/at76c503a/Attic/fw-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/Attic/vnet503-rfmd.c,v
at76c503a/at76c503a/Attic/usbdfu.c,v
at76c503a/at76c503a/Attic/usbdfu.h,v
at76c503a/at76c503a/Attic/fw-pkg-i3861.h,v
at76c503a/at76c503a/Attic/fw-pkg-i3863.h,v
at76c503a/at76c503a/Attic/externalr.h,v
at76c503a/at76c503a/Attic/fw-505rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/Attic/at76_ieee802_11.h,v
at76c503a/at76c503a/Attic/Makefile.k26,v
at76c503a/at76c503a/Attic/vnet503-i3861.c,v
at76c503a/at76c503a/Attic/vnet503-i3863.c,v
at76c503a/at76c503a/Attic/at76c505a-rfmd2958.c,v
at76c503a/at76c503a/Attic/kernel_patch.sh,v
at76c503a/at76c503a/Attic/rom2h.c,v
at76c503a/at76c503a/.cvsignore,v
at76c503a/at76c503a/compat.h,v
at76c503a/at76c503a/scripts/
at76c503a/at76c503a/scripts/Attic/
at76c503a/at76c503a/scripts/Attic/fwbin2h,v
at76c503a/at76c503a/scripts/Attic/fwversion,v
at76c503a/at76c503a/scripts/Attic/fwbin2pkg.sh,v
at76c503a/at76c503a/scripts/Attic/fwconvert,v
at76c503a/at76c503a/README,v
at76c503a/at76c503a/README.CVS,v
at76c503a/at76c503a/fwutils/
at76c503a/at76c503a/fwutils/atmel_rfmd2958_fw.h,v
at76c503a/at76c503a/fwutils/atmel_rfmd2958-smc_fw.h,v
at76c503a/at76c503a/fwutils/Attic/
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-0.100.4-16.h,v
at76c503a/at76c503a/fwutils/Attic/fwbin2h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/fwutils/Attic/fw-i3861.h,v
at76c503a/at76c503a/fwutils/Attic/fw-i3863.h,v
at76c503a/at76c503a/fwutils/Attic/fwversion,v
at76c503a/at76c503a/fwutils/Attic/fw-r505.h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/fwutils/Attic/fwbin2pkg.sh,v
at76c503a/at76c503a/fwutils/Attic/fw-505rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/fwutils/Attic/fwconvert,v
at76c503a/at76c503a/fwutils/atmel_intersil_fw.h,v
at76c503a/at76c503a/fwutils/.cvsignore,v
at76c503a/at76c503a/fwutils/fw-at76c505amx.h,v
at76c503a/at76c503a/fwutils/atmel_at76c503_rfmd2_fw.h,v
at76c503a/at76c503a/fwutils/atmel_at76c503_i3863_fw.h,v
at76c503a/at76c503a/fwutils/COPYRIGHT,v
at76c503a/at76c503a/fwutils/README,v
at76c503a/at76c503a/fwutils/readme.filenames,v
at76c503a/at76c503a/fwutils/atmel_at76c505_rfmd.h,v
at76c503a/at76c503a/fwutils/gen_fw.c,v
at76c503a/at76c503a/fwutils/fw-at76c505-2958.h,v
at76c503a/at76c503a/fwutils/Makefile,v
at76c503a/at76c503a/fwutils/atmel_at76c503_rfmd_acc_fw.h,v
at76c503a/at76c503a/fwutils/atmel_rfmd_fw.h,v
at76c503a/at76c503a/fwutils/fw-at76c503.h,v
at76c503a/at76c503a/fwutils/fw-at76c505.h,v
at76c503a/at76c503a/fwutils/fw-at76c505a-2958.h,v
at76c503a/at76c503a/lindent,v
at76c503a/at76c503a/Makefile,v
at76c503a/at76c503a/COPYING,v
[COLOR=Red]exogenic@deadbox:~/Desktop$ cd at76c503a
exogenic@deadbox:~/Desktop/at76c503a$ make
make: *** No targets specified and no makefile found.  Stop.
exogenic@deadbox:~/Desktop/at76c503a$ ls
at76c503a  CVSROOT
exogenic@deadbox:~/Desktop/at76c503a$ cd at76c503a
exogenic@deadbox:~/Desktop/at76c503a/at76c503a$ make
co  Makefile,v Makefile
make: co: Command not found
make: *** No targets specified and no makefile found.  Stop.
exogenic@deadbox:~/Desktop/at76c503a/at76c503a$ ls
at76_usb.c,v  at76_usb.spec,v  compat.h,v  fwutils    Makefile,v    README,v
at76_usb.h,v  Attic            COPYING,v   lindent,v  README.CVS,v  scripts
exogenic@deadbox:~/Desktop/at76c503a/at76c503a$[/COLOR] 

```

As you can see, I ran into problems with the 'make' command. I noticed there was another folder inside the one I was supposed to be working in so cd'ed into that and tried make from there too, but still no joy. I listed the directory contents just in case that's helpful.

---

### Post by unutbu on 2009-05-14
Sigh. It does look like you'll need the cvs package. 
To install this package on your machine, you'll need another computer with internet access, and some method of transferring a downloaded file from the internet-connected machine to your machine (such as a USB flash key).


To get the cvs package, click System>Admin>Synaptic. Type in "cvs" to the search box.
Right-Click the cvs package and select "Mark for installation".
Click File>"Generate package download script".
Save as dlscript. 

Click Places>Home Folder.
Double-click on dlscript. This will open dlscript in a text editor.
Write down the URL. It should look something like this:
```

http://ftp.ussg.iu.edu/linux/ubuntu/pool/main/c/cvs/cvs_1.12.13-11_i386.deb 
```

Now go to a computer with internet access and download this deb file. 
Save it onto the USB flash key, and then transfer this file to your machine.

To install this file, on your machine, type
```

sudo dpkg -i cvs_1.12.13-11_i386.deb
```

Once this file is installed, try the instructions at [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11) again, this time *not* skipping steps 14,15,etc.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
Searching for 'cvs' yields no results in Synaptic. Maybe this is because my package list isn't up to date as I have no internet connection in Ubuntu?

---

### Post by unutbu on 2009-05-14
Which version (e.g. Hardy, Intrepid, Jaunty) of Ubuntu are you using, and is it the 32-bit or 64-bit version?

---

### Post by e&gt;&lt;ogenic on 2009-05-14
It's 32-bit 9.04 Jaunty. Downloaded the CD from the Ubuntu.com homepage.

---

### Post by unutbu on 2009-05-14
Download this file:

[http://us.archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb)

---

### Post by e&gt;&lt;ogenic on 2009-05-14
CVS installed no problems (thanks for pointing me to the .deb!), but, although the 'make' command now works, I'm getting errors (as below) in the output (I've highlighted the 'make' command - everything below that indicates the errors I'm getting):

```
exogenic@deadbox:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for exogenic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.28-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
exogenic@deadbox:~$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cvs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
exogenic@deadbox:~$ cd /home/exogenic/Desktop
exogenic@deadbox:~/Desktop$ tar xzvf at76c503a-cvsroot.tar.gz
at76c503a/
at76c503a/CVSROOT/
at76c503a/CVSROOT/verifymsg,v
at76c503a/CVSROOT/editinfo
at76c503a/CVSROOT/rcsinfo
at76c503a/CVSROOT/readers
at76c503a/CVSROOT/Emptydir/
at76c503a/CVSROOT/notify,v
at76c503a/CVSROOT/commitlog
at76c503a/CVSROOT/taginfo
at76c503a/CVSROOT/loginfo
at76c503a/CVSROOT/loginfo,v
at76c503a/CVSROOT/cvswrappers,v
at76c503a/CVSROOT/rcsinfo,v
at76c503a/CVSROOT/config
at76c503a/CVSROOT/config,v
at76c503a/CVSROOT/modules
at76c503a/CVSROOT/checkoutlist
at76c503a/CVSROOT/checkoutlist,v
at76c503a/CVSROOT/notify
at76c503a/CVSROOT/passwd
at76c503a/CVSROOT/taginfo,v
at76c503a/CVSROOT/modules,v
at76c503a/CVSROOT/history
at76c503a/CVSROOT/editinfo,v
at76c503a/CVSROOT/verifymsg
at76c503a/CVSROOT/commitinfo,v
at76c503a/CVSROOT/val-tags
at76c503a/CVSROOT/commitinfo
at76c503a/CVSROOT/cvswrappers
at76c503a/at76c503a/
at76c503a/at76c503a/at76_usb.spec,v
at76c503a/at76c503a/at76_usb.c,v
at76c503a/at76c503a/at76_usb.h,v
at76c503a/at76c503a/Attic/
at76c503a/at76c503a/Attic/fw-pkg-505a-rfmd2958.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/Attic/at76c503-rfmd-acc.c,v
at76c503a/at76c503a/Attic/at76c503-i3861.c,v
at76c503a/at76c503a/Attic/at76c503-i3863.c,v
at76c503a/at76c503a/Attic/fw-empty.h,v
at76c503a/at76c503a/Attic/fw-pkg-505-rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/Attic/fw-rfmd-0.100.4-16.h,v
at76c503a/at76c503a/Attic/at76c505-rfmd2958.c,v
at76c503a/at76c503a/Attic/fw-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/Attic/at76c503-fw_skel.c,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-acc.h,v
at76c503a/at76c503a/Attic/at76c505-rfmd.c,v
at76c503a/at76c503a/Attic/fw-pkg-505a-rfmd2958-1.102.0-113.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/Attic/at76c503fw.c,v
at76c503a/at76c503a/Attic/at76c503.c,v
at76c503a/at76c503a/Attic/at76c503.h,v
at76c503a/at76c503a/Attic/internalr.h,v
at76c503a/at76c503a/Attic/fw-i3861.h,v
at76c503a/at76c503a/Attic/fw-i3863.h,v
at76c503a/at76c503a/Attic/at76_usb_ids.h,v
at76c503a/at76c503a/Attic/vnet505-rfmd.c,v
at76c503a/at76c503a/Attic/kernel_patch.diff,v
at76c503a/at76c503a/Attic/.indent.pro,v
at76c503a/at76c503a/Attic/ieee802_11.h,v
at76c503a/at76c503a/Attic/readme.filenames,v
at76c503a/at76c503a/Attic/at76c503a.spec,v
at76c503a/at76c503a/Attic/fw-r505.h,v
at76c503a/at76c503a/Attic/fw-pkg-505-rfmd2958.h,v
at76c503a/at76c503a/Attic/ChangeLog,v
at76c503a/at76c503a/Attic/fw-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/Attic/fw-pkg-r505.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd.h,v
at76c503a/at76c503a/Attic/fw-pkg-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/Attic/at76c503-rfmd.c,v
at76c503a/at76c503a/Attic/gen_fw.c,v
at76c503a/at76c503a/Attic/at76fw.c,v
at76c503a/at76c503a/Attic/CHANGELOG,v
at76c503a/at76c503a/Attic/at76_usbdfu.c,v
at76c503a/at76c503a/Attic/at76_usbdfu.h,v
at76c503a/at76c503a/Attic/fw-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/Attic/vnet503-rfmd.c,v
at76c503a/at76c503a/Attic/usbdfu.c,v
at76c503a/at76c503a/Attic/usbdfu.h,v
at76c503a/at76c503a/Attic/fw-pkg-i3861.h,v
at76c503a/at76c503a/Attic/fw-pkg-i3863.h,v
at76c503a/at76c503a/Attic/externalr.h,v
at76c503a/at76c503a/Attic/fw-505rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/Attic/at76_ieee802_11.h,v
at76c503a/at76c503a/Attic/Makefile.k26,v
at76c503a/at76c503a/Attic/vnet503-i3861.c,v
at76c503a/at76c503a/Attic/vnet503-i3863.c,v
at76c503a/at76c503a/Attic/at76c505a-rfmd2958.c,v
at76c503a/at76c503a/Attic/kernel_patch.sh,v
at76c503a/at76c503a/Attic/rom2h.c,v
at76c503a/at76c503a/.cvsignore,v
at76c503a/at76c503a/compat.h,v
at76c503a/at76c503a/scripts/
at76c503a/at76c503a/scripts/Attic/
at76c503a/at76c503a/scripts/Attic/fwbin2h,v
at76c503a/at76c503a/scripts/Attic/fwversion,v
at76c503a/at76c503a/scripts/Attic/fwbin2pkg.sh,v
at76c503a/at76c503a/scripts/Attic/fwconvert,v
at76c503a/at76c503a/README,v
at76c503a/at76c503a/README.CVS,v
at76c503a/at76c503a/fwutils/
at76c503a/at76c503a/fwutils/atmel_rfmd2958_fw.h,v
at76c503a/at76c503a/fwutils/atmel_rfmd2958-smc_fw.h,v
at76c503a/at76c503a/fwutils/Attic/
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-0.100.4-16.h,v
at76c503a/at76c503a/fwutils/Attic/fwbin2h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-0.90.2-140.h,v
at76c503a/at76c503a/fwutils/Attic/fw-i3861.h,v
at76c503a/at76c503a/fwutils/Attic/fw-i3863.h,v
at76c503a/at76c503a/fwutils/Attic/fwversion,v
at76c503a/at76c503a/fwutils/Attic/fw-r505.h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-acc-1.101.0-84.h,v
at76c503a/at76c503a/fwutils/Attic/fw-rfmd-1.101.0-84.h,v
at76c503a/at76c503a/fwutils/Attic/fwbin2pkg.sh,v
at76c503a/at76c503a/fwutils/Attic/fw-505rfmd2958-1.101.0-86.h,v
at76c503a/at76c503a/fwutils/Attic/fwconvert,v
at76c503a/at76c503a/fwutils/atmel_intersil_fw.h,v
at76c503a/at76c503a/fwutils/.cvsignore,v
at76c503a/at76c503a/fwutils/fw-at76c505amx.h,v
at76c503a/at76c503a/fwutils/atmel_at76c503_rfmd2_fw.h,v
at76c503a/at76c503a/fwutils/atmel_at76c503_i3863_fw.h,v
at76c503a/at76c503a/fwutils/COPYRIGHT,v
at76c503a/at76c503a/fwutils/README,v
at76c503a/at76c503a/fwutils/readme.filenames,v
at76c503a/at76c503a/fwutils/atmel_at76c505_rfmd.h,v
at76c503a/at76c503a/fwutils/gen_fw.c,v
at76c503a/at76c503a/fwutils/fw-at76c505-2958.h,v
at76c503a/at76c503a/fwutils/Makefile,v
at76c503a/at76c503a/fwutils/atmel_at76c503_rfmd_acc_fw.h,v
at76c503a/at76c503a/fwutils/atmel_rfmd_fw.h,v
at76c503a/at76c503a/fwutils/fw-at76c503.h,v
at76c503a/at76c503a/fwutils/fw-at76c505.h,v
at76c503a/at76c503a/fwutils/fw-at76c505a-2958.h,v
at76c503a/at76c503a/lindent,v
at76c503a/at76c503a/Makefile,v
at76c503a/at76c503a/COPYING,v
exogenic@deadbox:~/Desktop$ mv at76c503a CVS
exogenic@deadbox:~/Desktop$ cvs -d /home/exogenic/Desktop/CVS co at76c503a
cvs checkout: Updating at76c503a
U at76c503a/.cvsignore
U at76c503a/COPYING
U at76c503a/Makefile
U at76c503a/README
U at76c503a/README.CVS
U at76c503a/at76_usb.c
U at76c503a/at76_usb.h
U at76c503a/at76_usb.spec
U at76c503a/compat.h
U at76c503a/lindent
cvs checkout: Updating at76c503a/fwutils
U at76c503a/fwutils/.cvsignore
U at76c503a/fwutils/COPYRIGHT
U at76c503a/fwutils/Makefile
U at76c503a/fwutils/README
U at76c503a/fwutils/atmel_at76c503_i3863_fw.h
U at76c503a/fwutils/atmel_at76c503_rfmd2_fw.h
U at76c503a/fwutils/atmel_at76c503_rfmd_acc_fw.h
U at76c503a/fwutils/atmel_at76c505_rfmd.h
U at76c503a/fwutils/atmel_intersil_fw.h
U at76c503a/fwutils/atmel_rfmd2958-smc_fw.h
U at76c503a/fwutils/atmel_rfmd2958_fw.h
U at76c503a/fwutils/atmel_rfmd_fw.h
U at76c503a/fwutils/fw-at76c503.h
U at76c503a/fwutils/fw-at76c505-2958.h
U at76c503a/fwutils/fw-at76c505.h
U at76c503a/fwutils/fw-at76c505a-2958.h
U at76c503a/fwutils/fw-at76c505amx.h
U at76c503a/fwutils/gen_fw.c
U at76c503a/fwutils/readme.filenames
cvs checkout: Updating at76c503a/scripts
exogenic@deadbox:~/Desktop$ cd at76c503a
[COLOR=Red]exogenic@deadbox:~/Desktop/at76c503a$ make[/COLOR]
make -C /usr/src/linux-headers-2.6.28-11-generic M=/home/exogenic/Desktop/at76c503a KERNELRELEASE=2.6.28-11-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/exogenic/Desktop/at76c503a/at76_usb.o
/home/exogenic/Desktop/at76c503a/at76_usb.c: In function â&#8364;&#732;at76_iw_handler_get_scanâ&#8364;&#8482;:
/home/exogenic/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; makes pointer from integer without a cast
/home/exogenic/Desktop/at76c503a/at76_usb.c:2332: error: too few arguments to function â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2340: error: too few arguments to function â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; makes pointer from integer without a cast
/home/exogenic/Desktop/at76c503a/at76_usb.c:2351: error: too few arguments to function â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; makes pointer from integer without a cast
/home/exogenic/Desktop/at76c503a/at76_usb.c:2358: error: too few arguments to function â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2369: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2369: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2369: error: too few arguments to function â&#8364;&#732;iwe_stream_add_pointâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 3 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482; makes pointer from integer without a cast
/home/exogenic/Desktop/at76c503a/at76_usb.c:2388: error: too few arguments to function â&#8364;&#732;iwe_stream_add_eventâ&#8364;&#8482;
/home/exogenic/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 1 of â&#8364;&#732;iwe_stream_add_valueâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 4 of â&#8364;&#732;iwe_stream_add_valueâ&#8364;&#8482; from incompatible pointer type
/home/exogenic/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 5 of â&#8364;&#732;iwe_stream_add_valueâ&#8364;&#8482; makes pointer from integer without a cast
/home/exogenic/Desktop/at76c503a/at76_usb.c:2407: error: too few arguments to function â&#8364;&#732;iwe_stream_add_valueâ&#8364;&#8482;
make[2]: *** [/home/exogenic/Desktop/at76c503a/at76_usb.o] Error 1
make[1]: *** [_module_/home/exogenic/Desktop/at76c503a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2
exogenic@deadbox:~/Desktop/at76c503a$

```

---

### Post by unutbu on 2009-05-14
I managed to compile at76c503a using the advice of markds from this page: [http://www.slax.org/forum.php?action=view&parentID=31051](http://www.slax.org/forum.php?action=view&parentID=31051). I changed all occurences of 

iwe_stream_add_event(  --->    iwe_stream_add_event(info,
iwe_stream_add_point(  --->    iwe_stream_add_point(info,
iwe_stream_add_value(  --->    iwe_stream_add_value(info,

Below I've attached my modified version of at76_usb.c. Because of forum restrictions, I had to compress it to at76_usb.c.bz2. 

Copy at76_usb.c.bz2 to /home/exogenic/Desktop/at76c503a/at76_usb.c.bz2.
Then run

```

cd /home/exogenic/Desktop/at76c503a
bunzip2 at76_usb.c.bz2       # uncompresses the file

```

Then try "make" again.

I must say I am disliking the instructions at [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11) more and more and wonder if there is an easier/better way. However, since I seem to have managed to compile this thing, perhaps it will work for you too and -- if we are lucky -- will then have overcome the biggest obstacle.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
Firstly let me say thanks for putting so much effort into this!

I followed your instructions from the previous post and successfully made and installed the driver:

```
exogenic@deadbox:~$ cd /home/exogenic/Desktop/at76c503a
exogenic@deadbox:~/Desktop/at76c503a$ make
make -C /usr/src/linux-headers-2.6.28-11-generic M=/home/exogenic/Desktop/at76c503a KERNELRELEASE=2.6.28-11-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
exogenic@deadbox:~/Desktop/at76c503a$ sudo make install
rm -rf /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/at76*
make -C /usr/src/linux-headers-2.6.28-11-generic M=/home/exogenic/Desktop/at76c503a KERNELRELEASE=2.6.28-11-generic modules_install \
        INSTALL_MOD_DIR="kernel/drivers/net/wireless"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  INSTALL /home/exogenic/Desktop/at76c503a/at76_usb.ko
  DEPMOD  2.6.28-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
/sbin/depmod -ae
exogenic@deadbox:~/Desktop/at76c503a$

```

At this point I reconnected the wireless adpater and restarted Ubuntu as the tutorial suggested.

When I got back into Ubuntu, NetworkManager still says 'No network connection'.

I created a new wireless connection in NetworkManager with my connection details. I'm not sure whether Mode should be set to 'Infrastructure' or 'Ad-hoc' but tried both. I assigned my machine a static IP address in Windows, so under the IPv4 Settings I added that IP address, the Subnet Mask and Default Gateway IPs from my router settings and two DNS server IPs. Saved all that, restarted and still 'No network connection'.

Next, I tried connecting via the 'Connect to Hidden Wireless Network' option (even though my router is set to broadcast the SSID I thought it was worth a try). At that point, the NetworkManager icon changes to some sort of activity indicator and after 20-30 seconds a 'Wireless Network Authentication Required' dialog pops up. No matter what details I put in there, every time I submit the changes, the NetworkManger icon changes for a little while and then pops up the same dialog. Does this suggest I don't have all the connection information correct? I'm 99% sure I do, but maybe I'm missing something.

There are two other local wireless networks picked up by Windows, so I'm loathed to disable the WEP security (although I understand it's a bit crap) and try connecting without, but I can try that if I have to.

---

### Post by unutbu on 2009-05-14
Hm. Let's try this:
```

gksu gedit /etc/network/interfaces
```

Assuming your wireless interface is called wlan0, add something like this:
```

auto wlan0
iface wlan0 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
wireless-essid XXXXXXXXXXXX
```

Change the numbers and X's as appropriate.

Next, open /etc/resolv.conf and add your DNS there. For example,
```

nameserver 192.168.1.1
```

Save and exit gedit. Then reboot. (I find, at least for my setup, that all configuration files must be in place at boot time for the network adapter to work.)

After reboot, see if you have a connection. If not, please post the output of 
```

ifconfig
iwconfig
iwlist scan
sudo /etc/init.d/networking restart
```

---

### Post by e&gt;&lt;ogenic on 2009-05-14
Just a couple of quick questions before I try that...

1) When editing the interfaces file, 'address' should be the IP of my machine, right?
2) When adding the nameserver information... I have 2 IP addresses for nameservers from my router configuration. Do I just comma-separate those as I did in NetworkManager, or should that be the IP address of the router (which would be the same as used in your example)?

---

### Post by unutbu on 2009-05-14
1) Yes, the "address" should be the IP of the machine. "gateway" should be the IP of the router. 

2) For 2 DNS addresses, list each on a separate line like this:
```

nameserver 192.168.1.1
nameserver 192.168.1.2
```
In my case, my router acts as my DNS server. They can be the IP address of remote DNS servers too, however. It depends on your ISP.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
OK, I made those changes and restarted but still no joy :(

There were auto and iface entries in the interfaces file already, so I just replaced those with the ones you gave me (hopefully that was the right thing to do!).

Here's the output you requested:

```
exogenic@deadbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:2b:40:5b:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9011 (9.0 KB)  TX bytes:9011 (9.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:25:0d:ce:49  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe0d:ce49/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

exogenic@deadbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Three17"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

exogenic@deadbox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

exogenic@deadbox:~$ sudo /etc/init.d/networking restart
[sudo] password for exogenic: 
 * Reconfiguring network interfaces...                                   [ OK ] 
exogenic@deadbox:~$ 

```

I noticed a couple things that might be worthy of mentioning. Before, when left-clicking NetworkManager, there were no entries under the Wireless Networks heading. Now, it shows:

```
**Wireless Networks**
device not managed
```

Also, before when I tried Firefox, it always started in offline mode and instantly failed when trying, eg, google.com. Now, Firefox does NOT start in offline mode and when I try google.com, the Firefox statusbar displays 'looking up [www.google.com](www.google.com)' for a little while before failing.

Not sure if all that's pertinent, but thought it might be helpful.

---

### Post by unutbu on 2009-05-14
First the good news: The driver works -- it gives you a wlan0 interface.
The /etc/network/interface file successfully sets your ip address and the essid of the router.

This is the problem:
```

exogenic@deadbox:~$ iwlist scan
...
wlan0     No scan results
```

Your wireless adapter is not seeing your router. 
All detectable routers should show up in the results of "iwlist scan". 
Is it on? Can you move the computer and/or router closer together to eliminate this variable?

Keep using "iwlist scan" to check if you can pick up a signal.
When you get output that looks something like this:

```
          Cell 02 - Address: 00:12:34:56:78:90
                    ESSID:"Three17"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
```


Run
```

sudo /etc/init.d/networking restart
```

until you get a connection. (Try a few times -- it sometimes take a few tries or a few moments before it works).

Edit: "iwlist scan" works for me, but just in case you might want to try "**sudo** iwlist scan" to make sure the lack of detected routers is not due to some permission issue.

---

### Post by e&gt;&lt;ogenic on 2009-05-14
Hmmm. Don't think there's much I can do about the physical location of the adapter and router :( They both work fine in Windows, so why would the distance be an issue with Ubuntu?

Regardless of whether or not we've gone as far as we can I really appreciate all of your help :)

---

### Post by unutbu on 2009-05-14
Have you tried ```


sudo iwlist scan
```
? Perhaps it is just a permission issue?

---

### Post by e&gt;&lt;ogenic on 2009-05-14
Same results as without sudo :(

```
exogenic@deadbox:~$ sudo iwlist scan
[sudo] password for exogenic: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

exogenic@deadbox:~$ 

```

---

### Post by Sparticusx on 2009-08-05
I could use some help with this adapter as well my problem is a little different in my network connections my linsys adapter comes up by name but it comes up as a wired network no a wireless one it says "Auto Ethernet" under wired network....not sure what to do

---

