---
title: "Ubuntu 18.04LTS - Archer T4UH AC1200 does not work"
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by skidders01926 on 2018-08-25
Hi - I have tried to install a TP-Link Archer T4UH version 1.0 AC1200 wifi adapter on my Ubuntu 18.04 LTS system and so far have been unable to get it to work. I am getting to the internet via a borrowed TP-Link TL-WN822N wifi adapter - so at least I can make this post!  :)

I have tried various drivers including the rtl8812au-dkms package via apt install rtl8812au-dkms and so far *nothing* seems to make the T4UH AC1200 adapter work. In fact, it doesn't even show up on the output from the lsusb command -even though the green light stays on steadily most of the time. 

Looking at the output from the network-info script the T4UH adapter is seen by part of the system but the dmesg output looks strange - the T4UH never gets properly fired up. I am wondering whether I might have a broken T4UH and am not sure how to prove it either way. The vendor driver doesn't compile and I have tried a couple of others plus the one available with the ubuntu distribution and am at a loss. Has anyone solved a similar problem please? 
The network-info output is at:  

             [http://paste.ubuntu.com/p/kfc8GxHcHY/](http://paste.ubuntu.com/p/kfc8GxHcHY/)

Thanks in advance for any and all help!

---

### Post by chili555 on 2018-08-25
Please check your pastebin. It contains no data. Please try again.

---

### Post by skidders01926 on 2018-08-26
Thanks Chili555 - I should have checked that! 

Here is the new pastebin URL for wireless-info.txt:   [http://paste.ubuntu.com/p/nCjCdSqVn7/](http://paste.ubuntu.com/p/nCjCdSqVn7/)

This time I have checked the URL content too. 

At the time I ran wireless-info there were 2 USB wireless adapters attached to Ubuntu: 
     -  TP-Link TL-WN822N which works (thankfully, so I can type this!)
     - TP-Link T4UH V1.0 which is the problem

There are several configured connections to the same wireless network (called VodafoneConnect55939218) - I am hoping to connect the T4UH to the same network, then remove the TL-WN822N adapter. 

Thanks again...Skidders

---

### Post by chili555 on 2018-08-26
Your device actually looks pretty healthy. What we see in your paste gives us, perhaps, some useful clues:>  Cell 01 - Address: <MAC 'VodafoneConnect55939218' [AC1]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"VodafoneConnect55939218"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000066250b9f73
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKDid you specifically select channel 12 for your router? I believe it is an overlapped channel and therefore not ideal.

I suspect that auto channel select chose channel 12. You know about auto channel select, don't you? That's the mechanism where the channel bounces all over hoping that your wireless card can keep up. Here is an interesting thread about it: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

We also see TKIP and mixed mode WPA and WPA2. Yikes!

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
```

Proofread carefully, save and close the text editor.

After making these changes, detach the TL-WN822N, reboot and tell us if there is any improvement.

---

### Post by praseodym on 2018-08-26
It loads 2 drivers:
```

sudo modprobe -rfv rtl8812au 8812au
sudo modprobe -v 8812au
```
Re-plug the stick

---

### Post by skidders01926 on 2018-08-26
Thanks Chili555 and Praseodym, 
                                                        I am amazed (and delighted!) to tell you that I am typing this update on a system which has only the TP-Link AC1200 T4UH USD wifi adapter attached - the TL-WN822n can now go back to its rightful home!

I cannot say that I fully understood your advice and how it fixed the problem, but what I do want to say is that your help was astoundingly quick, clearly articulated and accurate. THANK YOU. 

I expected that my problem might get a little bit of attention in a week's time or maybe more. Instead, I made the original post 22 hours ago; now the problem is fixed. That's a phenomenal turnaround - especially after I messed up the posting of the original diagnostic information. I would not have even considered router changes.  

Thanks to both of you for your efforts and attention - you are stars! 

Skidders

---

