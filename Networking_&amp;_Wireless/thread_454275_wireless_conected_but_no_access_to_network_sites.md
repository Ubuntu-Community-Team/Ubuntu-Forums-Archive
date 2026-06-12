---
title: "wireless conected but no access to network sites"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by drorl on 2007-05-25
hi.
i'm connected to the internet throw a wireless concection or at least that's what shows (i have two bars blue in the gnome network manager and it says "wireless connection to 3com(the network) 51%", but i can't access any internet site.
this is the iwconfig of my eth1 (my wireless port)
eth1      IEEE 802.11g  ESSID:"3Com"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0D:54:F9:78:04   
          Bit Rate:48 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/100  Signal level=-78 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:503   Missed beacon:0
any ideas?
thanks
dror

---

### Post by matoxxx on 2007-05-25
are you using DHCP or STATIC IP ? have you set up DNS server right ?

---

### Post by om~namas~ganga on 2007-05-26
Are you using  encryption key ?   

If so, remember to specify  the following on the list above the textbox on the  screen that  shows up when you enter the key manually , you need to specify this parameter too

For me ( Running Ubuntu 7.02 Feisty with GNOME )  , the options are

   - Hexadecimal  WEP 128/64  or  
  -  Password Sentence WEP 128 ) 
   - ASCII WEP 

In my particular case, its  only works when I select "Hexadecimal WEP 128/64" 

and its happily  working  sweetly fast with no errors and no disconnections. 

good luck

---

