---
title: "Toshiba A210-12U Wireless!"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by bunny_basher on 2008-06-09
I believe that the wireless card is an Atheros AR5007EG.

When i go into the networking manager, there is nothing about wireless:confused: 

Can anybody help me get online with my laptop?

Cheers,
Marcus

---

### Post by rlzyoner on 2008-06-09
Check that you have installed the necessary drivers for your card.

Also,

Post the output of *iwconfig* and *iwconfig*

Now, System -> Administration -> Networking
Can you see a wireless connection here.

---

### Post by bunny_basher on 2008-06-09
Cant see the Wireless connection anywhere!

results of the iwconfig dont look good :p

lo          no wireless extensions

eth0        no wireless extensions

HELP!

---

### Post by rlzyoner on 2008-06-09
ok so try 

sudo ifconfig eth0 up

This should enable the eth0 adaptor, sometimes, the wireless adaptor can be called eth0 or something similar.

Having activated this device, try both 
ifconfig and iwconfig again.

Type
iwlist scanning 
at a terminal to scan for wireless networks in range

---

### Post by bunny_basher on 2008-06-09
Done that, iwconfig is the same :(

---

### Post by rlzyoner on 2008-06-09
Chances are this is not the case, but just to be sure.
Can you confirm that there isn't a wireless switch (or could be a keystroke combo) somewhere on the device that may be turned off.

Run 
lspci -nn (This should tell us the card type)
lshw -C network 

Advise / Post the output

---

### Post by bunny_basher on 2008-06-09
The wireless switch is ON :)

jemima@Jemima-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
1a:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
1a:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
1a:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
1a:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

---

### Post by bunny_basher on 2008-06-09
jemima@Jemima-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:3e:cf:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by rlzyoner on 2008-06-09
You may need to install the madwifi drivers.

Check their site for more info

[http://madwifi.org/](http://madwifi.org/)

Hope that helps

---

### Post by Jeztastic on 2008-06-09
I have the exact same laptop, and it works fine. 

You need to use ndiswrapers. This basically means you need to install the windows drivers, and then add another program that tells linux how to use them.

If you search the forums for your card there are numerous instructions on different ways to do this. Have you had a look?

---

### Post by bunny_basher on 2008-06-09
Cant install madwifi because i get this...

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ?
r
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_xauth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_tkip.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_scan_sta.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_wep.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/ath_rate_onoe.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/ath_rate_amrr.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_ccmp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_scan_ap.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/ath_rate_sample.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/ath_pci.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/ath_hal.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.20-1.2948.fc6/extra/madwifi/wlan_acl.ko': Permission denied
make: *** [install-modules] Error 1

---

### Post by rlzyoner on 2008-06-09
Are you running the installation command as root (sudo) ?

---

### Post by bunny_basher on 2008-06-09
AFAIK :p im following the instructions on the madwifi website.

What do I have to do to do this?

---

### Post by rlzyoner on 2008-06-09
Now I may not have been viewing the same page as you but from their instructions, they seem to assume that you are running the commands as root.
try prepending sudo before them - just a suggestion though

---

### Post by bunny_basher on 2008-06-09
Tried that, nothing happens now when i do this...

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ?
r

---

### Post by rlzyoner on 2008-06-09
You should then proceed to remove the older modules.
You can do this by tying r at the above prompt.

Gotta split, let me know if that works for you..

---

### Post by bunny_basher on 2008-06-09
I did type r :p and nothing at all happened!

---

### Post by rlzyoner on 2008-06-09
Ok maybe if you click applications-> add/remove

Remove any existing madwifi drivers and then install the new ones via the terminal

---

### Post by lisati on 2008-06-09
> **rlzyoner said:**
> 
Can you confirm that there isn't a wireless switch (or could be a keystroke combo) somewhere on the device that may be turned off.


Jumping in here with a couple of thoughts:

I have one of the A100 range of laptops and have successfully set it up with Wireless.


[LIST=1]
[*]There is a switch on the model I use, it's on the right, just in front of two of the USB ports, a light goes on when it is switched on.
[*]The wifi setup on my machine was set up by Ubuntu 7.04 to be ATH0
[/LIST]
Hope these help.....

---

