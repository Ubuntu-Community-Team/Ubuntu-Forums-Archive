---
title: "Consistent issue with SMB shares on WD router"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by gde061-www on 2015-01-30
I have had a WD MyNet router for some time.  I recently switched to Ubuntu 14.04 from my systems preinstalled Win 8, and a number of other household PC's of family members are running prior versions from Win 7 to XP.  For all windows garbage, it did allow me to map to the network drives on the router.  And once mounted, there was never a problem manipulating any of the files in the router's HDD.  I have a MnNet central router, and everything is running on the same LAN. 

Now that I have had Ubuntu for a while,the shared drives are giving me major problems.  First off, I can't consistently move files to them in through the normal file-browser environment.  Also, sometimes a file just won't open, like if I try to play an MP3: I can browse the directory tree, even "open" the file, but then Rythembox might decide to tell me "File failed to open (null)".  Other times if I try to copy files up to the mounted location it will die with an "unexpected" error to wit: "General input/output error while accessing /run/user/1000/gvfs/smb-share ..."

I can get in to the share with FTP, but it's just not as convenient as having it mapped and readily accessible through the GUI, without having to make local copies of everything.  

Interesting thing, when I first installed I was NEVER able to copy to these shares when I just mounted them through the nautalis window. Then I found an online guide to permanently mount the location at startup first getting CIFS, and then editing fstab.  That seemed to help - sometimes - and for limited times.  Eventually even those mounted locations end up crapping out on me.  Then I have to reboot and cross my fingers. 

Anyone have an idea what might be the problem?

Thanks

---

### Post by gde061-www on 2015-02-06
Bump -

I see many threads here with issues about smb shares.  I would really appreciate some suggestions about how to troubleshoot this problem.  In unity/nautilus, I can see the "Windows Network", and under that my router, but clicking on it just brings up the same icon of the server - it never gets to the actual shares.  Adding by network address (i.e., smb://IP_ADDRESS/share name) works only sometimes.  It's flukey, like one second I go into Nautilus and connect "connect to server", choose smb://IP_ADDR/, and I get a blank window with no shares.  Then I go to "Browse Network", it shows me Windows shares... click that and I see the server name (Netbios I guess), click that, and it's empty.  So then I go back to the "connect to server", do exactly the same thing I did before, and now suddenly all the share folders are there.

What's the issue?  Is it Nautilus?  Unity?  A problem with 14.04?   I connect to these shares using a variety of windows and andriod devices all the time with never anything as bizarre as with the one Ubunto 14.04 machine, so I'm inclined to think it's not the a problem with the router.  Any incite - and I mean ANY thoughts - would be appreciated to help me figure this out.

---

