---
title: "ubuntu on dell dim 2400"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Kogneto on 2009-06-21
hello, quick question

trying to install 9.04 on dell dimension 2400 that was previously running windows-xp-sp2. popped in the disk, clicked install, orange bar bounces back and forth a few times then freezes.

grabbed an old 8.10 disk to see if maybe it was just the new version, went through same thing, freezes.

tried going through and reformatting the whole disk to ntfs (should i have done ext3?) and try again, same thing.

anyone know of any issues on dimension 2400? had another dimension awhile back that i slapped 8.10 on and it ran fine...i'm thinking it might be the disk drive, but let me know if you think i'm doing something wrong

thanks in advance
-kogneto

---

### Post by wpshooter on 2009-06-21
Is this a new Ubuntu disk ?  If so, have you checked the integrity by running the verification function that is found on the initial Ubuntu boot screen menu ?

If it has been tested, then have you tried the safe graphics mode parameter ?

---

### Post by Kogneto on 2009-06-21
you know i tried getting suse11 on this computer a couple weeks back too, and had a similar problem, and ran a disk scan and it came up funky, i think i had set the burner to max when i burned it so i attributed it to that.

i haven't tried running a disk check on the ubuntu disks, but like i said the 8.10 worked on another computer...damn i'm thinking it's gotta be the drive...anyone got a spare drive? i'd get a thumbdrive but am college student (i.e. broke) :P

think i could get it to boot off my iPhone? lol that would be a sweet feature for 3.0

---

### Post by mattwilkes512 on 2009-06-23
> **Kogneto said:**
> hello, quick question

trying to install 9.04 on dell dimension 2400 that was previously running windows-xp-sp2. popped in the disk, clicked install, orange bar bounces back and forth a few times then freezes.

grabbed an old 8.10 disk to see if maybe it was just the new version, went through same thing, freezes.

tried going through and reformatting the whole disk to ntfs (should i have done ext3?) and try again, same thing.

anyone know of any issues on dimension 2400? had another dimension awhile back that i slapped 8.10 on and it ran fine...i'm thinking it might be the disk drive, but let me know if you think i'm doing something wrong

thanks in advance
-kogneto

Strange.  I have a dell dimension 2400 and have not been able to install any Ubuntu past 8.04 do to unsupported graphics.  Ubuntu 8.10 and 9.04 work but you have to purge compiz.  Your other option is to get a new PCI graphics card and you can install Ubuntu 9.04 .

---

### Post by abn91c on 2009-06-23
> **mattwilkes512 said:**
> Strange.  I have a dell dimension 2400 and have not been able to install any Ubuntu past 8.04 do to unsupported graphics.  Ubuntu 8.10 and 9.04 work but you have to purge compiz.  Your other option is to get a new PCI graphics card and you can install Ubuntu 9.04 .
+1, the issue is the i845 video card and ubuntu 8.10 and above. a new PCI card will fix your problem, here is one I installed on my dell 2400 [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4471396&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4471396&CatId=319)

---

### Post by Kogneto on 2009-06-24
hmm yeah, is that really the problem though?

I created a .img usb drive with 9.04 and when I plug it in and select boot options, then the usb drive, it does not even load the main ubuntu screen, it just gives a "press F1 to retry boot"

...hrm...i was hoping to use the computer as a home server of sorts, but this is so troublesome

might have to be a project for another day :(

---

### Post by presence1960 on 2009-06-24
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
did you try installing in safe graphics mode?

if that doesnt work try the alternate text based installer : [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by mattwilkes512 on 2009-06-24
> **Kogneto said:**
> hmm yeah, is that really the problem though?

I created a .img usb drive with 9.04 and when I plug it in and select boot options, then the usb drive, it does not even load the main ubuntu screen, it just gives a "press F1 to retry boot"

...hrm...i was hoping to use the computer as a home server of sorts, but this is so troublesome

might have to be a project for another day :(

I dont think the BIOS A05 on the dimension 2400 has an option to boot from USB.  If you dont have a graophics card and want to use compiz 8.04 is your best bet.  You can purge compiz for later releases but then you wont have sound either.

---

