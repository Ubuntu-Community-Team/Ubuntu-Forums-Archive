---
title: "Asus AC53 network adapter driver"
date: 2019-08-04
forum: Networking &amp; Wireless
---

### Post by Patricia_Budamis on 2019-08-04
Hi all,

I'm currently trying to connect to the 5ghz network using an Asus AC53 USB adapter. I installed the driver as explained here [https://github.com/jeremyb31/rtl8822bu](https://github.com/jeremyb31/rtl8822bu) without any issues, but I still fail to connect to 5ghz, even though this frequency seems to be available as you can see through the output of "**iwlist wlan0 freq**":

```

wlan0     22 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

I also ran the script requested in this post: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
And the output can be seen here: [https://pastebin.com/uevduBZt](https://pastebin.com/uevduBZt)

As you can see in the output I also tried installing the driver 88x2bu.

I'm running Ubuntu 18.04 with kernel 4.15. When I installed Ubuntu in this computer (Thinkpad E470) I had quite some trouble being able to connect to the WIFI as I had to manually install the driver rtl8821ce. Now after installing the rtl8822bu driver, it appears in the menu a new option: "USB wi-fi" but when I selected the 5GHz network it fails to connect and I have to reboot to be able to connect to the 2GHz network again.

Any ideas about how I could solve this issue are highly appreciated :)

---

### Post by chili555 on 2019-08-04
First, wlan0, where you show 5 gHz frequencies, is your internal device, not the USB. Second, you have two wireless devices and *three* drivers, no doubt conflicting and no doubt making it difficult to see what is going wrong and which is in control.

What evidence do you have that suggests that the USB will be better able to connect in preference to your internal device? Isn't it more likely that the internal, with a bigger antenna, has a better chance of connecting than the tiny USB?

---

### Post by Patricia_Budamis on 2019-08-04
Hi Chili555, thank you for replying.

Yes, definitely, if I can use my internal device that would be awesome!
So I removed drivers 88x2bu and rtl8822bu ("modprobe -r driver_name") and I left rtl8821ce (otherwise I cannot use connect to the WIFI at all).

If I ran "iw list" I get:
```

Band 2:
        Capabilities: 0x1862
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 16 usec (0x07)
        HT Max RX data rate: 476 Mbps
        HT TX/RX MCS rate indexes supported: 0-7
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 5180 MHz [36] (30.0 dBm)
            * 5200 MHz [40] (30.0 dBm)
            * 5220 MHz [44] (30.0 dBm)
            * 5240 MHz [48] (30.0 dBm)
            * 5260 MHz [52] (disabled)
            * 5280 MHz [56] (disabled)
            * 5300 MHz [60] (disabled)
            * 5320 MHz [64] (disabled)
            * 5500 MHz [100] (disabled)
            * 5520 MHz [104] (disabled)
            * 5540 MHz [108] (disabled)
            * 5560 MHz [112] (disabled)
            * 5580 MHz [116] (disabled)
            * 5600 MHz [120] (disabled)
            * 5620 MHz [124] (disabled)
            * 5640 MHz [128] (disabled)
            * 5660 MHz [132] (disabled)
            * 5680 MHz [136] (disabled)
            * 5700 MHz [140] (disabled)
            * 5720 MHz [144] (disabled)
            * 5745 MHz [149] (30.0 dBm)
            * 5765 MHz [153] (30.0 dBm)
            * 5785 MHz [157] (30.0 dBm)
            * 5805 MHz [161] (30.0 dBm)
            * 5825 MHz [165] (30.0 dBm)
            * 5845 MHz [169] (disabled)
            * 5865 MHz [173] (disabled)
            * 5885 MHz [177] (disabled)


```

A lot of them are disabled, but some are enabled. In my router configuration the channel selected is 36, that seems to be available for me, but I still cannot  connect to it.

I also ran the script again and this time I got this: [https://pastebin.com/nm7f3y89](https://pastebin.com/nm7f3y89)

Do you have any suggestion? :)

---

### Post by Patricia_Budamis on 2019-08-04
So in the end I was able to connect to the 5GHz, but I had to "forget" the 2GHz network and restart the computer, and then it manages to connect to the 5g network on the first attempt. If I connect to the 2g and try to connect to 5g, I cannot connect to any network at all anymore and I have to restart my computer...
Any idea of how I could solve this issue? Is it maybe something related to the driver? :)

---

### Post by chili555 on 2019-08-04
One of the reasons that certain channels are disabled and some enabled is that some channels are not supported in your regulatory domain. Yours is evidently 00, the usual one-size-maybe-fits-all default. > global
country 00: DFS-UNSET
I recommend that your regulatory domain be set explicitly. Check yours:

Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

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
```

Proofread carefully, save and close the text editor.

I suspect that Network Manager is responsible for connecting automagically is that you've selected 'Connect Automatically.' I suggest that you find and un-check it for all and every network you connect to: [https://i.stack.imgur.com/hxuua.png](https://i.stack.imgur.com/hxuua.png)

Now is there any improvement?

---

