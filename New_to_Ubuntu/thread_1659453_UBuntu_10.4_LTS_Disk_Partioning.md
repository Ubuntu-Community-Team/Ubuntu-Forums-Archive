---
title: "UBuntu 10.4 LTS Disk Partioning"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Refreshe on 2011-01-04
Ok so im trying to install Ubuntu 10.04 LTS and whet I get to step 4 (Disk partioning) There are no drives in the window. And when I click forward I get "No root file system is defined.Please correct this from the partitioning menu." What do I do to fix this?

---

### Post by Quackers on 2011-01-04
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

