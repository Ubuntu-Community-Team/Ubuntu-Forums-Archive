---
title: "Unable to locate packages"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Roseport on 2011-03-04
Thought I posted this yesterday but cannot find it.  Doing it again.  I am new to Linux/Ubuntu so please bear with me.

I recently installed Ubuntu 10.10 (server Maverik-meerkat) on an Intel x86_64 bit system and can get to the terminal window.  No GUI installed.  Then I am trying to install KVM and another OS.  The sudo apt-get succeeded in installing kvm and libvirt (can see in dpkg output).  However > sudo apt-get install virtinst  fails.
It says unable to locate the package.  I tried to do > sudo apt-get update followed by the previous command. The update part worked but not the actual virtinst.  I also see this for other packages.   I am guessing that these packages are not part of the Ubuntu server download?  I have network connection (I can ping internal system at home and external site like yahoo.com).   
By the way when I installed Ubuntu, I specified that it load support for Virtualization, but apparently that didn't work or install KVM,  This is surprising but guess can live with it if I can manually do it.  Yes, my processor (core i7) can support KVM.

In general this seems to have been the issue for a few others as well (going by a thread here, but the suggestion there to use apt-get update first, did not work for me).   In general where would one get missing packages fro Ubuntu? Debian site?

---

### Post by NCLI on 2011-03-04
That package doesn't exist, do you mean [virtinst]("http://apt.ubuntu.com/virtinst")?

---

### Post by maqtanim on 2011-03-04
Are you looking for [this one]("http://packages.ubuntu.com/maverick-updates/all/virtinst")?

---

### Post by Roseport on 2011-03-04
thanks.  Not sure what you meant by that package doesn't exist.  Anyway I went to the other link that sent and got the package on an USB thumb drive and now struggling to get it mounted.   Being a newbie, it is rather frustrating
I know it recognized the USB drive since I see it in /var/log/kern.log under various labels (?) - sg2 sg3 sr2 etc.  When I try to mount them none of them works.  I tried modprobe usb_storage and I get back to usual Unable to locate package.

Why doesn't Ubuntu put these as part of download anyway?  Seems like expecting an USB drive to work seems to a minimal expectation at this point in computing.

---

### Post by uRock on 2011-03-04
> **Roseport said:**
> Thought I posted this yesterday but cannot find it.  Doing it again.  I am new to Linux/Ubuntu so please bear with me.
You did and I moved it to its own thread and bumped it, so it should have shown up in your [UserCP]("http://ubuntuforums.org/usercp.php") page. Anyway it is here and being this thread is getting attention I will close the other. [http://ubuntuforums.org/showthread.php?t=1699562](http://ubuntuforums.org/showthread.php?t=1699562)

---

### Post by oldos2er on 2011-03-05
Looks like virtinst is in the extras repository. To enable it, see [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

