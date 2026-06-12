---
title: "Cannot Enable Restricted Driver, Broadcom 43xx chipset family / bcm 43xx-fwcutter"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by mawil10132 on 2013-09-29
[Ubuntu 7.10 (Gutsy Gibbon)]("http://old-releases.ubuntu.com/releases/gutsy/")  **This does install on emachine 5414 !**

There  were no issues during install, install went smoothly, 

This was the  first unbuntu version which seems to recognize the Linksys WUSB600n wireless  thumb drive. But for now I cannot enable, 'Broadcom 43xx chipset family', 

I  go to System, Administration, Restricted Drivers, then the list pops  up, but when I select 'Enable' box. I get this message; the software source for  package, bcm 43xx-fwcutter is not enabled.  

Can anyone say what's going on? Why I cannot enable the restricted driver when I click on it's enable box and instead of becoming enabled I get this message, "the software source for  package, bcm 43xx-fwcutter is not enabled."

This is the finial step that I need to cross in order to have a fully function and fully installed version of ubuntu on the old emachine 5414 which originally came with windows xp.

By the way, Ethernet does work and I can get the emachine online.

I've been working on this for two days and I got to make this one thing work!

Michael

---

### Post by wildmanne39 on 2013-09-29
Hi, as you may know 7.10 is very outdated and is not even receiving security updates anymore which also means you can not install any software except from an archive repository so that software would be only update until support stopped on 7.10 several years ago now. So you can not install the driver because it is not on the server any longer.

I recommend you try lubuntu or xubuntu 12.04.
Thanks

---

### Post by MIJ-VI on 2013-09-30
> **mawil10132 said:**
> [Ubuntu 7.10 (Gutsy Gibbon)]("http://old-releases.ubuntu.com/releases/gutsy/")  **This does install on emachine 5414 !**

There  were no issues during install, install went smoothly, 

This was the  first unbuntu version which seems to recognize the Linksys WUSB600n wireless  thumb drive. But for now I cannot enable, 'Broadcom 43xx chipset family', 

I  go to System, Administration, Restricted Drivers, then the list pops  up, but when I select 'Enable' box. I get this message; the software source for  package, bcm 43xx-fwcutter is not enabled.  

Can anyone say what's going on? Why I cannot enable the restricted driver when I click on it's enable box and instead of becoming enabled I get this message, "the software source for  package, bcm 43xx-fwcutter is not enabled."

This is the finial step that I need to cross in order to have a fully function and fully installed version of ubuntu on the old emachine 5414 which originally came with windows xp.

By the way, Ethernet does work and I can get the emachine online.

I've been working on this for two days and I got to make this one thing work!

Michael

The obsolete Ubuntu option:

How to Use Obsolete Versions of Ubuntu on Old Computers | LinuxG.net
[http://linuxg.net/how-to-use-obsolete-versions-of-ubuntu-on-old-computers/](http://linuxg.net/how-to-use-obsolete-versions-of-ubuntu-on-old-computers/)

Some modern LXDE options which installed (barely) on a 500MHz Socket 370 Celeron with 192MB RAM

Marginally useable under the most desperate of circumstances on said machine:

(antiX-13.1_386-full)

antiX-Linux - Browse /Final/antiX-13.1 at SourceForge.net
[http://sourceforge.net/projects/antix-linux/files/Final/antiX-13.1/](http://sourceforge.net/projects/antix-linux/files/Final/antiX-13.1/)

debian-7.1.0-i386-lxde-CD-1 (This uses a text-based installer.)

Index of /debian-cd/7.1.0/i386/iso-cd
[http://cdimage.debian.org/debian-cd/7.1.0/i386/iso-cd/](http://cdimage.debian.org/debian-cd/7.1.0/i386/iso-cd/)

Precise Puppy is version 5.7.1
[http://www.puppylinux.com/download/index.html](http://www.puppylinux.com/download/index.html)

Completely unusable at 500MHz / 192MB:

"Zorin OS 6.2 Lite is the streamlined version of Zorin OS for old and low-spec computers."
[http://zorin-os.com/free6.html](http://zorin-os.com/free6.html)

---

### Post by mawil10132 on 2013-09-30
> **Wild Man said:**
> Hi, as you may know 7.10 is very outdated and is not even receiving security updates anymore which also means you can not install any software except from an archive repository so that software would be only update until support stopped on 7.10 several years ago now. So you can not install the driver because it is not on the server any longer.

I recommend you try lubuntu or xubuntu 12.04.
Thanks


I tired them both and they both stopped right off the bat.  I did manage to jump up to hardy heron from an older version, I used a special ISO version which could be used to upgrade without being online, I had tried using the same version a few days ago by trying a full install but it didn't make it thru. I assumed it run out of memory. I'm guessing that because I 'upgraded' this time instead of full install it uses least memory?

Anyway, Hardy Heron worked differently, it installed the broadcom driver! and it says it is active and enable!

Now maybe because I'm not familiar with ubuntu over windows that I cannot see how to select my home router, I'm looking for a window that shows found wifi and I'm not seeing it, Soooo, How does one find a home wifi get connected??   Man O Man I'm so close I can taste it!!!  

Michael

---

### Post by MIJ-VI on 2013-10-01
> **mawil10132 said:**
> I tired them both and they both stopped right off the bat.  I did manage to jump up to hardy heron from an older version, I used a special ISO version which could be used to upgrade without being online, I had tried using the same version a few days ago by trying a full install but it didn't make it thru. I assumed it run out of memory. I'm guessing that because I 'upgraded' this time instead of full install it uses least memory?

Anyway, _Hardy Heron worked differently, it installed_ the broadcom driver! and it says it is active and enable!

Now maybe because I'm not familiar with ubuntu over windows that I cannot see how to select my home router, I'm looking for a window that shows found wifi and I'm not seeing it, Soooo, How does one find a home wifi get connected??   Man O Man I'm so close I can taste it!!!  

Michael

Can you run [SIZE=1][FONT=courier new]sudo lshw[/FONT][/SIZE] in Terminal and then post the results here within CODE (#) tags? That way others can see exactly which hardware components your machine is made of.

---

### Post by varunendra on 2013-10-02
> **mawil10132 said:**
> Man O Man I'm so close I can taste it!!!

I wouldn't call being on an OS from 2008 as being "close" :P

Most of us may not even know or remember how the network manager looked like or was configured in Hardy.

What are your system's hardware specs by the way (CPU, memory)? Did you verify the integrity of the downloaded ISOs of xubuntu and lubuntu that you tried with? ([How to MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")).

I would say just make sure your optical drive is working fine, burn a cd of a supported version of xubuntu/lubuntu and do a fresh install.

We maybe able to predict in advance how well your wireless card may work if you show us the output of -
```
lspci -nnk | grep -iA2 net
```

---

