---
title: "Access Ubuntu partitions from within Windows 7"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by the8thstar on 2009-02-14
Hello all,

I'm looking for a way to access my Ubuntu partitions from Windows 7. I have tried several programs, but ultimately, Windows tells me it needs to format the Ubuntu drive to access it...

Have you guys been able to access Ext3 drives? If so, how?

Thanks in advance.

---

### Post by Paqman on 2009-02-14
Do you have Win 7 installed on it's own partition, or in a VM?

There are drivers for Windows to be able to read Ext partitions, but they don't officially support Win 7. You could try them and see: [Ext2ifs](http://www.fs-driver.org/)

One thing to watch out for: make sure that your Windows virus scanners don't scan the Ubuntu partitions. They'll probably report all sorts of false positives.

---

### Post by HavocXphere on 2009-02-14
Not happening afaik. The node size used in 8.10 isn't supported by the windows tools/plugins.

So one would have to format the *nix partition to do that. Or fix the tools.

---

### Post by Paqman on 2009-02-14
Sounds like you might need to create a separate partition for sharing data then. I'd suggest using NTFS for that, as both systems can read/write to it by default.

---

### Post by the8thstar on 2009-02-14
Extifs doesn't work. I get a popup that asks me to format the drive in order to be able to access it... which obviously I won't do.

---

### Post by Paqman on 2009-02-14
> **the8thstar said:**
> Extifs doesn't work. I get a popup that asks me to format the drive in order to be able to access it... which obviously I won't do.

That's due to the node size issue that HavocXphere mentioned.

---

### Post by the8thstar on 2009-02-17
Indeed. I guess I have no choice but wait until the dev figures something out in his/her next release.

---

### Post by yther on 2009-02-17
I have a sneaky idea for you, not sure if it's actually possible, though.

Make a VM with VirtualBox or something, inside Windows 7, load up something small like Crux or SystemRescueCD.  Get the VM to mount your ext3 drives.  Set up Samba shares from inside the VM.  Now you should be able to access those shares from Windows 7 as long as you have the VM running.

I haven't tried it, of course, so good luck if you do!  ;)

*Edit:  It just occurred to me that I came across a thumb-drive-sized Linux distro a couple of years ago.  I think it was designed to run from inside Windows using Qemu or something.  If you can find whatever the heck that was, it might do the trick.*

---

### Post by stchman on 2009-02-17
Amazing that Windows 7 does not have ext2/3 native.  Linux can read/write to ntfs OOB.

This works on Vista.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by the8thstar on 2009-02-20
I installed ext2fs. It works!

---

### Post by pirate_tux on 2009-02-20
> **the8thstar said:**
> Hello all,

I'm looking for a way to access my Ubuntu partitions from Windows 7. I have tried several programs, but ultimately, Windows tells me it needs to format the Ubuntu drive to access it...

Have you guys been able to access Ext3 drives? If so, how?

Thanks in advance.

Ext3 is an open source and free software filesystem.

So if Windows does not recognize it you should blame Microsoft and ask them for a refund.

---

### Post by the8thstar on 2009-03-11
What if they deny me? Do you think I have my chances with the Supreme Court?

---

### Post by guiohm on 2009-06-29
Hello the8thstar,

Which ext2fs did you installed ? I'm testing windows 7 x64 build 7232 and I can't install any of ext2fs drivers I can find : from [www.fs-driver.org/]("http://www.fs-driver.org/") nor [URL="http://e2fsprogs.sourceforge.net/ext2.html"]e2fsprogs.sourceforge.net/ext2.html
[/URL] 
Did anyone else found a soluce?

---

### Post by Kunzem on 2009-07-03
Hello everyone ( first post on Ubuntuforum :))

I have the same problem the application ext2IFS worked fine when i had Ubuntu 8.04 installed but since i installed Jaunty my win XP asks if i want to format the partition ?

I tried Linux reader it picks up my ubuntu drive but doesn't access it 

after some further research i found a app mountdiag to check your drives in dos prompt i ran it and it gave me this message 
"The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because the file system has an inode size unequal to 128 bytes (inode size: 256 bytes).
The only way to solve it is to backup the volume's files and format the file system: give the mkfs.ext3 utility the -I 128 switch. Finally , restore all backed-up files.
After that, the Ext2 IFS software should be able to access the volume"

hehe i'm not going to go through all that pt , is there a work around?

---

### Post by sandyd on 2009-10-27
> **yther said:**
> I have a sneaky idea for you, not sure if it's actually possible, though.
 
Make a VM with VirtualBox or something, inside Windows 7, load up something small like Crux or SystemRescueCD. Get the VM to mount your ext3 drives. Set up Samba shares from inside the VM. Now you should be able to access those shares from Windows 7 as long as you have the VM running.
 
I haven't tried it, of course, so good luck if you do! ;)
 
*Edit: It just occurred to me that I came across a thumb-drive-sized Linux distro a couple of years ago. I think it was designed to run from inside Windows using Qemu or something. If you can find whatever the heck that was, it might do the trick.*
 pendrivelinux!

---

### Post by sandyd on 2009-10-27
> **guiohm said:**
> Hello the8thstar,
 
Which ext2fs did you installed ? I'm testing windows 7 x64 build 7232 and I can't install any of ext2fs drivers I can find : from [www.fs-driver.org/]("http://www.fs-driver.org/") nor [URL="http://e2fsprogs.sourceforge.net/ext2.html"]e2fsprogs.sourceforge.net/ext2.html
[/URL]
Did anyone else found a soluce?
you can install it, but it doesn't work.
 
right click on the downloaded file and go to the compatability tab.
select a version of windows.
 
EDIT: WAIT!
THATS IT!!!!
download the driver at [http://fs-driver.org](http://fs-driver.org)
 
then right click on the file, select the compatability tab.
flip the settings to vista sp2
 
and it works!
for me at least.

---

### Post by MG2R on 2010-11-25
Damn, doesn't work for me... any other ideas? :(

---

### Post by ArtBIT on 2011-11-17
I know this is an old thread, but I'll leave this link here, because it helped me to solve this issue.

[http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/]("http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/")

Cheers

---

### Post by Rubi1200 on 2011-11-18
> **ArtBIT said:**
> I know this is an old thread, but I'll leave this link here, because it helped me to solve this issue.

[http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/](http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/)

Cheers
Thanks for sharing this information with the community :)

Thread closed.

Reason: necromancy

---

