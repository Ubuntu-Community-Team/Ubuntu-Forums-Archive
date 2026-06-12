---
title: "HDD to Flash drive file transfer is dead slow.please help!"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by human75 on 2010-05-19
hi there.i am using ubuntu 10.04LTS X64 AMD (WUBI installed) and file transfer is so slow between HDD to USB flash drive.let sayi want to copy 350mb mkv it starts very fast and it gets slower and slower....copying a file takes 10 min...:( what should i do?how can i fix this problem.it kills me every time when i want to copy a movie:( please help.thanks in advance

---

### Post by mike555 on 2010-05-19
Make sure you are using a usb2 plug (some makers put usb1.1 plugs on the front of your computer but usb2 on the back )also if your using an extension usb cord make sure it's usb2 also ..

---

### Post by human75 on 2010-05-19
thanks for reply.i dont use any hub.i have toshiba A210 laptop.i tried 4 port all have same problem.usb flash drive works ok with windows7.the weird thing is file transfer starts super fast after it gets hell slow.let say the  file is 700mb first 250mb is very fast afterwards turns hell slow.please help.thanks in advance
ps:when i copy file from flash drive to hdd transfer speed is normal.???i dont now what is wrong:)

---

### Post by philinux on 2010-05-19
Yes this is bugged at launchpad there are several duplicates too. I wish they would sort this out.

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=slow+usb+transfer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=slow+usb+transfer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by LowSky on 2010-05-19
I used to have the same issue for years, and everyone (ahem... developers) told me it wasnt a real problem. This is a Linux issue not just Ubuntu. Look around the internet this has been a problem for years. Unfortunatly it seems not many people (ahem... developers) try to move large files to flash drives in a Linux enviroment, which seems odd to me.

I think its a USB driver or Northbridge chipset driver issue for Linux. It effects my netbook and my HTPC but not my newer desktop. Its really baffling that this isn't a bigger problem.

---

### Post by human75 on 2010-05-19
> **LowSky said:**
> I used to have the same issue for years, and everyone (ahem... developers) told me it wasnt a real problem. This is a Linux issue not just Ubuntu. Look around the internet this has been a problem for years. Unfortunatly it seems not many people (ahem... developers) try to move large files to flash drives in a Linux enviroment, which seems odd to me.

I think its a USB driver or Northbridge chipset driver issue for Linux. It effects my netbook and my HTPC but not my newer desktop. Its really baffling that this isn't a bigger problem.
for me it is really big problem.everyday i have to transfer a lots of large amount file so it takes ages to transfer:(i hope there is some way to fix this problem?!!!do we have any luck to fix you guys think?!!thanks

---

### Post by nhasian on 2010-05-19
I used to experience this as well until I switched to the mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

you will need to install 3 packages.

> For 32 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)

> for 64 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb)

please install in order listed.  Then run from a from a terminal afterwards:

```
sudo update-grub
```

reboot.  to confirm you are running the new kernel type in a terminal:

```
uname -a
```

---

### Post by philinux on 2010-05-19
@nhasian could you explain what the mainline kernel is and the implications. Just so anyone else following this understands.

---

### Post by nhasian on 2010-05-19
The Ubuntu Mainline Kernel allow users to run the unmodified upstream vanilla kernel.  

> This can be useful for verifying fixes upstream, testing for regressions introduced by Ubuntu specific changes, or confirming bugs exist upstream and subsequently help to report bugs upstream.

The mainline kernels are packaged for each stable release.  They are available as .deb files for easy installation.  Keep in mind that even though they are built using the Ubuntu kernel config files, they do not contain any Ubuntu specific drivers.  Also, there are no restricted modules for these kernels.  They are strictly the vanilla mainline kernel source.

I dont know what changes ubuntu makes but whatever it is, it kills the speed of USB file transfers.  I get full speed usb file transfers when i use the mainline kernel.  Also I get ATA-TRIM for my SSD with the newer kernel.

---

### Post by philinux on 2010-05-19
ok got that. How would this affect a normal ubuntu users installation?

---

### Post by nhasian on 2010-05-19
it just adds another kernel to the system which you can select from the list of kernels during startup from the GRUB menu.  if for some reason the new kernel doesn't agree with your system, you can always restart and choose your original kernel again.  I haven't experienced any regressions from using the mainline kernel, and I've installed them on several laptops and desktops now and have been using it for the past six months or so.

I'm not pretending to be an expert on the linux kernel.  I haven't compiled my own kernel since Redhat 5.  I'm glad these are prepackaged by the Ubuntu Kernel Team.  They make it easy to install and use the latest linux kernel.

---

### Post by human75 on 2010-05-19
> **nhasian said:**
> I used to experience this as well until I switched to the mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")

you will need to install 3 packages.





please install in order listed.  Then run from a from a terminal afterwards:

```
sudo update-grub
```reboot.  to confirm you are running the new kernel type in a terminal:

```
uname -a
```
thanks a billion.worked like a charm.now file transfer is super fast.thanks in advance

---

### Post by philinux on 2010-05-19
cheers for that. I guess the normal kernel updates still come through then.

---

### Post by mantaor on 2010-05-21
Hi,

I installed the packages i386 following the right order, grub ok, but during installation i saw a crash icon reporting a problem with nvidia 173 driver. After reboot, I selected the new kernel and I had a black screen with prompt requesting my ID and PW. After filling with my informations, an error "no screen available" and something like no nvidia 173 driver available stopped all and I have to reboot with usual kernel.
Any suggestion to help me?
Thank you

---

### Post by nhasian on 2010-05-21
sounds like you should reinstall the nvidia-current driver.

> **mantaor said:**
> Hi,

I installed the packages i386 following the right order, grub ok, but during installation i saw a crash icon reporting a problem with nvidia 173 driver. After reboot, I selected the new kernel and I had a black screen with prompt requesting my ID and PW. After filling with my informations, an error "no screen available" and something like no nvidia 173 driver available stopped all and I have to reboot with usual kernel.
Any suggestion to help me?
Thank you

---

### Post by mantaor on 2010-05-23
I reinstalled nvidia 173 and nvidia 173 modealiases but during process, I still have had error 10 with mainline kernel. Please, have you any other idea?
Thank you

---

### Post by nhasian on 2010-05-23
you should start your own thread since the opening posters question was already answered in this thread, and you are experiencing a completely different issue than his.

> **mantaor said:**
> I reinstalled nvidia 173 and nvidia 173 modealiases but during process, I still have had error 10 with mainline kernel. Please, have you any other idea?
Thank you

---

### Post by mantaor on 2010-05-24
OK thanks

---

### Post by mantaor on 2010-05-24
ok thanks

---

### Post by aparigraha on 2010-09-29
Sorry to bump this a bit. But I tried the mainline kernel as posted, and it did not change one thing.
Kernel installed flawlessly but transfer to USB Flash is still as slow as it has been for years.

---

