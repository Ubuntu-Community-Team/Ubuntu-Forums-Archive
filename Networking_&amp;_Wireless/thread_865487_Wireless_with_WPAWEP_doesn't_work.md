---
title: "Wireless with WPA/WEP doesn't work"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by panda2004 on 2008-07-20
I installed Ubuntu 8.04 with Vista dual bootable on my laptop Dell Vostro 1500. The installation went smoothly, thanks to all the forum posts.

However, I'm having difficult to make my wireless work with WPA enabled home network. I tried to adjust the route with no security, with WPA, or with WEP enabled choices, and get the following result:
1. Wireless worked under Vista with no security, with WPA enabled, or with WEP enabled, without any issue.
2. I installed ndiswrapper according to forum posts. Under Ubuntu, it can connect using wired connection, or wireless connection without any security.
3. Then I started adding wireless security. My route is configured using WPA-TKIP. I used network manager to type in pwd, it just tried to connect, but failed acquiring IP address.
4. I tried the method from sticky post "Wireless Security - WPA1, WPA2, LEAP, etc. ", I installed wpa-supplicant, manually config interface file, restart networking, reboot, still no luck.
5. I then tried install wicd package. It has very nice gui, but still no connect to WPA wireless network.
6. I changed route setting from WPA to WEP, and repeated step 3,4,5, same result: can't connect as long as wireless is encryption enabled. 

I've tried all methods and read all posts in the past 2 days. 
Now I exhausted all ideas after I tried all ways from forum and online search. Please, Any help/suggestions/comments is highly welcome!

---

### Post by panda2004 on 2008-07-20
By the way, the wireless scanning can find all hotspots around, but can't connect to any WPA/WEP enabled network.

lspci:

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

 iwconfig:
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


iwlist scanning
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:A9:CF:8D:F2
                    ESSID:"the essid"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-30 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-104
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by sputnikkk on 2008-07-20
Its becoming apparent to me that wireless networking in linux is FUBAR.

Ive got mine working with the Network Manager GUI - but only until the next reboot. Then its change the WPA setting and re enter the passkey phrase.

Hundreds of threads - no real solutions other than ...

No WAP2 / No static IP's and no Linksys or Broadcom chipsets

---

### Post by Tigin on 2008-07-20
guys i d try this how-to , it is the last one on forums seems like promising :)

/cheers



[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

---

### Post by sputnikkk on 2008-07-20
Tigin thanks for that link ...  

I had seen that already but - am looking to not add windows to this system - seems like a hack?

So is what the linux community telling me as a new ubuntu user ... That if you want to effectively run Wireless Networking securly in Linux - you need to install "Windows software"?

very very confusing ....

---

### Post by Tigin on 2008-07-20
in your case madwifi drivers come to my mind , i am using madwifi drivers , i have found an easy solution for my atheros wifi card .

BUT i am not sure if there is a madwifi driver for your wireless card .

Besides correct me if i am wrong , whie using ndiswrapper , i believe you do not use windows it self , you are using only a file ( written by hardware company which i believe you have already payed its worth when you bought the hardware ) which does not belong to microsoft :)

---

### Post by panda2004 on 2008-07-20
Thanks for all the reply. 
One thing confused me is some people in the forum says no problem with WPA wireless while others has even using similar chipset and configuration. 
Anyway I can see more detailed log information to figure out why no IP acquiring from the route while using WPA?

---

### Post by panda2004 on 2008-07-20
> **Tigin said:**
> guys i d try this how-to , it is the last one on forums seems like promising :)

/cheers



[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

went through the process again, still no luck
Wifi indicator lights on, signal is strong 100%, but just can't connect. So frustrating. Any suggestions?

---

### Post by Tigin on 2008-07-20
try some of these


[http://ubuntuforums.org/showthread.php?t=846258](http://ubuntuforums.org/showthread.php?t=846258)



[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)   



> **mexpolk said:**
> I've found a post that fixed the problem, thanks to **[Nathan.Flow]("http://backports.ubuntuforums.com/member.php?u=233875")** who posted it **[here]("http://backports.ubuntuforums.com/showthread.php?t=650729&page=2")**.

1. Download latest stable **[ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/")**. And compile and install it (make, make install).
2. Download your latest AND CORRECT drivers. I've an XPS M-1330 with Broadcom BCM4310 USB, and I downloaded drivers from **[here]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819")**.
2. Follow **[this]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")** instructions.

Hope that works for you also.






/cheers

---

### Post by panda2004 on 2008-07-20
Thanks for the reply and tips. I tried again according to the step by step instruction, started with removing all preinstalled stuff. 
Somehow, I managed to connect wireless with WEP, but still no luck with wireless with WPA. 
For now, I just changed my route from WPA to WEP so that I can use this laptop. However, I still have no idea why one works while the other way doesn't. It costs me three days to get at least something working....
seems like if ubuntu wants to gain more popularity, it really needs to improve its network handling. Other than that, it's a charm to install it...much faster than vista installation.

---

