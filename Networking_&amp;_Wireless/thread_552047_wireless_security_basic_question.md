---
title: "wireless security basic question"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by linuxted on 2007-09-16
I know this is basic but my intuition tells me something is amiss and I've been unable to find the solution by scanning the posts.

I have got my wireless router working (yay! thanks to this forum) and I put a password using the "Administration->Network->Properties" GUI.  However, I just don't think this has done anything to the router.  I say this because I would expect one to configure the wireless router and the wireless card for a password "handshake"...

Thanks, 
linuxted

Just in case, here is some info:
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:4C:C5:00   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:4C:C5:00
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:95:EA:51:41
                    ESSID:" "
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:16:01:DF:57:B6
                    ESSID:"WOO"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK

---

### Post by wieman01 on 2007-09-16
It has not done anything to the router at all. The scan results confirm that encryption is turned off ("NETGEAR"), so my recommendation is that you enabled WPA2 (AES, CCMP) on the router and use that instead. The only question is whether your wireless card & driver do support WPA. 

I see you are using "ndiswrapper", Is the WIndows driver WPA or WPA2 capable? Do you see such an option when you open Network Manager?

---

### Post by mojoman on 2007-09-16
I have a netgear wireless router using wep and in order to set the password I have to log into the router first, which I normally do using a browser to connect to 192.168.0.1. After the password in the router is set the same password is set in the computers that use the netword and they then 'shake hands'. Or have I totally misunderstood what you're getting at...?

---

### Post by linuxted on 2007-09-16
> **wieman01 said:**
> It has not done anything to the router at all. The scan results confirm that encryption is turned off ("NETGEAR"), so my recommendation is that you enabled WPA2 (AES, CCMP) on the router and use that instead. The only question is whether your wireless card & driver do support WPA. 

I see you are using "ndiswrapper", Is the WIndows driver WPA or WPA2 capable? Do you see such an option when you open Network Manager?

When I open Network Manager (I assume that is the "System->Administration->Network" GUI) only have  WEP hex and ASCII.

I have a Netgear router and wireless card (WGR614v7 WGS311) according to the website it does have WPA encription though.   I take it my next step is to enable WPA on the router and card?  Any guidance would be appreciated on that one...

---

### Post by linuxted on 2007-09-16
> **mojoman said:**
> I have a netgear wireless router using wep and in order to set the password I have to log into the router first, which I normally do using a browser to connect to 192.168.0.1. After the password in the router is set the same password is set in the computers that use the netword and they then 'shake hands'. Or have I totally misunderstood what you're getting at...?

That may be the way to go.  I tried logging onto [http://192.168.0.1](http://192.168.0.1) and it doesn't find anything :(

I apologize for the basic questions and appreciate the help

---

### Post by mojoman on 2007-09-16
> **linuxted said:**
> That may be the way to go.  I tried logging onto [http://192.168.0.1](http://192.168.0.1) and it doesn't find anything :(


Hmm, do you know if this is the IP number? I think that's the number they use but I can't swear that there are no other alternatives. Anyway, try to ping it and see if you get a response
```

ping -c 3 192.168.0.1
```

(this pings it three times)

Are you connected to the Internet at all?

/mojoman

---

### Post by linuxted on 2007-09-16
> **mojoman said:**
> Hmm, do you know if this is the IP number? I think that's the number they use but I can't swear that there are no other alternatives. Anyway, try to ping it and see if you get a response
```

ping -c 3 192.168.0.1
```

(this pings it three times)

Are you connected to the Internet at all?

/mojoman

I am connected to the internet but the ping has 100% packet loss.  I'm not sure if that is the right IP address either

---

### Post by mojoman on 2007-09-17
> **linuxted said:**
> I am connected to the internet but the ping has 100% packet loss.  I'm not sure if that is the right IP address either

If you're connected to the internet then your router most likley have another IP. 

The output of 'ifconfig' should give you the computer IP. A visit to [www.whatismyip.com](www.whatismyip.com) should reveal your external IP, i.e. the IP from your ISP. I don't know any command to find out the router IP (there must be one though...?) but normally it's the same as your computers IP but ending with 1. For exammple, my computer have 192.168.0.4 and my router have 192.168.0.1. Use ifconfig to find out your IP and substitute the last number with 1. That, I think, should be the router IP.

/mojoman

---

