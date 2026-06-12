---
title: "Blinking Cursor after BIOS post"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by hockeyfighter09 on 2010-12-06
I am having trouble trying to boot into Ubuntu 10.04 on my netbook.  I think a update did this, because after installing a bunch of update and restarting all I get is a blinking cursor in the top left corner of my screen after BIOS post.  I have tried booting into Ubuntu with a usb device but I still got the same result.  Does anyone have any idea how to solve this problem?  The netbook is a base model Dell Inspiron mini 10v.

---

### Post by davidmohammed on 2010-12-06
when booting, press shift to display grub and the list of kernels.  Use your cursor keys and choose the kernel previous to the current one e.g. if the current is .26 then choose .25

---

### Post by hockeyfighter09 on 2010-12-06
> **davidmohammed said:**
> when booting, press shift to display grub and the list of kernels.  Use your cursor keys and choose the kernel previous to the current one e.g. if the current is .26 then choose .25

Trying this method, the cursor stops blinking momentarily displays "Grub Loading" then continues to blink as before with no grub menu coming up to be displayed.

---

### Post by davidmohammed on 2010-12-06
can be fiddly - press and hold shift when booting.  As soon as you see "grub loading", press the down arrow.  The menu should stay on screen rather than booting using the first kernel.

---

### Post by hockeyfighter09 on 2010-12-06
> **davidmohammed said:**
> can be fiddly - press and hold shift when booting.  As soon as you see "grub loading", press the down arrow.  The menu should stay on screen rather than booting using the first kernel.

Holding the shift key down worked, thanks!  But now I have selected every kernel that appears on my grub list and all result in the same thing, the blinking cursor.

---

### Post by davidmohammed on 2010-12-06
hmmm,

try the same thing again but choose "recovery mode".  Choose the option to drop down to a command line.  Enter the following

sudo apt-get update

sudo apt-get upgrade

does this work? N.B. make sure you are connected to the ethernet via your ethernet (RJ45) port.

---

### Post by hockeyfighter09 on 2010-12-06
> **davidmohammed said:**
> hmmm,

try the same thing again but choose "recovery mode".  Choose the option to drop down to a command line.  Enter the following

sudo apt-get update

sudo apt-get upgrade

does this work? N.B. make sure you are connected to the ethernet via your ethernet (RJ45) port.

Forgot to mention this before, But I also tried to boot into the recovery mode kernels as well and no dice.  It gets stuck at  "0.1966721 ACPI: BIOS _OSI(Linux) query ignored"

---

### Post by davidmohammed on 2010-12-06
strange?  What version of ubuntu are you running?  Did you update via update-manager?


try the following

on the list of kernels press e to edit

find the line ending with "quiet splash --"

change that line to 

nomodeset quiet splash --

and boot with CTRL + X

if that doesnt work try one of

i915.modeset=0 quiet splash --
i915.modeset=1 quiet splash --
noapic quiet splash --
noacpi quiet splash --
acpi=off quiet splash --

---

### Post by hockeyfighter09 on 2010-12-06
> **davidmohammed said:**
> strange?  What version of ubuntu are you running?  Did you update via update-manager?


try the following

on the list of kernels press e to edit

find the line ending with "quiet splash --"

change that line to 

nomodeset quiet splash --

and boot with CTRL + X

if that doesnt work try one of

i915.modeset=0 quiet splash --
i915.modeset=1 quiet splash --
noapic quiet splash --
noacpi quiet splash --
acpi=off quiet splash --

Alright the "noapic quiet splash --" option worked with the 2.32.24 kernel.  I am using Ubuntu 10.04 netbook remix.  Is there a way to make this change permanent?  Also would it be ok to just enable security fixes for the future, since I need absolute stability for this machine?  Thanks for your help!

---

### Post by davidmohammed on 2010-12-06
Ok,
  to permanently fix it, when you get to the desktop open up a terminal window.

type the following

gksudo gedit /etc/default/grub

find the line 

GRUB_CMDLINE_LINUX=""

change to

GRUB_CMDLINE_LINUX="noapic"

save and close

then type

sudo update-grub



if you just want security fixes launch update manager

click the settings... button

on the update tab just set the options that you want to update

---

