---
title: "b43 in ubuntu vs. other major distros"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by igknighted on 2008-10-06
I have a broadcom wireless card that is supported by the b43 drivers in the kernel (and extracted firmware).  In Suse, Fedora, Mandriva and others this works wonderfully and the performance is comparable to what I get under windows.  However in Ubuntu (every version I have used... back to Dapper), performance of the native broadcom driver has been, well, awful.  I can be sitting right next to the access point and have 50% signal.  Same driver (in theory, I haven't compared the source code myself), same firmware, same everything as far as I can tell.  But performance is way off.

Has anyone else noticed this?  And is there any explanation as to why this is the case from the devs anywhere?

---

### Post by Ayuthia on 2008-10-06
Which card do you have?  I have a 4311 rev 01 and I have not seen too many differences between the distros.  I have used Gentoo, Arch, Kubuntu/Ubuntu/Knoppix, and Suse and they all produce similar results.  The bcm43xx driver was not that great but once the b43 came around, it has worked better, but that was more about improvements in the driver.

However, I have seen that the 4311 rev 02 and 4312 rev 02 have some problems in Ubuntu.  I recall that 8.04 did not work so well for those cards.  All I know is that it is partially based on the patches that are made and when the distro is released.  Unfortunately, I am not one of the developers so I can't give you an exact answer on what happened.

---

