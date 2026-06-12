---
title: "Trouble With Linksys WMP54GS Wireless Card and Network Manager"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by blackhole82 on 2007-03-14
I just recently upgraded my wireless card and now I can't detect my wireless network.  The card I was using before was a Belkin and worked fine.  My new card is a WMP54GS and  I would like it to work with network manager and WPA2 wireless security.  This is how I had the belkin working.  I've installed the wireless driver(s) via ndiswrapper and my /etc/network/interfaces file is set to work uninhibited with network manager.

I've tried adding my network in network manager and connecting, but to no avail.  Does anyone have an alternate method or suggestions for getting my WP54GS card to work?  It does show up under, administration > networking but is not configured for ease of use with network manager.

---

### Post by teaker1s on 2007-03-14
sudo apt-get install network-manager-gnome
un check network interfaces in network manager,  remove ethernet cable,reboot and by volume icon(top panel right) will be networking icon-if your wireless is active you can click and select it.

otherwise ndiswrapper and network-manager-gnome
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys?highlight=%28wireless%29]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys?highlight=%28wireless%29")

---

### Post by blackhole82 on 2007-03-14
I already have network manager installed.  I've reinstalled it several times to see if that would help.  I don't have an ethernet cable plugged in since I'm using wireless.  What do you mean uncheck network interfaces in network manager?  Is that in network-manager gnome?

---

### Post by teaker1s on 2007-03-14
for icon on panel(network-manager-gnome) to work 
on panel
System>Administration>Networking (network manager)
interfaces must be unchecked

is wireless light on?

---

### Post by blackhole82 on 2007-03-14
No the light does not appear to be on.  I got the card to work in Vista though.

---

### Post by teaker1s on 2007-03-14
basically your wireless is dead because driver isn't installed and loaded, vista is vista /ubuntu is linux and we need to see what chipset you have either Broadcom (BCM4306 rev3) or Broadcom (BCM4318 )
terminal type
```
lsusb
```
```
lspci
```
post output

---

### Post by fleshberkowski on 2007-03-14
i'm seeing a similiar problem with installing my wireless card (wpc54g)

i checked the chipset and it's broadcom bcm4318

i've been having a death of a time getting this wifi card installed. i ran through a couple of tutorials which had me install ndiswrapper and creating a folder with all the linksys info. and under "windows wireless drivers" it says that the following drivers are installed: lsbcmnds and lstinds, but underneath it, it says no hardware present. which i don't understand, because it's recognized in the device manager. but what's even stranger is that my internet wasn't working before without the wireless card in the computer. 

so.. it won't work w/ just the cable, or just the wifi card. it needs both to run (i'm assuming on the cable even though the network manager says my connection is "lo"

i'm new to ubuntu (less than a week) and totally lost. any info would be greatly appreciated. 

best

doug

---

