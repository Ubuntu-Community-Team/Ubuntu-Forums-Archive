---
title: "Mounting a Windows XP partition"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Devilham on 2010-01-15
I want to first and foremost say thanks to this community for guiding me through a tricky install of Ubuntu in a dual boot configuration with XP, formerly occupied by Vista (Ubuntu lives where Vista once did, and good riddance)

Now that I have them dual booting in perfect harmony one last issue remains.  When I try and mount the NTFS drive inside of Ubuntu I get the following 

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I have booted to the XP install disk and run Fdisk /f on the partition, so any tips would be appreciated

---

### Post by SteveHillier on 2010-01-15
It is a while since I did this and a long time since I have gone dual boot but I cannot recall any real issue although I recall having had samba loaded.  I could then just access the files directly.
hope this offers a crumb of comfort

---

### Post by audiomick on 2010-01-15
> **Devilham said:**
> ... In the first case [COLOR="Red"]run chkdsk /f[/COLOR] on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! 

> **Devilham said:**
> I have booted to the XP install disk and run [COLOR="Red"]Fdisk /f[/COLOR] on the partition, so any tips would be appreciated

Have you made a typo, or did you run something different to what the error message suggested?

---

### Post by Devilham on 2010-01-15
hehe, yes typo, ran chkdsk /f (holey moley if I didn't), and just to clear up any confusion, I have since booted to said windows partition just fine....it has NOT been fdisked!

Just want to make that partition viewable now in Ubuntu, and seem to be having (sporadic, it worked like once) attempts at mounting the volume

---

