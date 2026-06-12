---
title: "Problems Mounting a NAS Drive"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by Richard_Beresford on 2014-07-01
I am having problems mounting a Synology DS211j NAS drive from a laptop running Lubuntu 12.04.
I can mount the "homes" folder on the NAS drive successfully to the /home/NAS_Drive folder from a terminal window using an IP address using the following command (without the outer quotes):
"sudo mount -t cifs //192.168.2.6/homes/ -o username=username,password=password  /home/NAS_Drive//

However, this is not satisfactory as the NAS drive's IP address can change.  I want to mount it using its network device name which is "Synology_Ds211j" (without the quotes) but when I try to use this name instead of an IP address, I get the following error message: "could not resolve address for Synology_DS211j:  Unknown error"

The command line that I have used which produces this error message is:
"sudo mount -t cifs //Synology_DS211j/homes/ -o username=username,password=password  /home/NAS_Drive/".

What am I doing wrong when trying to use the device name instead of the IP address?

Once I can mount the NAS drive using its network name, I then want to auto mount it on boot up.  How can I achieve this?

All help gratefully appreciated by a complete newbie to Linux.

---

