---
title: "Advantages of separate boot and home partitions?"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by Lkm on 2011-07-17
Hi, I was wondering if there was much point to having a separate boot partition as the bootloader is always installed to the mbr.
Also, if I set one partition as /home, can I use that as the home folder for another distro too? If this is the case which other folders (usr etc) can be shared by multiple distros?

---

### Post by mikejonesey on 2011-07-17
all things are posible; but i wouldn't share a home dir across distros, (diff software overwriting each other)... also different UID's... same partition would be fine though and this is regularly done...

the benefit of having /home as a sep partition is it is unefected during sys upgrades...

as regards the /boot partition, i wouldn't bother; it only ever existed to get around cruddy bios software limitations... (a thing of the past)

---

### Post by mikejonesey on 2011-07-17
ps; it's safe to partition /boot, /home, /opt, /tmp, /usr, /var, and of coarse swap...

---

### Post by jmszr on 2011-07-17
Lkm,

This thread: [http://ubuntuforums.org/showthread.php?t=1806369](http://ubuntuforums.org/showthread.php?t=1806369) does an excellent job of discussing partitioning with more than one distro.

Hope that helps.

---

### Post by Lkm on 2011-07-18
I see, so a possible solution would be shared /data .. how would that work? Would the data partition be mounted within home, so one save items to the home folder normally and then this would save to the data partition automatically?

And if I have a separate /home partition from /, would root only need up to a set amount of space since it only saves settings-type things? What do the other folders within root do? :)

Cheers!

---

### Post by Lkm on 2011-07-18
About that last part, I found this actually: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by oldfred on 2011-07-18
I do not think Herman even uses a separate partition for swap but a swap file:
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Explaination of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I actually mount my /data in /mnt/data and link folders into /home. My data partition at the top level has all the standard folders like Documents, Music etc and a few more. On a new install when I know they are empty I just delete the standard folders and link in my folders from /mnt/data. Then it looks like standard. I now keep /home in / (root) since it is so small with just the hidden settings. I do also move some hidden folders that have lots of data like my Firefox & Thunderbird profiles. I have not yet moved .wine as I gather it is a bit more complicated than just relinking, but with Picasa in my /home it is about 1GB and 3/4 of that is .wine.

---

### Post by Paqman on 2011-07-18
> **Lkm said:**
> Hi, I was wondering if there was much point to having a separate boot partition as the bootloader is always installed to the mbr.


No, I agree with the others, there's no advantage to putting /boot on a separate partition.

> 
Also, if I set one partition as /home, can I use that as the home folder for another distro too? If this is the case which other folders (usr etc) can be shared by multiple distros?

Different distros can share one /home partition, just use different accounts on each distro. That way each account will have it's own directories under /home and they won't conflict with each other. Different distros use different versiosn of software, and number the UID of the users differently, so you would have config and permissions issues otherwise.

---

### Post by SeijiSensei on 2011-07-18
> **Paqman said:**
> No, I agree with the others, there's no advantage to putting /boot on a separate partition.

Yes, there is.  If you want to support multiple distributions on the same machine, having a separate /boot partition makes this much easier.  At installation, grub will create a single composite /boot/grub/grub.cfg that contains the definitions for all the operating systems it finds.  If /boot is created within a particular distribution's filesystem, that won't be possible.

512 MB is plenty large enough for /boot and miniscule by the standards of modern hard drives.  It does use up one of your primary partitions, but that's not a big deal.

I also put /home on a separate partition and share it among different distributions.  The only time this becomes problematic is when the desktop environment undergoes a major change.  For instance, the move from KDE 3 to KDE 4 made profound changes to $HOME/.kde. Such changes are pretty rare, though.  I kept /home the same when moving from KDE 4.3 to 4.6 without incident.

