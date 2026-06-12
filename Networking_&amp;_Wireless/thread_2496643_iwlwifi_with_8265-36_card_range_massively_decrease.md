---
title: "iwlwifi with 8265-36 card range massively decreased with newer kernel"
date: 2024-04-06
forum: Networking &amp; Wireless
---

### Post by db0 on 2024-04-06
I recently got me a refurbished HP Elitebook x260 1030 G3 which comes with a 8265-36 intel wireless card. Installation of Ubuntu 22.04 went fine and it recognised my wireless network fine. Likewise first use was also OK. However after first apt upgrade and reboot, we noticed the wireless is still working but not seeing any wifi networks, (the router is one floor away) which works fine for every other device.

I did some significant troubleshooting the past few hours and I've tracked it down to the kernel version. Currently the laptop is using the latest 6.5.0-26-generic kernel. 

The steps I've tried during troubleshooting:

* Reboot from the liveCD. The wifi network is seen as normal in the liveCD 5.19.0-32-generic kernel. The firmware on the liveCD is the same as the firmware on the installed version.
* Downgrade the iwlwifi firmware to the previous version available in linux-firmware. No change. Restored to latest firmware
* Downgraded to various other kernels, along with their iwlwifi module (e.g. linux-modules-iwlwifi-6.2.0-25-generic). Most of them didn't even recognise the wifi device.
* Eventually downgraded to linux kernel 5.19.0-50-generic which finally seems to work as normal (i.e. with proper wifi range)
* The system also still includes the liveCD 5.19.0-32 kernel, but that one doesn't work. I assume because the linux-modules-iwlwifi-5.19.0-32-generic package does not exist in the ubuntu repositories to be installed. Not sure.

So currently, only 5.19.0-50-generic along with linux-modules-iwlwifi-5.19.0-25-generic works as expected. All the other kernel versions either don't recognise the wireless card, or have massively reduced range (I have to be standing almost next to the router).

I would have just stayed on 5.19.0-50 but unfortunately that one has a buggy touchpad making it borderline unusable.

Any suggestions on how I can make the wifi work correctly on the latest kernel?

---

### Post by karimoui on 2024-04-13
[COLOR=#000000]Hi all, I realize this is a (as well) normal issue among Nitro and Try PCs, for what I'm seeing on the Web. My Nitro PC is over two years of age. Everything has consistently functioned admirably, it still for the most part does, except for the touchpad, which, a long time back, began introducing a very irritating slack (it requires around 1 second to respond to my orders). Some of the time its reaction is nervous, to the level it makes the touchpad fringe unusable. Additionally, it now and again presents ghost orders, the clicking doesn't work, and so forth. Utilizing the PC this way is downright horrendous. I have a Nitro AN515-44 with Windows 10, 64 digit. The driver for the touchpad (Spirit I2C Channel Driver) is variant 13.6.16.1. The touchpad is perfect. I've cleaned it with liquor. Had no effect on the slacking/jittering. The issue happens freely of the PC being associated with an electrical plug or not (and I don't utilize electrical ropes). Truly, since it started, it's been there essentially continually, with fluctuating degrees of disagreeableness. I've taken a stab at crippling the gadget on the gadget supervisor and restarting the PC. Didn't tackle it. Supposedly from the Acer Driver site, this (13.6.16.1) is the most recent variant of the driver. Someone kindly let me know on the off chance that I'm off-base. I won't contact the Profiles, as I've found in certain posts out there, for a touchpad issue except if someone has substantial confirmation that that is the best approach. I realize this is influencing a Ton of people out there, and it's making my involvement in the (for the rest, fantastic) PC solidly more regrettable. Please, Acer/Acer help group, show us a real answer for this issue. Kindly can allow me to say whether anyone needs more data (programming/equipment) about my PC. [/COLOR]
Thanks to you




[[color=#a9a9a9][size=1]192.168.100.1[/size][/color]](https://1921681001.id/) [[color=#a9a9a9][size=1]192.168.1.1[/size][/color]](https://19216811.cam/)

---

### Post by praseodym on 2024-04-13
Try the classic:

echo 'options iwlwifi 11n_disable=0' | sudo tee /etc/modprobe.d/iwlwifi-11n.conf

This is one line 

Reboot

---

