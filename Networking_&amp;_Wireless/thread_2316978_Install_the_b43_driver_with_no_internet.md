---
title: "Install the b43 driver with no internet"
date: 2016-03-12
forum: Networking &amp; Wireless
---

### Post by Hadaka on 2016-03-12
Please Verify installing the **b43** driver is correct per this guide..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
The pci-id [14e4:XXXX] determines what driver performs best with the wireless card.

**Important to do first. ****Attached ZIP file**  *

To load the **b43** driver with ***no internet*** access, first drag and drop the attached 
 **b43.zip **file ..see[* **Attached ZIP file** *]  below
to the **Desktop**. Then at the **b43.zip** icon on the **Desktop** 
>***right*** click then choose > ***Extract Here***.

Next open a terminal...ctrl/alt/t..then please copy and paste one line at a time.
ignore any error or file not found on the first two commands.

This removes the bcmwl-kernel-source driver if it was installed by error or default.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```

Then to install the b43 driver, please copy and paste..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe b43
```

boot 

* Attached Zip File *
[ATTACH=CONFIG]267780[/ATTACH]

---

