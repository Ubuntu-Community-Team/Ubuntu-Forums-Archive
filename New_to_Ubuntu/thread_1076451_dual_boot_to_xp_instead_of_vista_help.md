---
title: "dual boot to xp instead of vista help"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by campbuds on 2009-02-21
I have a vaio vgn-cr220e and I primarily use ubuntu on the laptop, but because of a crappy driver for the webcam I need to have windows installed to use skype to video chat.

I want to ditch vista and downgrade to xp... problem is I cannot get xp to complete and install. Searching google though it seems no one else has had an issue with this laptop.

I know this is ubuntu forum, I tried posting to the "other os" section but cannot. I use ubuntu most the time and the only reason I use windows is for skype and my webcam functionality.

Please help! I HATE VISTA!

---

### Post by Jack Shankle on 2009-02-21
Hi,
Try this site. It helped me with triple booting problems.
In that site look for a forum called: Freebcd.

    [www.neosmartt.net/forums](www.neosmartt.net/forums)
Hope this helps.

---

### Post by Crandom on 2009-02-21
Do you have any more information? What is the exact error problem with the install?

---

### Post by campbuds on 2009-02-21
> **Crandom said:**
> Do you have any more information? What is the exact error problem with the install?

This seems to best describe it, but the solution they offer does nothing for me at all.

[http://support.microsoft.com/kb/828267/en-us]("http://support.microsoft.com/kb/828267/en-us")

---

### Post by campbuds on 2009-02-21
i would very much appreciate help figuring this one out.

thanks in advance!

---

### Post by TimDaniels on 2009-02-22
> **campbuds said:**
> I have a vaio vgn-cr220e and I primarily use ubuntu on the laptop, but because of a crappy driver for the webcam I need to have windows installed to use skype to video chat.

[....]

Please help! I HATE VISTA!

If you by chance want to keep Vista and not hassle with getting XP drivers for your Vaio, I have a mashup (summary/compendium) of several articles on how to dual-boot Vista and Ubuntu without using apps like EasyBCD, etc.  Editing Ubuntu's boot menu to include Vista is done automatically by the Ubuntu installer, but if you want to put an entry in Vista's boot menu to boot Ubuntu, here's how:
---------------------------------------
DISTILLATION OF SEVERAL ARTICLES -
USING BCDEDIT TO ADD A LINUX ENTRY TO VISTA'S BCD STORE
-------------------------------------------------------

Install Grub to Linux partitiion (not to MBR)

in Ubuntu:

find device names of Vista(VV) and Linux(LL) partitions
  System/Preferences/Hardware Information/SCSI Adapter [CANNOT FIND]
or
  sudo fdisk -l

copy the boot sector of the Linux partition
  directly to the root of the Vista partition
(check the name of the Vista partition in /media)
  sudo dd if=/dev/sdLL  of=/media/sdVV/Ubootsect.bin  bs=512  count=1

Use Synaptic to load Gparted from installation DVD,
mark Vista partition "active" to load Vista's BCD
  [use Gparted's "Manage flags" to set the "boot" flag]

  System/Administration/Partition_Editor
or
  sudo gparted


in Vista:

rt-click command prompt icon, select "Run as administrator",
show the current boot menu entries
  bcdedit /enum

(if there is already an obsolete entry for Ubuntu,
 delete it with:  bcdedit /delete {obsoleteID}     )

in Vista's command prompt, make a new BCD entry
  bcdedit /create /d "Ubuntu" /application BOOTSECTOR

  [rt-click|Mark, highlight "{long hex no.}", rt-click]
  [refer to the returned long hex no. as "UbuntuID"]

declare the ID as a boot device
  [rt-click|Paste to fill in "{UbuntuID}" in cmd below]

  bcdedit /set {UbuntuID} device boot
  [including the braces]

specify the path to the copy of the Ubuntu boot sector
  bcdedit /set {UbuntuID} path \Ubootsect.bin

add Ubuntu entry to the boot time menu
  bcdedit /displayorder {UbuntuID} /addlast

set default OS timeout to be 10 seconds
  bcdedit /timeout 10

show the new boot menu entries
  bcdedit /enum

in Ubuntu, edit boot menu
  sudo gedit /boot/grub/menu.lst
-----------------------------------

*TimDaniels*

---

### Post by campbuds on 2009-02-22
thank you, but I want to dual boot xp and ubuntu,

the dual boot part is not the problem, getting XP to install is the problem

---

### Post by TimDaniels on 2009-02-22
> **campbuds said:**
> thank you, but I want to dual boot xp and ubuntu,

the dual boot part is not the problem, getting XP to install is the problem

Then this website should help:
apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm

Clickable:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

*TimDaniels*

---

