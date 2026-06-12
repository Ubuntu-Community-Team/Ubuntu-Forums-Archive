---
title: "Problem Updating Packages"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by s.fox on 2009-03-08
Hi,  

I am having a little trouble running some updates on Intrepid Ibex.  I get the following error message:
```

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?
```If I click Yes, I get some more error messages:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-8-generic_2.6.27-8.17_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.27-8.13_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.1.3-0ubuntu1~intrepid2_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.1.3-0ubuntu1~intrepid2_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.1.3-0ubuntu1~intrepid2_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-2ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-2ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-2ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cupsys_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cupsys-client_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-common_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.27.8.12_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.27.8.12_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.27.8.12_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-8_2.6.27-8.17_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-8-generic_2.6.27-8.17_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.27.8.12_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-8.17_i386.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cupsys-bsd_1.3.9-2ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.24.0-0ubuntu3.2_i386.deb
  404 Not Found

```Can anyone please help me sort this out?  

Many thanks,

Ash R

---

### Post by bettlebrox on 2009-03-08
Have you run "apt-get update"?

---

### Post by s.fox on 2009-03-09
Hi,

Things looked like they were going well and packages were being downloaded. Then this happened:

```
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

This seems like a circle to me,  :(

Can someone please help?

Many Thanks,

Ash R

---

### Post by taurus on 2009-03-09
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by s.fox on 2009-03-09
> **taurus said:**
> ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Ahh, thanks for that :)

I seem to have hit a problem at the last hurdle though :(

I have installed the entire medibuntu repository and looking under the section,
"Playing Non-Native Media Formats"

I don't know which of the following I am supposed to run because I don't know if I am i386, amd64 or ppc.  How would I find out?

Many thanks for all the help,

Ash R

---

### Post by taurus on 2009-03-09
```
uname -m
```
i686 = 32bit
x86_64 = 64bit

---

### Post by s.fox on 2009-03-09
> **taurus said:**
> ```
uname -m
```i686 = 32bit
x86_64 = 64bit

Wow taurus.  Thank you.

I think the problem may be solved now because I accidentally clicked the red install arrow and its started downloading 331 packages!  Apparently this will take 40 minutes.

Would I be right in thinking that the stuff in the "Playing Non-Native Media Formats" is nothing at all to do with my update problems and that I have simply got side tracked?

Once again,  thank you for all the support.  This community is awesome!

-Ash R

---

### Post by taurus on 2009-03-09
If you do your normal **sudo apt-get update && sudo apt-get upgrade**, you don't have to worry about which arch. you are running since the system knows which version (32bit or 64bit) to download.

But if you plan to download something by hand, then you do need to know so you would download/install the right version for your system.

---

### Post by s.fox on 2009-03-09
Well,  I think its all sorted now.  

Thanks to everyone,

-Ash R

---

