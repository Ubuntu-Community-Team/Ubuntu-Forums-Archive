---
title: "WUSB54G v2 in 8.04"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by untermensch on 2008-10-17
Hello, I'm having troubles getting the linksys WUSB54G working with Ubuntu 8.04. I'd like to find an ndiswrapper for it, since I doubt there's any other way it'll work. Can anyone help?

---

### Post by Mark224 on 2008-10-31
The WUSB54G seems to be a real pain to set up in Ubuntu 8.04!  I did get it to work although it does not work any more.

The best article I found was [here]("http://ubuntuforums.org/showthread.php?t=225206").  I didn't have to do everything in this but it is a good place to start.

I didn't need to build the ndiswrapper, I just downloaded the following packages and burned them onto a CD:

[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)

I then had to install the drivers onto a windows machine because the files are packed into the ".exe" file.  You'll need:
    * rndismp.sys
    * usb8023.sys
    * WUSB54GSv2.inf

Burn these onto a CD too and copy them onto your Ubuntu machine.

Once you have installed the packages just run ndisgtk and install the drivers.  I had to manually copy the driver files as in the referenced article.

HTH

---

