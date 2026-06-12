---
title: "Upgrading to 9.4"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by bj218 on 2009-05-21
I would like to up grade from Ubuntu 8.10 to Ubuntu 9.4 but I have a few questions.
Can I do an upgrade ie not delete 8.10?
If I can do this where can I get the upgrade + instructions?
I now have Ubuntu8.10 and Mint6 on one drive and WinXP on a second drive. The Mint grub now control's the boot sequence I would like to change this so that Ubuntu is in control is this possible? If so where can I get inst. on how to do this?

---

### Post by maybeway36 on 2009-05-21
When you install Ubuntu, by default it will take control over the boot sequence. It will detect Mint and XP for you too.
Ubuntu has official upgrade instructions: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by the.dark.lord on 2009-05-21
For upgrading, check this out - [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) .

---

### Post by the.dark.lord on 2009-05-21
Hey may, you beat me!

---

### Post by bj218 on 2009-05-24
> **maybeway36 said:**
> When you install Ubuntu, by default it will take control over the boot sequence. It will detect Mint and XP for you too.
Ubuntu has official upgrade instructions: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I downloaded the 9.04iso and then transfered it to a CD. But when I run the CD it wants to format my Ubuntu partition. I want to do an upgrade is their a up ISO for just upgrading?

---

### Post by Dill on 2009-05-24
The thing about upgrading is that you actually don't have to install the new version from a boot CD. The instructions that the two above posters provided explain how to upgrade from 8.10 automatically, without having to install Ubuntu again.

For reconfiguring GRUB, you should be able to use that boot CD you just burned. Check this out: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) .

Cheers,
Dill

---

### Post by Didius Falco on 2009-05-24
If you want to upgrade from an ISO, you need to get the Alternate installer:

 1. Download the alternate installation CD ISO.
   
2.  Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded. *

*If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

           ```
 sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
```

3. A dialog will be displayed offering you the opportunity to upgrade using that CD.

4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```

Regards,

Didius

PS, do the following before Upgrading.

1. Turn off any 3rd party software sources in your Software Sources.

2. Un-activate or uninstall any proprietary video drivers.

3. Make sure you've applied all the Updates for your current version before Upgrading.

---

### Post by bj218 on 2009-05-26
> **Didius Falco said:**
> If you want to upgrade from an ISO, you need to get the Alternate installer:

 1. Download the alternate installation CD ISO.
   
2.  Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded. *

*If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

           ```
 sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
```

3. A dialog will be displayed offering you the opportunity to upgrade using that CD.

4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```

Regards,

Didius

PS, do the following before Upgrading.

1. Turn off any 3rd party software sources in your Software Sources.

2. Un-activate or uninstall any proprietary video drivers.

3. Make sure you've applied all the Updates for your current version before Upgrading.

WHER DO i GET THE ALTERNET INSTALLER?

---

### Post by bj218 on 2009-05-28
I gave up on trying to update Ubuntu8.10  from  the Internet. I did not want to lose my installed 
software I only wanted to get the latest Ubuntu9.04 upgrades. On top of that the ISO that I downloaded
when converted to a CD was unbootable by me as it contained nothing but folders and I was unable
to find a folder that would start the install process. As a last resort I did the following:
  
To update Ubuntu8.10 to 9.04 
Clk on System then clk on Administration then clk on Software Sources clk on Updates tab  and make sure &#8220;Release Upgrade&#8221; is set to &#8220;Normal releases&#8221; clk Close.

Next press Alt and F2 in &#8220;Run Application&#8221; type &#8220;update-manager -d&#8221; clk Run you should see
&#8220;New distribution release 9.04 is available&#8221; clk on Upgrade.

 I do not understand how this works but I think I now have Ubuntu 9.04. The only problem I can see right now is that I lost a few of the things that I had installed but not all of them ??!!  This method sure
beats downloading an ISO and then making a bootable CD. I have a feeling that I may be missing
something this was just to easy! Can someone comment on what I on what I did!!

---

### Post by Didius Falco on 2009-05-28
> **bj218 said:**
> I gave up on trying to update Ubuntu8.10  from  the Internet.

<snip> As a last resort I did the following:
  
To update Ubuntu8.10 to 9.04 
Clk on System then clk on Administration then clk on Software Sources clk on Updates tab  and make sure “Release Upgrade” is set to “Normal releases” clk Close.

Next press Alt and F2 in “Run Application” type “update-manager -d” clk Run you should see
“New distribution release 9.04 is available” clk on Upgrade.

 I do not understand how this works but I think I now have Ubuntu 9.04. The only problem I can see right now is that I lost a few of the things that I had installed but not all of them ??!!  This method sure
beats downloading an ISO and then making a bootable CD. I have a feeling that I may be missing
something this was just to easy! Can someone comment on what I did!!


You just upgraded from the internet. ;) To test that you have 9.04 now, open a Terminal shell and type:

```
lsb_release -a
```

Regards,

Didius

---

### Post by bj218 on 2009-05-31
> **Didius Falco said:**
> You just upgraded from the internet. ;) To test that you have 9.04 now, open a Terminal shell and type:

```
lsb_release -a
```

Regards,

Didius

Thanks much it looks like I now have Ubuntu9.04

bill@bill-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty
bill@bill-desktop:~$ 
What does "No LSB modules are available." meane?

---

### Post by Didius Falco on 2009-05-31
LSB is the Linux Standards Base. It's a standard designed to help with cross-compatibility for linux apps. That way, developers, rather than having to compile for different distros, could generate one package that could be installed on all linux distros.

Instead, the way it works now is that often a developer will release one type of package and the source code, and then others (whether the end-user or a web site) would compile that source code into an installable package for the desired distro.  

Here is a Wiki page about it:

[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

Here is an interview with Theodore Tso, the Chief Platform Strategist at the Linux Foundation about LSB.

[http://broadcast.oreilly.com/2008/09/theodore-tso-how-the-lsb-helps.html](http://broadcast.oreilly.com/2008/09/theodore-tso-how-the-lsb-helps.html)


This is the web site of the Linux Foundation, the people trying to implement this as a standard for all linux distros. This section of the web site is LSB-specific:

[http://ldn.linuxfoundation.org/lsb/charter](http://ldn.linuxfoundation.org/lsb/charter)

Finally, if you open Synaptic (**System/Administration/Synaptic Package** **Manager**) and do a search for "lsb" you'll see a lot of LSB related-things you can install.

If you installed those files and reran that command, you'd get a different message.

Regards,

Didius

---

