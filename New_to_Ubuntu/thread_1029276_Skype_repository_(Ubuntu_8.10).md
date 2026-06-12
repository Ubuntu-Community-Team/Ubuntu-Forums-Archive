---
title: "Skype repository (Ubuntu 8.10)"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by bnleez on 2009-01-03
I'm getting the following error message:

Could not download all repository indexes: 

Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.53.130 80]

URI: [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)

Anyone have a solution to this problem?

---

### Post by plucky on 2009-01-03
Try adding the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu) and install skype from there or use the [Skype download website](http://www.skype.com/intl/en/download/skype/linux/choose/)


I think the Medibuntu Repo is best as that will keep you up to date.


Good Luck

---

### Post by superprash2003 on 2009-01-03
its easier to download it from the skype website

---

### Post by bnleez on 2009-01-04
Thanks for your response.  

When I try to download directly from Skype, I get the following message: Error: Wrong architecture 'i386'

Any idea why I'm unable to install this package?

---

### Post by taurus on 2009-01-04
You downloaded the x86 version while you run a x86_64.  That's why it is complaining about the wrong arch.

p.s.  Try this one, [http://packages.medibuntu.org/intrepid/skype.html](http://packages.medibuntu.org/intrepid/skype.html).

[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

### Post by sadaruwan12 on 2009-01-04
OK, I think you're trying to run skype on a 64 bit Ubuntu OS i386 means you're software supports 32 bit OS's like the Ubuntu 32 bit version try to install that and you want get this massage.

---

### Post by bnleez on 2009-01-04
@Taurus, I tried reinstalling Skype as you instructed but I´m still getting the same error message (as above) when I run the Update Manager.  Any other suggestions?

---

### Post by bnleez on 2009-01-04
@sadaruwan12, so you're saying I should install Ubuntu 32 bit version?  Stupid question: How do I find the version I'm currently running?

---

### Post by plucky on 2009-01-04
> **bnleez said:**
> @sadaruwan12, so you're saying I should install Ubuntu 32 bit version?  Stupid question: How do I find the version I'm currently running?

From a terminal ```
uname -a
sudo lsb_release
```

Should tell you either x86 for 32Bit or x86_64 for 64Bit.

Good Luck

---

### Post by swoody on 2009-02-17
> **bnleez said:**
> @Taurus, I tried reinstalling Skype as you instructed but I´m still getting the same error message (as above) when I run the Update Manager.  Any other suggestions?

Have you tried removing the Skype Repo, and then running Update manager again? I would recommend using the Medibuntu Repo to add Skype. It will be a lot easier to install, remove, and stay updated that way. Also, you get all the great Medibuntu multimedia stuff available:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

