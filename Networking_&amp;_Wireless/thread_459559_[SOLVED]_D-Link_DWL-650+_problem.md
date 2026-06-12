---
title: "[SOLVED] D-Link DWL-650+ problem"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by neptune229 on 2007-05-30
I have Xubuntu 7.04 on a Compaq Presario 1200CA with an Intel Celeron 800Mhz processor and 128 MB of RAM. I used to have Windows ME installed but installed Xubuntu over it with the alternate install CD. I have a D-Link DWL-650+ which I cannot get to work on Xubuntu. By the way, it worked on Windows ME, but stopped working after no problems for many years. I tried ndiswrapper (b/c I suspected a driver problem) but I am new to Linux and I am not even sure if I did it properly. Could someone please help?

---

### Post by tturrisi on 2007-05-30
Atheros chipset > needs madwifi drivers > install linux-restricted-modules

---

### Post by neptune229 on 2007-05-31
Sorry I am completely new to Linux. I kind of know what that means but I have absolutely no idea how to do it.

---

### Post by tturrisi on 2007-05-31
Enable "restricted" Repository"
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Enable_.22restricted.22_Repository](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Enable_.22restricted.22_Repository)

install restricted-modules:
sudo apt-get install linux-restricted-modules-$(uname -r)

---

### Post by neptune229 on 2007-05-31
I tried that but of course I am not connected to the Internet because my wireless card does not work. I have a Windows XP computer that I am using to download the things and then transferring them to the linux box with a flash drive.

---

### Post by tturrisi on 2007-05-31
then connect by wire temporarily.
You should also be able to install the restricted modules from the ubuntu cd.

---

### Post by tturrisi on 2007-05-31
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-386](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-386)
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic)
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-386](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-386)
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-generic)
[http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages)

---

### Post by neptune229 on 2007-05-31
I tried all of these four of these packages but when I open them in the Package Installer, I get the message:

Error: Dependency is not satisfiable: linux-image-2.6.20-15-386

Also, after typing *uname -a* into Terminal, the following appears (I think it's something important but I really have no idea...maybe it will help)

Linux ubuntu 2.6.20-15-generic #2 SMP Sun APR 15 07:36:31 UTC 2007 i686 GNU/Linux

BTW that time is wrong
Thank you so much for your trouble.

oh and by the way I did not connect my linux box to the internet when doing this, I didn't think it was necessary b/c I used my windows machine to download the packages and the flash drive to transfer them

---

### Post by neptune229 on 2007-05-31
Here is some more information that might help:
when I type *sudo pccardctl ident* into terminal, it says

Socket 0:
   no product info available

so now I assume that the os doesn't even know the card is there, which is odd because the light on the card is on indicating that it is powered up and linked to the router

thanks again

---

### Post by stoian on 2007-05-31
Actually I have the same wireless wifi card (D-Link AirPlus DWL-650+) and was natively supported by 6.06 Dapper all the way to 7.04 Feisty... and it worked out of the box until a few days ago when some update broke wireless access.

See this thread that was started on this (more general) problem:
[http://ubuntuforums.org/showthread.php?p=2752526#post2752526](http://ubuntuforums.org/showthread.php?p=2752526#post2752526)

Let's bump that thread, perhaps they'll bother to answer.
Thanks.

---

### Post by stoian on 2007-06-01
as far as this card is related to the latest ubuntu kernel update, a bug has been logged and confirmed:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580)

---

### Post by neptune229 on 2007-06-02
[SIZE="7"]OMG!!![/SIZE]
 [SIZE="3"]I got it to work!!! I have a Dell lappy hooked up to the same network and I looked in the network configuration or properties or something like that (mind you it runs XP) and I tinkered with Network Settings in Xubuntu and after a couple tries I got my Internet to work!!! Amazing! I've been trying for days!!! I will try to get a more detailed description here.
This confirms that there is no bug in 7.04 (well in Xubuntu anyway) but maybe my situation is odd or something. I just cannot believe I got it to work!!! I am a complete linux n00b.[/SIZE]

---

### Post by tturrisi on 2007-06-02
> **stoian said:**
> as far as this card is related to the latest ubuntu kernel update, a bug has been logged and confirmed:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580)

The url posted above and bug does not apply to the card in this thread.  The url links to a bug report re an Intel chipset adapter, not an atheros adapter.

---

### Post by tturrisi on 2007-06-02
You can always build your own madwifi driver:
[http://ubuntuforums.org/showthread.php?t=461165&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=461165&highlight=madwifi)

---

### Post by neptune229 on 2007-06-03
No there was another bug report about the DWL-650+

---

### Post by stoian on 2007-06-04
> **tturrisi said:**
> The url posted above and bug does not apply to the card in this thread.  The url links to a bug report re an Intel chipset adapter, not an atheros adapter.

you might wanna read again, the bug is not wireless card specific, the issue is not about the chipset of the adapter - the bug has been confirmed and even bumped to high importance by ubuntu developers.

---

