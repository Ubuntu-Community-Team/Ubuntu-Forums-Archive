---
title: "problem with scanner."
date: 2009-04-27
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-04-27
i've installed unbuntu 9.04 and when i connect my samsung scx-4521f (all-in-one) printer, ubuntu searched for its drivers and installed it. i can use my printer, but i can't use my scanner. ubnutu can't detect my scanner. Any help please?

---

### Post by yahs on 2009-04-27
Go to samsung.co.uk
Search for your printer under Support,Downloads
Select driver and choose Unified Linux driver (ver3.00.37)
Download this file and extract to Desktop or Home Folder
You will now have a folder called cdroot, inside that is a folder called Linux.
Open a terminal and change to this directory
cd /cdroot/Linux
Run the following command
sudo ./install.sh
Follow the prompts and that's it.
The Samsung Unified Driver Configurator will appear on your desktop
Reboot may be necessary for scanning

---

### Post by RajaAjmal on 2009-04-28
thanks for the reply yahs. i'll try it

---

### Post by jack frost on 2009-12-08
> **yahs said:**
> Go to samsung.co.uk
Search for your printer under Support,Downloads
Select driver and choose Unified Linux driver (ver3.00.37)
Download this file and extract to Desktop or Home Folder
You will now have a folder called cdroot, inside that is a folder called Linux.
Open a terminal and change to this directory
cd /cdroot/Linux
Run the following command
sudo ./install.sh
Follow the prompts and that's it.
The Samsung Unified Driver Configurator will appear on your desktop
Reboot may be necessary for scanning

do you have the link. i went there and no linux driver is there.. it used to be on the usa site.but not anymore.

---

### Post by ramjet_1953 on 2009-12-08
This post may be of use to you:

[http://ubuntuforums.org/showthread.php?t=563159](http://ubuntuforums.org/showthread.php?t=563159)

If you scroll down, there is even a copy of the patched driver to download.

Regards,
Roger :D

---

### Post by jack frost on 2009-12-09
> **ramjet_1953 said:**
> This post may be of use to you:

[http://ubuntuforums.org/showthread.php?t=563159](http://ubuntuforums.org/showthread.php?t=563159)

If you scroll down, there is even a copy of the patched driver to download.

Regards,
Roger :D

thanks... i will check it out.. i was able to find the driver googling around. printer portion is now fine.. but scanner is not detected.. hopefully that updated patch will help.

---

### Post by jack frost on 2009-12-09
> **ramjet_1953 said:**
> This post may be of use to you:

[http://ubuntuforums.org/showthread.php?t=563159](http://ubuntuforums.org/showthread.php?t=563159)

If you scroll down, there is even a copy of the patched driver to download.

Regards,
Roger :D

thanks.. everything works now.. i have to run xsane as root, but i will work on that later.  vpn is my biggest task at this time.

---

