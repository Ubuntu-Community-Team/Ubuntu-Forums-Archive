---
title: "Formatting external HDD to FAT32"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by random turnip on 2010-05-09
I need to format my 80GB external HDD to FAT32 so that my PS3 will recognize it so that i can do a backup and install a new HDD in there.

In Ubuntu it only seems to have the option to convert it to FAT, i tried that and it didn't work, any ideas?
Special program i could use?
I looked in the add/remove bit but couldn't find anything.

Keep in mind that i can barely use the terminal.

---

### Post by buntudawg on 2010-05-09
You can use gparted . Already forgotten if the disk manager option is available in 9.10 administration menu, how's that for a short memory!

---

### Post by random turnip on 2010-05-09
Tried that.
Although, when on the disk in Disk Utility it says "FAT (32-bit version)" for type.  So surely that should be the right one?
But when i click format the only option there is just FAT.

I'm now wondering weather this is actually the problem or if there's some other reason my PS3 won't recognise it.

---

### Post by buntudawg on 2010-05-09
So you are saying that the drive is actually formatted as FAT 32? If not, FAT is FAT32, so choose that as your format option.

I'm not sure when it comes to PS3 stuff (don't have one) but a quick look found alot of stuff on PS3 and HDDs. 

Don't know if this link is any help?
[http://whirlpool.net.au/wiki/?tag=ps3_hdd]("http://ubuntuforums.org//whirlpool.net.au/wiki/?tag=ps3_hdd")

---

### Post by coffeecat on 2010-05-09
@random turnip, you're right that Disk Utility says just "FAT", but I would have thought that was FAT32. Try using gParted as buntudawg suggested. It's in the repositories and you'll find it in System > Administration after installation. With gparted you can definitely specify which FAT filesystem you want, and I've used it successfully to format an external HD with FAT32 for my PS3.

**Edit:** I've just noticed you said that Disk Utility says that it is already formatted FAT32. If so, there must be some other problem because PS3's definitely read FAT32 OK. The only other thing I can suggest also involves gparted. Try re-creating the partition table (Device > Create Partition table). Ensure that it is a MS-DOS (MBR) partition table type and then you can reformat as FAT32 and see if that makes a difference.

---

### Post by b.bugra on 2010-05-09
I don't know if the same thing happens for HDDs but for memory sticks I've read from internet that 0x03 offset of boot sector (I don't know what that means) has information about "where" the disk is formatted and if the disk is not formatted in "Windows" PS3 will not use it.

Hope it helps.

---

### Post by random turnip on 2010-10-04
> **b.bugra said:**
> I don't know if the same thing happens for HDDs but for memory sticks I've read from internet that 0x03 offset of boot sector (I don't know what that means) has information about "where" the disk is formatted and if the disk is not formatted in "Windows" PS3 will not use it.

Hope it helps.

I think you may be right, because i downloaded a program called SwissKnife 3.09 (free version, download here: [http://download.cnet.com/SwissKnife/3000-2248_4-10389770.html](http://download.cnet.com/SwissKnife/3000-2248_4-10389770.html)) for Windows and it worked just fine.

Silly Sony, they've gone from letting you install Ubuntu on the PS3 to not even letting you format your HDD with it.

Thanks for everyone's help though, just thought i'd clear this up for future reference.

---

### Post by coffeecat on 2010-10-04
> **random turnip said:**
> Silly Sony, they've gone from letting you install Ubuntu on the PS3 to not even letting you format your HDD with it.

Not so. Last May I said:

> **coffeecat said:**
> With gparted you can definitely specify which  FAT filesystem you want, and I've used it successfully to format an  external HD with FAT32 for my PS3.

And the passage of 5 months has not changed this for me. I've just done an experiment. I formatted an 8GB USB flash drive with FAT using Disk Utility and found that my PS3 could not recognise it. I then reformatted it FAT32 in Gparted and the PS3 then did recognise it. I was able to read music and video files in the PS3 that I'd copied onto the drive using Ubuntu and I could copy files from the PS3 onto the drive and then read them in Ubuntu. 

> **random turnip said:**
>  just thought i'd clear this up for future reference.

And I thought I'd just clear this up. There **is** a problem when you use Disk Utility. But if you use Gparted there is **no** problem. Two people suggested you try Gparted, but you did not take heed.

I don't know what the problem with Disk Utility is. I did notice that it left a 1MB unallocated space before the FAT32 partition, whereas Gparted used the whole drive. Whether that is what the PS3 doesn't like, I don't know.

---

