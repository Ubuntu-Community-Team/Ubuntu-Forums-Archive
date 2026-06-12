---
title: "SIlly Size question/problem"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by GenericGirlName on 2011-02-04
I wish I wasn't new to linux. I've been trying to have it since forever, but driver issues on every computer I've ever had has rendered this impossible until now. D: So I'm a noob at Linux.

I make a 96GB~ partition a few days ago and finally got around to putting linux on it, I wasn't paying attention really and I let it install as 17GB installation. I kind of assumed that was the size of the "necessary files" though in retrospect that seems kind of dumb, so obviously it was resritcing the size of the linux partition, but within my huge partition? Welp, my music doesn't fit on this partition. I guess I could just not move it to this partition, but I'd like to have it as some kind of back up, so is there a way to expand the size of the linux installation?

tl;dr: Can I make my installation size match my partition size?

:rolleyes: And I call myself a CS major!

---

### Post by shof2k on 2011-02-04
If you want to resize your 17GB parition to use all of the 96GB you can install gparted and resize the partition.

You are best doing this from a live cd as it is quite risky.

---

### Post by GenericGirlName on 2011-02-04
I dont have any blank discs, and I'm not too excited about the idea of going to the campus bookstore and over paying for one ~.~. Would there be a way to do this from my windows partition? Kind of like how I installed linux from my windows partition?

EDIT2: Oh wait, I think I found the answer to my own question on the gparted download page. I'll come back after I've tried and ruined my partitions.

---

### Post by coffeecat on 2011-02-04
> **GenericGirlName said:**
> Kind of like how I installed linux from my windows partition?

Ah! Did you do a wubi install? From what you've described it sounds as though you prepared a separate 96GB partition for a conventional dual-boot and then did a wubi install which will be within your Windows C: partition - hence the small size.

Boot into Windows and open (My) Computer and have a look at the C: drive. If you have a C:\ubuntu folder you have a wubi install.

---

### Post by GenericGirlName on 2011-02-04
> **coffeecat said:**
> Ah! Did you do a wubi install? From what you've described it sounds as though you prepared a separate 96GB partition for a conventional dual-boot and then did a wubi install which will be within your Windows C: partition - hence the small size.

Boot into Windows and open (My) Computer and have a look at the C: drive. If you have a C:\ubuntu folder you have a wubi install.

Nope, though I did do that the first time with linux mint, but then everything fudged and I uninstalled it and tried it with ubuntu. This time though I took the live boot iso and extracted it and ran the setup and installed it on the 96GB partition. :/ I have no more physical disks left because I didn't double check the checksum on the mint iso and it is essentially trash.

---

### Post by coffeecat on 2011-02-04
OK. So let's see what partitions you have. I'm puzzled by Ubuntu making a 17GB partition out of a 96GB one. Boot up Ubuntu and do one or both of the following.

Install Gparted (or you could use the live CD which has Gparted with it). Open Gparted from System > Administration, take a screenshot of the Gparted window and post it for us to see. 

And/or:

