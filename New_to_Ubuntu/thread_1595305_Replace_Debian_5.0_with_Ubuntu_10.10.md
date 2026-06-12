---
title: "Replace Debian 5.0 with Ubuntu 10.10"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by k3jsparks on 2010-10-13
Help! I am new to Linux (3 weeks ago got Ubuntu for first time) and saw an ad for Debian and thought I would try it out. I downloaded disk 1 and installed and formatted the entire hard drive, erasing Ubuntu (first mistake of many). Now I found out that I want Ubuntu back because I can actually understand how to use it.

I am stuck. I downloaded the Ubuntu and burned it to a disk, but when i reboot, I get nothing but the Debian system. I tell it to boot from the CD, and it tries, but can't seem to boot from it. Does the download only work for leaving a Windows system? How can I get out of this situation if I can't reinstall?

I have something called Unetbootin-linux-494 and downloaded it (can't figure out how to use apt-get on the machine so just I downloaded and installed that way). It says it needs p7zip-full. I see it in the packages for Debian, but I cannot understand how to install it. I tried apt-get install but have not figured out how to get it. I clicked on their link, got it, but I cannot open it now to use it.

At this point I am temmpted to install Windows just so I can have something I know how to use so I can boot from that. I WANT MY UBUNTU BACK!!!! :) 
Thanks

---

### Post by migs73 on 2010-10-13
You should check the ISO image file you downloaded is not corrupted using an MD5checksum;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn it to a disk using image burning sofware (don't know what is available on Debian, but assume Brasero will be) just select the ISO or image burn option, and burn at slowest speed. Then you could check the CD MD5 again.
Then try again to boot from the CD.

---

### Post by amjjawad on 2010-10-13
> **k3jsparks said:**
> Help! I am new to Linux (3 weeks ago got Ubuntu for first time) 


Welcome to Linux's World ;)

> 
I am stuck. I downloaded the Ubuntu and burned it to a disk, but when i reboot, I get nothing but the Debian system. I tell it to boot from the CD, and it tries, but can't seem to boot from it. 

Double check your BIOS settings. Perhaps the CD-ROM is not your first device to boot from.

If you have another machine (PC/Laptop), try the CD there.

Perhaps you need to check this: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Just to make sure your .iso file that you downloaded is not broken/damaged.

> 
Does the download only work for leaving a Windows system? 


Certainly not. It should work in general.

> 
I have something called Unetbootin-linux-494 and downloaded it (can't figure out how to use apt-get on the machine so just I downloaded and installed that way). It says it needs p7zip-full. I see it in the packages for Debian, but I cannot understand how to install it. I tried apt-get install but have not figured out how to get it. I clicked on their link, got it, but I cannot open it now to use it.


I'm not sure how to run that from Debian but that software you got is to create LiveUSB I suppose. 

> 
At this point I am temmpted to install Windows just so I can have something I know how to use so I can boot from that. I WANT MY UBUNTU BACK!!!! :) 
Thanks

Don't give up hope from the first problem ;)

---

### Post by ibuclaw on 2010-10-13
Debian is an awesome system, but admittedly for those who know a thing or two about administration...

Also, on a side note, most "Desktop" users now use Debian 6.0 testing, as is more up-to-date with the times compared to the current stable. I suspect the age of the OS is probably what through you off Debian 5.0...

> **k3jsparks said:**
> I am stuck. I downloaded the Ubuntu and burned it to a disk, but when i reboot, I get nothing but the Debian system. I tell it to boot from the CD, and it tries, but can't seem to boot from it. Does the download only work for leaving a Windows system? How can I get out of this situation if I can't reinstall?

How did you install Ubuntu the first time round? Also, are you "burning" the ISO to the CD correctly?
Hint: take a look at the contents of the CD, what do you see?

> 
I have something called Unetbootin-linux-494 and downloaded it (can't figure out how to use apt-get on the machine so just I downloaded and installed that way). It says it needs p7zip-full. I see it in the packages for Debian, but I cannot understand how to install it. I tried apt-get install but have not figured out how to get it. I clicked on their link, got it, but I cannot open it now to use it.

Unetbootin is only available in the Debian testing repository, not the stable one.

---

### Post by k3jsparks on 2010-10-13
I downloaded Unetbootin. It has an option I tried. It downloads the ISO  for me, to be sure it is done correctly. It then tells me to reboot. An  option comes up for me to choose between Debian, Single User Debian, and  Unetbootin. I selected Unetbootin and it said it could not find the  file. 
 
 As for having a corrupted file, I don't see how that is possible because  I downloaded it 4 times yesterday and each time got the same results.
 
 I am familiar with booting from a CD, that's not an issue. When i tell  it to boot, it sits for a few seconds as if trying to find the file,  then moves on to a normal boot with Debian.
 
 As for what I see when I download, I see one ISO file. Then when I  unpack it there are many files. Those are the things I burned on the CD  each time. I just think it is missing some file that would allow it to  boot from the CD.

---

### Post by k3jsparks on 2010-10-13
Oh, I forgot a question related that might help...
When I download the file from Ubuntu, on the page ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) under Burn Your CD or Create a USB Drive. I selected CD, and I selected Ubuntu as what I would be using to create it. There was not a setting for anything but Windows, Mac, or Ubuntu. Is there somewhere I need to find the download for Debian?

---

### Post by k3jsparks on 2010-10-13
Your suggestions solved it. thanks a lot!! it turns out that it was a bad download. The 5th one I did from another computer and now I am back in Ubuntu!. I am sure Debian will be great to use when I get a clue. 

thanks for the help!

---

### Post by sgosnell on 2010-10-14
Debian and Ubuntu work almost exactly the same - same apt-get, same Synaptic, same terminal commands, same everything I've found.  I have Debian testing on an SDHC card, and I boot it about as often as I boot Ubuntu.  The desktop is slightly different, but not radically so, and I find the functions in the two distros to be about the same.  A simple change of themes would probably make them indistinguishable to the eye.

---

### Post by QLee on 2010-10-14
One of the main differences most users would notice quickly is that the default Debian install does have a root password and is not setup with the sudo structure for users to temporarily obtain superuser permissions the way Ubuntu is. First user added is a limited user, not an admin by default.

Even though the applications are the same, sometimes there are version differences.

---

