---
title: "Slow wifi internet speed with usb wifi adapter"
date: 2018-10-26
forum: Networking &amp; Wireless
---

### Post by blasqen on 2018-10-26
I just finished installing Ubuntu 18.10 and noticed my download speeds were rather low while downloading some software. I went to speedtest.net to test my speed. speeds fluctuate, but they don't go beyond 10 Mb/s. By comparison, if I do the same test under Windows 10 it goes as high as 100 Mb/s. I searched around and noticed there are other people with such issues, but could not yet find a solution that fixes the issue. I suspect it is a driver issue. The adapter is from Sitecom, I don't know exactly what model it is, but it looks pretty much identical to this one: [https://www.sitecom.com/en/n300-usb-adapter/wla-2100/p/1563](https://www.sitecom.com/en/n300-usb-adapter/wla-2100/p/1563). Could anyone help me to try and fix the issue?

---

### Post by jeremy31 on 2018-10-26
See the wireless script link in my signature and post results

---

### Post by blasqen on 2018-10-26
Hi, thanks for your reply. I ran the script. Results can be found here: [http://paste.ubuntu.com/p/BQ9yTTS3BS/](http://paste.ubuntu.com/p/BQ9yTTS3BS/)

---

### Post by jeremy31 on 2018-10-26
Try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

If that doesn't help a lot, change the wifi router encryption to WPA2 only with AES/CCMP no, WPA/WEP/TKIP

---

### Post by blasqen on 2018-10-28
I tried both. But no results so far...Any other ideas? Or should I buy a new usb dongle?

---

### Post by blasqen on 2018-10-29
I plugged the usb dongle in one of the usb ports at the back and I am now getting speeds close to normal, even though the signal strength is slightly worse. So it could be an issue with the USB drivers. Any idea to diagnose/fix this?

---

### Post by chili555 on 2018-10-29
> Cell 01 - Address: <MAC 'U=-tanh(beta)' [AC1]>
                    [COLOR="#FF0000"]Channel:3[/COLOR]
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"U=-tanh(beta)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028f8d15aa9
                    Extra: Last beacon: 548ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```Reboot the computer and tell us if there is any improvement.

Proofread carefully, save and close the text editor.

---

