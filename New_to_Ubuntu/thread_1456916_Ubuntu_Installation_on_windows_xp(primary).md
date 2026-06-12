---
title: "Ubuntu Installation on windows xp(primary)"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by anandnz on 2010-04-17
Hi 

Ubuntu 9.10 installation

I have used gparted to create unallocated memory after defragmentation and was trying to install ubuntu. But strangely, it asks for login and password, this is first time ubuntu is being installed and i have not seen ubuntu creating swap and linux file sytem either.
obviously any combination of login and password gives authentication failure.

Also i have no password for xp in the initial boot, this is formatted laptop with 20 gb each assigned for windows and 20 gb unallocated by gparted.

When i remove the cd and let it run from internal hdd, it has no trace of ubuntu being installed. 

In the text mode, i see the following error ..

"
Failed to load module "i810" (module does not exist, 0) 
less /var/log/Xorg.0.log | grep EE "

Any help is appreciated.

Cheers
- Anand

---

### Post by Elfy on 2010-04-18
Moved to ABT.

If you are being asked for a password I would check that the cd and iso is good.

Check the md5sum of the downloaded iso - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The relevant md5sum to check against can be found here - [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Before you boot with the cd - check the integrity of the burn - [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by anandnz on 2010-04-20
Hi forestpiskie 
Thank you for the response, i had taken a new copy of ISO and this time tried to boot from USB, i have same result, prompting me for login and password.

Please can someone help me. 

Cheers
- Anand

---

### Post by anandnz on 2010-04-22
Hi Forestpiskie,

Thank you, problem resolved and new problem found

Strangely Md5 checksum for the above problem was success.
However, i took a new iso file and created USB bootable thus could install successfully. 


Note: Strangely, even after bios was set to USB, after initial screens as if booting from USB, the D610 laptop falls back to booting from CD thus tricking me. I got this sucess only after i removed the CD from drive and used only USB. 

Ubuntu 9.10 is successfully installed but i cannot update or connect to internet. I will post a separate thread for the issue. But Thank you very much Forestpiskie. much appreciated.:)

Cheers
- Anand

---

