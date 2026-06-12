---
title: "Bad sectors"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Phan76 on 2010-04-19
Hi all,

Some time ago my wife got a Toshiba laptop, soon after she got it the system started complaing about issues with the boot sector and wouldn't start at all.. Time pased and a number of failed restores later she got a new lap top and so I took over this one.. I installed Ubuntu 9.10 and it works fine however I was told by the system a couple of times that the disk maybe failing due to bad sectors, now as I'm fairly new to Ubuntu and I have stopped getting that message about the bad sectors is it possible that Ubuntu was able to fix whatever the issue was where WIndows Vista wasn't? Is there a tool I can use from Ubuntu that would allow me to see if this problem is still outstanding ? Just looking into my options

Thanks

---

### Post by e4uforums on 2010-04-19
I don't believe Ubuntu would have fixed your disks, perhaps it's just more tolerant to the bad sectors or works around them better than Windows did.  I've used SpinRite on my disks for a while now and they all perform incredibly well (even some that are very old).

Check it out:

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

---

### Post by Penguin Guy on 2010-04-19
If you're using 9.10 or above you can use the [palimpsest]("apt:gnome-disk-utility")'s SMART Data viewer. Open [COLOR="green"]System -> Administration -> Disk Utility[/COLOR], select the hard drive you want, then click the [COLOR="Green"]More Information[/COLOR] link.

---

### Post by philinux on 2010-04-19
> **Penguin Guy said:**
> If you're using 9.10 or above you can use the [palimpsest]("apt:gnome-disk-utility")'s SMART Data viewer. Open [COLOR="green"]System -> Administration -> Disk Utility[/COLOR], select the hard drive you want, then click the [COLOR="Green"]More Information[/COLOR] link.

On 9.10 smart is currently disabled in Disk Utility due to the bad sector bug, i.e. reporting false bad sectors. Should be fixed soon I hope.

Meanwhile there's gsmartcontrol available from synaptic.

---

### Post by Phan76 on 2010-04-19
Thank you for the replies folks, I guess I have to just keep hoping it holds together.. Penguin Guy that's the method I use but I don't have a "More info" Link.. I used to but now it's just not there

---

### Post by philinux on 2010-04-19
> **Phan76 said:**
> Thank you for the replies folks, I guess I have to just keep hoping it holds together.. Penguin Guy that's the method I use but I don't have a "More info" Link.. I used to but now it's just not there

See post #4

---

### Post by quadproc on 2010-04-19
> **Phan76 said:**
> Hi all,

Some time ago my wife got a Toshiba laptop, soon after she got it the system started complaing about issues with the boot sector and wouldn't start at all.. Time pased and a number of failed restores later she got a new lap top and so I took over this one.. I installed Ubuntu 9.10 and it works fine however I was told by the system a couple of times that the disk maybe failing due to bad sectors, now as I'm fairly new to Ubuntu and I have stopped getting that message about the bad sectors is it possible that Ubuntu was able to fix whatever the issue was where WIndows Vista wasn't? Is there a tool I can use from Ubuntu that would allow me to see if this problem is still outstanding ? Just looking into my options

Thanks
I don't know what kind of disk you have, but it is possible that the disk drive itself may have recognized the fact that it had bad spots and remapped itself to avoid the problem area.  Some modern day disk drives have a lot of intelligence built in.  These drives are also SMART capable so you might ask the disk for a report using the smartctl program.  Unfortunately, you'll have to use 9.04 to get this since 9.10 has disabled the function.

quadproc

---

### Post by RedRat on 2010-04-19
I would say that since the computer complained with Windows about bad sectors, this should be considered a warning that you have a failing disk. Face it, disks do fail. I would say that prudence dictates looking into replacing that drive in your laptop, particularly if you have valuable data on the drive. It could have fixed itself, but then maybe it did not, who knows. I'd replace the drive.

---

