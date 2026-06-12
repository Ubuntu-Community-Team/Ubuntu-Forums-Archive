---
title: "brcm/brcmfmac43455-sdio.txt failed with error -2 - No wireless"
date: 2018-06-03
forum: Networking &amp; Wireless
---

### Post by jacklebird on 2018-06-03
Hey everyone, I'm completely new to the Linux OS and thought I'd use an old netbook i wasn't using to try it out, only issue I'm having so far is my wireless. I've been trawling through various solutions that might apply to me but i haven't managed to get anything to work as of yet. To make sure no other potential fixes can cause conflicts I've completely reinstalled Lubuntu 18.04 amd64, and have run the commands listed in the sticky. Wifi worked fine in windows 10 but i no longer have the OS installed. There isn't much information about the netbook on the manufacturers website unless I'm missing something, but here's the model [http://www.unisurf.com.au/unisurf-14-Notebook.html](http://www.unisurf.com.au/unisurf-14-Notebook.html)

Thanks.

[http://paste.ubuntu.com/p/PM46KHcFZ8/](http://paste.ubuntu.com/p/PM46KHcFZ8/)

And the errors found at the bottom of the results.
[    6.231619] bluetooth hci0: Direct firmware load for brcm/BCM4345C0.hcd failed with error -2
[    6.231629] Bluetooth: hci0: BCM: Patch brcm/BCM4345C0.hcd not found
[    6.246260] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    6.576281] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43455-sdio.bin for chip 0x004345(17221) rev 0x000006
[    6.582341] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43455-sdio.txt failed with error -2
[    7.381978] rndis_host 1-1:1.0 enp0s20u1: renamed from usb0
[    8.128879] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1: link is not ready
[    9.590094] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50 (repeated 2 times)

---

### Post by jeremy31 on 2018-06-03
So I take it that ```
ls /sys/firmware/efi/efivars/ | grep nvram
```
has no results

---

### Post by jacklebird on 2018-06-03
> **jeremy31 said:**
> So I take it that ```
ls /sys/firmware/efi/efivars/ | grep nvram
```
has no results

That's correct.

...

Solved it, to anyone else with the same problem here's the solution i used: [https://askubuntu.com/questions/1007163/ubuntu-16-04-how-do-i-logically-troubleshoot-ap6212-6255-broadcom-wireless-blu](https://askubuntu.com/questions/1007163/ubuntu-16-04-how-do-i-logically-troubleshoot-ap6212-6255-broadcom-wireless-blu)

---

