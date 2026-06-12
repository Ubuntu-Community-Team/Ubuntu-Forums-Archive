---
title: "Can't make network driver"
date: 2018-10-27
forum: Networking &amp; Wireless
---

### Post by sunkencathedral on 2018-10-27
Hi,

I have just installed Ubuntu and am trying to get my network driver (based on the **rtl8812AU** chip) installed. I copied the files to my Ubuntu installation via USB, and am trying to follow the directions here: [https://marcnu.github.io/2016-09-10/How-to-install-Netgear-A6100-USB-Wifi-adapter-on-Ubuntu-16.04/](https://marcnu.github.io/2016-09-10/How-to-install-Netgear-A6100-USB-Wifi-adapter-on-Ubuntu-16.04/)

Apparently I need to build the binary using the make command. But when I try, I get the error:

```
The program 'make' is currently not installed. You can install it by typing: sudo apt-get install make
```

When I try this, however, I get an error message that the package was not found. But I've read that doing this may require build essentials, which can apparently be installed with:
```

sudo apt-get install build-essential

```

But this fails to be found, too. Of course, I have no internet - so it's expected I suppose? I seem to need internet access to install what I need to install my driver and get internet access... I think. I'm not sure how to break out of this circle. :confused:

---

### Post by jeremy31 on 2018-10-27
What kernel are you using?  Results for ```
uname -a
```

Thread moved to networking and wireless

---

### Post by sunkencathedral on 2018-10-27
4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC

Just downloaded and installed today.

---

### Post by chili555 on 2018-10-27
If you still have the installation USB from which you installed Ubuntu, all the needed packages are there.

I have been looking for a proven reliable way to use USB drive as an apt repository and simply apt-get install build-essential. I have, so far, been unsuccessful. I propose another method that will get the prerequisite build-essential installed.

This method, although it is tedious, will work. The list of deb files you need is this (with the exception of bcmwl-kernel-source): [https://paste.ubuntu.com/p/GbZ689gYXw/](https://paste.ubuntu.com/p/GbZ689gYXw/)

Create a folder on your desktop to hold the files. I suggest:

```
mkdir ~/Desktop/debs
```
Browse the USB drive and look in pool/main/b for build-essential; in pool/main/d for dkms and dpkg-dev; in pool/main/f for fakeroot and so on. Continue until every package on the list I provided is dragged into the debs folder.

Now, back to the terminal:

```
cd ~/Desktop/debs
sudo dpkg -i *.deb
```

---

### Post by sunkencathedral on 2018-10-28
That worked, thanks! FYI, the libcilkrts5 file was not anywhere in pool/main/, I checked every folder and searched. But all of the other files were, and they seemed enough to do the trick. The driver compiled and I was able to get online.

---

