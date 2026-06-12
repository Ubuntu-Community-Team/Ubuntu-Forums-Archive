---
title: "Can't Install Ubuntu with wubi"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by TuxTorvalds on 2010-12-02
So I finished downloading ubuntu from wubi, restarted, but nothing showed up, it just booted to Windows 7. so now I'm going to try a disc, but before I use it, if I put it in, will it take over my computer or will I be able to boot to windows 7 if I take the disc out?

---

### Post by Verbeck on 2010-12-02
the live cd wont do anything to data on the hard disk, its running off from the cd

unless you shif+delete everything...

---

### Post by TuxTorvalds on 2010-12-02
okay thanks just wanted to be able to boot from Windows 7 and Ubuntu when ever I want.

---

### Post by Tijssiej on 2010-12-02
> **TuxTorvalds said:**
> okay thanks just wanted to be able to boot from Windows 7 and Ubuntu when ever I want.

Running Ubuntu from a live cd can be very slow. Try an USB instead of it ;) But the best should be installing ubuntu!

---

### Post by TuxTorvalds on 2010-12-02
I don't have a usb.

---

### Post by TuxTorvalds on 2010-12-02
I have an inkjet printable disc, so I put the file to the disc, restarted and immediately put the disc in, nothing shows up, and windows suggests to me that I should burn the file to the disc with " Windows Image Burner " so I do that, but it doesn't work! it says the selected image file isn't valid! what should I do?

---

### Post by Verbeck on 2010-12-02
try imgburn with the slowest speed [http://www.imgburn.com/](http://www.imgburn.com/)

are you using the .iso image file or the wubi installer file?

---

### Post by TuxTorvalds on 2010-12-02
I'm using the ISO file.

---

### Post by Verbeck on 2010-12-02
if it still fails, another thing you could do is check the integrity of the iso
> 

[LIST=1]
[*]Download and install [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum"), a free and open source hash verification program.
[*]Right-click the ISO file.
[*]Click Send To, then winMD5Sum.
[*]Wait for winMD5Sum to load and finish the checksum (this may take a significant amount of time depending on your computer's performance).
[*]Copy the corresponding hash from [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") into the bottom text box.
[*]Click "Compare"
[/LIST]
useful links
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TuxTorvalds on 2010-12-02
I'm not sure what to do, I put the file to the disc and then try to burn it to ImgBurn, but should I wait and I don't know if it's even burning.....

---

### Post by bcbc on 2010-12-02
> **TuxTorvalds said:**
> So I finished downloading ubuntu from wubi, restarted, but nothing showed up, it just booted to Windows 7. so now I'm going to try a disc, but before I use it, if I put it in, will it take over my computer or will I be able to boot to windows 7 if I take the disc out?

Look at the Startup & Recovery settings and check whether the Timeout is set to zero. (Check the Advanced Tab in the System Properties dialog box).

(If you get it working, don't update the packages grub-pc or grub-common or it will break).

---

### Post by Verbeck on 2010-12-02
> **TuxTorvalds said:**
> I'm not sure what to do, I put the file to the disc and then try to burn it to ImgBurn, but should I wait and I don't know if it's even burning.....
copying the file directly to the disk wont work..

insert the cd
run imgburn
select 'write image file to disk'
for the source, select the iso file you downloaded
change the write speed to the slowest possible value
then click the big icon on the lower left to start

---

