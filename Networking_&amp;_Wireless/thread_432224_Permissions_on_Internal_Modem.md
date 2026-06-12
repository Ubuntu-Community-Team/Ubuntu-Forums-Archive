---
title: "Permissions on Internal Modem"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by artesvida on 2007-05-03
My internal modem (hardware, USR/3Com 2977) is working fine in my Ubuntu 6.10 server.  It's installed as /dev/ttyS1, and when I set the permissions correctly on ttyS1 it works correctly.  However, every time I reboot the server the permissions on ttyS1 are reset.

ls -l /dev/ttyS1
crw-rw---- 1 root root 4, 65 2007-05-03 14:54 /dev/ttyS1

So, at this point, to get regular old users to be able to use this device, I've tried two different things:
1.  chown root:tty /dev/ttyS1, then put the users who need to use the modem into the tty group, OR
2.  chmod 666 /dev/ttyS1

Either method works fine.  However, when I reboot the system, the modem goes back to root:root ownership and 660 permissions.  Why?!  Any thoughts on how to fix this?

---

### Post by artesvida on 2007-05-04
<wrong>
I figured it out.  If anyone else needs to know, you need to edit the /dev/MAKEDEV script.  I had to look and see where the ttyS[#] devices were getting set, where I noticed that they were getting setup with the "dialout" group, which was a group that had been deleted.  So, I could have either set this to a different group, or (what I did) was re-create the "dialout" group and add the necessary users to it.  In this script, at the top, you can also set different permissions as well.
</wrong>

D'oh, my bad.  Adding the "dialout" group fixed something, but the MAKEDEV script isn't where this is getting set (as I noticed after I changed the permissions here and it didn't stick).  I needed to add a file to /etc/udev/rules.d.  I called the file 50-modempermissions.rules and added a single line:
KERNEL=="ttyS[0-9]",          GROUP="dialout",          MODE="0666"

After rebooting, all was good.  See "man udev" and /etc/udev/rules.d/README for more information.

---

