---
title: "wi-fi disabled Please help"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Aditya Bhavaraju on 2009-12-17
Hi!
I have a problem with the wi-fi connectivity on my sony vaio laptop,I am using 9.04 jj.I recently installed 9.04 using a CD and after that the wi-fi worked just fine but after a while I was prompted o update by the update manager.After the reboot my wi-fi connection seems to be broken.I donot understand why this happened.I browsed through the replies posted b many members in the networking and wireless fora but to no avail.I get the following information when I issue the following command. 
lspci -v | grep -i Network03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

the iwconfig gives the following information

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
ppp0      no wireless extensions.

The network manager  doesnot show any signal and the pppoeconf does not locate a wlan access concentrator....
Please help me out.
Regards
Aditya

---

### Post by cariboo on 2009-12-17
What is the output of:

```
sudo lshw -C network
```

---

### Post by drpjkurian on 2009-12-17
> **Aditya Bhavaraju said:**
> Hi!
I have a problem with the wi-fi connectivity on my sony vaio laptop,I am using 9.04 jj.I recently installed 9.04 using a CD and after that the wi-fi worked just fine but after a while I was prompted o update by the update manager.After the reboot my wi-fi connection seems to be broken.I donot understand why this happened.I browsed through the replies posted b many members in the networking and wireless fora but to no avail.I get the following information when I issue the following command. 
lspci -v | grep -i Network03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

the iwconfig gives the following information

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
ppp0      no wireless extensions.

The network manager  doesnot show any signal and the pppoeconf does not locate a wlan access concentrator....
Please help me out.
Regards
Aditya

Hi,Aditya
The wifi became non operational due to kernel updates. It is a usual phenomenon for some drivers. This can be solved by recompiling your drivers.
Your wireless card seems to be Atheros, so you can try my Howto thread of installing Madwifi drivers for your Atheros card.
The URL is [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

Best of luck
Dr Kurian

---

### Post by jajodo on 2009-12-17
The atheros cards cause serious grief with the new kernel and certainly with Karmic.  The forums are full of posts on this.  I tried Dr. Kurian's excellent instructions for Mad WIFI on my Asus EeePC 1000ha but this only worked briefly. Also wasted hours (or days per my wife) trying Ubuntu, NBR, Eeebuntu, Puppy Linux, Mint, PCLinux OS (nearly worked), Easy Peasy and probably more.

Finally I just popped in a broadcom card from a deceased HP Pavilion dv6000 laptop I had lying around, and instantly had 4 bars and perfect wireless.  This is a 10 minute surgery- 2 screws and antenna.  If you have no luck with mad wifi this is a practical (though admittedly not elegant) solution.  Countless wifi cards are available on ebay as well for 10-25 dollars.  Good luck!

---

