---
title: "Wireless hardware not detected"
date: 2019-11-18
forum: Networking &amp; Wireless
---

### Post by re-bootycity88 on 2019-11-18
Hi all, I recently installed Ubuntu on a mini pc and it will not detect the wireless hardware. I've been reading all sorts of post from this forum and many others but I don't think my situation is the same. The wifi info in setup utility is Broadcom AP 6234(currently set) & AP 6212. I have yet to find any firmware and have found only drivers. What else can I do? 

Thanks for considering!

---

### Post by chili555 on 2019-11-18
Please run and post the result of these terminal commands:

```
dmesg | grep -i sdio
dmesg | grep brcm
```

---

### Post by re-bootycity88 on 2019-11-19
imx@imx-Z83-II:~$ dmesg | grep -i sdio
[    3.195690] mmc1: new ultra high speed DDR50 SDIO card at address 0001
[    6.101210] Bluetooth: Generic Bluetooth SDIO driver ver 0.1
[    6.210689] brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43340-sdio for chip BCM43340/2
[    6.303251] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.AZW-Z83 II.txt failed with error -2
[    6.303278] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2
[    7.310323] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
imx@imx-Z83-II:~$ dmesg | grep brcm
[    6.210689] brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43340-sdio for chip BCM43340/2
[    6.211043] usbcore: registered new interface driver brcmfmac
[    6.269208] bluetooth hci0: Direct firmware load for brcm/BCM43341B0.hcd failed with error -2
[    6.269219] Bluetooth: hci0: BCM: Patch brcm/BCM43341B0.hcd not found
[    6.303251] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.AZW-Z83 II.txt failed with error -2
[    6.303278] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2
[    7.310323] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50



Thanks for taking a look!

---

### Post by chili555 on 2019-11-19
> Direct firmware load for brcm/brcmfmac43340-sdio.AZW-Z83 II.txt failed with error -2I have serached pretty exhaustively for this file. I can find it nowhere.

However, I wonder if the txt file might work alone:

> Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2Zanna's excellent answer here tells us how to get the txt file: [https://askubuntu.com/questions/751374/do-i-need-to-install-a-wireless-patch-for-asus-x205ta-after-upgrading-the-kernel](https://askubuntu.com/questions/751374/do-i-need-to-install-a-wireless-patch-for-asus-x205ta-after-upgrading-the-kernel)

Please be a bit cautious here: ```
sudo cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113  /lib/firmware/brcm/brcmfmac43340-sdio.txt
```The long string of numbers after *nvram* may differ on your machine; susbtitute as needed.

Reboot and show us:```
dmesg | grep brcm
```

---

### Post by re-bootycity88 on 2019-11-25
Hi there,

Sorry for the delay. I've been trying what the other person did but got stuck at the part where it creates a new directory. Then I started going on a tangent trying to figure out why it didn't work. Here is what happens -  

[COLOR=#444444][FONT=tahoma]imx@imx-Z83-II:~$ sudo apt-get install git[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma][sudo] password for imx: [/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]Building dependency tree       [/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]Reading state information... Done[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]git is already the newest version (1:2.17.1-1ubuntu0.4).[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]imx@imx-Z83-II:~$ sudo cp linux-firmware/brcm/[/FONT][/COLOR][COLOR=#444444][FONT=tahoma]brcmfmac43340-sdio.bin lib/firmware/brcm/[/FONT][/COLOR][COLOR=#444444][FONT=tahoma]brcmfmac43340-sdio.bin[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]cp: cannot create regular file 'lib/firmware/brcm/[/FONT][/COLOR][COLOR=#444444][FONT=tahoma]brcmfmac43340-sdio.bin': No such file or directory[/FONT][/COLOR]
[COLOR=#444444][FONT=tahoma]imx@imx-Z83-II:~$[/FONT][/COLOR]

---

### Post by chili555 on 2019-11-25
> imx@imx-Z83-II:~$ sudo cp linux-firmware/brcm/brcmfmac43340-sdio.bin lib/firmware/brcm/brcmfmac43340-sdio.binYou missed a character. It should be:```

imx@imx-Z83-II:~$ sudo cp linux-firmware/brcm/brcmfmac43340-sdio.bin [COLOR="#FF0000"]/[/COLOR]lib/firmware/brcm/brcmfmac43340-sdio.bin

```Please try again.

---

