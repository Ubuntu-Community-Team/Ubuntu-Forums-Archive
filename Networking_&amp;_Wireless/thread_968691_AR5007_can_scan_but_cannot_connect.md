---
title: "AR5007 can scan but cannot connect"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by High Chief on 2008-11-02
Please help me there are so many threads on this but I am overwhelmed.

My wireless went out again so I figured I'd upgrade to 8.10(I read that my chipset would automatically work with it, it didn't). I have used madwifi and ndiswrapper with networkmanager and WICD. No joy. I downloaded and set the 64bit driver and now it shows up under iwconfig.

I can scan in WICD and terminal but when I try to connect in WICD(encrypted or not) nothing happens. It doesn't look like its even trying. 

What can I do?

Is it possible to connect with terminal?

---

### Post by High Chief on 2008-11-03
Bump ):P

---

### Post by jasonruk on 2008-11-03
Hi Chief

I have a similar problem, I have the ar5007 or ar242x and recently upgraded from 8.04 to 8.10 ubuntu and the wifi just dropped out.

It looks as though it's going to connect but never actually does and keeps asking for the password, does this sound like your problem?

I have a whole thread about the things I tried here [http://ubuntuforums.org/showthread.php?t=964166](http://ubuntuforums.org/showthread.php?t=964166)

But basically to get the wireless to work albeit not in the way I want I've used ndiswrapper and a windows driver.

Unload the driver and remove ndis from synaptic (please have other means of connection on the computer in question, this worked for me but might not for anyone else) reboot and reinstall ndis and then add the driver.  This is when it connected for me.

The down side.  Before shuting the computer down I have to repeat the process, removing the driver and ndis to boot up without them installed and then adding them after reboot.

Read the thread I added and see if any of that sounds like it might be similar.

Jason

---

### Post by eks on 2008-11-03
With Intrepid, you can use the native modules simply installing one package. More information here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Regarding the connection with wicd, I also had that problem (being able to see but not to connect). Which was simply the WPA_Supplicant was configured to use "madwifi" (the driver used on my 8.04 installation), changing it to "wext" and it connected to my WEP wifi. But if you are using an installed driver/module, try also others wpa supplicants.

---

### Post by High Chief on 2008-11-03
Jasonruk the problem sounds similar. I have tried most of the things you've tried on your thread except for the thing that worked for you. I am too stubborn to do all that everytime I turn on my laptop. :p

Eks I tried wext in wicd and that just results in an endless acquiring ip address...
Right now I am trying the ath5k driver. It shows up under hardware drivers but says "activated but not currently in use" :confused:

When I run "sudo lshw -C network" it gives me this... 

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

---

### Post by jasonruk on 2008-11-03
*-network UNCLAIMED 

This part here says that nothing is using your driver.

I think I've gotten round the uninstall each time of ndis by opening up and checking 
/etc/modules
 using a terminal

$ cat /etc/modules

I had more than one listing of ndiswrapper and so deleted one of them, it works fine now with the net5211 windows driver.

---

### Post by High Chief on 2008-11-03
I reloaded the net5211 driver and opened /etc/modules. It had ndiswrapper on there three times so I took two off. Nothing changed unfortunately. Wicd just says acquiring ip address.

Grrrrr

---

### Post by High Chief on 2008-11-03
I may be dreaming... I got it working! :guitar:

I enabled the ath5k driver and removed ndiswrapper from /etc/modules. Wext is set as the wpa supplicant in WICD. I am scared to reboot, but I will later and report back. Thanks jasonruk and eks for the help!

Edit sorry for the double post.

---

### Post by High Chief on 2008-11-03
ARRRRGGGGGGGGGG

My wireless is dead again. I have no idea what else to try. It seems like it would be easier to change the bloody chipset...

Edit: modprobe ath5k makes it work again. I am proud of myself I have learned alot.

---

### Post by eks on 2008-11-04
> **High Chief said:**
> Edit: modprobe ath5k makes it work again. I am proud of myself I have learned alot.

There is a very simple command to add a module to load automatically on boot, but I don't remember which is it, and I'm at work now.

It just added the module to a file anyway, something around /etc/mod*

You can also check if ath5k is not being blacklisted anywhere, maybe that's why you need to do modprobe ath5k after reboot.

---

