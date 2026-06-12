---
title: "trying to go back to vista,cant get rid of grub"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-09-18
I got in a real mess trying to get back to a single boot with just vista.I deleted the ubuntu partition as I read on line it was best to do this first. But when I tryed to boot the windows recovery disc to fix mbr.,I couldn't get it to boot at all,grub keeps coming up with error 17.I can boot from a usb stick which has fedora installed and I am using it to go online.But I cant get at vista and I guess ubuntu is gone! What shall I do now?I am in despair with no way into my laptop.When  I choose cd drive to boot from,it just goes to the grub loader.Help!!!:(

---

### Post by yanceypd on 2009-09-18
If you have the system cd boot to it.  Select repair my computer. select Dos promp option.
at prompt type "bootrec.exe /fixMBR"
next prompt type " bootrec.exe /fixBoot"  without quotatin marks.

---

### Post by gertrude58 on 2009-09-18
I havent got a system cd only a recovery cd I made from software preinstalled on my toshiba laptop. It didnt come with a vista cd. The recovery cd wont boot.So I cant fix the mbr.some one please help,I am getting desperate.

---

### Post by kellemes on 2009-09-18
As far as I know [SuperGrubDisk]("http://www.supergrubdisk.org/") can restore the Windows-bootloader.
And I think you can use it to skip Grub at boot, and so boot straight from disk.

---

### Post by gertrude58 on 2009-09-18
Thanks but how do I download a disc when all I have is fedora installed on a usb stick?? I cant access windows todo it and ubuntu is gone.Oh how I wish I hadnt started this.Sorry but I am in despair.

---

### Post by Deadite on 2009-09-18
If you can get to another computer you can find a Vista Recovery Disc here [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You said you made a recovery cd from the software on the toshiba? Toshiba didnt supply a "Toshiba Recovery & Applications/Drivers Media" CD 2-pack with your system?

That CD really saved me on my vista--->xp pro upgrade.

---

### Post by tlarkin on 2009-09-18
You can go here

[www.bootdisk.com](www.bootdisk.com)

Grab any old DOS boot disk for free and boot from it and then just do this

```
[COLOR="Red"]fdisk /mbr[/COLOR]
```

That will wipe out the master boot record, then you can go back to just booting Vista or whatever OS you were before that.

---

### Post by kellemes on 2009-09-18
You can download/burn from your Ubuntu livedisk.

---

### Post by emoguitarist06 on 2009-09-18
Why would you want to go back to vista?

Anyways I once went back to Vista as well and I had the same problem. I found that the easiest solution is to reinstall ubuntu or fedora and once fully installed grub won't give you any more errors and so you should be able to startup from the recovery disc again of course by pressing f9 or f11 when your computer starts up.

---

### Post by tlarkin on 2009-09-18
> **emoguitarist06 said:**
> Why would you want to go back to vista?

Anyways I once went back to Vista as well and I had the same problem. I found that the easiest solution is to reinstall ubuntu or fedora and once fully installed grub won't give you any more errors and so you should be able to startup from the recovery disc again of course by pressing f9 or f11 when your computer starts up.

GRUB is just a boot loader and lives in the MBR, you can format your drive or reload 10 thousand OSes, but it won't wipe out the master boot record.

---

### Post by LewRockwell on 2009-09-18
> **tlarkin said:**
> GRUB is just a boot loader and lives in the MBR, you can format your drive or reload 10 thousand OSes, but it won't wipe out the master boot record.

Cheerios Mates!

of course, the /boot/grub/menu.lst file does NOT exist in the MBR, so you've got to put it somewhere

Good Day Mates!

.

---

### Post by bumanie on 2009-09-18
Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). The disk will repair your bootloader and get rid of grub.

---

### Post by gertrude58 on 2009-09-18
I cant load a recovery disk.I have two,one downloaded from that site and the other made from software preinstalled on my laptop.I just get grub error 17.So if I try to reinstall ubuntu from the live cd would it work and would I be able to boot into window as well?or would it be better to try  the usb stick I am using and install that?[its fedora]

---

### Post by oldfred on 2009-09-18
If you keep getting the grub error it is booting from your hard drive not your CD. Most laptops use f2, desktops f12, some others show a key to use as the BIOS initially loads. Some older computers only allow you to go into the BIOS to choose boot order. You then choose which drive to boot from. CD must be a bootable CD.

---

