---
title: "belkin f5d8053 N usb adaptor driver not executable"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Mylastconfusion on 2011-03-23
I'm trying to install the belkin  f5d8053 N usb adaptor. I have tried to follow this: 
[https://help.ubuntu.com/community/Wi...lkin%20F5D8053]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053")
but when I try to run the belkin driver with "wine" I get a message  saying my .exe file is not executable and yet I cannot change the  permissions to make it executable when i go to its properties... ](*,)

This is the message i get:

"The file '/home/teigeruby/Desktop/belkin f5d8053/f5d8053v3000.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

How do I make my file "executable"?

And how do I create the .inf file that ndiswrapper needs to load the driver??

Please help!

Many thanks

---

### Post by Daveth on 2011-03-23
one typically goes the file, right/left clicks (depending on right/left handedness), goes to Properties, and in the Permissions tab, tick the "Execute" box. Make sure you "own" the file as well- you will be in the user and group. You can do this true the terminal, if you can be bothered.

---

### Post by Onesimus on 2011-03-23
Another method that you could try is to install ndisgtk from System->Adminstration->Synaptic Package Manager.

Once install then load the .inf file supplied with the Belkin adaptor.

It should have been supplied.  if not, then right click on the executable and select 'extract here...'.  This should create a directory with the files inside.  

You don't need wine at all - if your using wine then you have gone wrong.

---

### Post by walt.smith1960 on 2011-03-23
> **Onesimus said:**
> Another method that you could try is to install ndisgtk from System->Adminstration->Synaptic Package Manager.

Once install then load the .inf file supplied with the Belkin adaptor.

It should have been supplied.  if not, then right click on the executable and select 'extract here...'.  This should create a directory with the files inside.  

You don't need wine at all - if your using wine then you have gone wrong.

As I read this, the O.P. doesn't have the .inf & .sys files, just the .exe file. If the O.P. has access to an XP install (Vista or Win7 won't work) they could "install" the .exe file then look in 'programs' for a folder with the name of the adapter.  Somewhere in that folder or a sub folder should be the .inf & .sys files.  Copy them to a safe place then uninstall the Windows software.  I've heard of people using a similar procedure in Wine but I have no experience with that.

O.P., have you searched for any threads beyond the one you mentioned?  NDISwrapper is generally recommended as a last resort.  It's preferred to use a native solution if at all possible.

Edit:  Here's a thread that may be relevant. [http://ubuntuforums.org/showthread.php?t=1673151&highlight=f5d8053](http://ubuntuforums.org/showthread.php?t=1673151&highlight=f5d8053).  I'm using an RTL8192SU device and it's a simple fix to create a folder, copy the firmware file into that folder and reboot.  Done!  Here's a link with a little more info:  [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)  This device should be recognized by Natty Narwahl with no tweaks required, the alpha 3 release does now.  

Edit 2:  I don't know if NDISwrapper will interfere or not.  It might be smart to remove it before trying the above solutions.  It should be easy to remove using Synaptic.

---

