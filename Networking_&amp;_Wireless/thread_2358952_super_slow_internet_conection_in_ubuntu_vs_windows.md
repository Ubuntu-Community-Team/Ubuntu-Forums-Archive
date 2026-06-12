---
title: "super slow internet conection in ubuntu vs windows on dual boot"
date: 2017-04-19
forum: Networking &amp; Wireless
---

### Post by yonibettan on 2017-04-19
hello

i just installed ubuntu 16.04 on dual boot with windows 10 and my internet conection is really slow comparing windows 10.
[ATTACH=CONFIG]274642[/ATTACH][ATTACH=CONFIG]274643[/ATTACH] (ubuntu is the lower one)

i ran the wifi-info script and here are my result :
[ATTACH]274644[/ATTACH]

i have seen an answer when searching that tell the problem is the MTU (mine is 1500 as same as in the other answer) but when i tried to change it acording to the described solution i recived an MTU even lower of ~1480... 

this is really frustrating and it will be great if some can point me in the right direction.

NOTE: i am fresh new to ubuntu so imagine you are explaining a possible solution to a complete idiot...

thanks very much for any help

---

### Post by chili555 on 2017-04-19
I notice this in your script:

> Cell 01 - Address: <MAC 'Crazy House_2.4' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Crazy House_2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001129b71181c
                    Extra: Last beacon: 90216ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

Remarkably, I have worked on several cases where removing spaces in the name of the network improved stability. I know; sounds crazy doesn't it? I suggest that you change the name of your network to CrazyHouse_2.4 or some such without spaces.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

---

### Post by yonibettan on 2017-04-24
hey chili and thanks you very much for your quick reply!
i was without network so it took me time to respond.

i tried what you had told me to check and unfortunattly it still don't work as expected

1. i test this problem with 3 different router on 3 deiffrent cities and the problem occured in all 3 so i doubt it is related with my router settings.
2. i have made a small research and i have notice my kernel is in version 4.4 and my intel AC-7260 last driver is supported till 4.2 kernel version - it is possible that the problem is related to that? 
3. i have tried also with an external network adapter and speed was ~7MB (better but still....) - do i need to downgrade my kernel version or maybe purchass a new internal wifi adapter?

thanks

---

### Post by chili555 on 2017-04-24
> i have notice my kernel is in version 4.4 and my intel AC-7260 last driver is supported till 4.2 kernel version - it is possible that the problem is related to that? That means that the 7260 is supported by default in kernel versions 4.2 and later. That includes, of course, 4.4 and what I run, 4.10. Downgrading your kernel to the earliest that the 7260 is supported will not be productive.

You are loading the -17 firmware; that is the latest available.> Cell 01 - Address: <MAC 'Crazy House_2.4' [AC1]>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=[COLOR="#FF0000"]18/70[/COLOR] Signal level=-92 dBm 
Encryption key:on
ESSID:"Crazy House_2.4"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000001129b71181c
Extra: Last beacon: 90216ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSKIs it possible that the antenna wires are not connected securely? [http://yehar.com/blog/wp-content/uploads/2010/08/028.jpg](http://yehar.com/blog/wp-content/uploads/2010/08/028.jpg) In this image, they are the white and black wires.

I am about 9.5 meters from my router and I get:> Cell 01 - Address: xx:2B:B0:DC:45:xx
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=[COLOR="#FF0000"]54/70[/COLOR]  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
I also run a 7260.

---

### Post by yonibettan on 2017-04-25
i oppned my dell 2 month ago and checked the antena - it was perfectly ok. furthermore the network works fine on window (dual boot).

if its help when i am really close to the router it work just fine but in my room there is a poor connectopn (only on ubuntu - on window the speed is correct even in my room)

i use dell XPS15 ... this start to be relly frustrating, my ubuntu is worthless without a proper network conection :(
i hope a solution will be found

---

### Post by harmoniser on 2017-04-27
Same here, on a Dell Vostro with an Intel Wireless 3165. Signal is much weaker than with Windows on the same machine.

---