I do try and enforce a common set of /etc/passwd and /etc/group files across distros so that user and group names map correctly.  I've generally adopted Debian/Ubuntu's numbering which starts users at UID=1000 for RHEL/CentOS to maintain consistency.  Just create master copies of /etc/passwd, /etc/group, and /etc/shadow and copy them to all the distros.  If you run servers, you may need to futz with with the various unprivileged users like "www-data" in Ubuntu which is the equivalent of "httpd" in RHEL-flavored distros.

---

### Post by psusi on 2011-07-18
> **SeijiSensei said:**
> Yes, there is.  If you want to support multiple distributions on the same machine, having a separate /boot partition makes this much easier.  At installation, grub will create a single composite /boot/grub/grub.cfg that contains the definitions for all the operating systems it finds.  If /boot is created within a particular distribution's filesystem, that won't be possible.

It will do that regardless of whether /boot is on its own partition or not.

There are two reasons to have /boot on its own partition:

1)  You have an ancient PC bios that can't access the whole disk, so /boot needs to be in the part it can access.

2)  You want to use a filesystem for / that the boot loader can't read, so you separate /boot and use a filesystem type there that the boot loader can read.

> **SeijiSensei said:**
> 512 MB is plenty large enough for /boot and miniscule by the standards of modern hard drives.  It does use up one of your primary partitions, but that's not a big deal.

There's no reason it has to be a primary.

---

### Post by SeijiSensei on 2011-07-18
> **psusi said:**
> It will do that regardless of whether /boot is on its own partition or not.

So if I put /boot under / in Fedora on, say, /dev/sda3, and I now install Ubuntu onto /dev/sda6, how does the Ubuntu installer know to look into /dev/sda3 and add the kernels and associated files to /boot there?   I'm surprised it would be able to do this, particularly if I don't reference /dev/sda3 at all during the drive configuration.  I always assumed that not referencing a partition in the installer meant that it would be ignored entirely during installation and not mounted at boot.  Wouldn't Ubuntu's kernel and associated files be stored in /boot on /dev/sda6, while Fedora's are on /dev/sda3?  How do they get integrated into a single boot menu?

Does this have to do with the fact that grub in installed in the MBR and thus somehow "knows" to look in an otherwise unmounted partition for its files?

---

### Post by oldfred on 2011-07-18
Grub2's os-prober looks for grub, grub2 or other menu entries which it tries to copy & convert to grub2 style. We have seen where some versions use non-standard menu entries and something does not quite get converted correctly into the grub2 boot stanza. Not sure if it looks also for boot files or not.

---

### Post by bodhi.zazen on 2011-07-19
There are several advantages of separate partitions, it sort of varies by partition.

A short description is here:

[http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html](http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html)

Several things have been discussed in this thread:

1. Separate /home partition - in addition to quota, noexec, etc, one can re-install the OS and preserve user data.

An alternate is a data partition.

In my experience, keeping data separate form the rest of the OS is always a good idea.

2. /boot vs /grub (/boot/grub).

If you try to share a /boot partition, it will be formatted over written by the second OS. You may, however, share a /boot/grub partition.

/boot is NOT the same as a MBR. The /boot partition contains (in a  nutshell) the kernel, initramfs, and grub files.

If you do not understand the boot process, see [http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-boot-init-shutdown-process.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-boot-init-shutdown-process.html) or any other guide ;)

A separate boot partition is required for partitions or file systems that can not be directly booted by Gurb - LVM, encryption, and RAID are the most common.

3. When sharing a /home partition across distros you will be fine so long as each user has a unique user name on each distro.

4. When sharing files across distros you need to keep in mind the system maps users by id , and some distroos (fedora) start at 500, and others at 1,000 .

---

### Post by psusi on 2011-07-19
> **bodhi.zazen said:**
> 
1. Separate /home partition - in addition to quota, noexec, etc, one can re-install the OS and preserve user data.

You can get the last by just not checking the format box when you reinstall.

> **bodhi.zazen said:**
> If you try to share a /boot partition, it will be formatted over written by the second OS. You may, however, share a /boot/grub partition.

