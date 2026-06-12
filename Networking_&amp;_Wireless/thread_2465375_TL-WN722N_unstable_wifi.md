---
title: "TL-WN722N unstable wifi"
date: 2021-07-31
forum: Networking &amp; Wireless
---

### Post by unstablewifi on 2021-07-31
My internal wifi card is broken (also didn't work on windows) and I have to use usb wifi card TL-WN722N. The problem is wifi randomly stops working and ping shows host unreachable. It starts working again after I remove and connect usb. Please give any advice.

---

### Post by mikewhatever on 2021-07-31
The advice is, provide more info. The following outputs should be useful:

> 
lsb_release -a
lsusb
lspci -nnk | grep -iA3 network



---

### Post by unstablewifi on 2021-07-31
```

bogdan@bogdan-HP-250-G3-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
bogdan@bogdan-HP-250-G3-Notebook-PC:~$ lsusb
Bus 001 Device 003: ID 05c8:0226 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 012: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 002 Device 013: ID 0cf3:9271 Qualcomm Atheros Communications AR9271 802.11n
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bogdan@bogdan-HP-250-G3-Notebook-PC:~$ lspci -nnk | grep -iA3 network
bogdan@bogdan-HP-250-G3-Notebook-PC:~$ 

```

---

### Post by chili555 on 2021-07-31
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

### Post by unstablewifi on 2021-08-01
So far internet is stable. Thanks for help. I did disable power management earlier, it didn't help. Wifi is in WPA2 PSK mode and it doesn't have AES option. Mode is 802.11b/g/n/ax. I changed channel width from 40 to 20 MHz. Also, I set persistent channel 6. And I changed 5GHz access point name. I will wait to see if it gets worse and mark thread as solved.

---

