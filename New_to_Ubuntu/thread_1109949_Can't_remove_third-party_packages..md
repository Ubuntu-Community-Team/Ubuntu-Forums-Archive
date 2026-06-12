---
title: "Can't remove third-party packages."
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Maniacal on 2009-03-29
Hello all and thanks for reading this thread.

Recently installed a couple of third-party packages that I'd like to remove. Can't seem to come up with the correct package name when using 'sudo apt-get remove XXXXXX'.

How do I request a list of all installed packages on my machine in Terminal? Long time ago I saw how to do it on another thread but am unable to locate.

Just in case it matters I'm running Ubuntu 8.10.

Thanks

---

### Post by hyper_ch on 2009-03-29
```

apt-cache search KEYWORD

```

or get a list of all installed packages:

```

dpkg -l | awk '/ii/ { print $2 }' > packages.txt

```

---

### Post by Maniacal on 2009-03-29
Thanks for the reply hyper_ch. Not having any luck with either option you listed. Guess my being a newbie with the command line is showing. Also having problems with printing as of late.

If I could just get a list of existing packages in Terminal it would be a great help. That way I could simply read through it and find these packages.

Thanks

---

### Post by Sarai the Geek on 2009-03-29
> **Maniacal said:**
> Hello all and thanks for reading this thread.

Recently installed a couple of third-party packages that I'd like to remove. Can't seem to come up with the correct package name when using 'sudo apt-get remove XXXXXX'.

How do I request a list of all installed packages on my machine in Terminal? Long time ago I saw how to do it on another thread but am unable to locate.

Just in case it matters I'm running Ubuntu 8.10.

Thanks

Did you install these packages through a package manager or as a .deb?

---

### Post by Maniacal on 2009-03-29
I did stumble across the package.txt file from hyper-ch's help. Can only find one of the packages I'm looking for in the file. 

Both packages were .deb.

1. 'ScrubbuUbuntu.deb' (listed as scrubbu in package.txt) was installed via command line using dpkg. Had to force install due to it being 32 bit instead of 64. I'm running AMD64 version of Ubuntu 8.10. When I use 'sudo apt-get remove scrubbu' Terminal states "E: Couldn't find package scrubbu". When I type 'scrubbu' at command line, the application starts. Application also starts and runs great via associated icon.

2. 'LimeWireLinux.deb' doesn't have a similar listing in package.txt. It was installed via Gdebi Package Installer. Following completion of install with no apparent errors, there was no icon to start the application.

Let me know if I can provide any additional information. Thanks

---

### Post by sydbat on 2009-03-29
You should be able to uninstall them via Synaptic. 

System > Administration > Synaptic...then (in Hardy at least) Status, which will give a left side menu that has Installed (local or obsolete). From there you should be able to remove the packages you want...unless it has dramatically changed in Intrepid.

---

### Post by Sarai the Geek on 2009-03-29
> **Maniacal said:**
> I did stumble across the package.txt file from hyper-ch's help. Can only find one of the packages I'm looking for in the file. 

Both packages were .deb.

1. 'ScrubbuUbuntu.deb' (listed as scrubbu in package.txt) was installed via command line using dpkg. Had to force install due to it being 32 bit instead of 64. I'm running AMD64 version of Ubuntu 8.10. When I use 'sudo apt-get remove scrubbu' Terminal states "E: Couldn't find package scrubbu". When I type 'scrubbu' at command line, the application starts. Application also starts and runs great via associated icon.

2. 'LimeWireLinux.deb' doesn't have a similar listing in package.txt. It was installed via Gdebi Package Installer. Following completion of install with no apparent errors, there was no icon to start the application.

Let me know if I can provide any additional information. Thanks

As long as you know the package names you can use

```
dpkg -r *package*
``` to remove deb packages. :)

---

### Post by Maniacal on 2009-03-29
Sydbat,
Nice try but neither package showed up under Synaptic > Status > Installed or Installed (local or obsolete). I didn't know that was possible under Synaptic. Although this didn't help with this particular problem it was good experience.

Thanks for the effort!

---

### Post by SunnyRabbiera on 2009-03-29
did you search for you applications in synaptic?

---

### Post by Maniacal on 2009-03-29
Sarai the Geek,
The 'dpkg -r' worked for "scrubba". Wonder why 'apt-get remove' wouldn't?

Think I'll see if Lime Wire has any tech support for their Ubuntu / Debian package.

Appreciate your assistance!

---

### Post by hyper_ch on 2009-03-29
well, the second commands makes a list of all installed packages and saves it to the text file specified in your current working directory.

---

### Post by Sarai the Geek on 2009-03-29
> **Maniacal said:**
> Sarai the Geek,
The 'dpkg -r' worked for "scrubba". Wonder why 'apt-get remove' wouldn't?

Think I'll see if Lime Wire has any tech support for their Ubuntu / Debian package.

Appreciate your assistance!

.deb package installation is separate from apt-get/synaptic. If you can find the correct package name you should be able to uninstall limewire the same way.

---

### Post by Sarai the Geek on 2009-03-29
> **Sarai the Geek said:**
> .deb package installation is separate from apt-get/synaptic. If you can find the correct package name you should be able to uninstall limewire the same way.

I downloaded limewire and it seems the package name is "limewire-basic". 
```
sudo dpkg -r limewire-basic
```^ That should remove it. :)

---

### Post by sir4taye on 2009-05-10
These other guys are way off. The guy who gave second post in this thread was right on. But... then open the packages.txt and look for limewire-basic. That's what you remove "supo apt-get remove limewire-basic" 
That worked for me. I was looking for the fix and came across this and wha-la.

---

