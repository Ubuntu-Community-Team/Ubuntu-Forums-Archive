---
title: "Pocket PC sync with Ubuntu 9.04"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-05-07
I have been attempting to sync my IPAQ 1940/1945 with Ubuntu. It seems all of the provided setup information is dated; e.g. I downloaded the following instructions from the Ubuntu documentation site and discovered the synce-dccm is not available from synaptics package manager. A web search indicates it really should be downloaded with a package installer.

In any event would like to find a valid current procedure for performing the task. Some of the posts I read indicated you can really screw things up if you don't have a good procedure to follow:

Connecting to a Windows Mobile 5, 2003 or PocketPC Device
Plug in the device via the included USB cable. 
Install the synce-dccm, synce-serial and librra0-tools packages. To sync with Evolution, you'll also need the multisync, synce-multisync-plugin, libmultisync-plugin-evolution and libmultisync-plugin-backup packages. See Installing Software. The packages installer will ask various questions about how to connect to your device: 
Leave the serial interface as "/dev/ttyUSB0" 
Leave the default local IP address "192.168.131.102" 
Leave the default remote IP address "192.168.131.201" 
Set the IP address of your DNS server to "192.168.0.1" 
Make sure ports 5678, 5679 and 990 are not blocked by a firewall 
Click Applications -> Accessories -> Terminal. In the Terminal window, run: 
    dccm
    sudo synce-serial-start
Depending on your device you may have to run the sudo synce-serial-start command within a few seconds of powering the Windows Mobile device on. The computer should now show: *synce-serial-start*is*now*waiting*for*your*device*to*connect. The Windows Mobile Device should appear connected, in a similar way to when connected via ActiveSync on Windows.

---

### Post by raul999 on 2009-05-11
Hi,
I tried yesterday this way: 
[http://ubuntuforums.org/showthread.php?t=1081897]("http://ubuntuforums.org/showthread.php?t=1081897")

I encountered also some problems, when I plugged off the usb and plug it immediately in, then my Ipaq is not able to connect. I have to reboot and its working again.

Tell me or somebody else if hi encounters the same problems.

Thx

---

### Post by stelmed on 2009-07-06
Hello, 
I have been using Evolution (Ubuntu 9.04) for some time and it has been synchronizing very smoothly with  my Dell Axim x50v.
I have just noticed that if I delete a Task from my Pocket PC it wont be synchronised (deleted) in Evolution. The other way around seems to work normally. Do you have any suggestion? The synchronising of the Calendar and Contacts works fine...

---

### Post by paulchinnz on 2009-08-21
Where did synce-dccm go? I've tried getting it via terminal and synaptic without success. Has it been renamed or removed?

---

### Post by stelmed on 2009-09-17
Try odccm instead.

---

### Post by paulchinnz on 2009-09-18
Thanks. Already got that. Maybe I should just get an Android!

---

