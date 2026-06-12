---
title: "bluetooth problems"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-02-04
Have 8.10 and can't get bluetooth working properly.  All the discussions I've looked at (such as [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset) )
refer to the bluetooth icon on the taskbar:  "...right click on the icon, choose preferences, and click on the services tab..." etc.

Well my icon>preferences does NOT have a services tab.  What is to be done?

I went to the bluez.org ([http://www.bluez.org](http://www.bluez.org)) website to download the latest version.  When extracting the files contained in this archive (bluez-4.28.tar.gz) where does one put them?

Any help would be greatly appreciated.

---

### Post by mpl34 on 2009-02-04
Hey, I'm very new to ubuntu/linux to however i was able to get my bluetooth mouse working with the following,

sudo apt-get install bluez-compat
sudo hidd --search

as for the extracting of bluez i believe it should have extracted it self in the directory that you were in when you preformed the extraction.

There is one fault i found with my method my bluetooth mouse does not stay "permantely" connected ie. every time i reboot or my computer goes to sleep i need to search for my mouse again, however others suggest that it should keep the mouse connected after reboots etc. You may have more luck than me hopefully.

---

### Post by raymondvillain on 2009-02-04
If I type the following command:

pactl load-module module-alsa-sink device=auto

I get this response:

Failure: Module initialization failed

Anybody know what causes this?  I'm at step 15, following the directions in the bluetooth how-to:

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Any ideas?

---

### Post by raymondvillain on 2009-02-20
Today (Friday, February 20, 2009) the update notification icon was glowing when I booted up.  I downloaded all the updates.  Included were a bunch of bluetooth and bluez files.

Now bluetooth works much better (Ubuntu 8.10 Intrepid) but unless they're in constant use, the mouse and keyboard still have to be jump started.

---

