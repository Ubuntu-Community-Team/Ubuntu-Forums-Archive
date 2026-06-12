---
title: "Get rid of Swap and Update Kernal to Trim Supported"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Rick 250 on 2010-07-22
So I want to put my 40GB solid state drive into my netbook that has 2GB of ram.  I could be wrong, but I believe that the Swap partition is similar to the pagefile system of windows, which I know you can get rid of, or shrink.  I previously tried Windows 7 with the SSD on the netbook, but it simply doesn't have the processing power to make a difference, and with my core i7 desktop, the SSD doesn't make that much difference either.  
So my question is, how could I install Ubuntu 10.04 (from the mini install, as that's the only way I can get the trackpad and keyboard working: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) ) without a swap partition, since space is scarce.  And then how to update the kernel to the one that supports Trim for the SSD.  
And if there is a hibernation system file like on Windows, how to delete that.

Thanks

---

### Post by LowSky on 2010-07-22
You dont need really swap, the only way for Ubuntu not to create a swap partition is to manually create your partitions. From a regular LiveCD used gparted. from the minimal, just set the partitions manually  when it asked you to format the drive.


Also by disabling SWAP I'm pretty sure hibernation goes out the window. Just remember that Linux is very different from Windows. Linux doesn't do page filing the same way. A swap partition is limited to the size it is created, while Windows page file can grow as required. I'm not a fan of hibernation or Sleep so I cant confirm.

---

### Post by Rick 250 on 2010-07-22
Thanks, anyone got suggestions about the Trim?  Or will the update automatically update to the newest kernel?

---

