---
title: "[SOLVED] Compaq Presario f700 wireless not working"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by tuong2000 on 2008-07-04
Hello,

I am a total beginner to Ubuntu and recently bought a laptop and threw Ubuntu 8.04 on it.

Everything seems to work fine except for the wireless card.  Someone please help because Ubuntu is useless to me on a laptop if I cant get the wireless working.  I want to give Ubuntu a chance... 

thanks,

-newb

---

### Post by alfredska on 2008-07-04
When you left click on the NetworkManager icon in the right hand corner, do any networks appear?

If yes, what happens when you try to connect to one of them?

If no, can you report a few command outputs please?

```
ifconfig
iwconfig
```

and if you are using an intel wireless adapter,
```
lsmod | grep iwl
```

if not intel, what wireless adapter are you using?

---

### Post by tuong2000 on 2008-07-04
No networks appear when i click on Network Manager.

Here is the output for the code...

```
chris@Renovatio:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:ef:1f:fc  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:feef:1ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:332135656 (316.7 MB)  TX bytes:22641723 (21.5 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13976 (13.6 KB)  TX bytes:13976 (13.6 KB)
```

```

chris@Renovatio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

I tried the code for the intel card and got nothing.  I googled how to find out my card and this was the output...

```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I read in one of these post somewhere that Ubuntu is recognizing this card wrong...  Supposedly it is actually...

```
AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

I hope all this makes sense to you...

if you need anything else let me know.

Thank you for your help.

---

### Post by alfredska on 2008-07-04
> **tuong2000 said:**
> I tried the code for the intel card and got nothing.  I googled how to find out my card and this was the output...

```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I read in one of these post somewhere that Ubuntu is recognizing this card wrong...  Supposedly it is actually...

```
AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```


I'm assuming the first code line you listed was a result of ```
lspci | grep Atheros
```

In any case, finding out for sure which wireless adapter you have will be useful.  Some other users might know more advanced queries to probe the hardware device name, I only know lspci.  My method usually involves opening up the compartment containing the wireless adapter and reading the model number off the card.

If you have a 242x series adapter, you should be able to enable proprietary drivers for it by going to System -> Administration -> Hardware Drivers.  (I'd suggest first connecting your laptop by Ethernet cable to the internet, and downloading all updates)

If you do have an AR500x series adapter, you will need the latest trunk version of madwifi.  [Here]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008") is a guide on checking out experimental madwifi drivers, and [here]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") is a guide on manual installation of madwifi drivers.

---

### Post by tuong2000 on 2008-07-04
I got it to work!!!!!!!!!!!!!!!

I kept reading on through the forum and found this reponse from someone...

> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

I followed this step by step and after the reboot i had wireless networks I could connect to!!!!

Now i just need to understand what I did and I will be on my way to becoming a real Linux user and not just a poser!

Thank you for you help alfredska, its good to know there are people out there that are willing to lend a hand.

Oh, and yes that is the code I used to find my wireless card.

Thanks again!!!!

---

