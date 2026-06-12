---
title: "[SOLVED] Atheros AR2413 Not Working after Suspend in Intrepid"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by guywithcable on 2008-11-15
I have a Toshiba M55-S135, which has an Atheros AR2413. The wireless quits working after I resume from a suspend. Anyone have any suggestions?

Here's the lspci -v results:
```
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Askey Computer Corp. Device 7094
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at b8000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath_pci
    Kernel modules: ath_pci
```Here's uname -a:
```
Linux hunter-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
```

---

### Post by dipaish on 2008-11-15
Try this one it may work ....

Atheros ath5k wireless driver not enabled by default

"The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. "

So inorder to enable type the following command in terminal mode 

deep@deep-laptop:~$ sudo apt-get install linux-backports-modules-intrepid-generic 


And disable any other wireless driver if enabled by going to system----administration--hardware drivers ---(in my case i need to disable support for atheros 802.11 wireless lan cards  )

Reboot and then enjoy ,,,you get ur wireless  working...

---

### Post by mcmax453 on 2008-11-15
> **guywithcable said:**
> I have a Toshiba M55-S135, which has an Atheros AR2413. The wireless quits working after I resume from a suspend. Anyone have any suggestions?

Here's the lspci -v results:
```
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Askey Computer Corp. Device 7094
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at b8000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath_pci
    Kernel modules: ath_pci
```Here's uname -a:
```
Linux hunter-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
```


I had the same issue, found the solution included in the "8.10 Release Notes"

"
Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. 
"

link:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Hope it works for you too :)

---

### Post by guywithcable on 2008-11-15
> **dipaish said:**
> So inorder to enable type the following command in terminal mode 

deep@deep-laptop:~$ sudo apt-get install linux-backports-modules-intrepid-generic 


And disable any other wireless driver if enabled by going to system----administration--hardware drivers ---(in my case i need to disable support for atheros 802.11 wireless lan cards  )

Reboot and then enjoy ,,,you get ur wireless  working...

That did the trick! :)

> **mcmax453 said:**
> I had the same issue, found the solution included in the "8.10 Release Notes"

"
Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. 
"

link:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Hope it works for you too :)

Is there any advantage to using this method over the one given above?

---

### Post by bryce4president on 2010-01-12
I tried to issue the apt-get install command but it couldn't find the backports... is there a specific software universe I need for this?

---

### Post by guywithcable on 2010-01-13
> **bryce4president said:**
> I tried to issue the apt-get install command but it couldn't find the backports... is there a specific software universe I need for this?

According to your info, you're using Karmic.

---

### Post by bryce4president on 2010-01-14
does that mean that I can't use the version from the intrepid backports?

---

### Post by guywithcable on 2010-01-15
> **bryce4president said:**
> does that mean that I can't use the version from the intrepid backports?

Yes, try linux-backports-modules-karmic-generic

or linux-backports-modules-wireless-karmic-generic

---

### Post by bryce4president on 2010-01-23
so apparently I must not have had the madwifi installed yet or something.  I reran the make on it and then did  a  $sudo modprobe ath5k

After that I did $sudo gedit /etc/modules 

This allows the driver to boot at start up.
It work as far as seeing networks, I just need to get it to connect to my WPA encryption now.

It prompts me for the password, but when I put it in it won't connect.

---

### Post by DataMatrix on 2010-02-22
> **mcmax453 said:**
> I had the same issue, found the solution included in the "8.10 Release Notes"

"
Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. 
"

link:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Hope it works for you too :)

Thanks a lot, I had the same issue with AR928x (ath9k) on 9.10, it didn't work after suspend. I've created /etc/pm/config.d/01wifi with SUSPEND_MODULES=ath_pci
and now wifi works fine after suspend :D

---

### Post by borikru on 2010-10-31
> **DataMatrix said:**
> Thanks a lot, I had the same issue with AR928x (ath9k) on 9.10, it didn't work after suspend. I've created /etc/pm/config.d/01wifi with SUSPEND_MODULES=ath_pci
and now wifi works fine after suspend :D

Thanks DataMatrix,
This worked for me with Maverick on Acer Aspire 5742 and Acer Aspire 5745 (both have Atheros AR928x), added  "SUSPEND_MODULES=ath" to /etc/pm/config.d/01wifi

---

