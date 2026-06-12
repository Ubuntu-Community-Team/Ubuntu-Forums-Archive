---
title: "WPA Wireless Woes - Got Card Installed Though"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Mierkat on 2006-12-23
OK, so first off I'm 100% new to Linux and much to my suprise I was able to get my wi-fi card installed via ndiswrapper "netbc564      driver installed, hardware present" so I know I'm good there. However, I cannot connect to my WPA enabled wireless network. I am at a complete loss as to how to do this.

I looked at other threads but only got confused. :(

---

### Post by Mierkat on 2006-12-23
Oh, and I should note that when I type iwconfig I get the following...

> 
eth1      IEEE 802.11b/g  ESSID:"Some Secret Place"  Nickname:"Broadcom 4306"
              Mode:Managed  Access Point: Invalid   
              RTS thr:off   Fragment thr:off
              Encryption key:0000-0000-0000-0000-0000-0000-00   Security mode:restricted
              Link Quality:0  Signal level:0  Noise level:0
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And, the reason why my ESSID is there is because I tried to configure my network with ndiswrapper but get stuck when trying to do the key restricted command "Error : unrecognised wireless request "xxxxxxxxxx"".

---

### Post by wieman01 on 2006-12-23
Don't use ESSID's with spaces... That will be a problem. Second, there is a HOWTO in my signature for WPA. Give it a go.

---

### Post by Mierkat on 2006-12-23
> **wieman01 said:**
> Don't use ESSID's with spaces... That will be a problem. Second, there is a HOWTO in my signature for WPA. Give it a go.

Yeah I saw your HOWTO already and was having a hard time, but maybe it was because of the spaces? I will change it and try again. Thank you!

---

### Post by wieman01 on 2006-12-23
Let us know what the exact error message is, please. The spaces are definitely a problem though...

---

