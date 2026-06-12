---
title: "installing linuxant drivers for conexant hcf v90"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by tmtjjhnsn on 2005-10-15
I am desparate for some help.  I have been trying for two weeks to get online with my newly installed Ubuntu Linux.  I have a Conexant HCF V90 internal modem, which I understand does not come with drivers with Linux support.  I have downloaded the drivers from Linuxant using Firefox for Windows, copied them to floppy, and then copied them to a tmp folder in Linux.  The downloaded file is "cnxtpcihcfinstall.run".  I have run the file in the terminal with sudo sh /tmp/cnxtpcihcfinstall.run, and it launches a browser window that asks for a username and password.  I enter the name and password that appears in the terminal, but a message is returned in the browser window saying that no packages for download can be found.  The modem never dials.  I have configured the modem using pppconfig and pon provider, but the modem still does not dial.  Does anyone have experience with installing the Linuxant drivers?

---

### Post by claydoh on 2005-10-15
I have a HSF based modem that installed with a deb package (in Hoary), as they have Ubuntu-based .deb files for Hoary.
[Look on this page for some info, if you are running Hoary]("https://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php")

If you follow the guidelines for picking which file to download, (most likely hcfpcimodem_1.07full_k2.6.10_5_386_ubuntu_i386.deb.zip if you are running Hoary), extracting the deb from the zip file, transferring it to the same temp file yo used before, then running the following command:

sudo dpkg -i hcfpcimodem_1.07full_k2.6.10_5_386_ubuntu_i386.deb

I have not  tried to install a driver in breezy yet, as I have dsl :) but if you are in breezy,  you are in a predicament as you will need to install some other tools in order to build and install the driver. Perhaps Linuxant will soon get a version for breezy, which would make it super easy for you.

As I have paid the $14 for the driver, I would love to see a new deb for Breezy, so I have emailed them asking about the possibility/timeline.

---

### Post by tmtjjhnsn on 2005-10-16
Never mind the linuxant situation.  I have a used hardware-controlled serial modem on order that I found on Amazon for $12.00 USD, delivered.  I'm no expert, but I consider myself an advanced PC user, and installing those drivers was a nightmare.  I give up.

t

---

