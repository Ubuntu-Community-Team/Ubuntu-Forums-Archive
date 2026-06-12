---
title: "Ubuntu 18.04 WiFi problem (Broadcom BCM43142)"
date: 2019-05-17
forum: Networking &amp; Wireless
---

### Post by nabizade on 2019-05-17
[COLOR=#242729][FONT=Arial]My laptop is HP Pavilion 15 p077. I cannot use my internal WiFi adapter very well. When I'm entering in other rooms, my WiFi is not connecting. So I bought TP link TL-WN725N. But problem is not gone. When I used Windows, I used my WiFi. What's the problem? I didn't found my solution in any of topics.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I use either internal or external WiFi adapter without any problem?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Output of lspci -nnk | grep -A3 0280

[/FONT][/COLOR]
08:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
    Kernel driver in use: wl
    Kernel modules: wl

---

### Post by nabizade on 2019-05-17
@chili555 Please help me :(

---

### Post by chili555 on 2019-05-17
I just noticed your post. Sorry for the delay.

With the USB wireless detached, please run:```
sudo iw reg get 
sudo iwlist scan
```And post the results.

For the scan command, I am only interested in your own network. Please redact the MAC address of your router like this:```

Cell 01 - Address:[COLOR="#FF0000"] XXXX[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000327d5fce609
                    Extra: Last beacon: 580ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK







```

---

### Post by nabizade on 2019-05-18
Thanks for your reply @chili555
Here is my results

[B]sudo iw reg get

[/B]```
globalcountry AZ: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 18), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 18), (0 ms), DFS, AUTO-BW
```[B]

sudo iwlist scan[/B]

```
Cell 02 - Address: D8:5D:4C:B3:A0:F4                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key: on
                    ESSID:"Nabizade WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 376288ms ago
                    IE: Unknown: 000D4E6162697A6164652057694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

**NOTE:** I'm near the my Own network. So I can use it's now, if it is needed I can move away

---

### Post by chili555 on 2019-05-18
Wow! Everything that can be set to make your wireless perform poorly is here in one place!

First, I have worked on more than one case where a space in the name of the SSID, usually the router, made connecting difficult. I suggest that you rename the router to something like NabizadeWiFi; that is, with no space in the name.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Most wireless drivers and old Chili hate hate hate TKIP!

Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, post back to tell us if there is any improvement.

---

### Post by nabizade on 2019-05-19
Now my settings looks like in screenshot, in 2-3 hours I will test and reply to this post if there can be changed please inform me

---

### Post by nabizade on 2019-05-19
Tested new settings, not success result :( Not sure it's a router problem, cause when I used Windows and phones in the home is catching Wireless very good

```
          Cell 02 - Address: D8:5D:4C:B3:A0:F4                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"NabizadeWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 31808ms ago
                    IE: Unknown: 000C4E6162697A61646557694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK



```

---

### Post by chili555 on 2019-05-19
You have posted for the world to see your WPA2 password! Please change it immediately.

Your settings look very good, however the signal strength is still low:> Cell 02 - Address: D8:5D:4C:B3:A0:F4                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="#FF0000"]Quality=43/70[/COLOR]  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"NabizadeWiFi"Is the signal strength also low in Windows?

I wonder if both of the antenna connections are securely attached. I suspect that the Windows driver has the ability to sense and switch connections; I suspect that the Ubuntu driver does not.

---

### Post by nabizade on 2019-05-19
My router is located on the 2nd floor, and &#304; catched it and worked with it perfectly in 1st floor kitchen, also my phone is catching from the 100m distance, but with Ubuntu i cannot catch it in neighbour room. Please write me guide to remove all wireless drivers from my system, and wrote new eligible driver for my wireless adapter, or guide to my usb wireless adapter, i wonder i have done all wireless driver guides.i need clean driver, may be it can help me to resolve this problem.
Thanks chili555 for your help

---

### Post by nabizade on 2019-05-19
My router is located on the 2nd floor, and &#304; catched it and worked with it perfectly in 1st floor kitchen, also my phone is catching from the 100m distance, but with Ubuntu i cannot catch it in neighbour room. Please write me guide to remove all wireless drivers from my system, and wrote new eligible driver for my wireless adapter, or guide to my usb wireless adapter, i wonder i have done all wireless driver guides.i need clean driver, may be it can help me to resolve this problem.
Thanks chili555 for your help

---

### Post by chili555 on 2019-05-19
> Please write me guide to remove all wireless drivers from my system, and wrote new eligible driver for my wireless adapter, I am assuming that you mean that you want to remove the usual default Broadcom driver and instead install a different, better driver. I know of none.

If you are asking me to *write *a better driver,  then that is far beyond my abilities. I am not a developer, I am a tinkerer.

If you are looking for a USB device, check here: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by nabizade on 2019-08-24
[IMG]https://ibb.co/0QP9xSg[/IMG][IMG]https://i.ibb.co/pnCKS8t/IMG-20190824-162934.jpg[/IMG]

Is it can be problem, I detached my laptop back for viewing antennas. Is there any new solutions? also I put my wireless test results.

[https://termbin.com/q4dw]("https://termbin.com/oi1c")

---

### Post by him610 on 2019-08-25
nabizade,
```

##### iw reg get ########################

Region: [COLOR="#FF0000"]Asia/Baku[/COLOR] (based on set time zone)

global
country [COLOR="#FF0000"]US[/COLOR]: DFS-FCC

```
Either you are in Asia/Baku or you are in US. Which is it? They both should be the same.

---

### Post by nabizade on 2019-08-25
I'm in Asia/Baku, how can I set it?

---

### Post by jeremy31 on 2019-08-25
I thought I mentioned that on IRC
```
sudo iw reg set AZ
```

---

### Post by nabizade on 2019-08-25
Yes, I remembered and already done it, Thanx jeremy :)

---

### Post by chili555 on 2019-08-25
It appears that there is only one antenna wire connected. Isn't there a second, possibly white one in there somewhere that needs to be connected?

[https://qph.fs.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807](https://qph.fs.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807)

---

### Post by him610 on 2019-08-27
> I'm in Asia/Baku, how can I set it?
To set it permanently, you need to open /etc/default/crda with your favorite editor, and change the last line to read,
```

DOMAIN=AZ

```
Save the file and exit.

---

