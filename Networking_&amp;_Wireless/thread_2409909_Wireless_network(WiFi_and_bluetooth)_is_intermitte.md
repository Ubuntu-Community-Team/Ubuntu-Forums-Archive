---
title: "Wireless network(WiFi and bluetooth) is intermittent after upgrading to Ubuntu 18.04"
date: 2019-01-08
forum: Networking &amp; Wireless
---

### Post by saravanakumar2 on 2019-01-08
Recentlt, I have upgraded my OS from 16.04 to 18.04 LTS. Since then, I have been facing a lot of issues with my wireless network. The connection is extremely slow and intermittent. I get disconnected randomly and often. 

 My Laptop model : HP15 - bs179tx. Any help would be greatly appreciated. 

Also, please let me know if you need another information.

---

### Post by chili555 on 2019-01-08
Indeed, we need additional information. Fortunately, some smart people created a script that gathers everything in one step and creates a report.
Please start here:  [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by carlsonv on 2019-01-08
I am having same issue here is my info.  [http://paste.ubuntu.com/p/DjbfjCtxqW/](http://paste.ubuntu.com/p/DjbfjCtxqW/) any help is much appreciated

kind regards
mark

---

### Post by chili555 on 2019-01-08
> **carlsonv said:**
> I am having same issue here is my info.  [http://paste.ubuntu.com/p/DjbfjCtxqW/](http://paste.ubuntu.com/p/DjbfjCtxqW/) any help is much appreciated

kind regards
markPlease don't hijack someone else's thread. Please start your own new question.

---

### Post by saravanakumar2 on 2019-01-09
Here is a link to the report the script created : [http://paste.ubuntu.com/p/GVxGt9Bvf5/](http://paste.ubuntu.com/p/GVxGt9Bvf5/)

---

### Post by chili555 on 2019-01-09
Is this a router over which you have administrative priveleges?> 
Cell 01 - Address: <MAC 'Rajasekaran' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Rajasekaran"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000029b0ce666
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKFirst, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by praseodym on 2019-01-09
options rtl8723de ant_sel=1

Tried "ant_sel=2"?

---

### Post by saravanakumar2 on 2019-01-26
First of all, sorry for the very late response.

I am made the changes to the router as you said.(Although I am not home anymore and not using that router).

I have changed my regulatory domain explicitly as you said. But the WIFi and Bluetooth are still not working. In fact, now the WiFi is not even detecting any connections.

What should I do now?

---

### Post by praseodym on 2019-01-26
Try installing the BT firmware (and only that!)

[https://superuser.com/questions/1301390/bluetooth-not-working-for-realtek-rtl8723de-hci0-didnt-find-patch-for-chip-i/1322067#1322067](https://superuser.com/questions/1301390/bluetooth-not-working-for-realtek-rtl8723de-hci0-didnt-find-patch-for-chip-i/1322067#1322067)

---

### Post by jeremy31 on 2019-01-26
If saravanakumar2 would fix the Secure Boot signing keys I could make a dkms fix attempt on the bluetooth.  It might be in BIOS settings to load default keys

---

### Post by saravanakumar2 on 2019-02-03
I tried the solution given in the link. (even though I don't really understand what those steps does)

While trying to install the kernel I encountered the following error:

> Warning: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
Secure Boot not enabled on this system.
dpkg: dependency problems prevent configuration of linux-image-unsigned-4.20.6-042006-generic:
 linux-image-unsigned-4.20.6-042006-generic depends on linux-modules-4.20.6-042006-generic; however:
  Package linux-modules-4.20.6-042006-generic is not installed.


dpkg: error processing package linux-image-unsigned-4.20.6-042006-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-unsigned-4.20.6-042006-generic




---

### Post by saravanakumar2 on 2019-04-07
Hi Jeremy: 

Here is the result : [https://paste.ubuntu.com/p/fSTgBRxwq6/](https://paste.ubuntu.com/p/fSTgBRxwq6/)   you asked for.

My WiFi and Bluetooth are still not working.

Thanks.

---

### Post by jeremy31 on 2019-04-07
Ok ```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot and try

---

### Post by saravanakumar2 on 2019-04-09
This worked! Thank you so much!!!
I have been facing this issue for the past 6 months! I cant thank you enough! Thank you very much!!!

---

