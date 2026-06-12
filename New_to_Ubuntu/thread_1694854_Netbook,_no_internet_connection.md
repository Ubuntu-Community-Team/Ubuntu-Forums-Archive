---
title: "Netbook, no internet connection"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by mr best buy on 2011-02-24
I need help.  
I have a netbook with no Ethernet connection.  I installed Ubuntu about 6 months ago and everything was fine.  My wireless worked and I cannot remember if I had problems getting it to work.
I had to reinstall my OS tonight because an update cause the netbook to become unstable.  I installed it from my flash drive as before.  While I was installing the OS, the wireless worked fine.  When I rebooted, the wireless was not working.  So I tried to activate additional drivers and  my hardware was listed.  But I cannot do it because I cannot get on the internet.  


I am not sure how I did it before and I am not sure how to do it now.  Please help me/

---

### Post by undecim on 2011-02-25
> **mr best buy said:**
> I need help.  
I have a netbook with no Ethernet connection.  I installed Ubuntu about 6 months ago and everything was fine.  My wireless worked and I cannot remember if I had problems getting it to work.
I had to reinstall my OS tonight because an update cause the netbook to become unstable.  I installed it from my flash drive as before.  While I was installing the OS, the wireless worked fine.  When I rebooted, the wireless was not working.  So I tried to activate additional drivers and  my hardware was listed.  But I cannot do it because I cannot get on the internet.  


I am not sure how I did it before and I am not sure how to do it now.  Please help me/

I believe the installation CD has packages for wireless that aren't included in the default install. If you have a broadcom card, look in pool/restricted/b/bcmwl/ on the install disk.

---

### Post by mr best buy on 2011-02-25
> **undecim said:**
> I believe the installation CD has packages for wireless that aren't included in the default install. If you have a broadcom card, look in pool/restricted/b/bcmwl/ on the install disk.

OK, I followed your instructions.  I installed from a flash drive because a netbook has no disk drive.  I went to Pendrive>open> pool>(ristricted>b>bcmwl. I click on the file and it came out as bcmwl-kernel-source_5.60.48.36.i3867.deb
I click on that file and after a time, it took me to getsoftware>system>broadcom 801.11 linux SYA wireless driver source.
I click on install and it informed me I am not connected to the internet...  Is there a way to do it from the terminal?
THANKS

---

### Post by grahammechanical on 2011-02-25
Have you tried adding the pen drive as a software source? So, that the install program looks to the pen drive and not to a server on the Internet.

If using the Synaptic Package Manager click Edit and then click Add CD ROM. It will see the pen drive as a CD.

If using Ubuntu Software Centre click Edit, click Software Sources and tick Installable from CD/DVD.

You can also do this through Update Manager. Click Settings. There you have an option for Other software and Add Volume. You get a message saying Please insert a disc in the drive.

These things might work.

Regards.

---

### Post by mr best buy on 2011-02-25
> **grahammechanical said:**
> Have you tried adding the pen drive as a software source? So, that the install program looks to the pen drive and not to a server on the Internet.

If using the Synaptic Package Manager click Edit and then click Add CD ROM. It will see the pen drive as a CD.

If using Ubuntu Software Centre click Edit, click Software Sources and tick Installable from CD/DVD.

You can also do this through Update Manager. Click Settings. There you have an option for Other software and Add Volume. You get a message saying Please insert a disc in the drive.

These things might work.

Regards.

I tried both of those with no success.  It will not recognize a pendrive.  I went to the pendrive and click on the file and it took me to the software center and told me not to install it unless I trusted the source.  when I did try to install it, it said it could not get on the internet.  This computers has been on the internet for 6 months using Ubuntu, but I do not remember how I did it.  Any help please.  Thanks

---

### Post by mr best buy on 2011-02-25
> **mr best buy said:**
> I tried both of those with no success.  It will not recognize a pendrive.  I went to the pendrive and click on the file and it took me to the software center and told me not to install it unless I trusted the source.  when I did try to install it, it said it could not get on the internet.  This computers has been on the internet for 6 months using Ubuntu, but I do not remember how I did it.  Any help please.  Thanks

By the way, the wireless works fine while I am installing the OS.  I have reinstalled it 3 times in the last two hours.  What m I doing wrong?

---

### Post by mr best buy on 2011-02-25
> **mr best buy said:**
> By the way, the wireless works fine while I am installing the OS.  I have reinstalled it 3 times in the last two hours.  What m I doing wrong?

ok I found the ethernet connection with the help of hp.  behind a rubber piece the same color as the case
then I install I get this message
installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu10.2_i386.deb) ...

Unpacking replacement libc-bin ...

Processing triggers for man-db ...

Setting up libc-bin (2.12.1-0ubuntu10.2) ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu10.2_i386.deb) ...

Unpacking replacement libc6 ...

Setting up libc6 (2.12.1-0ubuntu10.2) ...

Generating locales...

  en_AG.UTF-8... done

  en_AU.UTF-8... done

  en_BW.UTF-8... done

  en_CA.UTF-8... done

  en_DK.UTF-8... done

  en_GB.UTF-8... done

  en_HK.UTF-8... done

  en_IE.UTF-8... done

  en_IN.UTF-8... done

  en_NG.UTF-8... done

  en_NZ.UTF-8... done

  en_PH.UTF-8... done

  en_SG.UTF-8... done

  en_US.UTF-8... done

  en_ZA.UTF-8... done

  en_ZW.UTF-8... done

Generation complete.

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Selecting previously deselected package binutils.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Unpacking binutils (from .../binutils_2.20.51.20100908-0ubuntu2_i386.deb) ...

Selecting previously deselected package gcc-4.4.

Unpacking gcc-4.4 (from .../gcc-4.4_4.4.4-14ubuntu5_i386.deb) ...

