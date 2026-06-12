---
title: "Ethernet, wireless not detecting , new laptop"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-07-28
Hi
I just persuaded my friend to try out ubuntu on his [Dell Inspiron]("http://www1.ap.dell.com/in/en/home/notebooks/inspiron-14r/pd.aspx?refid=inspiron-14r&s=dhs&cs=indhs1&%7Eoid=in%7Een%7E78002%7Einspn_14r_t540510in8%7E%7E") . But his laptop shows no sign of detecting the ethernet internet connection, let alone the wireless. There is no problem in the net connection, I am using the same connection to post this right now.
Output of lspci is

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

### Post by jjcylk on 2010-07-28
I have had to go to SYSTEM>Preference> Network Settings & >Network Proxies and make sure it was set up to see the ethernet connection. Then u need to download all the updates, over 230. It will have a wireless update for u.

---

### Post by jfreak_ on 2010-07-28
The solution is probably in this post [http://ubuntuforums.org/showthread.php?p=9449490 ]("http://ubuntuforums.org/showthread.php?p=9449490") as the output to all commands is the same. But I need a net connection to get the build-essential package which I don't have on that system obviously because the ethernet and wireless needs to get solved. Any ideas?

---

### Post by Darkness Des on 2010-07-28
Do a little google search to get the .deb package and all of it's dependencies.

---

### Post by jjcylk on 2010-07-28
i just did a search on others who might have had this issue & there seems to be a few. Go up tot he top & do a search on "ethernet missing" and read some of the other post. there are a bunch of ideas & solutions that might help you. 

I would pst them here but it might be redundant

---

### Post by jfreak_ on 2010-07-29
Update:
Managed to install build-essential as required by link in post 3 by copying the .deb's from my var/cache to his laptop. Tried to install the compat-wireless drivers as required but apparantly only the bluetooth drivers are getting installed, some error with the ethernet stuff. Forgot to take down details but will uninstall and try again after I come from college and post the error report.

---

### Post by jfreak_ on 2010-08-21
Well basically i found out that mandriva has the atheros ethernet drivers pre-installed. why doesn't ubuntu include the same? 
as a result of which nobody who is buying new dell systems here can install ubuntu , everyone is moving to mandriva.

---

