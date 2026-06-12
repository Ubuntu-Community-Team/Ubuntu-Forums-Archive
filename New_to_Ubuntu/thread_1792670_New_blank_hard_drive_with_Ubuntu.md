---
title: "New blank hard drive with Ubuntu"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Innernet on 2011-06-28
Hi.
What surprises will surface putting a new blank hard drive in a Compaq Presario CQ50 laptop and install Ubuntu **only** ?

Will some Compaq something (partition or proprietary or driver or...) be mandatory to have; for keyboard, display, wifi and the rest of its hardware recognition ?
Anyone done it ?

I remember someone doing that on an older laptop and the keyboard layout and many other things did not work.

---

### Post by mikewhatever on 2011-06-28
Hard drives are pretty irrelevant as far as hardware compatibility goes. If you want to make sure everything works, on any computer, test from the Live CD/USB.

---

### Post by ratcheer on 2011-06-28
As long as the BIOS recognizes the hard drive, you should be able to start an Ubuntu installation. When you get to the partitioning step, I think you should tell it to create a new partition table, then go on from there.

Tim

---

### Post by mcduck on 2011-06-28
What comes to blank hard drive, nothing. It makes no difference if the drive is blank or formatted in some filesystem or other, Ubuntu's installer will create appropriate partitions and format them anyway.

You don't need any drivers from Compaq either, in Linux most drivers are included in the kernel itself, and in general the drivers are related to the actual devices, not the manufacturer who placed their logo sticker on the device. Anyway, based on the specs of the machine you shouldn't have any problems. You might have to install nVidia's graphics card driver (using the tool provided with Ubuntu) but rest of the stuff should work out-of-the-box. Trying the live-CD to confirm that everything works before installing is of course always a good way to go.

---

### Post by Innernet on 2011-06-28
Thanks.
The "new partition table" you mention; how many partitions would be necessary ? 
Is one of them to be used for a Compaq proprietary something in there ? 
Such laptop as sold with Windows Vista, has a Windows partition and a Hewlett-Packard partition.

---

### Post by ratcheer on 2011-06-28
The "create new partition table" does not create the partitions, it basically just creates a new table on the disk for the metadata of the partitions you will then create. Creating a new partition table will wipe out any hidden partitions that may have been put on the disk by the PC manufacturer.

Then, if the machine is to be for Linux, only, you can get by with as few as two partitions, one for swap and one for / (called root). From there, you can complicate it to your heart's desire. Many like to have a separate /home partition. You could also create an extended partition and put many logical partitions in it, including swap, /, and /home, if you want.

There are so many ways to do it....

Tim

---

### Post by mcduck on 2011-06-28
> **Innernet said:**
> Thanks.
The "new partition table" you mention; how many partitions would be necessary ? 
Is one of them to be used for a Compaq proprietary something in there ? 
Such laptop as sold with Windows Vista, has a Windows partition and a Hewlett-Packard partition.

No, Ubuntu dosn't need such recovery partitions. In general no computer needs them, they are usually just provided as a way to reinstall Windows or it's drivers (and cheaper option for the manufacturer than giving you a CD or DVD with those drivers with the computer)

Anyway, you can just select the "Use entire disk"-option in Ubuntu's installer and it will create all the required partitions for you automatically.

---

### Post by Innernet on 2011-06-28
That was clear, mcduck; thanks !
They save $ by not supplying the OS or recovery CDs at expense of the customer hard drive space.

---

