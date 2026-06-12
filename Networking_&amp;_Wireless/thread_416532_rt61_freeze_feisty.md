---
title: "rt61 freeze feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by BXCracer on 2007-04-21
Hi to all ! 
yesterday i installed kubuntu 7.04 and tryed to get my rt61 card to work . i used network manager to connect to my wirelles network that uses 64-bit wep and when its connecting my system sudenly freezes . later i tryed to get my card working with konsole i used iwpriv command and when i get my ip from dhcp my computer freezes again. could you tell me whats wrong and how to solve it ?

---

### Post by Ynem on 2007-04-21
I got these errors in the system logbook after being connected (and being able to surf) for 6 minutes.

Apr 21 12:44:23 LaptopYen2 kernel: [   89.868000] ondemand governor failed to load due to too long transition latency
Apr 21 12:44:27 LaptopYen2 gconfd (yen-4930): Resolved address "xml:readwrite:/home/yen/.gconf" to a writable configuration source at position 0
Apr 21 12:44:29 LaptopYen2 NetworkManager: <information>^IUpdating allowed wireless network lists. 
Apr 21 12:44:29 LaptopYen2 NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

could check wich errors you got? (system->management->systemlogbook)

Y

---

### Post by kashms on 2007-04-21
I think the RT61 driver has a problem SMP in the generic kernel. I changed to the i386 kernel and my system was no longer freezing.

---

### Post by Ynem on 2007-04-21
I'm relatively new to ubuntu, so can you explain how I change to a different kernel?

Thnx

Y

---

### Post by Ynem on 2007-04-22
since I have installed 7.04 with the alternate i386 cd rom I suppose I allready have that specific kernel...
Other solutions?

Y

---

### Post by TDsai on 2007-04-24
same issue here. Fresh installed FF, I disabled NetworkManager by sudo killall NetworkManager but it still freezes after few minutes.

lspci:
Network controller: Ralink RT2600 802.11 MIMO

I want to try different driver but don't know how to uninstall the default driver that came with Fiesty.

---

### Post by TDsai on 2007-04-24
amazing! kashms is right! upgrade to latest i386 kernel then the freeze is gone.

the easiest way to upgrade is to connect your pc using cables first make sure ur connected to the internet then open System > Administration >Synaptic, click reload, then click search and look for linux-image, right click and install the latest linux-image 386. 

now... on to making rt61 work with fiesty! thanks!

---

### Post by Ynem on 2007-04-24
Do you have to remove/completely remove the generic kernel?
Wil the card work afterwards?
Y

---

### Post by Ynem on 2007-04-24
Hi,

thanks for the advice!!!! installed linux-image-i386 and cards works fine, without freezing the system.

Y

---

### Post by QwUo173Hy on 2007-05-26
Just a quickie - what will the effect of this kernel be for a Core 2 Duo processor? Will just one core run or will both?

Thanks,
Jarlath

---

### Post by vergeh on 2007-09-12
I have the EXACT same issue as this. However, I don't have the benefit of a wired connection, so I've got to find a way to update my kernel offline. How would I go about doing that? Also, I've got an x86 processor, but I'm using linux-image-generic insteal of linux-image-386. Should I change that as well?

---

