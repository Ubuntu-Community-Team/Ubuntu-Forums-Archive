---
title: "Can't Hibernate nor Suspend cause swap isn't detected !"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Speed Of Light on 2010-05-21
Hello "Ubuntuers" :)
Hibernate and Suspend options have disappeared from my "Indicator Applet Session"
I tried to install "hibernate" package from Synaptic, but I got a dialog telling me:
> To be able to suspend the system, uswsusp needs a swap partition or file to write a system snapshot to. No such space seems to be available for this.

You should create a swap partition or file, preferably twice the size of the system's physical RAM.

Then, run 'dpkg-reconfigure uswsusp' or edit the configuration file manually.

I have a 2GB swap partition as my RAM is 2GB too.
and I had Hibernate and Suspend options working before ...
any way I grew the swap partition using GParted to 4GB, and then tried 'sudo dpkg-reconfigure uswsusp' and I get this message (with yes & no):
> The swap file or partition that was found in uswsusp's configuration file is not active.
In most cases this means userspace software suspend will not work as expected. You should choose another swap space.
However, in some rare cases, this configuration may be intentional.
Continue without a valid swap space? 
now whatever I choose I get:
> No suitable swap space for software suspend
To be able to suspend the system, uswsusp needs a swap partition or file to write a system snapshot to. No such space seems to be available for this.
You should create a swap partition or file, preferably twice the size of the system's physical RAM.
Then, run 'dpkg-reconfigure uswsusp' or edit the configuration file manually. 

Any ideas what is the problem?
How can I "relink" the swap partition again ?
How can I get Hibernate & Suspend options available?

---

