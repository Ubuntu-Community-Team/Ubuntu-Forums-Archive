---
title: "internet connection asks for the wrong key"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by hockeyhead019 on 2008-10-20
ok guys i have a wireless card which is showing my network fine and stuff but when i go to connect to it the gui asks for a wep 128 passphrase instead of the actual 64bit hex key... any reason y it would do this? and anybody got a quick fix? 

thanks

---

### Post by Asgar on 2008-10-20
ja jy sal jy gat uit hail met sudo maar jy is nog a doos vir al die kak wat jy nou vra.

---

### Post by hockeyhead019 on 2008-10-20
wtf? kinda looking for real help haha

---

### Post by Asgar on 2008-10-20
Ek weet van help, I install unbuntu on XT. you can not claim the same.

---

### Post by hockeyhead019 on 2008-10-20
ummm you're right because i don't know what your trying to say to me haha but does anybody have a serious answer?

---

### Post by blue13130 on 2008-10-20
post a screenshot of the window please.

There should be an option to change the type of key that you have to input.  On mine I remember selected an option to input a hex key.

---

### Post by hockeyhead019 on 2008-10-20
well ya i tried that... like it's a drop down bar and i choose the 64 hex but then it tries to connect and the two blue balls swirl in the top right corner and then they stop and it asks for a 128 passphrase again

---

### Post by Monotoko on 2008-10-20
You want the option saying "64/128 Hex Key" or something similar, click show key, then type your key (if there are people around that you dont want to see the key, dont click show key, but if not, its always best to, as you can double check what your typing)

---

### Post by hockeyhead019 on 2008-10-20
ya i tried that and retried it... and then i checked the key on my other computer and if worked fine (windows XP tho) and then put it in again it did the same thing... asked for a 128 passphrase

---

### Post by blue13130 on 2008-10-20
I am not sure why that is happening.  Are you sure your wireless card is fully supported in Ubuntu?  Double check the hex key you are inputting, perhaps you wrote it down wrong?  Are there any other security settings on the router preventing you from connecting like a MAC filter?

---

### Post by hockeyhead019 on 2008-10-20
hhhmmmm a mac filter? idk what that is... and i attempted to set it up via the terminal and when i got to the step which says "sudo dhclient" it test the connection or whatever it does but then it says that it didn't recieve an incoming address and that the router was "sleeping" or something to that extent... forgive the vaugeness but i'm on my xp system which is dual boot so i don't have it in front of me at the moment...

blue if there was a mac filter how would i know and how would i disable it?...

ok wait used google to answer my question about the mac filter... no it doesn't have a mac address filter to answer your question

---

### Post by blue13130 on 2008-10-20
Post the output of the following commands:
lspci
iwconfig

---

### Post by hockeyhead019 on 2008-10-20
ok i will restart my system go in and then get the result and post... please keep an eye on the thread blue cuz you might be able to help and this has been driving me crazy haha

---

### Post by hockeyhead019 on 2008-10-20
ok here it is... sorry for the double post haha 

```

**This is the lspci output**
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem

**ok now this is the output of dhclient which I mentioned earlier**
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:50:d4:6f:30
Sending on   LPF/ath0/00:11:50:d4:6f:30
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1a:a0:98:23:0b
Sending on   LPF/eth0/00:1a:a0:98:23:0b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database &#8211; sleeping.

**this is the output for iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
wifi0     no wireless extensions.
ath0      IEEE 802.11g  ESSID:"Poogie"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-61 dBm  Noise level=-96 dBm
          Rx invalid nwid:1553  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by blue13130 on 2008-10-20
Hello Hockeyhead,

I just searched your card type in the forums and looks like lots of people are having trouble with it...I searched for AR2413.

This post look promising, the user says they were never able to get WEP working but was able to use WPA no problem.  Perhaps you should try that out.
[http://ubuntuforums.org/showpost.php?p=5882850&postcount=3](http://ubuntuforums.org/showpost.php?p=5882850&postcount=3)

---

### Post by hockeyhead019 on 2008-10-20
ok well i truly do appreciate your help blue... and idk i guess i'll try and get my dad to change the security... but that's probably not gonna happen but thank you for your help anyways. 

cheers

---

