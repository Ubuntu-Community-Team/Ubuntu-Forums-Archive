---
title: "Can't see windows partition in gparted"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by susan.kamal on 2009-06-01
Hi,

I just installed ubuntu from a usb flash disk (because I have no functioning cd-rom) on my laptop which used to run on windows xp and I can't locate my windows partition. It's not there when I open gparted. Is it possible that I formated all my windows drives in the installation process? When I boot there is no selection menu it's just ubuntu.

Is there anyway I can recover my windows drives?

---

### Post by Hospadar on 2009-06-01
It sounds like you accidentally wiped your windows partition.  If so, there is unfortunately no way to recover it (short of paying a data forensics specialist vast sums of money).

To be sure, if you could open up the terminal (Applications->Accesories->Terminal) and post the output of the command ```
sudo fdisk -l
``` that would help us be sure of your predicament.

---

### Post by louieb on 2009-06-01
Its certainly possible that widows got replace. If you chose use entire disk and that disk had your window install then windows is gone.

It may be possible to recover some of your files. 1st don't do anything that would cause writes to that drive. 2nd. Get a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") - there is a version that will install to a USB stick. Two programs that might be of use to you are testdisk and photorec.

---

### Post by susan.kamal on 2009-06-01
When I open the terminal it prompts for my password then for some reason the keyboard freezes and I can't type  anything.

sue@sue-laptop:~$ sudo fdisk -l
[sudo] password for sue: 

There^^

---

### Post by LewRockwell on 2009-06-01
> **susan.kamal said:**
> When I open the terminal it prompts for my password then for some reason the keyboard freezes and I can't type  anything.

sue@sue-laptop:~$ sudo fdisk -l
[sudo] password for sue: 

There^^

  keyboard isn't freezing, it doesn't show the password you're entering

---

### Post by susan.kamal on 2009-06-01
Right. So This is what I got:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb33eb33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7114    57143173+  83  Linux
/dev/sda2            7115        7296     1461915    5  Extended
/dev/sda5            7115        7296     1461883+  82  Linux swap / Solaris

No windows, eh?

---

### Post by LewRockwell on 2009-06-01
up in smoke

---

### Post by wpshooter on 2009-06-01
> **LewRockwell said:**
> up in smoke

May be the best accident that ever happened !!!

---

### Post by LewRockwell on 2009-06-01
> **wpshooter said:**
> May be the best accident that ever happened !!!

a toast to the almighty "smoke"...

---

### Post by LewRockwell on 2009-06-01
although if there is no back-up it might be kinda gut-wrenching at first

---

### Post by logos34 on 2009-06-01
come on guys, that's not even funny joking about it--maybe she had important documents on it!  

Do like louieb suggested--use testdisk.  It should be able to recover the windows partition.  You can just use the ubuntu live usb.  >System>admin>software sources>enable **universe** repository

sudo apt-get install testdisk

sudo testdisk

Read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS") and [this]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by wpshooter on 2009-06-01
> **logos34 said:**
> come on guys, that's not even funny joking about it--maybe she had important documents on it!  

Do like louieb suggested--use testdisk.  It should be able to recover the windows partition.  You can just use the ubuntu live usb.  >System>admin>software sources>enable **universe** repository

sudo apt-get install testdisk

sudo testdisk

Read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS") and [this]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

Yes, you are correct.  But hopefully, if there was anything critical on this machine, there was a backup of it.  I would NEVER, attempt to install another O/S on a machine that had critical information on it without that info being backed up FIRST.

---

### Post by LewRockwell on 2009-06-01
> **logos34 said:**
> come on guys, that's not even funny joking about it--maybe she had important documents on it!  

Do like louieb suggested--use testdisk.  It should be able to recover the windows partition.  You can just use the ubuntu live usb.  >System>admin>software sources>enable **universe** repository

sudo apt-get install testdisk

sudo testdisk

Read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS") and [this]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

look, the harsh reality is that almost everywhere you go, everyone TELLS you to back up your valuable data.

Some people do, and some people don't.

Laugh or cry, either way there is a very distinct possibility that it is not recoverable(and if it wasn't something that they would spend three to five hundred dollars ATTEMPTING to recover, then I wouldn't bother...spend the money on a good external back-up drive)

most of my associates that have had lost data issues are now my best back-up advocates, go figure...

---

### Post by susan.kamal on 2009-06-01
I ran Photorec and I think My partition might still be there:

Disk /dev/sda - 60 GB / 55 GiB (RO) - ATA HTS421260H9AT00
     Partition                  Start        End    Size in sectors
   D No partition             0   0  1  7295 254 63  117210240 [Whole disk]

In windows I had two partitions, C which  was backed up and D (which I am guessing is the same D as above, eh?) which wasn't backed up.

I didn't/couldn't get the same thing with testdisk but if this works out then there is hope.

What do you think?

Estimated time is 4 hours. Fingers crossed.

---

### Post by Mark Phelps on 2009-06-01
> **susan.kamal said:**
> Is there anyway I can recover my windows drives?

Using testdisk is an excellent way to recover your data, but you need to realize that every time you use the existing PC, your chances of data recovery get worse and worse -- because it's actively overwriting the space previously used by your MS Windows files.