Again, just don't check the format box.

> **bodhi.zazen said:**
> A separate boot partition is required for partitions or file systems that can not be directly booted by Gurb - LVM, encryption, and RAID are the most common.

Grub2 understands LVM and raid.

---

### Post by bodhi.zazen on 2011-07-19
> **psusi said:**
> You can get the last by just not checking the format box when you reinstall.

While you can do lots of things, some things that can be done are not very good ideas. 

Installing system files over the top of an unformated partition is asking for problems. Sure it can be done, but a separate /home or /data partition is a much better idea.

> Again, just don't check the format box.

Many distros installers will not give that option (to not format /boot).

Same advice for a /boot partition. Best practice is, IMO, to use a unique /boot partition, either as a physical partition or on your / partition for each distro.

> Grub2 understands LVM and raid.

grub2 yes, but some OS, such as Fedora, still use grub 1, thus a boot partition is necessary.

And you still need a separate /boot partition for LUKS.

---

### Post by psusi on 2011-07-19
> **bodhi.zazen said:**
> While you can do lots of things, some things that can be done are not very good ideas. 

Installing system files over the top of an unformated partition is asking for problems. Sure it can be done, but a separate /home or /data partition is a much better idea.

Ubuntu at least, is smart enough to delete everything in the usual system directories before installing, leaving /home intact.  It might be a problem for other distros, but this is the recommended way to do it in Ubuntu.

> **bodhi.zazen said:**
> Many distros installers will not give that option (to not format /boot).

Then bug reports should be filed against them.  When one does create a /boot partition, one usually does share it between multiple installs so it is important that the new install not wipe out the others' kernels.

> **bodhi.zazen said:**
> grub2 yes, but some OS, such as Fedora, still use grub 1, thus a boot partition is necessary.

If you are dual booting, you can just reinstall Ubuntu's grub2.  It will automatically add Fedora to the menu.

---

### Post by Lkm on 2011-07-19
I recentlly installed openSUSE which used the earlier version of GRUB. It was pretty, but it only recognised windows and itself, but not ubuntu.
I had a /boot partition for ubuntu, I don't think I  specified it to openSUSE at install. Would this have avoided that problem? Or would there have been other issues since ubuntu and openSUSE use different versions of GRUB?
(I got rid of the separate boot partition as I could not reinstall GRUB2 as I had done on previous occasions. Mounting the boot partition and / both didn't work. I just ended up reinstalling ubuntu with home still intact.)

Thanks for all the infos :)
I think on future installs, if I ever reorganise my system with multiple distros I'll have the separate /home and a shared /data partition.

If I shared a partition with /usr or /usr/local would that share extra installed programs, or would that not work for different distros?

---

### Post by psusi on 2011-07-19
> **Lkm said:**
> 
If I shared a partition with /usr or /usr/local would that share extra installed programs, or would that not work for different distros?

Won't work for different distros; they will each try to put their own files there and overwrite the other, causing all kinds of breakage.

---

### Post by SeijiSensei on 2011-07-19
> **psusi said:**
> Won't work for different distros; they will each try to put their own files there and overwrite the other, causing all kinds of breakage.

That shouldn't be true for /usr/local.  Both RHEL-flavored and Debian-flavored distros only create the directory skeleton but don't write any files there.  Same is true, I believe, for /opt.  To put files there would violate the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

I have a separate partition for /usr/local. I use it for scripts I write and for software I compile from source.  That way I can use these items in multiple distributions.

---

### Post by amjjawad on 2011-07-20
All my advanced friends are here so my input would be totally a waste :)

---

### Post by psusi on 2011-07-20
> **SeijiSensei said:**
> That shouldn't be true for /usr/local.  

You might or might not get away with it, because when you do compile a program from source you are linking it against the libraries in the distribution you compile it on.  It may not work with the libraries in the other distribution when you run it from there.

---

