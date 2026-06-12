---
title: "Acer Aspire E5 575G Bluetooth and Wifi lag and stutter when used at the same time"
date: 2017-06-25
forum: Networking &amp; Wireless
---

### Post by roberttseu on 2017-06-25
Hiya, I am posting this in the hopes that this will help someone encountering a similar problem as I was.

Long story short. After experiencing concurrent wifi/bluetooth lag on my Acer Aspire E5-575G and spending a week troubleshooting
the problem, I managed to solve it by doing the following.

***backup /lib/firmware/ath10k/QCA9377/board-2.bin***


***download "board-2.bin" from [https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0](https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0) and overwrite to ***

***/lib/firmware/ath10k/QCA9377/board-2.bin***

***reboot***

***This fix was specific to my wireless hardware and my distro, so in case you have similar but different hardware read the full story below:-***



I recently installed LXLE based on lubuntu LTS 16.04 Xenial Xerus on an Acer Aspire E5-575G.
Everything seemed to be working fine until I tried to use a bluetooth stereo headset
(Samsung Level U Pro 69B5) in a2dp audiosink mode. I found that if I was not connected to 
a wifi network and actively using the network, there would be no issue. As soon as I connected to 
a wireless network and browsed the net, the audio on my headset would start to stutter and i would 
notice a steadily increasing A/V sync problem if I was watching a youtube video or any local video
on a media player (mplayer). The wifi performance would get progressively worse until a point at
which it would be completely unusable. Disconnecting the bluetooth device and reconnecting the wifi
network would momentarily restore normal operation but the problem would return after a few seconds.

I googled the problem and discovered that others were experiencing this issue and attributed this to 
a bluetooth coexistence as the wifi and bluetooth function were being handled by the same hardware 
so there was some interference between the two. Their solution was to enable bluetooth coexistence 
on their wifi/bluetooth driver specifically the bt_coex_active parameter on the iwlwifi(Intel) driver.

Unfortunately my laptop is running on an atheros and not an intel chipset. After further googling I stumbled
upon the [COLOR=#000000][FONT=&amp]btcoex_enable parameter for the ath9k driver. Unfortunately my kernel was using the ath10k_pci
driver which did not support this parameter and enabling it in /etc/module.d/ath10k_pci.conf resulted in
an invalid parameter warning and no visible effect. My specific hardware is the QCA9377 which I determined
when booting in to windows and looking at the driver in device manager.
[/FONT][/COLOR] [COLOR=#000000][FONT=&amp]
I decided to see if there were any new firmware releases for my specific hardware and noticed that the "[/FONT][/COLOR]board-2.bin"
at [https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0](https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0) was updated a few days ago. I went and downloaded
the file at overwrote the file with the same name in the "/lib/firmware/ath10k/QCA9377/board-2.bin". After a reboot the problem
went away. So if you have an atheros/qualcomm chipset in your laptop, check what hardware you are using. In my case it was
QCA9377. You might be able to determine this by looking at the output of "lspci -vv" but in my case, it was not listed there so I
booted into windows and checked the device manager. Go to [https://github.com/kvalo/ath10k-firmware/tree/master](https://github.com/kvalo/ath10k-firmware/tree/master) and click on 
the correct folder for your hardware and check for newer files than the ones in your /lib/firmware/ath*/QXXXX/hwX.X folder.
Download and overwrite any newer files into your local firmware folder after backing up the originals and reboot to test.


Hope this helps someone. I could not find a solution online for this and was for a while using a separate wifi dongle on 
my laptop to work around this problem.:(

Thanks.

---

### Post by peng3 on 2017-07-20
Did you edit anything else aside from the board-2.bin? I have the same setup and same issue but can't get my bluetooth and wifi working. Also from what date are the other firmware files for the wifi driver you have?

---

