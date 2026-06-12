---
title: "Belkin Wireless G USB Network Adapter (54mbps, 802.11g)"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by cooltuyul on 2008-06-15
I just can't get it to work.

---

### Post by Lupgaru on 2008-06-16
I tried to use Belkin myself on a Thinkpad but found out from Belkin Support that they do not support Linux and couldn't (Wouldn't) help me so I got my money back and bought a Linksys USB Modem(Wireless G) standard, not the Speed Booster Model, works great with Ubuntu. Just Plug and Play. Speed Booster is the new model and not recognized yet. Good Luck.

---

### Post by mohitchawla on 2008-06-16
@cooltuyul: Which model version do you have ?

---

### Post by james_vanb on 2008-06-16
Not sure what you've tried, but I have Belkin Wireless G USB F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

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

Give it a shot.

---

### Post by cooltuyul on 2008-06-20
doesn't work - i have f5d7050 does it make a difference?

---

### Post by cooltuyul on 2008-06-20
> **mohitchawla said:**
> @cooltuyul: Which model version do you have ?
i have the model f5d7050

---

### Post by james_vanb on 2008-06-21
Same model.  Maybe different version.  Confirm driver loaded as follows and post output:

```
ndiswrapper -l
```

If your router has security settings enabled (WEP, etc.) - Disable and see if you can connect.  There are issues setting up security.  

Also try manual configuration of Network Manager.  

Otherwise and if the driver loaded, post output of:

```
iwconfig
```

to see if it's a configuration problem.

---

### Post by zasiliou on 2010-11-03
Thank You!!!! You were a huge help!!! Thanks for helping me get online :)

---

### Post by james_vanb on 2010-11-04
Congrats - Enjoy

---

