---
title: "Wireless Indicator"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by shoaibi on 2010-01-27
I have Dell Inspiron 1545 and this model has no lights or any sort of indicator on the outside/hardware to tell me if my wireless is on or not. I just blindly press the wireless shortcut key on keyboard, left click on network manager and wait for minutes to see if i could see any wlans to validate that my wireless is turn on or not. Worst is when i am in a region which has no wlan with ssid broadcast.

The checkbox with "enable wireless" in the right click menu of network manager stays checked irrespective of wireless being on or not. Same goes for ifconfig or iwconfig.

I am looking for a way by which i can distinguish easily and quickly between my wireless on/off states.

---

### Post by Hospadar on 2010-01-27
it depends I suppose on how the hardware handles turning off the wireless.  On my lappy there is a physical switch which (I think) cuts power to the wireless card, and the hardware disappears from all hardware detection methods (lshw, iwconfig, lspci, etc).

First off are you sure that button does anything?  If you are connected to a wifi network, and you hit the button, does your connectivity go away?  I could imagine a situation where there is some windows program dell might normally install (which of course doesn't exist in linux) which listens for that button and disables the wifi in a software sort of way (i.e. nothing happens when you push that button in linux).

Other than that, if there's no light or anything and the hardware still shows up, you could maybe run a scan with the wifi which would give you instant results as to whether or not any networks are detected.  I'm not sure how this handles hidden networks, but you can give it a try, it's definitely quicker than waiting to see if network manager finds anything.
Try a command like 'iwlist wlan0 scan' (assuming your wifi card is wlan0)

Also if your button doesn't work, I'd just use network manager do enable and disable your wireless.

---

### Post by shoaibi on 2010-01-27
My hardware switch does disable the wireless as i am disconnected and any visible wireless networks are not show in network manager anymore. But my hardware still appears everywhere and iwlist eth1 scanning tells that eth1 doesn't support scanning which is my wlan interface, using broadcom sta driver.

---

### Post by warfacegod on 2010-01-27
> **Hospadar said:**
> Try a command like 'iwlist wlan0 scan' (assuming your wifi card is wlan0)

```
sudo iwlist scanning
```

works well for this also. With no need to figure out if the wireless card is wlan0 because the code will tell you.

---

### Post by shoaibi on 2010-01-29
works, thanks :)

---

