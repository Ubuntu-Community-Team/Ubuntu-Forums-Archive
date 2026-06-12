---
title: "Ubuntu and XP via Samba"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by addisor on 2006-08-30
Been trying for a few days to share files, but without much sucess. Searched a few threads and howto's but struggle a bit when editing SMB file. I've got a desktop running solely Ubuntu (its great), with one user called rob, this is wired to a TEC broadband wireless router. (internet and email all work a treat.) I'd like to be able to access my XP laptop files and share a printer bi-directional. The laptop connects to internet via wireless. User on this is called ROB 1, computer called laptop, and workgroup called Starhouse. Where do i go from here?

cheers

---

### Post by huygens on 2006-08-30
OK, you can follow my advice here to share folder (allmost no command line intructions or smb.conf direct modification ;-) ): [http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)

Then to share a printer, here it is: [http://www.ubuntuforums.org/showthread.php?p=1416519#post1416519](http://www.ubuntuforums.org/showthread.php?p=1416519#post1416519)

Now, try these, and tell us what do not still work? Then I can help you further :-)

Huygens

---

### Post by addisor on 2006-08-31
Thanks I followed that. When I access network serves, a windows network icon appears, if you open its empty, or making a link is denied.

---

### Post by tophiechrisp on 2006-08-31
I had the same problem after I installed a firewall... it seemed to be blocking the internal network. My set-up is precicely the same as yours, except that UBUNTU's on my laptop and XP on the desktop. I haven't established how to configure the firewall so it doesn't hide the home network, but I thought i'd let you know that that's an option to consider. My firewall on Ubuntu is the most recent Firestarter version.

To find out if that is the problem, disable the firewall app and try clicking on the Windows network icon again. If you can see your network ,at least we know what your problem is! (Don't forget to re-enable the firewall afterwards though... I wouldn't like to be responsible for you gettin hacked!)

---

### Post by addisor on 2006-08-31
progress is made, by disabling the firewall i can see my own files but not the laptop files, still no talking to the laptop.

---

