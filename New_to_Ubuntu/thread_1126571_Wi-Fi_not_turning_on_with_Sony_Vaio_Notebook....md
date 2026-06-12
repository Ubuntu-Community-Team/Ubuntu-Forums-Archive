---
title: "Wi-Fi not turning on with Sony Vaio Notebook..."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-15
Now, EVERYTHING else on my notebook works. USB ports, sound, graphics card, etc. I just went to turn on my wi-fi (it's a small switch on the front of the notebook), and it won't turn on.

Do I have to do something special to turn Wi-Fi on in Ubuntu, or are my computer's wi-fi components just not supported?

The notebook is a Sony Vaio VGN-NR498E/W.

---

### Post by SpenceMakesSense on 2009-04-15
Try installing the windows driver for it via ndiswrapper or better yet ndisgtk. 
ndisgtk is easier to use too ```
sudo apt-get install ndisgtk
```

---

### Post by Noise... on 2009-04-15
> **SpenceMakesSense said:**
> Try installing the windows driver for it via ndiswrapper or better yet ndisgtk. 
ndisgtk is easier to use too ```
sudo apt-get install ndisgtk
```


Thanks. Any idea how large that download is? I'm at 4.8GB usage of 5GB bandwidth usage for the month, and REALLY don't want to go over.

---

### Post by LowSky on 2009-04-15
Go to System Admin> Restricted dirvers

see if there isn't a restricted driver that is not being used. if there is check it on... then your all set otherwsie follow my next idea

open a terminal (it under applications)
type
```
lspci
```

and paste back the info

---

### Post by Noise... on 2009-04-15
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

There's the output from lspci.

I checked system>administration, and didn't see anything for restricted drivers?

---

### Post by LowSky on 2009-04-15
Intel Corporation PRO/Wireless 4965 AG 

 this card should just work, leave wifi switch in on psoition and reboot, does wifi come on then?

---

### Post by Noise... on 2009-04-15
> **LowSky said:**
> Intel Corporation PRO/Wireless 4965 AG 

 this card should just work, leave wifi switch in on psoition and reboot, does wifi come on then?

Sorry for the delay in response.

I did a reboot, and the light is still off. 

I'm not on a network - there's no network to connect to. I'm trying to set up an ad-hoc network for my iPod Touch to connect to so that I can SSH into it.

Maybe I'm just going about this the wrong way? 

I checked, and in Windows when I flip the switch on, the light pops right on.

---

### Post by Noise... on 2009-04-15
Bump. 

Is there something I need to configure to make it work? Or, do I need a wireless network to work with first?

---

### Post by SpenceMakesSense on 2009-04-15
ndisgtk shouldnt be large at all. Dont worry it should be fine. After that go to System-admin-windows driver(something like ) and it should be pretty self explanatory. Just makes you have the windows drivers to the wireless card

---

### Post by Noise... on 2009-04-16
> **SpenceMakesSense said:**
> ndisgtk shouldnt be large at all. Dont worry it should be fine. After that go to System-admin-windows driver(something like ) and it should be pretty self explanatory. Just makes you have the windows drivers to the wireless card

So I would just need to go download the drivers from Sony? I looked around, but couldn't find them in the windows partition.

---

### Post by SpenceMakesSense on 2009-04-16
The model of your wireless card should be
Intel Corporation PRO/Wireless 4965 AG 
look for drivers for that on google.

---

### Post by SpenceMakesSense on 2009-04-16
[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/17228/eng/12.2.0.0_X_Drivers.zip&agr=N&ProductID=2753&DwnldId=17228&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/17228/eng/12.2.0.0_X_Drivers.zip&agr=N&ProductID=2753&DwnldId=17228&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

Go there for the drivers for your card(if that's not right like I said double check on google)

After you get those go to System-admin-windows wireless drivers

Select install new driver and find the correct *.inf* file(there's two from what I saw and im not totally sure which ones right)

If done correctly look in the windows wireless drivers it should say hardware detected. If it says undetected (or something of the sorts) then try a different driver. Then once installed go to the network icon in your panel or go to system-preferences-network configuration and and configure it to work. 

Any problems feel free to ask :D

---

### Post by Noise... on 2009-04-16
> **SpenceMakesSense said:**
> [http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/17228/eng/12.2.0.0_X_Drivers.zip&agr=N&ProductID=2753&DwnldId=17228&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/17228/eng/12.2.0.0_X_Drivers.zip&agr=N&ProductID=2753&DwnldId=17228&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

Go there for the drivers for your card(if that's not right like I said double check on google)

After you get those go to System-admin-windows wireless drivers

Select install new driver and find the correct *.inf* file(there's two from what I saw and im not totally sure which ones right)

If done correctly look in the windows wireless drivers it should say hardware detected. If it says undetected (or something of the sorts) then try a different driver. Then once installed go to the network icon in your panel or go to system-preferences-network configuration and and configure it to work. 

Any problems feel free to ask :D

Hm. I don't even HAVE network configuration in preferences. 

I have a big update that needs downloaded (my copy of Ubuntu Studio is early 8.04). Before going any further I think I need to get the updates.

---

### Post by SpenceMakesSense on 2009-04-17
Good plan. do that and get back to me

---

### Post by Noise... on 2009-04-17
Ok. I'm now fully updated, and I installed the windows driver that recognizes the hardware. 

However, still no wi-fi light. Could wi-fi actually be on, but the light just isn't? I don't have a wi-fi network to connect to to test it, but I will be taking my computer out tomorrow while I'm in town, so I will need wi-fi for hotspots and such. 

Maybe it's just not configured? What should I do next?

---

### Post by Noise... on 2009-04-17
Bump.

---