Open a terminal. Sorry! :) (It's in Applications > Administration). Post the output of:

```
sudo fdisk -lu
```Please post the output between [noparse]```
 and 
```[/noparse] tags otherwise it's very difficult to read. You can use the # icon in the message toolbar for this.

---

### Post by GenericGirlName on 2011-02-04
Actually, now that I'm on the windows partition I see that I did use Wubi. But I used it on the empty partition, which explains why it did what it did. But why doesn't it use the whole partition if its empty? The folder is exactly 17.3 GB, and I guess its restricted from being any bigger? I'll switch back over and take those screen shots you wanted.

EDIT:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19f7787f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   774350847   387072000    7  HPFS/NTFS
/dev/sda2       774350848   976769023   101209088    7  HPFS/NTFS

```

If im not mistaken those botton two lines are telling you what/where the partitions are? If I'm correct then don't be alarmed by the missing chunk in the beginning. Botched Windows installation that stole some space I'm too lazy to get back. I have the best track record for installing OS don't I?

---

### Post by coffeecat on 2011-02-04
> **GenericGirlName said:**
> Actually, now that I'm on the windows partition I see that I did use Wubi. But I used it on the empty partition, which explains why it did what it did. But why doesn't it use the whole partition if its empty? The folder is exactly 17.3 GB, and I guess its restricted from being any bigger? I'll switch back over and take those screen shots you wanted.

I'll have to log off soon, possible before you post again, but I think I can see what's happened. The 96GB partition must be NTFS if it has the wubi ubuntu folder in it - you must have prepared it in Windows. NTFS is not suitable for Ubuntu when it is installed to its own partition as a native install - only for wubi. I'm not sure why wubi produces small  virtual discs - virtual is what they are - but probably something to do with wubi only ever being intended for people to try Ubuntu out.

If you want Ubuntu on the 96GB partition you need first to uninstall wubi from inside Windows. Then you need to boot up Ubuntu from a live CD - you don't install from inside Windows. The Ubuntu installer will reformat the 96GB space with filesystems suitable for Linux and then install Ubuntu properly.

Others should be able to take you through what you need to do. Which version of Ubuntu live CD do you have? If 10.10, be very careful of the side-by-side option. There is a design flaw which can destroy your Windows partition if you make a wrong choice.

**EDIT**: OK, I've seen your edit. Your sda2 partition is the NTFS one you made for Ubuntu - 103.6GB (base 10) or 96.5 GiB (= gibibytes, base 2). You can use that 96.5 GiB to install Ubuntu, but the Ubuntu installer will have to reformat it - in fact it will have to make at least 2 partitions in that space.

I've had another thought. Is Windows seeing the 96.5 GiB partition as E: or something? If so, it *might* be appearing in the Places menu of your wubi Ubuntu.

Whatever, I really have to log off now - late here - so hopefully someone can take you through what you need to do now.

---

### Post by GenericGirlName on 2011-02-04
Oh boy. D:

I have the 10.10 Ubuntu live DVD 64bit ISO (Its not burned to anything, but I guess that can be arranged over the weekend). I suppose for now I'll uninstall the wubi and get further instructions. I'm just loathing the idea of waiting for 96GB of my HDD to be reformatted. I think I'll shrink that partition.

Thanks for your help though! Made this a lot simpler then I thought it would be.

---

### Post by coffeecat on 2011-02-04
> **GenericGirlName said:**
> Oh boy. D:

I have the 10.10 Ubuntu live DVD 64bit ISO (Its not burned to anything, but I guess that can be arranged over the weekend). I suppose for now I'll uninstall the wubi and get further instructions. I'm just loathing the idea of waiting for 96GB of my HDD to be reformatted. I think I'll shrink that partition.

Thanks for your help though! Made this a lot simpler then I thought it would be.

Not quite logged off. :)

First - in case you've missed it, have a look at the edit in my last post.

Second - waiting for 96GB to be formatted? Haha. You're used to Windows. It will take seconds in Ubuntu. The reason: Windows defaults to the 'long' format which zeroes everything out first. In fact you can format a large partition in Windows in a short time if you choose 'quick format'. That's no good if you want to securely erase a partition, but for routine use a 'quick' format is all you need. All it has to do is to write the new filesystem leaving old data inaccessible and ready to be overwritten.

Good luck! And now I really must go offline.

---

### Post by GenericGirlName on 2011-02-04
> **coffeecat said:**
> Not quite logged off. :)

First - in case you've missed it, have a look at the edit in my last post.

Second - waiting for 96GB to be formatted? Haha. You're used to Windows. It will take seconds in Ubuntu. The reason: Windows defaults to the 'long' format which zeroes everything out first. In fact you can format a large partition in Windows in a short time if you choose 'quick format'. That's no good if you want to securely erase a partition, but for routine use a 'quick' format is all you need. All it has to do is to write the new filesystem leaving old data inaccessible and ready to be overwritten.

Good luck! And now I really must go offline.

Longest log off process I've ever seen! xD Thanks for taking the time to reply to me though.

@__@ This must be the reason why I'm dieing to use Linux, its not like windows in the ridiculousness!

I have one other question (Which will be directed to anyone reading this because you should be gone coffeecat), If I get the ubuntu Live ISO and then just extract it and run whatever setup is inside will it install windows on another partition in the same way a Windows 7 ISO would? Or will it try to install it like a Wubi and not do what I need it to do (install it like an actual OS not a wubi.)?

---

### Post by Acidpunk on 2011-02-04
> **GenericGirlName said:**
> Longest log off process I've ever seen! xD Thanks for taking the time to reply to me though.

@__@ This must be the reason why I'm dieing to use Linux, its not like windows in the ridiculousness!

I have one other question (Which will be directed to anyone reading this because you should be gone coffeecat), If I get the ubuntu Live ISO and then just extract it and run whatever setup is inside will it install windows on another partition in the same way a Windows 7 ISO would? Or will it try to install it like a Wubi and not do what I need it to do (install it like an actual OS not a wubi.)?

If you burn the ISo to a disk and boot from the disk then it should just install like a regular OS and install to the 96GB partion. 

Does that help ?

---

### Post by GenericGirlName on 2011-02-04
> **Acidpunk said:**
> If you burn the ISo to a disk and boot from the disk then it should just install like a regular OS and install to the 96GB partion. 

Does that help ?

No, because I know it would do that. But I don't have a disk, so I'll be working with a .iso. Which is what I was asking about.

---

### Post by coffeecat on 2011-02-05
> **GenericGirlName said:**
> No, because I know it would do that. But I don't have a disk, so I'll be working with a .iso. Which is what I was asking about.

Good morning!. Logged on again. :)

You don't have a disc? Writeable/rewriteable CDs and DVDs don't cost that much (you can burn a CD ISO to a DVD) and quite the easiest way is to use a disc, so it's worth getting yourself a small supply. If that's not an option, you can transfer the ISO to a USB pendrive and set the BIOS to boot from USB and run the Ubuntu installer that way. Don't copy the ISO directly to USB - it's more complicated than that. Have a look here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Scroll down to "From Windows". Either use Virtual Clone Drive to access the inside of the ISO to copy usb-creator.exe and then use usb-creator.exe with the whole ISO to make your bootable USB. Or use the Windows version of Unetbootin - link in the text.

Before you make your USB, be sure to check the md5sum hash. You do get bad downloads occasionally so this is worth doing. Howto here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

And if, by chance, you do decide to use a CD/DVD after all, useful howto here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Paqman on 2011-02-05
> **GenericGirlName said:**
> This time though I took the live boot iso and **extracted it** and ran the setup and installed it on the 96GB partition. :/

That's why you ended up with a Wubi install. To do a full install to a partition you need to put it on a CD or  USB and boot up from that.

---

