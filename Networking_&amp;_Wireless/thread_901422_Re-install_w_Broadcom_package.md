---
title: "Re-install w/ Broadcom package"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-08-26
I only have wireless access in my dormitory.  I installed 8.04 and disconnected one of the WAP's so I could use the wired port to download the [Broadcom driver](http://linuxwireless.org/en/users/Drivers/b43).  Is there a way to install 8.04 on another machine and include this driver so I don't have to disconnect the WAP for a few minutes (and probably make the IT staff visit my room and charge me with misuse of state property)?

Even if I download the package from [Linux Wireless](http://linuxwireless.org/en/users/Drivers/b43) it still is just a .sh that when run, downloads the proper driver and installs it.

Thanks!

---

### Post by Sam Lars on 2008-08-26
If you have a flash drive that would work to transfer the files.
I'm sure there's some way to make a custom install CD, and I'd love to try that some time, but I'm not sure how at the moment.

---

### Post by MaindotC on 2008-08-27
Hi, Sam.  I'm aware of the ability of a flash drive or optical media, but the problem is that I don't know what files to transfer.  As I stated, there are these packages in the repositories:
```

b43-fwcutter - Utility for extracting Broadcom 43xx firmware
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
bcm5700-source - module source for Broadcom's bcm5700 ethernet driver

```

but I think even if I transfer those files, they aren't everything I need for the driver.  If I download the package from linuxwireless, the file is install_bcm43xx_firmware.sh:
```

      sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```

All it does is connect to a location to download the firmware and then when its downloaded, install it.  Obviously I won't be able to do this if I have no connectivity to begin with.  Does that make sense?

---

### Post by Sam Lars on 2008-08-27
Well if it has the same card you should look at what your first computer used, only one of those should be installed.
Also, if you're sure that it's the same card, you can copy the
/lib/firmware/b43 directory over to the other computer.  This is all the cutter script installs.
Another option is to grab the driver file it's cutting from so it doesn't have to download it.  Links to the files are in the sh script you mentioned.

---

### Post by MaindotC on 2008-08-27
The card I had when I first installed is the integrated, wired Ethernet card.  Since I moved into my dormitory we only have wireless access.

I'll try what you suggested and let you know if it works.  Thanks!

---

