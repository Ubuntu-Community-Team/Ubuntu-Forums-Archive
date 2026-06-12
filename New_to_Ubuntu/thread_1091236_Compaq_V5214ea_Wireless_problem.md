---
title: "Compaq V5214ea Wireless problem"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Neil Purling on 2009-03-09
I got the CD of Ubuntu 8.10 desktop and put in my Compaq laptop.
As I see now it has booted from the Live CD.
How can I tell if Ubuntu has found the wireless network function & configure it if necessary?
The laptop has a button for the Wireless function, that normally glows when active. Thus I assume it is not working because the tell-tale glow is not on.
If I stick a network cable into the appropriate port I can browse the Web.
Where do I find if the hardware has been detected?
I would like to work out the bugs while running the Live CD.
If it is possible to get the wireless networking activated then I will probably install Ubuntu 8.10. is there a Ubuntu for laptop distro?

---

### Post by Neil Purling on 2009-03-09
I remembered that in my laptop bag I have a WLAN Dongle so I re-booted with that plugged in a USB port.
The icon on the toolbar shows the presence of the device and the Hewlett Packard Company BCM4311 020.11b/g Wireless.
It is greyed out & selecting it was thus not possible.
Is that better information to work with?
This is being typed on the Compaq in Ubuntu. If i have to I will always use the dongle, but it is an irritant that there is a device that does not want to work that will do the same job.

---

### Post by Neil Purling on 2009-04-02
I did a proper install, XP is gone forever!
Ubuntu works well with the dongle WLAN, but it is a mild irritant that I do not have the internal WLAN active. The drop-down box that appears after you click on the network icon shows the internal adapter, as I said in post #2. It is in pale greay so I assume that although it is detected there is some reason why it is not functional. Has anyone got any ideas?

---

### Post by lkraemer on 2009-04-02
in a Terminal window do:
```

lshw -C network
ndiswrapper -l

```

Then post the output here.

lkraemer

---

### Post by divague on 2009-04-02
it's grayed because you have to install the drivers for the wireless card, here's a guide that may help you

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

