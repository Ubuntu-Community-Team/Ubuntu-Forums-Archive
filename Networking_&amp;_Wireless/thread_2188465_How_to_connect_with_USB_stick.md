---
title: "How to connect with USB stick?"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by rva1945 on 2013-11-17
I try to connect using a Tp-Link WN722N USB wireless antenna.

sudo ifconfig wlan2 up
and it's light turns on.

sudo iwlist wlan2 scan
and it founds some networks. Now I can't connect:

sudo iwconfig wlan2 essid rva1945network key s:mypassword

gives

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan2 ; Invalid argument.

?

---

### Post by chili555 on 2013-11-17
> sudo iwconfig wlan2 essid rva1945network key s:mypasswordThis is appropriate if you have removed Network Manager and your encryption method is WEP with the key being an ASCII string. I'll bet neither of those is true. Is it? 

Is Network Manager not working for you as expected? If you do indeed rely on WEP for security, I strongly recommend that you stop everything and change to WPA2-AES.

---

