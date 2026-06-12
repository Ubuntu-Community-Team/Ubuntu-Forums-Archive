---
title: "Intel Wireless 7260 randomly dropping connection on ubuntu 18.04"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by rbailo on 2018-07-10
I have got a somewhat strange issue with my wifi connection and I haven't managed to find a solution.

The laptop connects to wifi without issue right after boot. The connection will work fine for a while (30 seconds to a couple of hours) before spontaneously dropping (often when streaming video but not always, sometimes just opening a news site). Switching wifi off and on does not help, nor restarting the network service. The issue persists after logging off and on, leaving the laptop idle for a few hours or hibernating through any length of time. However, the connection always works right after reboot.

Wireless script output: [http://paste.ubuntu.com/p/KwGrQCqsv6/](http://paste.ubuntu.com/p/KwGrQCqsv6/)

Due to the random occurrence of the issue this is proving tricky to debug. Any ideas?

---

### Post by chili555 on 2018-07-10
There appear to be several SSIDs available named Imperial-WPA. I am quite confident that your wireless device, much like my old girlfriend, is roaming to another instance looking for a better connection.

I suggest that you bind to the strongest like is described here.  [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by rbailo on 2018-07-11
Thanks for the suggestion, chili555. Unfortunately I get the same issue at home, where there is only one SSID for my network (as there is only one router).

---

### Post by chili555 on 2018-07-11
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nan /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Any improvement?

---

### Post by rbailo on 2018-07-16
I have a number of devices connected to the router which work fine, so I think I will leave changing its configuration as a last resort. I have set the regulatory domain explicitly, and I have also both disabled power management and chosen the option for antenna aggregation as described in [https://www.reddit.com/r/archlinux/comments/5r2u1x/turn_off_power_management_in_iwlwifi/](https://www.reddit.com/r/archlinux/comments/5r2u1x/turn_off_power_management_in_iwlwifi/) .

It seems to be working fine, but I will wait a couple of days before claiming victory just to be sure. In the meantime, thanks for the suggestions!

---

### Post by rbailo on 2018-07-17
Got the bug again. Strangely enough, lshw shows the wireless card as disabled ([https://paste.ubuntu.com/p/ZGzwZ6RcmR/](https://paste.ubuntu.com/p/ZGzwZ6RcmR/)) but the wireless script reckons there is no software or hardware lock on the wireless LAN ([https://paste.ubuntu.com/p/hVmXmsYqnC/](https://paste.ubuntu.com/p/hVmXmsYqnC/)). Do you think it is still worth trying to configure the router?

---

### Post by chili555 on 2018-07-17
I do think you should change the settings in the router. I have worked on many cases where these exact same settings improved connectivity immensely, including my own! For what it's worth, I also, obviously, run Ubuntu, and I use an Intel 7260. 

I have many other devices here that connect easily and quickly using my suggested settings. They include a generation 1 iPad, a Chromebook, Roku, two smart TVs and more. I need none of the parameters that you are using:```
options iwlwifi power_save=0 swcrypto=1 11n_disable=8

```

However, the wireless isn't going to connect no matter the settings because of this:> [17317.868939] iwlwifi 0000:04:00.0: Could not load the [0] uCode section
[17317.868945] iwlwifi 0000:04:00.0: Failed to start INIT ucode: -5
[17317.868947] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -5
[17317.868948] iwlwifi 0000:04:00.0: Failed to start RT ucode: -5
[17320.742629] iwlwifi 0000:04:00.0: Could not load the [0] uCode section
[17320.742639] iwlwifi 0000:04:00.0: Failed to start INIT ucode: -5
[17320.742641] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -5
[17320.742642] iwlwifi 0000:04:00.0: Failed to start RT ucode: -5
[17323.609684] iwlwifi 0000:04:00.0: Could not load the [0] uCode section
[17323.609691] iwlwifi 0000:04:00.0: Failed to start INIT ucode: -5In short, the firmware file is corrupted in some way or else, the card is failing to load it because the card is failing.

Let's check the firmware:```
md5sum /lib/firmware/iwlwifi-7260-17.ucode
```We hope we see:```
[COLOR="#FF0000"]cfb5b4d56795ec43ea79a7abfc345f79[/COLOR]  /lib/firmware/iwlwifi-7260-17.ucode

```If not, let's reinstall the firmware:```
sudo apt install --reinstall linux-firmware
```Reboot and show us:```
dmesg | grep iwl
```

---

### Post by rbailo on 2018-09-15
I eventually came back to fix the issue with the laptop. I tried reinstalling the firmware, which didn't solve things. I eventually changed the router settings and it worked like a charm, it has been a week with no incidents. Thank you very much, I should have tried that the first time!

---

