---
title: "Wireless adapter not found. Asus P550c Laptop Mediatek (MT7630e)"
date: 2018-11-12
forum: Networking &amp; Wireless
---

### Post by igotsanevo4g on 2018-11-12
Fresh install of 18.04, and no wireless like many others. 
I got it to work using this guide [https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working](https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working) but it barely stays connected, drops out a lot and is generally not working well enough at all. 

Is there a more current solution? Very sad if i cant use ubuntu on this laptop because of wifi issues :(
Heres some lspci output, if there is another output youd like to see just let me know as im a linux noob still and am not sure of other commands.

I have it connected to ethernet currently in order to fix the wifi, if that helps. Bluetooth doesn't work either but one problem at a time i suppose.

Oh and i found this [https://github.com/lwfinger/mt7630](https://github.com/lwfinger/mt7630) but im not sure what to make of it. Readme says it may not work with newer kernels or something? 

[http://paste.ubuntu.com/p/BRQPmXBsQp/](http://paste.ubuntu.com/p/BRQPmXBsQp/)
 

> [FONT=Arial]ubuntu@ubuntupad:~$ lspci[/FONT]
[FONT=Arial]00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)[/FONT]
[FONT=Arial]00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)[/FONT]
[FONT=Arial]00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)[/FONT]
[FONT=Arial]00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)[/FONT]
[FONT=Arial]00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)[/FONT]
[FONT=Arial]00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)[/FONT]
[FONT=Arial]00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)[/FONT]
[FONT=Arial]00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)[/FONT]
[FONT=Arial]00:1c.3 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 (rev c4)[/FONT]
[FONT=Arial]00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)[/FONT]
[FONT=Arial]00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)[/FONT]
[FONT=Arial]00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)[/FONT]
[FONT=Arial]00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)[/FONT]
[FONT=Arial]02:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter[/FONT]
[FONT=Arial]03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader (rev 01)[/FONT]
[FONT=Arial]03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)[/FONT]
[FONT=Arial]ubuntu@ubuntupad:~$[/FONT]

---

### Post by jeremy31 on 2018-11-12
See the wireless script link in my signature and post results

---

### Post by igotsanevo4g on 2018-11-12
Sorry about that, missed the sticky. doh. Heres the output

[https://raw.githubusercontent.com/ubuntuforums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/ubuntuforums/wireless-info/master/wireless-info)

It did update somethings as well but didnt fix the issue.

---

### Post by jeremy31 on 2018-11-12
That is the script, not the output

---

### Post by igotsanevo4g on 2018-11-12
[http://paste.ubuntu.com/p/BRQPmXBsQp/](http://paste.ubuntu.com/p/BRQPmXBsQp/)

Whoops!

---

### Post by igotsanevo4g on 2018-11-12
Would i be better off reinstalling the driver from [https://github.com/neurobin/MT7630E](https://github.com/neurobin/MT7630E) and trying to solve the connection issues from there instead?

---

