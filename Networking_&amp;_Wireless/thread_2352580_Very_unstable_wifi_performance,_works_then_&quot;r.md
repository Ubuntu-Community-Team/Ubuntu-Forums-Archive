---
title: "Very unstable wifi performance, works then &quot;resolving, looking for &quot; for ever."
date: 2017-02-13
forum: Networking &amp; Wireless
---

### Post by fred-lorrain on 2017-02-13
I have installed Ubuntu Studio 16.4 on my Thinkpad T510 and the wifi is almost unuseable, it connects fine, but then takes forever to open a page. It will work fine randomly, then just quit working to where I have to reboot to use any browser. I originally installed 16.10 but had the same issue, so thought the LTS distro might not have this issue. I was wrong, I tried setting IPv6 to "Ignore" and added the google dns servers in the connection properties, which seemed to help, but then I had the same very slow performance, talking worse than dialup. Then I turned IPv6 back on, which seemed to help for a few minutes, but it is still nothing anybody would put up with. (Before installing Ubuntu I was running windows 10 with no wifi problems.) [ATTACH]273695[/ATTACH]

---

### Post by chili555 on 2017-02-14
Please see:>           Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"Dorknet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015669bddab
                    Extra: Last beacon: 46ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication SupportedYour driver, your hardware and your Doc Chili hate hate hate TKIP.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

After rebooting the computer and router, post back and tell us if the connectivity is improved.

---

### Post by fred-lorrain on 2017-02-15
Thanks very much for your suggestions. I performed the steps you mentioned, I set AES encryption from "mixed",  "sudo iw reg get" showed USA which is correct (not Iceland), 20mhz instead of 20/40. I have fixed the channel. I stay connected, but after a few minutes, or a few links I have unusable Internet again. I've been making wireless work in Linux since back in the FWcutter days, and feel strongly that there is something seriously wrong with the wifi driver here. There are many posts about it, to which I notice you reply. What is going on here? I'll be going back to older flavors of Ubuntu if a solution eludes me for much longer. It seems a step back for Linux, wireless used to be a pain then it became a breeze, now it's a pain again in my case, and many others. Thanks for your help again, do you have any further suggestions?

---

### Post by chili555 on 2017-02-15
> feel strongly that there is something seriously wrong with the wifi driver here. My own laptop uses the exact same driver and it works perfectly. I don't believe it is an overall defect. 

[http://www.dslreports.com/speedtest/10583218](http://www.dslreports.com/speedtest/10583218)

Let's try a couple of other steps. Let's disable power saving in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Let's try a driver parameter:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Is your router set to channel 1? There are three other networks on 1 in your scan, but only one on 11. You might try 11.

Let's also be certain that you have the newest possible firmware:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.163_all.deb
sudo dpkg -i linux-firmware*.deb 
```

Reboot and let us hear your report.> I've been making wireless work in Linux since back in the FWcutter days,Likewise; it was pretty near impossible when I started in Linux.

---

### Post by fred-lorrain on 2017-02-18
Thanks again for your suggestions, I went through the steps you described and it seemed to have had a good effect for awhile, but the performance went back to horrible after 20 mins or so. This morning I set the DNS servers to the ones reported by the router from my ISP instead of the 8.8.8.8, 8.8.4.4 I had added as secondary DNS, so far it seems to be stable. We shall see.. Thanks again

---

### Post by fred-lorrain on 2017-02-19
Back to unstable performance, almost unusable really. I did set the router to channel 11, but the performance is a joke. I have read other threads about bad wireless performance but they are using different hardware in most instances. I'm not sure how to proceed, I don't want to go back to Windoze, I guess I'll give this a few more days hoping some update will come down the pike and address this deal killer of an issue.

---

### Post by chili555 on 2017-02-19
> **fred-lorrain said:**
> Back to unstable performance, almost unusable really. I did set the router to channel 11, but the performance is a joke. I have read other threads about bad wireless performance but they are using different hardware in most instances. I'm not sure how to proceed, I don't want to go back to Windoze, I guess I'll give this a few more days hoping some update will come down the pike and address this deal killer of an issue.
May we see a new wireless info as in your initial post?

---

