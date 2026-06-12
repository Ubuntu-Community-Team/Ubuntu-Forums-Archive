---
title: "Ubuntu 16.04 wireless down"
date: 2017-01-31
forum: Networking &amp; Wireless
---

### Post by vampiremr on 2017-01-31
Hi all, I know that there are many solutions there but I can't found my

Env: laptop samsung R700, wireless PRO/Wireless 3945ABG [Golan] Network Connection, ubuntu 16.04
Problem: sometimes (random) wifi module go to down. And up only after reboot or suspend.
Additional info after down:

```
sudo lshw -C network  
*-network             
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 13
       serial: 00:13:77:69:8d:2f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d5000000-d5003fff ioport:3000(size=256) memory:d5020000-d503ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 02
       serial: 00:1c:bf:9c:1d:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=4.4.0-59-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:d5100000-d5100fff



```

```
 sudo ifconfig wlp4s0 up
SIOCSIFFLAGS: Input/output error

```

Any solutions? What else info needed?

---

### Post by wildmanne39 on 2017-01-31
*Thread moved to **Networking & Wireless for better support**.*

---

### Post by wildmanne39 on 2017-01-31
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by vampiremr on 2017-02-01
[ATTACH]273467[/ATTACH]

---

### Post by wildmanne39 on 2017-02-01
Let's try this one thing then I am getting of for tonight, copy and paste the commands one line at a time into the terminal for accuracy:
```
echo "options iwl3945 disable swcrypto=1" | sudo tee /etc/modprobe.d/iwl3945 .conf
sudo modprobe -rfv iwl3945
sudo modprobe -v  iwl3945
```
Thanks

---

### Post by vampiremr on 2017-02-01
Its do not help. Problem still here

---

### Post by wildmanne39 on 2017-02-01
While the system will not connect run:
```
./wireless-info
```
that will run the wireless script again without downloading it again, then post the new file create here, I suspect you have a block or the module is not loading.
Thanks

---

### Post by vampiremr on 2017-02-02
See in attach

[ATTACH]273478[/ATTACH]

---

### Post by vampiremr on 2017-02-02
And as I see today, wi-fi go to down every 15 minutes

upd: and now every 1 hour

---

### Post by wildmanne39 on 2017-02-02
Let's turn power management off:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Let's clean a few things up and see if that helps.

You have a connection called vampirehome 1 that you are connected too without internet, and you have vampirehome which you should be connected too, so go into network manager and remove the vampireone connection and any others that you do not need.

Please do:
```
sudo dpkg-reconfigure resolvconf
```
to reset this file to it's default setting.

Please set your settings in network manager to match the screenshots:
[ATTACH=CONFIG]273480[/ATTACH][ATTACH=CONFIG]273481[/ATTACH]
If you are in the Ukrane we need to change the Country code for your router, please do:
```
sudo iw reg set UA
sudo sed -i 's/^REG.*=$/&UA/' /etc/default/crda
```
Change the settings in the router. WPA2-AES (CCMP) is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, preferably one in the 5GHZ range because you have so many networks in range of your computer , rather than automatic channel selection. After making these changes, reboot the router and computer.

> Failed check-sdata-in-driver check, flags: 0x4
That is a bug the effects many people, if the above changes do not help we might can try one or two more things but no one has solved this completely.

If it still disconnects please try to give more information then one line, be specific it disconnects every so many minutes and tell us how you get the internet back please and post a new wireless files so we can make sure all the changes stuck.

You need to know that getting it to disconnect a lot less is probably the best we are going to do.
Thanks

---

### Post by vampiremr on 2017-02-02
> [COLOR=#000000]Change the settings in the router. WPA2-AES (CCMP) is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, preferably one in the 5GHZ range because you have so many networks in range of your computer , rather than automatic channel selection. After making these changes, reboot the router and computer.[/COLOR]


I do not have this settings. Below you can see screens

[[img]http://pix.toile-libre.org/upload/img/1486062501.png[/img]](http://pix.toile-libre.org/?img=1486062501.png)

[[IMG]http://pix.toile-libre.org/upload/img/1486062381.png[/IMG]]("http://pix.toile-libre.org/?img=1486062381.png")

---

### Post by jeremy31 on 2017-02-02
For your router use WPA2-PSK and it seems to have another encryption setting below, keep that one AES

---

### Post by vampiremr on 2017-02-05
[wildmanne39]("https://ubuntuforums.org/member.php?u=508533")[COLOR=#000000], it seems that problem was solved. Thanks![/COLOR]

---

### Post by wildmanne39 on 2017-02-05
I am glad to hear that it is working!
Enjoy!:)

---

