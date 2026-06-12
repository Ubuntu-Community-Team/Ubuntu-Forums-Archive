---
title: "Ubuntu mate 20.04: problem with Realtek RTL8821CE WiFi network card"
date: 2022-01-06
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2022-01-06
Hi,
I have a problem with the Realtek RTL8821CE WiFi network card on ubuntu mate 20.04. In short, if I leave the default driver, the card is detected and I can connect to the various WiFi networks, but the performance is poor (continuous disconnections). If I activate the open source driver installed as described [here]("https://askubuntu.com/a/1268534"), the network card is detected, but inside the connection manager it is not available any WiFi.

```
lsusb 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 003 Device 004: ID 05c8:03d2 Cheng Uei Precision Industry Co., Ltd (Foxlink) ASM105X series
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 174c:55aa ASMedia Technology Inc. Name: ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge, ASM1153E SATA 6Gb/s bridge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lshw | grep Wireless
WARNING: you should run this program as super-user.
                description: Wireless interface
                product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```


Any idea?
Thank you

---

### Post by chili555 on 2022-01-06
> but the performance is poor (continuous disconnections).I suggest that you try some trobleshooting steps.

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

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
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

