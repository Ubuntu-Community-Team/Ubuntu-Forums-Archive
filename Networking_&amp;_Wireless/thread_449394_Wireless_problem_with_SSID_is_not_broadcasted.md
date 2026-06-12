---
title: "Wireless problem with SSID is not broadcasted"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by bence8810 on 2007-05-20
Hi

I have posted a thread a few days ago about my card not working properly, but I found out what the problem was, and I dont think its with my card.

I have an Atheros 5212 based card, and it uses the MadWiFi driver. 

When the router is set to not broadcast the SSID, it wouldnt connect, only raphsodically. Now, that I enabled the SSID broadcast, it connects with no problem. I am using 128bit encryption WEP in shared mode, MAC is filtered on the router side.

Any ideas? I dont like broadcasting my SSID.

Thanks

Ben

---

### Post by johntelthorst on 2007-05-20
This seems to be a known issue.  I have to use WPA_supplicant to connect to non-SSID broadcasted networks, hopefully this issue will be fixed.

---

### Post by bence8810 on 2007-05-20
Hi

What is exactly the difference between using NetworkManager and or wpa-supplicant? I thought NetworkManager uses Wpa-supplicant to get the job done, this isnt true?

What file do you configure for WPA-supplicant with the profiles, and how to you kill Network Manager? Just change the Sxx entry to Kxx in /etc/rc.x/ ?

Thanks

Ben

---

### Post by tl3000 on 2007-05-20
> **bence8810 said:**
> When the router is set to not broadcast the SSID, it wouldnt connect, only raphsodically. Now, that I enabled the SSID broadcast, it connects with no problem. I am using 128bit encryption WEP in shared mode, MAC is filtered on the router side.

Any ideas? I dont like broadcasting my SSID.

No idea about your wireless card but "hiding" your SSID is simply useless and just a false sense of security!  [FYI...]("http://blogs.zdnet.com/Ou/index.php?p=43")

---

### Post by tturrisi on 2007-05-20
Disable ssid broadcast w/ wep or wpa is like putting a jar of candy on a shelf, the young child can still see it but he just can't reach it!  If the child knows how to use kismet & aircrack-ng he'll get the candy in less than an hour too.

---

### Post by AndyPopely on 2007-05-23
I'm on Feisty Fawn using a Netgear WPN511 wireless adapter card with an Atheros AR5212 chipset.

I couldn't get a wireless connection with SSID broadcast disabled on my router and when I was connected with the SSID broadcast enabled the signal strength was at best 70-75% with the wireless adapter card right next to the router.

The disabled SSID broadcast problem and the poor signal strength problem were both caused by the system using the ATH_PCI driver and not the Ndiswrapper driver which I had installed.

This was confirmed by going to the Device Manager (System -> Preferences -> Hardware Information) then selecting the AR5212 entry in the Devices column. In the right hand column select the Advanced tab and the Info.Linux.Driver value should say ndiswrapper and not ATH_PCI.

What I did was  ......

1) Added the following entries to /etc/modprobe.d/blacklist
    blacklist ath_hal
    blacklist ath_pci
    blacklist ath_rate_sample
2) Installed the 1.44 version of Ndiswrapper
3) Ensured I had the latest windows XP driver for the wireless adapter card

---

### Post by tturrisi on 2007-05-23
> **AndyPopely said:**
> I'm on Feisty Fawn using a Netgear WPN511 wireless adapter card with an Atheros AR5212 chipset.

I couldn't get a wireless connection with SSID broadcast disabled on my router and when I was connected with the SSID broadcast enabled the signal strength was at best 70-75% with the wireless adapter card right next to the router.

The disabled SSID broadcast problem and the poor signal strength problem were both caused by the system using the ATH_PCI driver and not the Ndiswrapper driver which I had installed.

This was confirmed by going to the Device Manager (System -> Preferences -> Hardware Information) then selecting the AR5212 entry in the Devices column. In the right hand column select the Advanced tab and the Info.Linux.Driver value should say ndiswrapper and not ATH_PCI.

What I did was  ......

1) Added the following entries to /etc/modprobe.d/blacklist
    blacklist ath_hal
    blacklist ath_pci
    blacklist ath_rate_sample
2) Installed the 1.44 version of Ndiswrapper
3) Ensured I had the latest windows XP driver for the wireless adapter card
You can't base anything on what signal strength is reported.  If a laptop, walk away from the ap until the connection drops, do same using ndiswrapper and I'll bet they both drop at around the same place.

---

### Post by bence8810 on 2007-05-24
Hi

As I am not with my laptop now, I cannot check, but you are suggesting the the wrapper takes care of the driver, and not ath_pci? 

If thats true, I would prefer to kill the wrapper, and just go with the MadWiFi, as I have MadWiFi on another laptop of mine with Debian working on an Atheros Chipset, and it works like a treat.

How do I go about killing the Ndiswrapper?

Thanks

Ben

p.s. Just re-read your comment, and I think I misunderstood it. So basically you had the ath_pci taking care of it, but you wanted Ndiswrapper instead? Then I just keep it the way it is now.

By the way, why did my laptop show the warning that its using a Non-default or something like that Driver for the Wifi, one that cannot be easily modified? Was it referring to MadWiFi, or maybe it was referring to Ndiswrapper? If so, the wrapper might be enabled for me now? Sorry I am completely confused....

---

### Post by bence8810 on 2007-05-24
Hi

I came home and checked my laptop, and the info.linux.driver for me says ath_pci

How come still I have the following in System -> Administration - > Restricted Drivers Manager