Your best bet would be to remove the drive and attach it as an external drive to another machine -- and do the file recovery from there.  You will need to have a separate physical drive for rile recovery anyway since you can't recover files to the same drive.

---

### Post by logos34 on 2009-06-01
> **susan.kamal said:**
> I ran Photorec and I think My partition might still be there:

Disk /dev/sda - 60 GB / 55 GiB (RO) - ATA HTS421260H9AT00
     Partition                  Start        End    Size in sectors
   D No partition             0   0  1  7295 254 63  117210240 [Whole disk]

In windows I had two partitions, C which  was backed up and D (which I am guessing is the same D as above, eh?) which wasn't backed up.

I didn't/couldn't get the same thing with testdisk but if this works out then there is hope.

What do you think?

Estimated time is 4 hours. Fingers crossed.

Photorec is for files and folder--you want to recover the whole partition(s).

Use testdisk again--"deeper search" (read the docs)

---

### Post by Nar'keth on 2009-06-01
i had a similar issue in my attempt to dual boot ubuntu/winXP, i had to use the windows disk recovery console to repair the ntdlr.sys and boot.ini files for they no longer had the correct info for windows to load.
once i had done that i had to modify the grub bootloader to point to the new location for the win partition and make it available on the grub boot list. once i had done this, it was no prob to hit 'esc' at boot and choose to boot win instead of ubuntu, i hope this helps =-)

i used testdisk to acquire the correct info for grub because gparted wasn't accurate

i had to use the commands fixmbr and fixboot in the win recovery console:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

---

### Post by LewRockwell on 2009-06-01
> **Nar'keth said:**
> i had a similar issue in my attempt to dual boot ubuntu/winXP, i had to use the windows disk recovery console to repair the ntdlr.sys and boot.ini files for they no longer had the correct info for windows to load.
once i had done that i had to modify the grub bootloader to point to the new location for the win partition and make it available on the grub boot list. once i had done this, it was no prob to hit 'esc' at boot and choose to boot win instead of ubuntu, i hope this helps =-)

this isn't that, perhaps you've posted to the wrong thread?

---

### Post by Nar'keth on 2009-06-01
what i think happened in my case was that when i installed win after ubuntu, win had changed the type of partition that it was on from logical to physical, so the grub info was incorrect, and when it was corrected in grub, i then needed to repair the win bootloaders info to match the new correct partition types and locations.

---

### Post by susan.kamal on 2009-06-01
testdisk doesn't seem to detect anything but the new linux partitions while( luckily) photorec can. I might be doing something wrong with testdisk I don't know but I'm gonna go back to photorec anyway even if the results so far are no way near the results I want to fetch.

Thanks everyone. Will post the results in -estimated time of- 6 hours. Hope it works.

---

### Post by Nar'keth on 2009-06-01
if testdisk doesn't see a ntfs partition or w/e your win format was, then its not there anymore =-(

---

### Post by susan.kamal on 2009-06-01
photorec can see it!

---

### Post by susan.kamal on 2009-06-02
So this looks like it was successful, but the results need to be sorted out. 

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

the [B]Post-recovery cleanup part mentioned in the link above is what i need to do but when I followed the instructions it didn't work out. so can anyone please guide me through this?
[/B]

---

### Post by LewRockwell on 2009-06-02
this step-by-step might help you more than what you've used so far.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by LewRockwell on 2009-06-02
I did want to point out that a drive that you are "rescuing" / "recovering" / "repairing" should NOT be accessible to the OS when it is booting/acquiring resources(especially when the overwrite contains one or more swap partitions).

The safest way would be to remove the hard drive from the machine and connect to it via an external drive cable/enclosure AFTER your system/recovery-software is UP AND RUNNING.

Even then, some OSes might STILL attempt to mount and utilize swap on the external drive(s) as you connect it and the OS tries to handshake with it.

Hopefully this makes sense.

---

### Post by susan.kamal on 2009-06-02
I already dig up the lost partition with photorec i just now need to access the output. they're 3000 recup_dir folders and i don't know how to start sorting out my files. Help?

---

### Post by susan.kamal on 2009-06-02
one more question after i take the filkes that i want from the recup_dir can i delete the rest? how? (delete/move to trash are not working out)

---

### Post by LewRockwell on 2009-06-02
for some reason I thought our objective was to recover your windows partition with testdisk?

I guess I was misled when someone else mentioned that photorec was only for folders and files.

either way the recovery effort requires "restoring" valid parameters/names to the lost items, which is part of the recovery software's process and procedure.

with what you are relating I'm under the impression that this part of the process has not been completed.

---

### Post by susan.kamal on 2009-06-02
obviously not. 

[http://ubuntuforums.org/showthread.php?t=442749](http://ubuntuforums.org/showthread.php?t=442749)

i tried this too but it ain't working out either.

---

### Post by LewRockwell on 2009-06-02
in most of the activities/processes there is a confirmation process(in windoze it's most often a pop-up window with something like yes/no/confirm...stuff like that).

in *nix distros you may find that to effectively complete your process you are asked to "write" or "save" your changes/updates/modifications/etc.

perhaps as you review the attempts you have previously made, you might have that "ah-ha" moment where it all makes sense.

and, as always, we're here for you and in this thing together!

---

