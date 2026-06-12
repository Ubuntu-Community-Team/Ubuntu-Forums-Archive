---
title: "Network sometimes OK sometimes very slow"
date: 2018-04-02
forum: Networking &amp; Wireless
---

### Post by mringer on 2018-04-02
L-UB 14.04, Firefox 59.0.2 (latest). I have done:

```

sudo apt update 
sudo apt dist-upgrade

```

and sometimes the net runs fast, sometimes slow. Typically, in Firefox, 
I click a new site, it either takes an awful long time to load or times out.
I append (I hope) the output of wireless-info but I dont think this is
actually a wireless problem as it sometimes happens when I connect
by wire. Please what should I do to try to diagnose a non-wireless 
problem? Thank you

[wireless info](http://paste.ubuntu.com/p/cZzDb5nTSg/)

---

### Post by chili555 on 2018-04-02
> Cell 01 - Address: <MAC 'AAISP-rd4' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-3 dBm  
                    Encryption key:on
                    ESSID:"AAISP-rd4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000dfd520df
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKIs this a router or access point over which you have administrative privileges? If so, I'd change it to WPA2-AES, sometimes known as CCMP.

I am also suspicious of the DNS nameservers:> DNS:             217.169.20.20
    DNS:             217.169.20.21
You might try 8.8.8.8 and 8.8.4.4 instead, like this:

[IMG]http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png[/IMG]

Change both the ethernet and the wireless.

---

