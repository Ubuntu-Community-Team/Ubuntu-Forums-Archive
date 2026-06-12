---
title: "Belkin F5D7050B cant get driver to work right"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by ptindall on 2008-08-29
Hi everyone!  

I have a belkin F5D7050B usb dongle and I cant seem to get the drivers to work.  I've already tried quite a few tutorials and posts here but with no luck.  I've managed to get the usb to come up as wlan0 with the serialmonkey rt73 drivers, but it still doesnt allow me to connect to any wireless signal. Im stuck here.  Is there any chance that my ipw2200 is interfering with the belkin? 

Any help?

Thanks

---

### Post by james_vanb on 2008-08-29
Have used Belkin USB on both Ubuntu Gutsy and Hardy. I've always had to use ndiswrapper and the Belkin install CD. Process is:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic (2 files ndiswrapper utils and common).

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```


add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following:

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

### Post by tanker60 on 2009-11-08
When I do these steps, I get an error page and when I open wireless networking in system/admin/windows wireless drivers, there is only wired and point to point ... which are greyed out.

I see rt73.inf driver is installed.

Any ideas ???

Thanks,

Randy

---

### Post by james_vanb on 2009-11-08
Randy

Sorry to hear you're having trouble with this adapter.  I believe the Belkin USB has been working "out of the box" since Ibex.  Which version of Ubuntu are you using?

---

### Post by sc298 on 2011-03-20
Sorry to bring up an old thread but I've been struggling all day to get the Belkin F5D7050B working with 64 bit Ubuntu 10.10.

Does anybody know which drivers I should use or if this adapter is even compatible with the 64 bit edition?


Thank you!
Sean

---

