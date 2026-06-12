---
title: "Trouble flashing BIOS"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-06-03
I have been [following this guide]("http://ubuntuforums.org/showthread.php?t=318789") to update my laptop's BIOS but am having trouble.  I've downloaded the latest BIOS from the Dell website - it's an .exe file and is sitting on my desktop.

The simplest solution seems to be to burn this to a CD, but I need to make the CD bootable by creating a temp dir on the CD using FreeDOS.  Now, I've copied and pasted the code (quoted below) straight into the Terminal but I get no luck and hit this problem:

dan@DansDell:~$ sudo cp ~/NewBiosFiles/* /tmp/cdr
cp: cannot stat `/home/dan/NewBiosFiles/*': No such file or directory

So two very noobish questions:

First, when code is up on a forum for me to just copy and paste, is it right to select the entire box and paste it all into the Terminal at once?  Or do I need to copy and paste line-by-line? (Which in this case seemed more effective as it told me where the problem occurred)

Second, what am I doing wrong?  How can I get my laptop to acknowledge and boot from the CD - as simply burning the .exe file to it isn't enough.


Apologies for all the questions!

> [B]
[SIZE=2][COLOR=Black] M2: CD[/COLOR][/SIZE]
[/B][SIZE=1]*Unpack FreeDOS image &#8594; create temp dir &#8594; mount  FreeDOS image to /tmp/cdr &#8594; copy flashing tool*[/SIZE][SIZE=1]*  and new BIOS image to /tmp/cdr *[/SIZE][SIZE=1]*(see  footnotes below) &#8594; unmount image &#8594; install mkisofs &#8594; create ISO &#8594; burn  ISO to disc *[/SIZE][SIZE=1][I]&#8594; reboot following vendor  instructions

[/I][/SIZE][SIZE=1]*Note: "NewBiosFiles" listed below is  pseudocode for the extracted location of the new BIOS image + related  files that you just downloaded*[/SIZE] 	Code:
 	wget [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz)
gunzip FDOEM.144.gz
mkdir /tmp/cdr
sudo mount -t vfat -o loop FDOEM.144 /tmp/cdr
sudo cp ~/NewBiosFiles/* /tmp/cdr
sudo umount /tmp/cdr
sudo apt-get install mkisofs
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144
cdrecord -v newBIOS.iso 
[note: in later releases, /usr/bin/mkisofs symlinks to  /usr/bin/genisoimage]
[note: in later releases, /usr/bin/cdrecord symlinks to /usr/bin/wodim]

---

### Post by echo.whoami on 2010-06-03
What's the model of the dell laptop???

---

### Post by danielgrosvenor on 2010-06-03
Dell Inspiron 1370.  I'm running Ubuntu x64 on it.

The BIOS file is called 1370_A02.exe if that's any help.

---

### Post by sandyd on 2010-06-03
> **danielgrosvenor said:**
> I have been [following this guide]("http://ubuntuforums.org/showthread.php?t=318789") to update my laptop's BIOS but am having trouble.  I've downloaded the latest BIOS from the Dell website - it's an .exe file and is sitting on my desktop.

The simplest solution seems to be to burn this to a CD, but I need to make the CD bootable by creating a temp dir on the CD using FreeDOS.  Now, I've copied and pasted the code (quoted below) straight into the Terminal but I get no luck and hit this problem:

dan@DansDell:~$ sudo cp ~/NewBiosFiles/* /tmp/cdr
cp: cannot stat `/home/dan/NewBiosFiles/*': No such file or directory

So two very noobish questions:

First, when code is up on a forum for me to just copy and paste, is it right to select the entire box and paste it all into the Terminal at once?  Or do I need to copy and paste line-by-line? (Which in this case seemed more effective as it told me where the problem occurred)

Second, what am I doing wrong?  How can I get my laptop to acknowledge and boot from the CD - as simply burning the .exe file to it isn't enough.


Apologies for all the questions!
> [B][SIZE=2][COLOR=Black]M2: CD[/COLOR][/SIZE]
[/B][SIZE=1]*Unpack FreeDOS image &#8594; create temp dir &#8594; mount   FreeDOS image to /tmp/cdr &#8594; copy flashing tool*[/SIZE][SIZE=1]*   and new BIOS image to /tmp/cdr *[/SIZE][SIZE=1]*(see   footnotes below) &#8594; unmount image &#8594; install mkisofs &#8594; create ISO &#8594; burn   ISO to disc *[/SIZE][SIZE=1][I]&#8594; reboot following vendor   instructions

[/I][/SIZE]_**[SIZE=1]*Note: "NewBiosFiles" listed below is   pseudocode for the extracted location of the new BIOS image + related   files that you just downloaded*[/SIZE]     Code:**_
     wget [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz)
gunzip FDOEM.144.gz
mkdir /tmp/cdr
sudo mount -t vfat -o loop FDOEM.144 /tmp/cdr
sudo cp ~/NewBiosFiles/* /tmp/cdr
sudo umount /tmp/cdr
sudo apt-get install mkisofs
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144
cdrecord -v newBIOS.iso 
[note: in later releases, /usr/bin/mkisofs symlinks to   /usr/bin/genisoimage]
[note: in later releases, /usr/bin/cdrecord symlinks to /usr/bin/wodim]                      

use the app firmware-addon-dell to install the bios instead.

---

### Post by danielgrosvenor on 2010-06-03
> **carlee said:**
> use the app firmware-addon-dell to install the bios instead.

How do I do that?  sudo apt-get firmware-addon-dell, or something along those lines?

---

### Post by colin.p on 2010-06-03
Open synaptic and paste in "firmware-addon-dell" and there it is. However, since I don't have a Dell, I have no idea what to do with it.

Colin

---

### Post by danielgrosvenor on 2010-06-04
Did so, and am being plagued with this error when trying to install:

[B]E: lib32nss-mdns: subprocess installed post-installation script returned error exit status 2
E: wine1.2: dependency problems - leaving unconfigured
[/B]
This is not the first time I've seen this error.  It also appeared [during my attempts to fix the screen brightness controls]("http://ubuntuforums.org/showthread.php?t=1500505"). 

Any idea how to stop this error? :S

---

### Post by Ivkosky on 2010-06-23
Hi all


I have the same problem. I would like to update BIOS on my DELL XPS M1330 from A14 to A15, but I simply don't know how to do that properly :)

Firsly I tried to do it by following this guide:

[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)

I ended with statement:
> IOError: [Errno 2] No such file or directory: './bios.hdr-2.3.2'

After entering the final command:
> dellBiosUpdate -u -f ./bios.hdr-2.3.2 

Please note that I am a beginner and it might happen that I made a silly mistake somewhere... :)

I found also another way of flashing my BIOS:

[http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk)

But I didn't try it (too confusing for me).

The third way I found:

[http://linux.dell.com/wiki/index.php/Oss/Firmware_Tools/announce](http://linux.dell.com/wiki/index.php/Oss/Firmware_Tools/announce)

It seems to be the best way, I have also found Firmware-addon-dell in Synaptic, but I don't know what to do once I have it installed... :( I don't want to damage the system, therefore I am really cautious and asking you for help.

Thank you!

---

### Post by spcwingo on 2010-06-23
If I had to do this I would just grab a 1GB or greater flash drive and make two partitions.  One only slightly bigger than your BIOS update program...the other could have the rest.  Then fire up unetbootin to install FreeDOS to the larger of the two partitions.  Finally just copy over the BIOS update program to the smaller partition.  Boot it and try different drive letter designations until you find the one holding the BIOS update and run it...just my $0.02.

---

### Post by Ivkosky on 2010-06-24
Wow, too complicated for me... :)

And what if I install and run Vista on the virtual machine and flash BIOS from Vista? :) Could it make any problem to do it like that?

Thanks for your help!

---

### Post by migs73 on 2010-06-24
I thought of that for mine, but I don't think you can flash the BIOS from a virtual machine as it ... well it's virtual and has its own virtual BIOS.

---

### Post by Ivkosky on 2010-06-24
All right, thanks. So the only chance to solve the issue if I don't want to mess around with codes and spoil the system is, that I would have to install clean Vista, flash bios (which takes 5 min. in Window$ by running exe file) and then install Ubuntu once again...

Painful process so or so... :( But I don't have any other possibility. It has to be done today latest, because tomorrow I have to report to Dell technical support if I had any problems with flashing my BIOS...

Any help regarding those three possibilities I wrote in my first post in this thread??? :(

Thanks!

---

### Post by CharlesA on 2010-06-24
It would probably be easier to just install Vista and run the exe then reinstall Ubuntu.

It looks like that "biosdisk" isn't that complicated, but idk.

This one seems to be the easiest:
 * The mkfloppy action will create the biosdisk image and write it directly to a floppy disk. Usage is the following:
 
     biosdisk mkfloppy [-o option] [-d device] [-k baseimage] /path/to/.exe 

But who has a floppy drive in their computer anymore?

---

### Post by Ivkosky on 2010-06-24
Thanks CharlesA


That's the problem... I have laptop, i.e. no floppy at all... :)

---

### Post by spcwingo on 2010-06-24
> **Ivkosky said:**
> What if I install and run Vista on the virtual machine and flash BIOS from Vista?

By emulating you won't have access to the physical hardware on your system.  So trying to do it that way won't work.

---

