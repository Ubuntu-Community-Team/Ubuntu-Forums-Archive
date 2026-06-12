---
title: "Error Message when updating"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-05-14
After I updated to 9.04 from 8.10 everytime I do an update with the update manager or reload in synaptics I get the following messages:

W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

I do not know the terminal commands necessary to get rid of these messages.

---

### Post by spiderbatdad on 2009-05-14
this looks like you need to edit the file /etc/apt/sources.list
```
gksu gedit /etc/apt/sources.list
```Add a # symbol at the beginning of the first line where it starts ...deb cdrom...

---

### Post by Rog3236 on 2009-05-15
Thanks, that eliminated one of the error messages. How about this one?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

---

### Post by kanikilu on 2009-05-15
It looks like you are using this PPA:

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

You can either add the key following the instructions here:

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

Or simply do the following from a terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0624A220
```

---

