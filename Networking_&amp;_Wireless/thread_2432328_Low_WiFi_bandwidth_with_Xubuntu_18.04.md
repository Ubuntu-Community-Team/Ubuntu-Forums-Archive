---
title: "Low WiFi bandwidth with Xubuntu 18.04"
date: 2019-11-30
forum: Networking &amp; Wireless
---

### Post by desesperado on 2019-11-30
Hi

I'm running Xubuntu 18.04.3 and facing an extremely low bandwidth in my house's WiFi. It's not any sort of issues with the router since I do get 200 Mb/s of download and 100Mb/s of upoload rates when using Windows 10.

Here's the result I got from the wireless script: [https://pastebin.com/Av7hnw1M](https://pastebin.com/Av7hnw1M)

Thanks in advance.

---

### Post by chili555 on 2019-11-30
I notice this in your wireless info results:

> RipAp                             <MAC 'RipAp' [AC1]>  Infra  5     2432 MHz  195 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     *      
RipAp                             <MAC 'RipAp' [AC25]>  Infra  100   5500 MHz  405 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no          

I suugest that you rename the 2.4 and 5 gHz segments so that your wireless doesn't disconnect to roam among them. I suggest RipAp24 and RipAp50 or some such.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Reboot and let us hear the result.

---

### Post by desesperado on 2019-12-01
Hi chili555.

First of all, let me thank you for stepping in and help me.

> **chili555 said:**
> I notice this in your wireless info results:

I suugest that you rename the 2.4 and 5 gHz segments so that your wireless doesn't disconnect to roam among them. I suggest RipAp24 and RipAp50 or some such.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 
Proceeded as you recommended but unfortunately there's no visible changes in the bandwidth I'm getting, The link to new wireless script output after these changes is the end of my post so you can further investigate.
   
> **chili555 said:**
> Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot and let us hear the result.
```
korrigan@RipAp:~$ sudo iw reg get
[sudo] password for korrigan: 
global
country PT: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

``` 
That's the correct country code, so I had PT to the REGDOMAIN in /etc/default/crda

