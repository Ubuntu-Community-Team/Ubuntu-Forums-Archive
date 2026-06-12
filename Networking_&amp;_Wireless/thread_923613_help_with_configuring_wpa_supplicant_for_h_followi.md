---
title: "help with configuring wpa_supplicant for h following network"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by arunvir on 2008-09-18
This is what I get when I scanned my network after a new configuration I made:-
> 
                    Address: 00:1E:40:40:C4:36
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


I setup WPA-PSK and enabled the WEP encrytion in it.(I have attched my screenshot on how I did it in my router.)

I was using WEP at first. Then Got on to WPA-PSK.
Is this correct? Can I have a network like this having both WPA-PSK and WEP?

I'm able to work with WEP or WPA-PSK seperately.....

I just want to know whether using both gives me additional strength against attackers???? or should I use WPA-PSK alone......

my neighbor uses WPA-PSK that I have resorted to now.....
(I just want to be slightly secure than what he is........)

Note:- I have hidden my access point that my neighbor has not done.....
I do employ MAC and IP Filtering(I dont think he does those....... )

I just want someone to tell me whether to use WPA-PSK with WEP is better than WEP or WPA-PSK seperately...... and how I should go about configuring wpa_supplicant for the above network..... It gives me the following error:-

> 
Line 8: invalid cipher 'WEP-40'.
Line 8: failed to parse group 'WEP-40'


this error when I try to give the following as my configuration file
> 
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="somenetwork"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="somepassphrase"
	wep_key0=somenumero
	wep_tx_keyidx=0
}




Help and advice will be highly helpful!!!!!!!!!!
thanks in advance!!!!!!!!!!!!

Till someone gives their opinion I'll be playing my keyboard.......

:guitar::guitar::guitar::guitar::guitar:

---

### Post by arunvir on 2008-09-18
ok I found that WEP-40 should be WEP40 actually......... but even then which is better???????


WPA-PSK with tkip or WEP and WPA-PSK

CAN I go for something like WPA-PSK with AES or

WPA-PSK with AES and TKIP
Answers are welcome????

I'm in middle of a jungle......... really someone can help me with useful advice.......

---