Selecting previously deselected package gcc.

Unpacking gcc (from .../gcc_4%3a4.4.4-1ubuntu2_i386.deb) ...

Selecting previously deselected package patch.

Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...

Selecting previously deselected package dkms.

Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...

Selecting previously deselected package fakeroot.

Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...

Selecting previously deselected package libc-dev-bin.

Unpacking libc-dev-bin (from .../libc-dev-bin_2.12.1-0ubuntu10.2_i386.deb) ...

Selecting previously deselected package linux-libc-dev.

Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.35-1025.44_i386.deb) ...

Selecting previously deselected package libc6-dev.

Unpacking libc6-dev (from .../libc6-dev_2.12.1-0ubuntu10.2_i386.deb) ...

Selecting previously deselected package manpages-dev.

Unpacking manpages-dev (from .../manpages-dev_3.24-1ubuntu1_all.deb) ...

Processing triggers for man-db ...

Setting up firmware-b43-installer (4.150.10.5-4) ...

Not supported low-power chip with PCI id 14e4:4315!

Aborting.

dpkg: error processing firmware-b43-installer (--configure):

 subprocess installed post-installation script returned error exit status 1

No apport report written because MaxReports is reached already
Setting up binutils (2.20.51.20100908-0ubuntu2) ...

Setting up gcc-4.4 (4.4.4-14ubuntu5) ...

Setting up gcc (4:4.4.4-1ubuntu2) ...

Setting up patch (2.6-2ubuntu1) ...

Setting up dkms (2.1.1.2-3ubuntu1.1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...

update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...

Setting up linux-libc-dev (2.6.35-1025.44) ...

Setting up libc6-dev (2.12.1-0ubuntu10.2) ...

Setting up manpages-dev (3.24-1ubuntu1) ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 firmware-b43-installer

Setting up firmware-b43-installer (4.150.10.5-4) ...

Not supported low-power chip with PCI id 14e4:4315!

Aborting.

dpkg: error processing firmware-b43-installer (--configure):

 subprocess installed post-installation script returned error exit status 1


I do not know what this means. 
please help

---

### Post by mr best buy on 2011-02-25
> **mr best buy said:**
> ok I found the ethernet connection with the help of hp.  behind a rubber piece the same color as the case
then I install I get this message
installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu10.2_i386.deb) ...

Unpacking replacement libc-bin ...

Processing triggers for man-db ...

Setting up libc-bin (2.12.1-0ubuntu10.2) ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu10.2_i386.deb) ...

Unpacking replacement libc6 ...

Setting up libc6 (2.12.1-0ubuntu10.2) ...

Generating locales...

  en_AG.UTF-8... done

  en_AU.UTF-8... done

  en_BW.UTF-8... done

  en_CA.UTF-8... done

  en_DK.UTF-8... done

  en_GB.UTF-8... done

  en_HK.UTF-8... done

  en_IE.UTF-8... done

  en_IN.UTF-8... done

  en_NG.UTF-8... done

  en_NZ.UTF-8... done

  en_PH.UTF-8... done

  en_SG.UTF-8... done

  en_US.UTF-8... done

  en_ZA.UTF-8... done

  en_ZW.UTF-8... done

Generation complete.

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Selecting previously deselected package binutils.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 117200 files and directories currently installed.)

Unpacking binutils (from .../binutils_2.20.51.20100908-0ubuntu2_i386.deb) ...

Selecting previously deselected package gcc-4.4.

Unpacking gcc-4.4 (from .../gcc-4.4_4.4.4-14ubuntu5_i386.deb) ...

Selecting previously deselected package gcc.

Unpacking gcc (from .../gcc_4%3a4.4.4-1ubuntu2_i386.deb) ...

Selecting previously deselected package patch.

Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...

Selecting previously deselected package dkms.

Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...

Selecting previously deselected package fakeroot.

Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...

Selecting previously deselected package libc-dev-bin.

Unpacking libc-dev-bin (from .../libc-dev-bin_2.12.1-0ubuntu10.2_i386.deb) ...

Selecting previously deselected package linux-libc-dev.

Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.35-1025.44_i386.deb) ...

Selecting previously deselected package libc6-dev.

Unpacking libc6-dev (from .../libc6-dev_2.12.1-0ubuntu10.2_i386.deb) ...

Selecting previously deselected package manpages-dev.

Unpacking manpages-dev (from .../manpages-dev_3.24-1ubuntu1_all.deb) ...

Processing triggers for man-db ...

Setting up firmware-b43-installer (4.150.10.5-4) ...

Not supported low-power chip with PCI id 14e4:4315!

Aborting.

dpkg: error processing firmware-b43-installer (--configure):

 subprocess installed post-installation script returned error exit status 1

No apport report written because MaxReports is reached already
Setting up binutils (2.20.51.20100908-0ubuntu2) ...

Setting up gcc-4.4 (4.4.4-14ubuntu5) ...

Setting up gcc (4:4.4.4-1ubuntu2) ...

Setting up patch (2.6-2ubuntu1) ...

Setting up dkms (2.1.1.2-3ubuntu1.1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...

update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...

Setting up linux-libc-dev (2.6.35-1025.44) ...

Setting up libc6-dev (2.12.1-0ubuntu10.2) ...

Setting up manpages-dev (3.24-1ubuntu1) ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 firmware-b43-installer

Setting up firmware-b43-installer (4.150.10.5-4) ...

Not supported low-power chip with PCI id 14e4:4315!

Aborting.

dpkg: error processing firmware-b43-installer (--configure):

 subprocess installed post-installation script returned error exit status 1


I do not know what this means. 
please help

it is fixed.  i used the terminal sudo commands.  had to go through them  three times.  thanks everyone

---

