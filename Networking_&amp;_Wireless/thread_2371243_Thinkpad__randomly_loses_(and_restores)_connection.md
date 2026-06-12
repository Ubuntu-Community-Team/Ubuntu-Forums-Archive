---
title: "Thinkpad  randomly loses (and restores) connection, Ubuntu 16.04"
date: 2017-09-12
forum: Networking &amp; Wireless
---

### Post by efallom on 2017-09-12
Hello everybody,

I've just got a Lenovo X1 carbon and installed Ubuntu 16.04 LTS. 

There seems to be a connectivity bug, that many users report according to a google search, but I was not able to find a solution.

Although the network manager says that I am connected to the router, and the router is connected to the internet (it works on other devices) I just do not get any connection on my laptop.

This occurs randomly, and the connectivity is restored randomly as well.

I tried rebooting the laptop, but i does not work, restarting the network manager only worked once, i changed the power management settings but that did not help either, so I really do not have any clue now.

My wireless card is Intel Dual-band 7260AC and the driver is iwlwifi. 

Any help is appreciated.

---

### Post by BenginM on 2017-09-12
Hiya , welcome to the forums .

So, the laptop is connected directly to the router AP, and not through a wifi extender, Right! 

in a terminal, please run : $ sudo apt update && sudo apt dist-upgrade

And share the output of the following commands under a CODE tag like so,

[PHP]
```

$ dmesg | grep iwlwifi
$ ls -l /lib/firmware
$ uname -a

``` 
[/PHP]

care to share links of those bug reports related to the wireless behavior you experiencin'. Thanks .
#
[URL="https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi"]https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi
[/URL][https://wireless.wiki.kernel.org/en/...i/core_release]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release")
[https://www.intel.com/content/www/us...000005511.html]("https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html")

---

### Post by efallom on 2017-09-12
Update: It is probably a router problem, since my iphone and ipad work, but three different laptop do not.
In particular on the windows laptop it shows limited connectivity, after rebooting the router it started working on the laptops to.

links to other people having the same issue:

[https://askubuntu.com/questions/653355/wireless-connected-but-no-internet-access](https://askubuntu.com/questions/653355/wireless-connected-but-no-internet-access)
[https://askubuntu.com/questions/790745/connected-to-wifi-but-no-internet](https://askubuntu.com/questions/790745/connected-to-wifi-but-no-internet)
[https://askubuntu.com/questions/725025/wifi-says-its-connected-but-it-isnt](https://askubuntu.com/questions/725025/wifi-says-its-connected-but-it-isnt)
[https://askubuntu.com/questions/907763/ubuntu-17-04-connected-to-wifi-but-cant-browse-internet](https://askubuntu.com/questions/907763/ubuntu-17-04-connected-to-wifi-but-cant-browse-internet)


The following is the output of the suggested commands (the connection was working at the time I ran the commands).

[https://paste.ubuntu.com/25522996/](https://paste.ubuntu.com/25522996/)


I am not sure whether this issue can be solved here, but I hope I can be helpful for other users.


Thanks!

---

### Post by BenginM on 2017-09-13
dmesg iwlwifi shows  the kernel driver iwlwifi is crashing for some reason , hence the the loose /hang/[FONT=-apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol][COLOR=#24292e]breaks .[/COLOR][/FONT] this could be a firmware/kernel regression / the firmware is corrupted/BROKEN. the driver not communicating nicely to the driver firmware for some reason!  Yes the cause could be coming from the router settings like the channel/band as well as a platform noise related ... #See [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_platform_noise](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_platform_noise)

I would suggest you try bootin' with a prior kernel than [COLOR=#000000]4.10.0-33-generic , or a newer one , and see if the issue persists there as well.[/COLOR]

---

### Post by efallom on 2017-09-28
So, I installed (I guess I did, I just copied the .ucode file into /lib/firmware) the suggested driver from the Intel website, and the output of dmesg is now this:

```
$ dmesg | grep iwlwifi[    8.661781] iwlwifi 0000:03:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[    8.708188] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.710507] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    8.711164] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    8.933236] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   10.878926] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   10.879432] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   11.061895] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   11.062398] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled



```

Does it mean the problem was fixed?

---

