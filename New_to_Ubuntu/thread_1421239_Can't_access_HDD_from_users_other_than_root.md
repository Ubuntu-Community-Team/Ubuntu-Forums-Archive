---
title: "Can't access HDD from users other than root"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by tinkerist on 2010-03-04
one of my HDDs is only available from root.  i've tried messing with the permissions but it usually says that permissions "...can not be determined".  it did let me look at the settings of that tab once but whenever i tried to change the users or groups that owned or had access to the drive the settings would instantly revert to root.

i don't want all users to have access, but i would like some users to have access, and not just root.  can someone help?

Edit:  idk if this helps but it allows me to view the permissions settings if i access properties from file browser, but if i access properties from the desktop icon it gives me the can not be determined error.  i still have the same problem with setting reverting to default though.

---

### Post by iMisspell on 2010-03-04
> **tinkerist said:**
> one of my HDDs
Cant help you with your problem, but you do want to watch out when changing permission's on your drive's. You say, *one of [your] hdd's*, there are folders and files which have the correct permissions set when Ubuntu installs itself, you do not want to go and change them. If this hard-drive is a storage drive, then its a different story.

---

### Post by tinkerist on 2010-03-04
i have three hard drives in my box, two IDE and one SATA.  one of the IDEs works fine in "root" user but is totally invisible from any other account.  it does not contain any files related to Ubuntu's operation since it was not even connected at the time of installation.

---

### Post by hobo14 on 2010-03-04
Edit the file /etc/fstab as root.

You will find the disks mounted at boot there, one per line.
Look in gparted or the result of typing "mount" in the terminal to determine which line is the disk you are talking about.

On that line in fstab the first 4 columns (separated by whitespace) will be the uuid, mount location, file system type, options, in that order.

You need to manipulate the options column.  Options are separated by commas(","), no spaces.

If the disk in question is ext3/4/etc all you need to do is add "user" to options (options will probably then be "defaults,user").

If the disk is FAT or NTFS it's not quite as simple. I usually add the following options:
uid=1000,umask=000
This makes you the owner of the files there (assuming you were the first user account created on the system - you can check if your user id is something other than 1000 in /etc/passwd) , AND gives you full access to them.
You may want to tone down the access rights mask, eg 022 instead 000...?

Save the file, reboot.

All done! ;)

---

