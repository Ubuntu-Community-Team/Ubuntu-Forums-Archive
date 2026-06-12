---
title: "After upgrade to Jaunty - bluetooth mgr inoperable"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-05-15
After upgrading to Jaunty, my bluetooth dongle wasn't identified/installed. Calling Bluetooth Manager doesn't launch and System Monitor does not not any program/process starting with "blue", i.e., no bluez, blueman, etc.

Both bluez and blueman show up as installed in synaptic. And lsusb shows the device as:

Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

How do I fix this?

---

### Post by 123456789123456789123456 on 2009-05-15
It is possible that something simular to what happened to me.  I was building a computer for a customer, and I originally put 8.10 on it, then upgraded to 9.04, after I upgraded I noticed that the bristo burning program showed up in update manager, but was greyed out, and the program would not work properly, when trying to burn disks.  I had to uninstall the cd/dvd creator program, and uninstall completely the burning program in question, and reinstall the burning program, after that it worked and fixed the problem in update manager.  I figured out that the problem accured with how the old program under 8.10 was handled changed in 9.04.  It sounds like something simular is happening here.  Expecially since the computer does tell you the device is connected.

Try finding all bluetooth programs on the computer, and telling synaptic to mark them for complete removal.

after that, make a list of the programs that were removed, restart the computer, and then mark the programs you removed for installation, and reinstall them.

that could fix the problem.

---

### Post by Mark_in_Hollywood on 2009-05-15
I had Synaptic look at doing the "removal". It showed it would also be removing Evolution!

I'm not doing a removal until I know what's going on. Has anybody tried doing a reinsallation without a removal?

---

