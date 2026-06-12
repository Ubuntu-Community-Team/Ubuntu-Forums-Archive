---
title: "Dell Mini 9 External DVD player"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by dcwinsagain on 2009-03-16
I apologize if this topic is already being addressed elsewhere, but nonetheless, here goes...
I'm fairly new to Linux...I have a new Dell Mini 9 with an I/O Magic external usb dvd player.  When I plug the dvd player into the laptop, the computer does not acknowledge it has been plugged in.  The light on the dvd player will come on and USUAllY if I press eject, it will open and I can insert a dvd.  Still then, the computer does not acknowledge the dvd player or the dvd.  I can USUALLY eject the dvd and start over, but I have no consistency.  Sometimes everything will work fine, but lately I have not been able to get it to work.  I have tried cleaning the lens of the dvd player, but to no avail.  I know the dvd player works because it was fine a few weeks ago and it works with Windows.  Now I did find a similar problem on a different thread, and I tried typing - dmesg into terminal and this is the end of what I received:

[ 2552.737387] usb-storage: waiting for device to settle before scanning
[ 2557.067965] usb-storage: device scan complete
[ 2557.179403] usb 5-8: reset high speed USB device using ehci_hcd and address 4
[ 2557.241174] usb 5-8: device descriptor read/64, error -71
[ 2557.347311] usb 5-8: device descriptor read/64, error -71
[ 2557.500994] usb 5-8: reset high speed USB device using ehci_hcd and address 4
[ 2557.610273] usb 5-8: device descriptor read/64, error -71
[ 2557.817012] usb 5-8: device descriptor read/64, error -71
[ 2557.989561] usb 5-8: reset high speed USB device using ehci_hcd and address 4
[ 2558.379031] usb 5-8: device not accepting address 4, error -71
[ 2558.490916] usb 5-8: reset high speed USB device using ehci_hcd and address 4
[ 2558.879891] usb 5-8: device not accepting address 4, error -71
[ 2558.880189] usb 5-8: USB disconnect, address 4
[ 2558.963830] usb 5-8: new high speed USB device using ehci_hcd and address 5
[ 2559.075735] usb 5-8: device descriptor read/64, error -71
[ 2559.282254] usb 5-8: device descriptor read/64, error -71
[ 2559.498946] usb 5-8: new high speed USB device using ehci_hcd and address 6
[ 2559.617856] usb 5-8: device descriptor read/64, error -71
[ 2559.829664] usb 5-8: device descriptor read/64, error -71
[ 2560.045445] usb 5-8: new high speed USB device using ehci_hcd and address 7
[ 2560.453045] usb 5-8: device not accepting address 7, error -71
[ 2560.564921] usb 5-8: new high speed USB device using ehci_hcd and address 8
[ 2560.972511] usb 5-8: device not accepting address 8, error -71
david@david:~$ 

I don't know if this has anything to do with my problem or not.  
My settings are set to auto mount when devices are plugged in.  Any help is greatly appreciated.

---

