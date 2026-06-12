---
title: "wifi times out after every five minutes only in ubuntu 20.04 works fine in windows."
date: 2020-11-03
forum: Networking &amp; Wireless
---

### Post by saaim on 2020-11-03
[SIZE=2]I tried setting power management off 
setting the [FONT=Consolas]wifi.powersave = 2 
disabling ipv6 settings 
changing router channel from auto to 9
I also tried reinstalling ubuntu and updating kernals this seems to be a common problem with [/FONT]QCA9377.[/SIZE][FONT=Consolas]
[/FONT]```
[COLOR=#242729][FONT=Consolas]lspci -knn | grep Net -A3[/FONT][/COLOR]
```

```
01:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Dell QCA9377 802.11ac Wireless Network Adapter [1028:1810]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)

```

---

### Post by morrownr on 2020-11-03
I don't have this network adapter but I will give what pops to mind:

- I would not use channel 9. Recommend you use only channels 1, 6, or 11. Also recommend you use a Wifi Analyzer app on a smart phone to determine which of those channels is least congested.

- The wifi APs and routers I am familiar with have a Power Save setting. You could toggle that to see if it makes a difference.

- Recommend setting a fixed 20 MHz bandwidth for 2.4G.

- If your Power Level is set to 100% and you are close to the router, you could try turning the power level down.

- Recommend Security be set to WPA-2 Personal with AES.

- Recommend you try different Mode settings such as: 802.11n only, 802.11 g only, or mixed to see what happens.

- Look at and research the other wifi settings that your router has and test the settings.

- Recommend you use "Forget Connection" for all current interfaces so you can start fresh each time you changes settings in the router.

Good luck.

---

### Post by praseodym on 2020-11-03
Lets see
```

iwconfig
ifconfig -a
iwlict chan
sudo iwlist scan
dmesg | egrep 'ath|firm|country'
```
Which country do you live?

---

### Post by fortifor44 on 2021-10-13
hi Saaim, I am having exact same issue for already more than a year and a half... Ubuntu 20.04 with QCA9377. Have you found a solution? thanks!

---

