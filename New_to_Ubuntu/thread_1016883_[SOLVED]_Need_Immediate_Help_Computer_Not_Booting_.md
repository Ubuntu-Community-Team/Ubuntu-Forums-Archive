---
title: "[SOLVED] Need Immediate Help: Computer Not Booting Up"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-20
Okay I deleted the swap partition for Ubuntu (was going to reinstall as a extended partition). Anyway my computer rebooted and now all I get is 

Grub Loading Stage1.5

Grub Loading, please wait.....
Error 17

Is their anyway to get into Windows, don't need to get into Ubuntu right now?

---

### Post by luctor on 2008-12-20
Try to boot from a windows install disk and repair the mbr
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by RookieUbuntuUser58 on 2008-12-20
> **luctor said:**
> Try to boot from a windows install disk and repair the mbr
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

My netbook doesn't have a CD/DVD drive. So I guess I'm out of luck.

---

### Post by Carl Hamlin on 2008-12-20
> **boost3d23 said:**
> My netbook doesn't have a CD/DVD drive. So I guess I'm out of luck.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Not necessarily. If you're able to boot the netbook from a flash drive, you're not dead in the water yet.

You can install a livecd to a flash drive and boot from there to fix your partition table.

I certainly wouldn't recommend using a flashdrive as an everyday installation platform, however. The media can only sustain a limited number of write/erase cycles before failing and taking your data with it.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNOjkACgkQyLm4ydrABvcHZACgpBz5rJoazO7KBKyGO9pSUUf9
D3sAoJlSPWMokVpvvcFy6XoS++yHRxCY
=MaSa
-----END PGP SIGNATURE-----

---

### Post by RookieUbuntuUser58 on 2008-12-20
How would I go about doing that? What would I need to install on the flash drive?

---

### Post by candtalan on 2008-12-20
ubuntu 8.10 live cd has a menu item to make a bootablelive usb stick

You will need to have the iso image of the live cd in a known place for the creation process. So the easy way is 
1) to use another pc, download 8.10 desktop iso file, make a live CD 
2) use the 8.10 live CD to run the PC
3) create the bootable usb stick
4) boot the netbook from the stick and examine and repair the problem.

note: grub will be expecting its boot files to be in a certain (mounted) partition. Changing (deleting, adding.... ) partition is likely to cause re name of existing partitons maybe? If this is your problem, then th econtents of the /boot/grub/menu.lst will be useful to examine.

good luck

---

### Post by RookieUbuntuUser58 on 2008-12-20
Can you also use Wubi installer method to create a live USB or not? Reason I ask is I don't have a CD burner.

---

### Post by nhasian on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

hopefully you have access to another pc.  you can use a USB pendrive and install ubuntu on it with unetbootin.  just download the program and the the ubuntu iso on a pc and then you can make a bootable USB stick.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)


-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)
Comment: [http://getfiregpg.org](http://getfiregpg.org)

iEYEARECAAYFAklNhAAACgkQvB0HFLis0nNOmQCfUPPmEdp49jhn1s2NWQ41qTNS
bSMAn0B8ZnphHRIrlvyH0CQSlgkdZGB5
=jAOl
-----END PGP SIGNATURE-----

---

### Post by candtalan on 2008-12-21
> **boost3d23 said:**
> Can you also use Wubi installer method to create a live USB or not? Reason I ask is I don't have a CD burner.
Wubi is easy to use if you only have Windows on a machine. I think it can get more complicated if you already have a dual boot configuration - maybe because you get wubi in the windows boot loader and the original dual boot uses grub.

Is it possible to get use of another machine to create the botable usb stick?

---

