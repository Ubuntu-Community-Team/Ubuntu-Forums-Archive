---
title: "Restoring windows 7 mbr from ubuntu"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by neo|oen on 2009-02-02
Hi,

Till recently,my computer dual booted Vista and Windows 7.After trying Windows 7 for a while,I decided to remove Vista and install Ubuntu.So I (very naively as I later found out)formatted the primary partition which had Vista and installed Kubuntu 8.10.Then I switched to Ubuntu installing GNOME.Then I realised that I could not boot into Windows 7.Its not showing up in the boot menu.After googling for a while,I found out that I might have removed the MBR on the primary partition.Is there anyway I can recover MBR and use Windows again without re-installing it?

Things I have already tried(if it is of any help)

1.Recovering from windows CD.I tried both Vista and Windows 7 DVD.Vista directly started installing it.My laptop is not recognising Windows & DVD(and a few others)

2.I've tried ms-sys.But it says:
 "/dev/sda5 has an x86 boot sector,
  it is an unknown boot record"
  I guess windows 7 is too new for it 

I would be very grateful for any help.Thanks

---

### Post by marshall.robert on 2009-02-02
I have recoverd a bootloader before using VMWare (on the same computer). If you have an ISO then that could work for you.

---

### Post by Gulyan on 2009-02-02
> **neo|oen said:**
> 
/dev/sda5 has an x86 boot sector,


I would try (but with no promises that it will work) to add the following code to the /boot/grub/menu.lst file
First of all backup the file.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

```

Then add this at the end of the file (/boot/grub/menu.lst):
```

title		Windows 7 (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1


```

---

### Post by neo|oen on 2009-02-02
> 
Originally Posted by Gulyan 
--------------------------------------------------------------------------------

Quote:
Originally Posted by neo|oen  
/dev/sda5 has an x86 boot sector, 

I would try (but with no promises that it will work) to add the following code to the /boot/grub/menu.lst file
First of all backup the file.

Code:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bakThen add this at the end of the file (/boot/grub/menu.lst):

Code:
title		Windows 7 (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1 

I have tried that.It didn't work.
It said something like unknown device requested.

Anyways,I reinstalled Vista again(I know I should have waited :redface:)

Thanks for the advice.

@marshall.robert:Thanks.I Should have waited.

---

### Post by neo|oen on 2009-02-03
My hastiness be cursed(:P)

I reinstal on led Vista.As expected grub was lost.Using a live cd.I could restore Grub.But now Vista does not boot.Back to the same problem.

@marshall.robert:Can you elucidate using VMWare please?

Thank you

---

### Post by banjo man on 2009-02-20
I have almost the exact same problem:

I was away from ubuntu for while on main laptop, had WinXP and Win7 installed dual booting with windows' booter-majjig

then, dropped xp and installed ubuntu..

so, I have kgrub editor installed (excellent program)

set it up the way I wanted, changed windows entry to Win7, and pointed in the right direction, but when I boot I get the "NTLDR is missing" etc...

(I suspect when I installed win7, it detected xp and decided to use certain files there instead of installing it's own)

so, I just got an idea from an earlier post in this thread, so I'll install Win7 in a virtual machine (Qemu, or vmware) and copy some files from virtual machine root (the boot files) to my Win7 partition...


I'll check back later and post if it worked...

---

### Post by rootbeerking on 2009-03-06
> **banjo man said:**
> I have almost the exact same problem:

I was away from ubuntu for while on main laptop, had WinXP and Win7 installed dual booting with windows' booter-majjig

then, dropped xp and installed ubuntu..

so, I have kgrub editor installed (excellent program)

set it up the way I wanted, changed windows entry to Win7, and pointed in the right direction, but when I boot I get the "NTLDR is missing" etc...

(I suspect when I installed win7, it detected xp and decided to use certain files there instead of installing it's own)

so, I just got an idea from an earlier post in this thread, so I'll install Win7 in a virtual machine (Qemu, or vmware) and copy some files from virtual machine root (the boot files) to my Win7 partition...


I'll check back later and post if it worked...

How'd this go? I'm having the same problem. 

I had an old hard drive, that I had xp installed on, and windows 7 was installed on my secondary drive. I recently bought a new hard drive, and replaced my windows xp drive with this new one, which I now have ubuntu and xp installed to. Problem is I can't get windows 7 to boot. This is what I'm using in the grub:

title		Microsoft Windows 7
root		(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

But when I select that, I get the "NTLDR is missing" error. If I replace my new hard drive, with my old one, I get the old boot menu, and I can easily boot into either my old shitty copy of XP that's on that old hard drive, or Windows 7 that is installed on my secondary drive. I'd like to be able to boot into Windows 7, without having to reinstall it on my new drive. But I'm having trouble finding a solution to this problem. Hopefully someone might have the answer here?

---

### Post by ToFue on 2009-03-25
I'm curious to know where the source of bootloader corruption is- This similar scenario happened to me three days ago (on sdb0 c:\[win7 bootloader stuff], sdb1 d:\[xp install], sdb2 e:\[win7]; and ubuntu on seperate hd as sda1 [swap], sda2 /home, sda3 / (sda0 is extended)) when I booted to ubuntu, then back to xp after, I recieved the missing \ntldr error..

 In my case when I ran fixmbr, it wrote over my /home partition and I Just got Ubuntu sorted out ( [http://ubuntuforums.org/showthread.php?t=1105124](http://ubuntuforums.org/showthread.php?t=1105124) ) after using ( [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ) to restore grub, and am currently searching to repair win mbr (this time my ubuntu hd will be unplugged) ;)

I wonder if this is a convenient update in win7 (which is understood in EULA to be buggy and not liable for it's bugginess) seems how I see the posts happen around the same relative time.. or perhaps I'm just paranoid.. :lolflag:

---

### Post by ToFue on 2009-03-28
Here's a link for an in-depth guide to repair /NTLDR that may help you, and has a link inside to download replacement /ntldr files, also (it wouldn't hurt to install easyBCD on win7 to manage the bootloader):


[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP)


thought: I had some troubles seeing the boot partition from win7, and permission issues when attempting to copy the /ntldr files from where they were stored from either win7 & ubuntu.. I wonder if it's x64 vs. x86, just permission conflicts, or both..? Oh well.. that'll be for a different post..

I suggest against tri-booting on the same disk (only from my own recent mishap, though a friend of mine told me that he had success installing xp, win7, & linux on the same disk, by following that order of installation, and linking to grub in win7 bootloader.. ).. if you keep linux on a separate disk, make sure to unplug it during install to eliminate /dev/sd? confusions & to keep fixMBR from overwriting the linux disk's mbr, I suppose..

If you're putting win7 & winxp on the same disk, perhaps set your partitions ahead of time in the xp installation, leaving the beginning of the disk RAW, and set the xp partition at the end.. the RAW space should be about what you want the size of win7 to be, plus a few hundred megs for the bootloader (keeping in mind that if you partition win7 for NTFS ahead of time, to leave space for the bootloader..). win7 should 'see' the xp install, and add the entry after/during win7's installation, or if not, there's easyBCD..
from there you can make an entry, referencing grub's startup path..  

Does this helps you?

---

### Post by aerbag on 2010-07-28
looks like none of this might work... because I'm running ubuntu from a pen drive ms-sys doesn't recognize any of my primary hd partitions...

---

### Post by g123386761 on 2013-03-07
If you can manage to get Windows running from the GRUB bootloader, install EasyBCD and go to advanced > change boot drive > [newDriveHere]

---

### Post by oldfred on 2013-03-07
Old thread closed.

---