Link to the wireless script output after the changes: [https://pastebin.com/QKQed7VL](https://pastebin.com/QKQed7VL)

Do you have any other ideas?

---

### Post by chili555 on 2019-12-01
Your router still appears to be on channel 5, an overlapped channel. [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

Please try 1, 6 or 11 and fixed, not autoselect.

---

### Post by desesperado on 2019-12-02
> **chili555 said:**
> Your router still appears to be on channel 5, an overlapped channel. [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

Please try 1, 6 or 11 and fixed, not autoselect.
Ups, something might have not get saved in the router config, without noticing it.

wireless script, 2.4 Ghz - channel 1: [https://pastebin.com/s8AWirCj](https://pastebin.com/s8AWirCj)

wireless script, 2.4 Ghz - channel 6: [https://pastebin.com/B8QPsHp3](https://pastebin.com/B8QPsHp3)

wireless script, 2.4 Ghz - channel 11: [https://pastebin.com/0NfHViPG](https://pastebin.com/0NfHViPG)

wireless script, 5.0 Ghz: [https://pastebin.com/DguTETUg](https://pastebin.com/DguTETUg)

With each I always get a bandwidth between 58 and 65 MB but with my Windows 10 laptop and my Android smartphone the bandwidth is always 200 - 210 MB.

Just hope you haven't run out of ideas.

---

### Post by chili555 on 2019-12-02
> Just hope you haven't run out of ideas.No, but I'm mighty low on new ideas.

First, this thread has some interesting points to make: [https://forums.intel.com/s/question/0D50P0000490WFUSA2/wifi-connectivity-issue-with-intel-wifi-link-5100-agn?language=en_US](https://forums.intel.com/s/question/0D50P0000490WFUSA2/wifi-connectivity-issue-with-intel-wifi-link-5100-agn?language=en_US)

> All the same, you should be able to get a connection rate of ~150 Mbps if connecting using Wireless-N in the 2.4 GHz frequency (using 20 MHz channels), or ~300 Mbps if your router supports legacy devices connecting to 5 GHz frequency (using 40 MHz channels). Some newer routers limit all legacy devices to the 2.4 GHz band.This is directed at Windows users, of course. I wonder if the Linux driver iwlwifi and its associated firmware support the enhanced bandwidth.

As we note, a great many things work perfectly in Linux but not Windows and vice versa.

I note this: > 5   APs on   Frequency:5.5 GHz (Channel 100)Your card does all these frequencies:

> Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHzYou might try another channel, if your router agrees, to see if it helps.

Finally, you might look into replacing the card.

---

### Post by desesperado on 2019-12-03
chili555, thanks for not giving up on this.
> **chili555 said:**
> No, but I'm mighty low on new ideas.

First, this thread has some interesting points to make: [https://forums.intel.com/s/question/0D50P0000490WFUSA2/wifi-connectivity-issue-with-intel-wifi-link-5100-agn?language=en_US](https://forums.intel.com/s/question/0D50P0000490WFUSA2/wifi-connectivity-issue-with-intel-wifi-link-5100-agn?language=en_US)

This is directed at Windows users, of course. I wonder if the Linux driver iwlwifi and its associated firmware support the enhanced bandwidth.

As we note, a great many things work perfectly in Linux but not Windows and vice versa.

I note this: Your card does all these frequencies:

You might try another channel, if your router agrees, to see if it helps.
No luck, unfortunately. Went through all channels and the best I got was 48 MB and with most either got 1 MB or no bandwidth at all.   

Is there anything else you can think of, I could try?
> **chili555 said:**
> Finally, you might look into replacing the card.
Thing is we're talking about a 10 plus year old laptop. Is it worth to buy a new card. Will it be easy to find one that actually works with my router? Not sure, to be honest.

---

### Post by chili555 on 2019-12-03
> Thing is we're talking about a 10 plus year old laptop. Is it worth to buy a new card. Will it be easy to find one that actually works with my router? Not sure, to be honest.Whether it is worh it tou you is a question only you can answer. If you must have 300 Mbps speeds, then upgrade. If 54 is satisfactory, then don't.

In my old laptop, I've upgraded the RAM, the HDD twice and the wireless card. I probably did it mostly because it's fun to see:

```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: XX:2B:B0:DC:45:XX
          [COLOR="#FF0000"]Bit Rate=866.7 Mb/s [/COLOR]  Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  

```I got one of these: [https://www.amazon.com/Intel-Wireless-AC-Network-Bluetooth-7260-HMWWB-R/dp/B00N7474CS/](https://www.amazon.com/Intel-Wireless-AC-Network-Bluetooth-7260-HMWWB-R/dp/B00N7474CS/)

Just be certain that the pin layout matches what you have and that you haven't any whitelist issues. [https://superuser.com/questions/848308/what-is-a-bios-whitelist-request-bios-mod-and-bios-unlock](https://superuser.com/questions/848308/what-is-a-bios-whitelist-request-bios-mod-and-bios-unlock)

---

### Post by desesperado on 2019-12-04
> **chili555 said:**
> .......

Just be certain that the pin layout matches what you have and that you haven't any whitelist issues. [https://superuser.com/questions/848308/what-is-a-bios-whitelist-request-bios-mod-and-bios-unlock](https://superuser.com/questions/848308/what-is-a-bios-whitelist-request-bios-mod-and-bios-unlock)
As it turns out this whitelist issue is a potential deal breaker in what HP laptops is concerned since they do it by definition, or at least they used to until 2013-2014. And since my mode l is older than that, I'm think I'm pretty much screwed.

That said, can you please help me with a few doubts I have, please?

So, what I did manage to find out, from its maintenance and service guide book is that my laptop has 2 WLAN antennas built in so it would be capable of dealing with a dual band wireless card, right?

[ATTACH=CONFIG]284555[/ATTACH]

Again, on the laptop maintenance and service guide book I have this:

[ATTACH=CONFIG]284556[/ATTACH]  [ATTACH=CONFIG]284557[/ATTACH]  [ATTACH=CONFIG]284558[/ATTACH]  [ATTACH=CONFIG]284559[/ATTACH]

which I assume to be the whitelisted wireless cards for my model. But just guessing by their models name, none is dual band capable. Are those assumptions correct, chili555?

If they're correct are you aware of any dual band wireless card that could potential work in this laptop (HP Probook 4150s)?

Once again I thank you for all the help you've provided me.

---

### Post by chili555 on 2019-12-04
> So, what I did manage to find out, from its maintenance and service guide book is that my laptop has 2 WLAN antennas built in so it would be capable of dealing with a dual band wireless card, right?

I'd certainly think so. Are both connectors actually connected? 

[IMG]https://qph.fs.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807[/IMG]

I would suspect so, since the bandwidth is as expected in Windows.

I notice that there are two Intel 5100s listed; one is ABG and the other is AGBN. I think I'd search for the part number 480985-001, the one that includes N, assuming it's available in your country, and see if the image shows two antenna connectors. [https://www.amazon.com/Compaq-480985-001-Wireless-Mini-pci-Intel/dp/B00B1OXYMU](https://www.amazon.com/Compaq-480985-001-Wireless-Mini-pci-Intel/dp/B00B1OXYMU) It does! 

I'd also see if you can compare the part number on your existing card; it it the same?

All of this is, of course, a gamble. I suspect that the real limitation is the driver and firmware available in Linux. The card was manufactured in the days of draft-N and the Linux software just might not support N at all. 

By the way, the process you are following is exactly what I did. I downloaded the service manual and looked for a faster card that fit within the whitelist. The card supplied with my Lenovo was ABGN. I found a card that also does AC on the service manual and got it for $12 on Ebay. Do I actually have any practical use for 400-500 Mbps speeds? Not really.

---

