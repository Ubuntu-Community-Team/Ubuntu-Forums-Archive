---
title: "frustrated -  how to upgrade user to admin group"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by darfield on 2010-04-08
I was given an old hp pc that is running ubuntu 5.10 breezy badger with gnome. I have zero experience with anything other than Windows. I managed to add myself as a user after the boot in grub, not realizing that I would be unable to add myself as an admin without knowing the password left by the previous user. I have tried everything; su, sudoers, sudo, sudo visudo, adding application launcher for root nautilus, to researching the top 500 most commonly used passwords. (no luck) How do I, (as a user) add user to admin group when I am restricted from doing so? Can I do this after the boot like before? And is the  sudo password the same one the default keyring is looking for? Can I remove keyring password prompt permanently?  I am unable to upgrade or install a newer version (i have the 9.04 live cd) due to an inoperable cdrom. Help?

---

### Post by -humanaut- on 2010-04-08
Upgrading from 5.10 would almost guarantee a busted system at this point. Do you have a cdrom drive in another computer you could swap out with ?

---

### Post by Jive Turkey on 2010-04-08
There is a way to make load a root shell at boot. I think if you choose recovery console from the grub menu.  I haven't done that for a long time so I'm not sure if that will give you root or not.  If not you will need to entor some boot parameter at the grub menu, or something in order to get root.

When you get to the prompt that says "root@<host>#" you are good to go.
This will give you access to the "passwd" command and you can change the password for the original user by running the command passwd <username>.  

It is also possible to load ubuntu onto a usb key and install from that.  If you can boot the live CD on another computer there is a tool for building the usb key installer under System > Administration.  You will probably not be able to upgrade automatically but I may be wrong.

---

### Post by darfield on 2010-04-09
Thank you,  your information set me on the right course. Boot into Grub, highlight kernel-recovery mode and edit line to rw init=/bin/bash. then boot into that mode, it takes you to "root@<>#. I changed the password, added myself to the admin group and then fixed the /etc/sudoers file,  that  contained errors that was preventing  "sudo" from working at all. 

I also found the best explanation for the  root/sudo/user confusion that is so confounding for a beginner to Linux.  "Root" is not the first user set up on the system,  "Root" doesn't actually have a password, but when prompted for the root password, you can't leave it blank either.  The first user added when the system is installed is the "Main User" whose password is different from root. Main User is added to the admin group and can access all programs needed to maintain the system.  So, if I (as a user with very limited permissions) needed to login as su <me> , the password I am prompted for is my own.  Then if permission to access the application is asked for again by the default keyring, it is asking for the Main users password. Finally the last prompt will be for the root password. I think......!   If someone stumbles inherits a system already set up (like I did) they will need to reset the root and Main user passwords in order to have full access to the system.  I think.........

---

### Post by darfield on 2010-04-09
:oops:

---

### Post by chappajar on 2010-04-09
Yes, user ID for root is 0, user ID for user accounts starts at 1000 and goes up.

---