### Post by wojox on 2010-05-21
Have you tried looking here for answers [SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Elfy on 2010-05-21
> any way I grew the swap partition using GParted to 4GB,

Check the uuid for the swap partition and check the one in fstab

```
sudo blkid

cat cat /etc/fstab |grep swap
```

fstab's entry should match the one given by blkid - if it does not then it neeeds to be changed

```
gksudo gedit /etc/fstab

sudo swapon -a

free -m
```

---

### Post by plucky on 2010-05-21
Also ```
cat /etc/initramfs-tools/conf.d/resume
``` has to have the correct UUID.

Good Luck

---

### Post by QLee on 2010-05-21
[QUOTE=Speed Of Light]Hibernate and Suspend options have disappeared from my "Indicator Applet Session"
I tried to install "hibernate" package from Synaptic, but I got a dialog telling me: ...[/QUOTE]

There is a possibility that you have not correctly assessed the situation. When you had suspend and hibernate working correctly it was probably with ACPI and installing software suspend (which in this case will be hibernate) is going to be a different thing. There is some chance that you want to investigate further into the possibility that what you might have needed to do was restore the options to the menu. Did the problem happen after an upgrade? I'm sure I saw some thread mentioning this issue.

You might consider purging the hibernate package, it would only give you hibernate anyway. a swap is not required for suspend (suspend to RAM), it is a power supply function.

---

### Post by Speed Of Light on 2010-05-21
Thank you all for you answers 
**@ wojox:** I did, but nothing is useful.
**@ forestpiskie:** the UUDI is the same, here is the output of both commands:
```
....
/dev/sda8: UUID="721282a7-a88d-4ea5-9b75-b527f47835a6" TYPE="swap" 

#UUID=721282a7-a88d-4ea5-9b75-b527f47835a6	none	swap	sw	0	0
```
**@ plucky:** I had the same UUID too.
**@ QLee :**

I didn't understand everything you said :oops: 
Is it that ACPI hardware support is an alternative to software support ? :?:
What do you mean by "restore the options to the menu" ?
No, the problem didn't happen after an upgrade. It happened after a while of fresh install.
How do I purge the hibernate package?

I think this could be useful: here is the output of "free" command after opening A LOT of programs:
```

             total       used       free     shared    buffers     cached
Mem:       2057832    2037976      19856          0      15028     198236
-/+ buffers/cache:    1824712     233120
Swap:            0          0          0

```

---

### Post by plucky on 2010-05-22
Post output of ```
sudo fdisk -l
``` that is lowercase L not a 1

---

### Post by Speed Of Light on 2010-05-22
Here it is:
[B]```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53ffeeaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sda2            6529       13056    52436160    7  HPFS/NTFS
/dev/sda3           13057       60801   383511650+   f  W95 Ext'd (LBA)
/dev/sda5           19744       37757   144697455    7  HPFS/NTFS
/dev/sda6           37758       60801   185100898+   7  HPFS/NTFS
/dev/sda7           13057       19220    49512267   83  Linux
/dev/sda8           19221       19743     4200966   82  Linux swap / Solaris

Partition table entries are not in disk order

```[/B]

---

### Post by QLee on 2010-05-22
[QUOTE=Speed Of Light]
I didn't understand everything you said :oops: [/QUOTE]

Yes, that happens, sometimes I write cryptically, knowing what I mean but hard for someone else to understand. You did the right thing though, ask for clarification.
 
[QUOTE=Speed Of Light]Is it that ACPI hardware support is an alternative to software support ? :?:[/QUOTE]

ACPI (these days) is what gives you suspend and hibernate, when you system was working it was probably working through ACPI. You said it was working and then stopped working. The choice you made then was to try installing something else, which had little chance of "restoring" what you had previously because it is something different.

[QUOTE=Speed Of Light]What do you mean by "restore the options to the menu" ?[/QUOTE]

That was a reference to a sparse memory I had of reading about the issue you were describing, I just can't remember all of what the thread was about. As I mentioned, I remember reading a thread (or perhaps more than one). I meant the implication to be that you would use the search function of the forum to see if any threads were applicable to your problem.

[QUOTE=Speed Of Light] No, the problem didn't happen after an upgrade. It happened after a while of fresh install.[/QUOTE]

Is your Update Manager optioned to do upgrades without confirmation or not? "after and upgrade" might have been mentioned in the other trouble reports.


[QUOTE=Speed Of Light]How do I purge the hibernate package?[/QUOTE]

Go back to the package manager you used to install it and purge it from there. If I remember correctly you used Synaptic, so completely remove.

But, don't just blindly take my advice or any advice until you understand and are sure that is what you want to do.

[QUOTE=Speed Of Light]I think this could be useful: here is the output of "free" command after opening A LOT of programs:[/QUOTE]

Yes, you mentioned that swap is not being used. However, since swap is not necessary in order to suspend (because it is suspend to RAM) that is certainly not going to be why there is no longer a suspend menu option. Did you follow my logic on that.

---

### Post by Speed Of Light on 2010-05-22
I understand you well now, thanks a lot
my update manager isn't optioned to do upgrades without confirmation, but I can't remember if this problem happened after a manual update or not.

I tried removing "hibernate" package, restarted ... but it wasn't solved

_now I had another idea to check what could be the problem_
I want to try suspending or hibernating from terminal
I found from [here]("http://ubuntuforums.org/showthread.php?t=591036") that I could run this to suspend:
```
sudo /etc/acpi/sleep.sh
```
and I got this output:
```
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
```

so the problem is in acpi-support, right?
any more ideas?

---

### Post by wojox on 2010-05-22
Try these three commands:

```

sudo swapoff -a
sudo /sbin/mkswap /dev/sda8
sudo swapon -a

```

---

### Post by Speed Of Light on 2010-05-22
I did wojox, but it didn't help.

---

### Post by wojox on 2010-05-23
I've done this before I just don't remember how. Try:

```
sudo blkid
```

And look for **TYPE="swap" UUID= some number**

Then 

```
sudo swapon –U uuid number
```

---

### Post by QLee on 2010-05-23
[QUOTE=Speed Of Light]I understand you well now, thanks a lot
my update manager isn't optioned to do upgrades without confirmation, but I can't remember if this problem happened after a manual update or not.[/QUOTE]

Good, it's always best to chase the correct problem. 

You might have been trying things for a long while, with no solution, if you had kept on as you started. However, if sometime you do actually need to worry about if you have a swap, try the command cat /var/log/dmesg | grep swap.

[QUOTE=Speed Of Light]I tried removing "hibernate" package, restarted ... but it wasn't solved[/QUOTE]

That couldn't fix anything, it was just to start getting back to the state your system was in before you installed the hibernate package.

[QUOTE=Speed Of Light]_now I had another idea to check what could be the problem_
I want to try suspending or hibernating from terminal
I found from [here]("http://ubuntuforums.org/showthread.php?t=591036") that I could run this to suspend:
```
sudo /etc/acpi/sleep.sh
```and I got this output:
```
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
```so the problem is in acpi-support, right?
any more ideas?[/QUOTE]

Well, if I saw that on my system I would check the package manager (whichever one you use) and see if I needed to install acpi-support. Seems reasonable.

Edit: I might as well mention now that the installation of the hibernate package probably disabled anything that would have conflicted with its operation, you might have to reconfigure the acpi packages.

---

### Post by Speed Of Light on 2010-05-23
Thank you very much, I'm getting closer
Please bare with me, I know I'm bothering, but I'm learning a lot

I did your [FONT="Courier New"]'sudo blkid'[/FONT] + [FONT="Courier New"]'sudo swapon -U b853285f-4f0e-467e-9bb7-f5d5e724a9dc'[/FONT]
**Can I say It was solved ? partially yes**
**- **Now 'free' command outputs:
```
             total       used       free     shared    buffers     cached
Mem:       2057832    1286972     770860          0      56608     523856
-/+ buffers/cache:     706508    1351324
Swap:      4200956      27096    4173860
```

**- **Now, when I run 'sudo dpkg-reconfigure uswsusp' It works fine.

**Seems like I have swap now :D, but still:**
**- **When I restart, everything goes back as it was **BEFORE [FONT="Courier New"]'sudo blkid'[/FONT]**
**- **I tried reinstalling packages I tought they are related to the problem (as I did before): acpi-support, acpid, apmd, indicator-applet-session, powermgmt-base, toshset
But still can't see hibernate nor suspend in THE indicator-applet-session
**- **I'm getting the same output when trying to suspend from terminal (using 'sudo /etc/acpi/sleep.sh'):
```
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
```

* I thought it would be a good idea to do 'sudo dpkg-reconfigure -a' !
I did ... the output is attached, nothing interesting but this:
```
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
```

(note: if you are wondering why there is question marks in the output, I have Arabic and Japanese language packages)

---

### Post by plucky on 2010-05-24
> I did your 'sudo blkid' + 'sudo swapon -U b853285f-4f0e-467e-9bb7-f5d5e724a9dc'

That UUID doesn't look like

> /dev/sda8: UUID="721282a7-a88d-4ea5-9b75-b527f47835a6" TYPE="swap" 

What does your **/etc/fstab** file use for the UUID as that is what mounts the swap partition?

Please post outputs of ```
cat /etc/fstab
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
```

Good Luck

---

### Post by Speed Of Light on 2010-05-24
Yes, it doesn't look like the old UUID "721282a7-a88d-4ea5-9b75-b527f47835a6"
Why did they change just now ?
Here's the output :
```

sol@sol-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=3e5e4078-06d0-4343-af8a-c6335c1ae705	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=16804CE1804CC947	/media/Hossam	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda6 :
UUID=A8304EDB304EAFDC	/media/Multimedia	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda2 :
UUID=CC9439399439277C	/media/Spare	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda1 :
UUID=F4C44D82C44D47D6	/media/Windows	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda8 :
#UUID=721282a7-a88d-4ea5-9b75-b527f47835a6	none	swap	sw	0	0
#/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


sol@sol-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="Windows" UUID="F4C44D82C44D47D6" TYPE="ntfs" 
/dev/sda2: LABEL="Spare" UUID="CC9439399439277C" TYPE="ntfs" 
/dev/sda5: LABEL="Hossam" UUID="16804CE1804CC947" TYPE="ntfs" 
/dev/sda6: LABEL="Multimedia" UUID="A8304EDB304EAFDC" TYPE="ntfs" 
/dev/sda7: LABEL="Ubuntu" UUID="3e5e4078-06d0-4343-af8a-c6335c1ae705" TYPE="ext4" 
/dev/sda8: UUID="b853285f-4f0e-467e-9bb7-f5d5e724a9dc" TYPE="swap" 
sol@sol-desktop:~$ cat /etc/initramfs-tools/conf.d/resume 
RESUME=UUID=721282a7-a88d-4ea5-9b75-b527f47835a6

```

---

### Post by plucky on 2010-05-24
```
#UUID=721282a7-a88d-4ea5-9b75-b527f47835a6	none	swap	sw	0	0

```
```
RESUME=UUID=721282a7-a88d-4ea5-9b75-b527f47835a6

```
```
/dev/sda8: UUID="b853285f-4f0e-467e-9bb7-f5d5e724a9dc" TYPE="swap"
```

The last one is the correct UUID,you have to edit the **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume** files and change them to the one specified with the blkid command and then reboot and see if now works.

Good Luck

---

### Post by Speed Of Light on 2010-05-24
Thank you man!:grin: it's done ! :grin:

I wonder why it was giving me the same UUID before ??

Anyway, now I have swap AND hibernate option, but not suspend.
acpi-support **IS** installed but "/var/lib/acpi-support" directory **IS** empty !

Any ideas?

---

### Post by wojox on 2010-05-24
Good job. It's no bother man, we've all been through this as well. :)

---

