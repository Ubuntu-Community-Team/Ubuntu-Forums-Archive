---
title: "Changing name of USB Volume"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-02-01
Hi folks,

So I just learned how to partition my external drive I wanted to use as a back up.
It's an old Maxstore 250 GB HD from a tower a friend gave me. I slapped it into 
a funky enclosure and got me a backup...

So now I have a 50 GB ntfs part and a ext3 part.

WHen I did hte partitioning at school, that machine runs Hardy, the name of the volume
was 'disk'.

/media/disk

I could live with that, but with Karmic, the name is four sets of bin hex or somthing separated by - 's ....pretty lame name...

would someone please direct me on how to change this to a suitable name.

thank you,
wbg

---

### Post by ajgreeny on 2010-02-01
Use gparted on the karmic live CD and set the partition labels by right clicking on partitions and choosing "Label".  Make sure the partitions are unmounted or you will not be able to do this.

You could also use tune2fs on the ext3 part with the command ```
sudo tune2fs -L labelname /dev/sdx#
```You can do this from your running install of ubuntu, you don't need the live CD, but if you want a GUI then it's gparted that's easiest.

---

### Post by Sir Jasper on 2010-02-01
Hi,

Plug in your External Drive and then, if they are mounted, unmount both partitions.

Load Partition Manager (it should be installed).

Near the top right-hand corner there is an arrow with a Drop Down List.
Select your External Drive.

Name the first partition (or both if you wish) and then click the green Apply button.

My regards

I see, our friend, ajgreeny was quicker and also gave another option.

---

### Post by philinux on 2010-02-01
I use System>admin>Disk Utility.

---

### Post by garvinrick4 on 2010-02-01
Use gparted in System/Admin to gparted. Go to gparted drop down menu pick devices, choose
the device you want to work on. Right click on partition you want to label. Choose label, type
the label you want in box click ok and you are done. Now it is media/(label name) if you choose 
karmic for name. It would be "sudo mount /dev/sda5 /media/karmic" to mount on live cd. Without quotes.
sda5  change to what ever partition it is in gparted or "sudo fdisk -l "  that is small L without quotes.

---

### Post by garvinrick4 on 2010-02-01
> **philinux said:**
> I use System>admin>Disk Utility.
I have opened disk utility a thousand times and never seen the Label function.
Have always used gparted but disk utility is nice to know.

---

### Post by Gatemaze on 2010-02-01
> **garvinrick4 said:**
> I have opened disk utility a thousand times and never seen the Label function.
Have always used gparted but disk utility is nice to know.

I think it might be a recent addon as neither I have seen it in the past.

---

### Post by wannabegeek on 2010-02-02
Hi all and thanks for the replies,

I made the partition with fdisk from term. so I like the idea of using that.
gparted has been easy in the past, however I'd rather go with command line stuff since I'm trying to be a geek...

'label' is the correct term is seems, for the name of the parition...that helps a lot.

I'll try changing and post back how it went.
thanks again,
wbg

---

### Post by wannabegeek on 2010-02-02
got it...

```
sudo tune2fs -L 'name' /dev/sdb2 
```

that worked nicely....so fdisk doesn't have a label change function ?
The only think I saw in the menu was bsd disk label, which said there were
no bsd partitions.

I have another question about mounting...
How do I mount a the volume I just edited through the terminal?
I know it goes onto ```
/media/'name' 
```

peace,
wbg

---

### Post by ajgreeny on 2010-02-02
Glad you did it.  Tune2fs is a powerful utility for ext filesystems that I use a lot, but will not help with vfat or ntfs partitions.  I will bet there is a command line way to do those as well, but I have always used gparted for those so can't help, I'm afraid.

---

### Post by philinux on 2010-02-02
> **garvinrick4 said:**
> I have opened disk utility a thousand times and never seen the Label function.
Have always used gparted but disk utility is nice to know.

Started in Karmic I think. Also the disk smart data available in there is really useful.

---

