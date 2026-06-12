---
title: "Help with VirtualBox"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-17
I am running w7 in my virtualbox, and am unable to see my external hd's. I added them to my shared folders. when i turned on w7, i saw that the drivers for the hd's were installed, but they are still not visible.

---

### Post by anewguy on 2010-07-17
Are they USB?  Did you install the open-source version (no USB support) or the PUEL version from the Sun/Oracle site (with USB support).  Did you add any filter to allow USB devices to be seen?

Dave ;)

---

### Post by TimEnid on 2010-07-17
> **anewguy said:**
> Are they USB?  Did you install the open-source version (no USB support) or the PUEL version from the Sun/Oracle site (with USB support).  Did you add any filter to allow USB devices to be seen?

Dave ;)

1 of them is usb, the other is esata. Not sure which version i installed. I installed it from Synpatic. How do i add a filter? thanks for the help

---

### Post by rwgale on 2010-07-17
Running XP in VBox, I've just added a shared folder (from ubuntu /home/robert/test) using VBox devices->shared folders.  I was able to locate it by mapping a netwrk drive under My Network Places (right click) and then browsing for the shared-folder.  It did not show in network places (and still doesn't) for me, but it is there (using the map drive).  Perhaps this might work for you, until a 'more correct' approach is found.

---

### Post by anewguy on 2010-07-17
> **TimEnid said:**
> 1 of them is usb, the other is esata. Not sure which version i installed. I installed it from Synpatic. How do i add a filter? thanks for the help

If you installed the version from the repositories using Synaptic, you installed the open-source version with no USB support.  You'll need to use Synaptic to uninstall it, then go to the Sun/Oracle site and install the PUEL version (it's still free, it's just no open source).  That should at least get you USB support.  I haven't used VirtualBox for a while now, but at the time I did you had to define a filter for USB devices to be seen (the PUEL version).

Dave ;)

---

### Post by TimEnid on 2010-07-17
> **rwgale said:**
> Running XP in VBox, I've just added a shared folder (from ubuntu /home/robert/test) using VBox devices->shared folders.  I was able to locate it by mapping a netwrk drive under My Network Places (right click) and then browsing for the shared-folder.  It did not show in network places (and still doesn't) for me, but it is there (using the map drive).  Perhaps this might work for you, until a 'more correct' approach is found.

so im in Network, but i dont see an option to add a networkd drive.

---

### Post by davec64 on 2010-07-17
> **anewguy said:**
> If you installed the version from the repositories using Synaptic, you installed the open-source version with no USB support.  You'll need to use Synaptic to uninstall it, then go to the Sun/Oracle site and install the PUEL version (it's still free, it's just no open source).  That should at least get you USB support.  I haven't used VirtualBox for a while now, but at the time I did you had to define a filter for USB devices to be seen (the PUEL version).

Dave ;)

Just to add to what Dave has said, here's the link to the download page:

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Once you've installed it and setup Win 7 you'll need to install **Guest Additions** from the **Devices** menu.

It's the Guest Additions that give you USB support.   :)

---

### Post by TimEnid on 2010-07-17
> **anewguy said:**
> If you installed the version from the repositories using Synaptic, you installed the open-source version with no USB support.  You'll need to use Synaptic to uninstall it, then go to the Sun/Oracle site and install the PUEL version (it's still free, it's just no open source).  That should at least get you USB support.  I haven't used VirtualBox for a while now, but at the time I did you had to define a filter for USB devices to be seen (the PUEL version).

Dave ;)

ok, this partially worked. my usb connected zune now shows up, but the usb connected hd does not. again, i saw the driver for it being installed, but i dont see anything under my computer.

---

### Post by digitalcitizenx on 2010-07-17
[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by oldefoxx on 2010-07-17
Anything set to be shared with a VirtualBox client will show up under My Network and the vboxsrvr on the client side.  You can make it appear to be a local drive by using the right mouse button and selecting the option to assign a drive letter to it, then it will also show up under My Computer.  The setup will be remembered, and if the shared status changes later, or the drive is flagged as being no longer shared, then each time the client starts up, you will have to designate whether to retain that setting for future use or not.

The instructions on possibly having to switch from the OSE version to the (now)Oracle version are valid.  But in many cases, you can simply decide to share the root directory of any drive or partition with a client, and use the drive letter designation approach described here to do almost as much,

By "almost as much", I mean that Windows regards what's shared as merely on loan, and while you can write or copy to what is shared, you are prevented from doing things like reformatting what is merely shared,

---

### Post by anewguy on 2010-07-17
> **TimEnid said:**
> ok, this partially worked. my usb connected zune now shows up, but the usb connected hd does not. again, i saw the driver for it being installed, but i dont see anything under my computer.

I don't know for sure about now, as I haven't used VirtualBox in quite a while, but you used to have to set up filters in the vbox machine's USB setup in order to see most devices.  Sometimes people get by with the single blank filter as described in the vbox help, but more often then not I had to add a filter for each device I wanted to see (if I remember correctly, it involves saying "this USB vendor:device can be used in vbox".

Dave ;)

---

