---
title: "help me out here guys"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by freihage on 2009-03-18
I need help. I installed ubuntu on my laptop which has a broadcom wireless setup in it. works great with windows but unbuntu would not let me activate the driver and now I can't figure out how to get the driver back so I can use my wireless. can anyone please tell me how to fix this? thanks

---

### Post by Chesamo on 2009-03-18
There is currently no driver available for your chipset native to Linux.

If you have the Windows drivers (I mean the drivers themselves, the .cab, the .inf and the .sys files) you can use NDISwrapper and [this handy tutorial](http://ubuntuforums.org/showthread.php?t=31926).

In order to get the drivers from Windows, right-click My Computer, click Properties. Then under the "Hardware" tab select "Device Manager". Right-click on your wireless network adapter and click "Properties". Under the "Driver" tab, click on the "Details" button. Now open up an Explorer window and navigate to C:\WINDOWS\system32. Hit Ctrl+F and search for the name of the first driver on the list (for example, if your driver says "rn2860.sys", search for "rn2860"). There should be at least one folder that is found (make sure you have "View Hidden Files and Foldrs" and "View Protected Operating System Files" enabled in Folder Options). Copy the contents of that folder into a folder on a Flash drive.

Now go to the [NDISwrapper homepage](http://sourceforge.net/projects/ndiswrapper/) and download the latest stable release. Put that on the Flash drive.

Install Ubuntu, then use the tutorial I mentioned above to install and configure your wireless drivers.

NOTE that NDISwrapper only works with XP drivers, not Vista drivers. If you're using 64-bit Ubuntu, you'll need to find the Windows XP x64 drivers, not the Vista x64 drivers.

---

