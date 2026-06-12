---
title: "I've tried lots of wifi dongles and none of them work"
date: 2021-12-22
forum: Networking &amp; Wireless
---

### Post by alandefreitas on 2021-12-22
Hello,

The problem is ethernet works perfectly but WiFi doesn't. It's the only peripheral that doesn't work in Ubuntu 20 or 21. 
When I try to connect from the settings GUI, I get an error "Activation of network connection failed.".
When I try to connect from the terminal, I usually get something like "Error: Connection activation failed: The Wi-Fi network could not be found" even though it's in the list of saved connections.

I've tried multiple combinations of (1) Ubuntu 20 and 21, (2) three different dongles, (3) lots of different drivers, and (4) lots of very different instructions from internet forums. 
All of the dongles work with 100% signal on Windows and macOS with no configuration. The third dongle I bought (tp-link TL-WN822N) explicitly says on the box it supports Linux but there is only a very experimental driver on their website.

I'm a little desperate because (i) I've been trying to make this work for over a week now, (ii) I need a computer running Ubuntu for work (depending on scripts meant to run on Ubuntu), (iii) my co-workers are starting to complain things are not moving, and (vi) I don't have easy access to Ethernet all the time because logistics here.

Before running the wireless info script, I installed Ubuntu 20 and 21 back and forth multiple times and ended up stopping at clean installation of Ubuntu 21.
The reason is I had less problems related to other peripherals on Ubuntu 21 and because I thought the wireless info script would be more useful on a clean installation.

So this is the output for the scripts with each of the dongles I bought:

1. D-Link Nano 300 Mbps Wireless 802.11n - DWA-131: [https://gist.github.com/alandefreitas/8d6bd7ba3f84f1a6fab594274acaa0d0](https://gist.github.com/alandefreitas/8d6bd7ba3f84f1a6fab594274acaa0d0) (This is first dongle I already had)

2. D-Link AC1300 MU-MIMO: [https://gist.github.com/alandefreitas/a2aba067ed88c467878d2074b2c4943f](https://gist.github.com/alandefreitas/a2aba067ed88c467878d2074b2c4943f) (With the second dongle, nothing appears in the settings/wifi tab. One of the drivers I tried made it appear but it didn't work anyway.)

3. Tp-Link TL-WN822N: [https://gist.github.com/alandefreitas/dbe0882a3c519b67efd096da54c41307](https://gist.github.com/alandefreitas/dbe0882a3c519b67efd096da54c41307) (The third dongle is the one that explicitly says on the box they support linux.)


Thanks.

---

### Post by morrownr on 2021-12-22
I feel your pain.

The following site has a lot of information about USB WiFi on Linux and it currently has 76 links to adapters that are Plug and Play on Ubuntu. Yes, Plug and Play. No need to hunt down a driver. Plug the adapter in and off you go. The adapters range from N150 to AC1300:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Good luck and let us know if you have any questions.

For anyone that reads this post and wonders why this info is not in a sticky post... have you checked the top sticky post?

---

### Post by morrownr on 2021-12-22
> **alandefreitas said:**
> Hello,

2. D-Link AC1300 MU-MIMO: [https://gist.github.com/alandefreitas/a2aba067ed88c467878d2074b2c4943f](https://gist.github.com/alandefreitas/a2aba067ed88c467878d2074b2c4943f) (With the second dongle, nothing appears in the settings/wifi tab. One of the drivers I tried made it appear but it didn't work anyway.)

Thanks.

I recommend getting adapters that are Plug and Play but if you are determined to make this adapter work:

[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

Follow the instructions carefully.

---

### Post by alandefreitas on 2021-12-23
Thank you for your answer. Yes. I did check the sticky post. I just described everything I did regardless because I thought it could be useful.
Yes. Adapters 1 and 3 seem to be on the list, but adapter 2 does not work out of the box even though it's on the list. I'm not really determined to make this one adapter work. Any of the adapters I bought would do.
Anyway, I did get adapter 2 to show up before with the same driver you recommended. The reason it's not there is because the output above is after a clean installation.

In any case, all adapters (including adapter 2 when its driver is installed) give me the same error regardless of the adapter being available. And all of them work on windows and macos with full signal (so the router must be ok).
As the error seems to be exactly the same for all adapters, I was hoping the output from the script would contain some hint or something to fix something I still have to configure properly.

---

### Post by chili555 on 2021-12-24
I wonder what explains this?

```
 SSID     BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Casa     <MAC 'Casa' [AN1]>  Infra  10    2457 MHz  270 Mbit/s  [COLOR="#FF0000"]27      &#9602;___[/COLOR]  WPA1 WPA2  yes     *      
```In all of your wireless-infos, the signal strength is very low or non-existent.

May we see: ```
sudo dmesg | grep -i rtl
```At a minimum, I'd change the router settings to WPA2 only, and a fixed channel, 1, 6 or 11, instead of autoselect.*

------------

*Autoselect: Let me find a channel where you are *not* and I'll go there. Sounds like my ex-girlfriend.

[https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311385](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311385)

---

### Post by alandefreitas on 2021-12-24
> **chili555 said:**
> I wonder what explains this?

```
 SSID     BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Casa     <MAC 'Casa' [AN1]>  Infra  10    2457 MHz  270 Mbit/s  [COLOR=#FF0000]27      &#9602;___[/COLOR]  WPA1 WPA2  yes     *      
```In all of your wireless-infos, the signal strength is very low or non-existent.

May we see: ```
sudo dmesg | grep -i rtl
```At a minimum, I'd change the router settings to WPA2 only, and a fixed channel, 1, 6 or 11, instead of autoselect.*

------------

*Autoselect: Let me find a channel where you are *not* and I'll go there. Sounds like my ex-girlfriend.

[https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311385](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311385)

Yes. I've noticed that. 

Because the dongles work on windows and macos with full signal, not to mention all the other small devices in the house, I thought this was related to the problem I'm having and something I still have to configure on Ubuntu to make it work. 

Of course, windows and macos might be lying about the full signal, but it's enough signal so they do connect to the internet even if the signal is somewhat bad.

---

