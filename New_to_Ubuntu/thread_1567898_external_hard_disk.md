---
title: "external hard disk"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by soramia on 2010-09-04
hi! I am a new Linux user, after 20 or more Windows' years!
I solved my first problem, but my second problem is:

i cannot read my external hard disk. i received an error

**E: Unable to locate any  package   files, perhaps this is not a Debian  Disc**

i don't understand what is this! there is a good heart ready to help me?

thank you
rosa:popcorn:):P


P.s. sorry for my english....i am italian!

---

### Post by jtarin on 2010-09-04
Can you type this in a terminal ```
fdisk -l
``` then post the results here. 




PS:Sorry for my Italian, I'm an English Teacher.:p

---

### Post by soramia on 2010-09-04
Disco /dev/sda: 160.0 GB, 160041885696 byte

255 heads, 63 sectors/track, 19457 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3e8e76

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4       19213   154304325   83  Linux
/dev/sda3           19214       19457     1959930   1c  W95 FAT32 (LBA) nascosto

---

### Post by -kg- on 2010-09-04
My next question would be, what method did you use to install Ubuntu?

The reason I ask is that you don't seem to have a swap partition.

What happens when you hot-plug the USB drive?  It should auto-mount.

---

### Post by soramia on 2010-09-04
Ubuntu was preinstalled on my netbook Dell Inspiron mini (damn! otherwise i would go straight with windows xp!!!!!!)
if I plug my usb flash memory, i can read my data without problems
if i plug my hard disk....error!
:confused:

---

### Post by -kg- on 2010-09-04
OK, next, plug in the Hard Drive, click on "OK" to clear it (if you can), then run "sudo fdisk -l" with the drive plugged in and post the results.

Did you check Software Sources?  It's strange that you get that specific message.  It tells me that something is trying to get or access "Packages" from that drive, and it shouldn't be.

---

### Post by soramia on 2010-09-04
GREAT!!!
i've tried to plug in the ext hd, i've written the sudo command and i saw the hd in the description......
and now it works

thank you so so so so so so :pmuch!

now i have another problem for the upgrade from 8.04 to 10.04..1 version, but...................................................................................................................................................................................
I prefere to stay in the old version!

I DON'T WANT ANY PROBLEM AGAIN!!!

Thank you again friend from Illinois!:guitar:

---

### Post by -kg- on 2010-09-04
Glad we got you up and running, but sooner or later you're going to need to deal with the upgrade, and sooner would be better than later.  I'm not sure when support ends for 8.04, being it is the last LTS (Long Term Support) version, but the current Lucid 10.04 release is the next LTS release.

Since LTS releases are supported for a 3 year period (as opposed to 18 months for the standard releases), support for Hardy will end at the end of April of next year.  While you can wait until then, upgrading is much more problematic.

I understand your dilemma, though.  It came pre-installed on a Dell, obviously with drivers and all included.  I know there are some issues with Dell (which is likely why Dell has [its own sub-forum here]("http://ubuntuforums.org/forumdisplay.php?f=342")), but before too long it's going to become necessary.

Just a heads-up.  There are methods to load an .iso to a USB Flash drive (I'm sure you know that), and you can use a Lucid Live USB to confirm that everything works before installing or upgrading.

Another alternative would be to back up your installation partitions to the USB hard drive before upgrading.  If there was too much problem with the upgrade (or what I would recommend...fresh installation), then you could recover your original installation from the backup.

At any rate, it's good to have a backup of your partitions in case of problems.  You might want to check out [Clonezilla]("http://www.clonezilla.org/").  Especially, check out Clonezilla Live, which can be loaded either to a CD or USB Device.  I have a Flash Drive dedicated to Clonezilla, and have already used it to back up my system.

Maybe you could contact Dell (or Costco) and ask about upgrading.  They might possibly do it for you, saving you all the hassle.  If you do, I'd certainly ask them why there is no swap partition.

Go ahead...show off your new-found knowledge!

:lolflag:

---

