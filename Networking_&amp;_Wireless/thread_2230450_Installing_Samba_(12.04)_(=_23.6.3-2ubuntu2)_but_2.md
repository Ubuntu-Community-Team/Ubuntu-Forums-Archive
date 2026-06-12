---
title: "Installing Samba (12.04) (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be install"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by martin112 on 2014-06-19
Hi

This problem happened when I tried to install Samba on Ubuntu (12.04) and I could find a proper solution to it.
Maybe it helps:
My error when trying to install it:
```

sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Recommends: tdb-tools but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

The problem is a conflict with the version of the library libwbclient0 (2:3.6.3-2ubuntu2 is installed but requieres 2:3.6.3-2ubuntu2.3)
So let's install version 2:3.6.3-2ubuntu2.3:

For tat go to [https://launchpad.net/ubuntu/precise/i386/samba/2:3.6.3-2ubuntu2.3](https://launchpad.net/ubuntu/precise/i386/samba/2:3.6.3-2ubuntu2.3) and download the .deb file [http://launchpadlibrarian.net/107185828/samba_3.6.3-2ubuntu2.3_i386.deb](http://launchpadlibrarian.net/107185828/samba_3.6.3-2ubuntu2.3_i386.deb)

Double Click, it will open with the Ubuntu Software Center and click to install.

Then run again the command sudo apt-get install samba. It should install propertly samba.

---

