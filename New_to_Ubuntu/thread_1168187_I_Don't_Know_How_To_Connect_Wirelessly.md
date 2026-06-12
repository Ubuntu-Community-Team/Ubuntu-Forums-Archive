---
title: "I Don't Know How To Connect Wirelessly"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by ConnorMarc on 2009-05-23
Guys,

I just installed ubuntu 9.04 on my Toshiba Satellite L305D-S5934 laptop.
250G HDm AMD Turion X2 processor, ATI Radeon Graphics that should be all the pertinent data.

Anyway, like I was saying, just installed Ubuntu and wiped over my Vista (good riddance) and I thought it would just detect everything as Windows did. Apparently not, so what do I need to do to get myself online with this thing?

Remember, i'm completely new to this,...so be gentle.

Sincerely,
marc

---

### Post by 67GTA on 2009-05-23
It depends on your wireless card. If it is supported out of the box, you will be able to click on the network manager icon on the panel and select a wireless signal to connect to if one is available. If it is not supported out of the box, then we can probably help you get it going. Open a terminal: Applications>Accessories>Terminal. Copy and paste this command into the terminal and hit enter. ```
lspci -vk
``` Then post the output of that here so we can see what wireless card you have.

---

### Post by duanedesign on 2009-05-23
L-click on the Network Manager icon in the Gnome Panel (upper right hand side of screen). You should see a list of available networks. Click the radio button next to the connection you want to establish. If you are connecting to a network for the first time, security details may be needed. If so, a dialog box will open, fill in appropriate details. In most cases the security type will be detected automatically. If not, select the security type from the Wireless Security drop-down box.Enter the password and click connect.

If these options are unavailable:
1.Ensure that your wireless device is turned on.
I usually achieve this by R-click on the Network Manager icon in the top Gnome Panel. There should be "Enable Networking" and "Enable Wireless" make sure these are checked. Additionally, many wireless network devices can be turned on or off. Check to see if there is a hardware switch, some devices can be switched off from Windows and may need to be turned back on from Windows.

If you still dont have any connections showing up in the Network manager drop down menu check to see if your device is recognized.
Open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command
```
sudo lshw -C network
```

Mine looks like this:
```
[COLOR="Red"]*-network ENABLED[/COLOR]
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:20:3d:75:49:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

```

You should see an output, along with the words [COLOR="Red"]"CLAIMED, UNCLAIMED, ENABLED or DISABLED"[/COLOR]

What does yours say?

---