Atheros Hardware Access Layer (HAL) - In USE

I just dont understand why is this a restricted driver. It also says the following in there:

In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported. Because the software is proprietary, it cannot easily be changed to fix any further problems.

Thanks for any hints, and the problem is still outstanding with the SSID broadcast. I know its not a security issue, but I dont have hackers around me, but still dont like my neighbours to see I have WLAN.

Thanks

Ben

---

### Post by tturrisi on 2007-05-24
try using disable ssid broadcast and open mode instead of closed.

---

### Post by bence8810 on 2007-05-25
Hi

I tried that before, and didnt work. 

I completely removed all encryption and security once, and just left the Broadcast off for testing, and it wasnt working.

It is definetally a problem with the broadcast thing.

What is the linux-restricted-modules? It was just updated on the system this morning.

Thanks

Ben

---

### Post by tturrisi on 2007-05-25
> What is the linux-restricted-modules? [http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-386](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-386)

---

### Post by bence8810 on 2007-05-25
Thanks

I found this at the link:

```
This package provides restricted modules for Linux version 2.6.20 on 386. Currently the following modules are included: 

 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)
These modules are "restricted" because they are not available under a completely Free licence. 


```

What If I remove this, and Install the MadWiFi driver manually from here?

[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

Is the Restricted thing needed? I am new to Ubuntu, and have been using MadWiFi in Debian without any need for this module.

Thanks

Ben

---

### Post by tturrisi on 2007-05-25
[http://ubuntuforums.org/showthread.php?p=2721298#post2721298](http://ubuntuforums.org/showthread.php?p=2721298#post2721298)

---

### Post by bence8810 on 2007-05-26
Hi

Very interesting post indeed. If I go down that road with the installation, what will I gain?

What exactly is that patch from aircrack-ng do?

Since we are touching the topic can I use Kismet with Atheros chipset, so any other Wireless sniffers, crackers?

Thanks

Ben

---

### Post by tturrisi on 2007-05-26
What you would gain:
1. latest madwifi drivers.
2. ability to use aircrack-ng
3. best performance possible fot atheros chipset adapters.

Yes, kismet works well with madwifi, but kismet will NOT work with any ndiswrapper windows drivers.

---

### Post by bence8810 on 2007-05-26
THanks

Could you further define option number 3?

I do have the latest madwifi drivers, 0.9.3, but they are with the Restricted package. Am I better to get rid of it and reinstall it manually?

Thanks

Ben

---

### Post by tturrisi on 2007-05-26
> **bence8810 said:**
> THanks

Could you further define option number 3?

I do have the latest madwifi drivers, 0.9.3, but they are with the Restricted package. Am I better to get rid of it and reinstall it manually?

Thanks

Ben
Not unless you plan of using tools like aircrack-ng (crack secured wlans and get the access key).
The madwifi driver performs as well as or better than ndiswrapper w/ windows atheros drivers.  It's just that when linux reports the signal %, it's not accurate because the madwifi driver itself determines what signal % should be displayed, but the signal is very good.  I'm 6' away from mt AP and the signals is reported as 84% and in windows it's reported as 100%.  the windows driver & madwifi use different math formulas for calculating that %, both are innacurate.

---

### Post by bence8810 on 2007-05-28
Hi

My problem after all isnt with what the driver reports in terms of signal, but with the SSID broadcast being disabled, and the laptop isnt able to connect to the WLAN.

My questions is basically the following, and plainly because I dont understand the linux restricted modules.

As far as I can see, my atheros card is driven by the ath_pci currently, which is the madwifi driver. It is at version 0.9.3 which is latest. With ubuntu, this madwifi driver is brought by the linux restricted modules.

If I uninstall the Restricted Modules, and re-install the madwifi 0.9.3 by itself, without the restricted package, will that in any ways behave differently, and thus may fix the problem with the SSID broadcast?

Thanks

Ben

---

### Post by tturrisi on 2007-05-28
> **bence8810 said:**
> Hi

My problem after all isnt with what the driver reports in terms of signal, but with the SSID broadcast being disabled, and the laptop isnt able to connect to the WLAN.

My questions is basically the following, and plainly because I dont understand the linux restricted modules.

As far as I can see, my atheros card is driven by the ath_pci currently, which is the madwifi driver. It is at version 0.9.3 which is latest. With ubuntu, this madwifi driver is brought by the linux restricted modules.

If I uninstall the Restricted Modules, and re-install the madwifi 0.9.3 by itself, without the restricted package, will that in any ways behave differently, and thus may fix the problem with the SSID broadcast?

Thanks

Ben
Not necessisarily!
Best to keep the restricted-module.
But even if ssid broadcast is disabled you should still be able to connect.
Post the entry for your wlan in /etc/network/interfaces.

---

### Post by bence8810 on 2007-05-28
Hi

My entry is crippled by the Network Manager I believe, on other laptops that I use the manual configuration, and not network manager, I have many more things.

Here it is:

```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

Ben

---

### Post by tturrisi on 2007-05-28
Oh, I see.
I never use Network Manager, just the inbuilt net-admin in Gnome which is a gui for /etc/network/interfaces.

---

### Post by bence8810 on 2007-05-28
Oh, so that might be it, if you have no problem with disabled SSID broadcast networks. It very well may be the Network Manager messing things up.

Anyways, I like it as it keeps track of all my connections, so until a fix is supplied, I just keep my SSID broadcasted.

Cheers

Ben

---

### Post by tturrisi on 2007-05-28
I just keep all my wlans I use in /etc/network/interfaces file & comment-uncomment as needed.  It's fail safe.

---

