---
title: "ASUS R518UA constantly disconnects from Internet"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by gal007 on 2017-04-17
Hi! I'm having some troubles with the Internet connection. I installed Ubuntu 17 in my ASUS R518UA, and sometimes it starts disconnecting every 5 seconds. I get NO notification most of the times, it is just a 'no internet connection' from Spotify ot the Web browser. Some few times Ubuntu tells me that I am disconnected. But the thing is I loose the connection while other computers in the same network do not. SO I tryed everything I found, including:
[LIST]
[*] disabling IPV6 
[*]disabling the power management. this is: [FONT=&amp]wifi.powersave = 2[/FONT] 
[*]and disabling the (protocol??) 11n with: sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=1" 
[/LIST]

The last option made the connection a little bit stable, but now it is randomly doing it again. Most of the times (I think) are when I have the notebook unplugged and just in 'battery mode'.

I saw most people is asked to run an script, so I did it in advance:
[http://pastebin.ubuntu.com/24403947/](http://pastebin.ubuntu.com/24403947/)

Can you please give me a hand? I have no idea about networks and drivers. I just installed Ubuntu 17 because the previous version had even more problems (it was almost impossible to connect with the 16 lts).
Thanks in advance,

---

### Post by chili555 on 2017-04-17
I notice this in your script results:> wlp2s0    IEEE 802.11  ESSID:"[COLOR="#FF0000"]hijas de la cruz 3[/COLOR]"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'hijas de la cruz 3' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  Remarkably, I have worked on several cases where removing spaces in the name of the network improved stability. I know; sounds crazy doesn't it? I suggest that you change the name of your network to hijas_de_la_cruz_3 or else hijasdelacruz3 or something similar.

I also see:> ##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

global
country 00: DFS-UNSETPlease set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Reboot and let us hear your report.

---

### Post by gal007 on 2017-04-23
Hello CHili555! Thanks for your help. Unfortunately I cannot change the id of the network, it is for the campus. You were right, I had no country code. My machine is from USA but as I'm living in Argentina I choose AR. This is the second day I'm trying this setting and the problem persist, but it is less frequent. Mondat morning I will connect the computer to another network, so I can check the whitespaces issue. I will let you know!

---

### Post by praseodym on 2017-04-23
> ```
wlp2s0    Scan completed :
          Cell 01 - Address: <[COLOR="#FF0000"]MAC[/COLOR] 'hijas de la cruz 3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"hijas de la cruz 3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000105b07541
                    Extra: Last beacon: 744ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
Please run 
```

sudo iwlist scan
```
and add the MAC address of your network into the field **BSSID** of the network manager profile

---

### Post by gal007 on 2017-04-23
Hello guys, thanks for your help. Today I discovered what's happening. There are two networks in the campus, and it seems that my computer is constantly disconnecting before checking if the other network is closer (to turn to that one). I was moving today and I realized that close to the router there is no problem, it is just in the 'middle area. I just removed one of the networks and it is working properly right now. I'm so happy now!!! :) I'm sharing it so others can solve the problem, and because it may be a bug (it should ask to disconnect after deciding it will change the network; mine disconnected before and then it connected to the same previous network!)

---

