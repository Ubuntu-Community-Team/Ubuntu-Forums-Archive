---
title: "Random Wifi Disconnects Intel Wireless 8265/8275 Ubuntu 17.10"
date: 2017-12-24
forum: Networking &amp; Wireless
---

### Post by cyphecx on 2017-12-24
For a couple weeks I have been struggling with an issue where my wifi with no rhyme or reason stops functioning until I reboot.
I am relatively inexperienced with Linux but I have a handle on the terminal and can follow instructions.
 I am also new to this forum so I apologize if I make any mistakes.

Info:
[LIST]
[*]I am dual booting Ubuntu 17.10 and windows 10 
[*]On a stock Aero 15 laptop from gigabyte 
[*]Output of the /wireless-info script: [URL="https://paste.ubuntu.com/26249030/"]https://paste.ubuntu.com/26249030/
[/URL] 
[/LIST]
[URL="https://paste.ubuntu.com/26249030/"]
[/URL]
What I know

[LIST]
[*]As far as I can tell there is no pattern to when the wifi cuts out 
[*]The wifi icon changes and eventually disappears 
[*]no networks show under the wifi page in settings 
[*]under the word wifi it says unavailable 
[*]Probably not a network manager issue
[LIST]
[*]sudo service network-manager restart has no effect 
[/LIST]
  
[*]lshw -C network shows *-network when wifi is functioning but *-network DISABLED once the wifi is no longer working 
[*]firmware seems up to date although there is something about firmware in the dmesg | grep iwl log but that happens before the wifi cuts out so I dont think it is the issue 
[/LIST]

Things I have tried
[LIST]
[*]Updating the firmware 
[*]Various kernel versions from 4.13 to 4.15 
[*]Reinstalling Ubuntu 
[*]Scouring Google with patent pending Google fu and search terms from things like dmesg 
[*]sudo service network-manager restart 
[*]disabling wifi power saving in TLP 
[*]sudo ifconfig wlp3s0 down/up
[LIST]
[*]returns an I/O error 
[/LIST]
   
[/LIST]

I have been dealing with this for a while so if I remember anything I have tried I will add it.
If I could get this fixed I could finally get on with enjoying ubuntu, any help would really be appreciated!


Edit: I fixed the issue by re-seating my wifi card.

---

### Post by Hadaka on 2017-12-25
Hi, here are a couple items from your wireless diagnostic report
 that are likely causing random drops..

Router..
 'Ridge_Chalet' [AC3]> Infra    1 [COLOR=#ff0000]2.142[/COLOR] MHz  54 Mbit/s 74 &#9602;&#9604;&#9606;_  **[COLOR=#ff0000][[/COLOR]**WPA1 WPA2**[COLOR=#ff0000]][/COLOR]** no         **2 MHz**
 'Ridge_Chalet' [AC1]> Infra 153 [COLOR=#ff0000]5.765[/COLOR] MHz  54 Mbit/s 60 &#9602;&#9604;&#9606;_ **[COLOR=#ff0000][[/COLOR]** WPA1 WPA2**[COLOR=#ff0000]][/COLOR]** yes*  **5 MHz**

 wlp3s0   
          Cell 01 - Address: <MAC 'Ridge_Chalet' [AC1]>
                    Frequency:5.765 GHz
                    Quality=43/70  Signal level=-67 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP **[COLOR=#ff0000]<-[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP **[COLOR=#ff0000]<-[/COLOR]**
                    IE: WPA Version 1
                        Group Cipher : TKIP **[COLOR=#ff0000]<-[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP [COLOR=#ff0000]<-[/COLOR]
 Please access your router configuration and remove the mixed mode..WPA1 WPA2
  Configure as..
 *Make changes to both connections.
  ```
WAPA2 AES...NO...TKIP
```
  ESSID 'Ridge_Chalet' name for both 2GHz and 5GHz..router roams between the 2
         causing random cut offs.
  Configure as..
  ```
 Ridge_Chalet-2
   Ridge_Chalet-5
```
                       
Country code..
  Region: America/New_York (based on set time zone)
  country **[COLOR=#ff0000]00[/COLOR]**: DFS-UNSET <-
Country code is unset-00 This also causes random drops and cut offs.
Please Copy and Paste..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
* Ubuntu 1704 -1710 have a known bug that causes wifi drops and issues
Please Copy and Paste
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
Boot and test wireless.

---

