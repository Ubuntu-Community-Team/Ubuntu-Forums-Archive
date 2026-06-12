---
title: "Cannot boot Ubuntu 10.04 with AHCI Enabled"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by HunterOfDay on 2010-09-04
Ok this is my problem: I have installed Ubuntu 10.04 onto one of the hard drives in my computer. The installation works perfectly, but when I go to boot after install, it hangs after the system checks for a cd. I have AHCI enabled, and I have been able to install and run Fedora on this machine, but for some reason Ubuntu is giving me grief. If more information is needed please let me know.

Thanks.

---

### Post by candtalan on 2010-09-04
Does a live cd work ok in this machine?
Also, the later image  10.04.1 is available now and includes bug fixes, so a new install may function better maybe?

---

### Post by ikt on 2010-09-04
Are you able to set AHCI to compatible or compatibility mode? or does it work if you disable it?

What error messages do you see before it hangs?

---

### Post by HunterOfDay on 2010-09-04
Ok The live CD works and can be booted from. I have the SATA mode set to AHCI in the BIOS, and There is no error message, it just hangs. I have even tried setting the hard drive to boot after the DVD-ROM drive and it still hangs. As a note, I previously installed Fedora 13 on this same drive without issue, so I don't think that it is a Linux issue, but more likely an issue with Ubuntu and this hard drive.

Edit: Ok I was able to get Ubuntu up and running on a different hard drive, so it looks like the problem was with Ubuntu not liking the hard drive I had installed it on the first time. Thanks for your help though.

---

### Post by Schuby007 on 2011-01-27
What kind of hard drive was it? Manufacturer? Model? Capacity? What motherboard were you using? This kind of information can help others avoid this problem.

Thanks.

---

