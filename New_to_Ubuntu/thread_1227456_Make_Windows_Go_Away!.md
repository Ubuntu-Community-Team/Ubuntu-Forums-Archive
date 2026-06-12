---
title: "Make Windows Go Away!"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by bert666 on 2009-07-30
I installed Ubuntu side by side with windows, but now want to delete Windows. I need to know, in relatively plain english (i'm computer retarded) how to accomplish my goal. windows is taking up so much space i can't do anything in ubuntu.

---

### Post by Humanum on 2009-07-30
Something you could do is to reinstall and format the Disk while creating the partition. In that case, you can be sure that Windows will dissapear without any further notice...

Or you can also use Gparted and delete the partition on which you have windows and allocate it to something else but not sure if this will solve you space problem...
Though I think my first suggestion is better


Just hope that you won't need it anymore ... cause once it's gone, it's gone... worst than a broken window:D

---

### Post by daimaru on 2009-07-30
just deleting the windows partition and using the space as a new storage partition for ubuntu would be no problem. But i have never tried merging free space with a existing linux partition, like you do with partition magic on windows. Dont know if that works in linux or not. 

If you just need a new partition to put files in that can be mounted in linux ( meaning you dont need more space for your root system or home folder ) then you can just delete the partition using gparted make it into an ext3 or whatever, mount it somewhere like /media/extrastorage/ and copy your files there. :=)

---

### Post by starcannon on 2009-07-30
You could absorb the windows partition, you'd likely have to reinstall grub as a result. 

If you want to run Ubuntu exclusively on this machine, I'd recommend as a previous poster did, a fresh clean install. Backup you /home directory somewhere safe; then just reinstall Ubuntu.

I'd also take a little time to learn how to set up the partitions manually in the installer, a separate /home is a wonderful thing.

My partition scheme is something like this:


[LIST]
[*]/
[LIST]
[*]aka "root" 20gb is usually plenty, if you want to try a lot of software maybe go as high as 30gb, don't go with less than 4gb though.
[/LIST]
[*]/swap
[LIST]
[*]This partition should be set => amount of installed ram, or the amount of ram you intend to have in the computer in some foreseeable future. Especially important for laptops with hibernation modes.
[/LIST]
[*]/home
[LIST]
[*]This is where your personal stuff lives, viz. music, pictures, office documents..., give it whats left of the hdd after root and swap have been created.
[/LIST]
[/LIST]
Thats how I like to do it; and it gives me a really nice advantage when it comes time to do an LTS upgrade; I get to do fresh clean upgrade installs without losing my /home partition, this has saved me many of the "upgrade install" headaches. If you ever need/want to reinstall Linux with this setup, its as easy as popping in the disk, resetting labels on the partitions, and then formatting root and only root, don't format /home and when you get back in, it will look and feel like it always did, and all your stuff will be there (warning, backups are still important, there are no gaurantees when futzing with your partitions).

GL and HF

---

### Post by credobyte on 2009-07-30
Use gparted: [http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/](http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/) ( delete & merge ) :)

---

### Post by bert666 on 2009-07-30
> **Humanum said:**
> Something you could do is to reinstall and format the Disk while creating the partition. In that case, you can be sure that Windows will dissapear without any further notice...


Just hope that you won't need it anymore ... cause once it's gone, it's gone... worst than a broken window:D

i already backed up all files i needed and i am through with windows.

i tried to reistall the disk but upon reboot it doesn't read the disk it just goes directly to the choice between windows and ubuntu. this is the option that sounds simplest to me, like i said. i am a computer retard. a guy at my work tried to explain it to me and said i looked as blank as a whiteboard after he was done talking.

---

### Post by sigurnjak on 2009-07-30
Check your bios settings and make your cd/dvd drive first boot device then hard drive ! Then try again!

---

### Post by starcannon on 2009-07-30
On many computers the Esc(ape) key will bring up a boot order menu(start rattling it right after you turn the computer on), if not you'll need to open bios setup and change your boot order there; you'll want to set CDROM as first boot device. Usually one of the F keys when you first turn the machine on will get you into bios setup, when you first turn your computer on, the first screen generally tells you the bios setup hotkey, and the boot device order hotkey; if you can tell us exactly what computer you have we can probably help get you into device boot order menu, or bios setup.

GL

---

### Post by sydbat on 2009-07-30
> **sigurnjak said:**
> Check your bios settings and make your cd/dvd drive first boot device then hard drive ! Then try again!To do this, when you boot/reboot, there should be an option at the bottom of the screen that says something like "to enter setup menu press DEL" (might also be F2, F12, depends on your computer). This will get you into the BIOS and you can go change basic system settings like choosing CD as first boot and then "save and exit". 

I suggest not changing anything else as it can really screw up your computer and make it useless if you do not know what you are doing.

Damn...starcannon beat me to it...

---

