---
title: "Wireless security settings removal???"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Big-B on 2008-04-10
This may sound a bit odd to most, but i'm looking to clear the wireless security setting either upon boot up or shut down.  I'm figuring that when you enter your credentials for the wireless network they are 'stored' in a .conf file perhaps??  I haven't come across anything yet, again i'm guessing that once I know the file, maybe have a script run to delete or clear that file on shutdown?  maybe?  Any help would be great whilst I keep digging around.  
BTW, I'm connecting on a WPA2 Enterprise connection flawlessly.  
Ubuntu 7.10 old Dell Inspiron 8600 w/ BCM4309 wireless. Gotta luv Ubuntu.

---

### Post by Jeff250 on 2008-04-10
Assuming you are using NetworkManager, this information is stored in the following user gconf key:
/system/networking/wireless/networks

So the following command should clear these settings:
gconftool --recursive-unset /system/networking/wireless/networks

You can create a new script to run that command in this directory (make sure its executable):
/etc/gdm/PostSession/

Then this script should be run for all users when they log off.

---

### Post by Big-B on 2008-04-11
Much appreciated Jeff, I got the settings removed, and am putting together a small script so the users credentials are wiped on logoff.  x'ing my fingers!   
Thanks again for the help!\\:D/

---

### Post by Jeff250 on 2008-04-11
Good to hear.  Something has occurred to me:  I think that the logout script part of the solution I gave won't work, since IIRC this will get run by root, not by the user, but the gconf keys we want removed are specific to users!  A disappointing subtlety.  I guess if we only have to remove these gconf keys for only one user, then we can run sudo -u USERNAME before the command and still get it to work in a rather crude way.  This technique can even work for multiple users, but this will increase script complexity.  I'm hoping that you've thought of a better way by now.

---

