---
title: "Slow file transfers on my 802.11g wlan (both samba and ftp)"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by PuleX on 2008-01-13
Just recently I installed a PCI wireless network card in my desktop pc, so I could get rid of the wires to my router. However, what I have noticed (and don't like) is that file transfers from my Ubuntu Gutsy deskop to/from our home network server over the wireless connection are painfully slow. However, wireless file transfers from the network server to a Windows XP laptop are _much_ faster: 

*Example: transfering a 350 MB file* 
Home network server to Gutsy desktop:   1 hour
Home network server to Gutsy desktop: 1 hour
(I tried both FTP connections and via Samba sharing)
Home network server to Windows XP laptop: ca 5 minutes 

All systems are using 802.11g. 

What stumps me is the difference between the Windows and Ubuntu system. So I was thinking this may be connected to the driver for my wireless networking card.  

My network card is: 
```
roel@poseidon:~$ lspci | grep Network
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI 
``` 

This is what iwconfig says: 
```
roel@poseidon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"Zeus"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:90:D0:F3:A0:BF   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` 

And the Ralink modules are loaded (rt61pci and rt2x-modules): 
```
roel@poseidon:~$ lsmod | grep rt
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rt61pci,rc80211_simple,rt2x00pci,rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib

``` 

(It could be that the rt61pci and the rt2x-modules are conflicting, but I couldn't find anything about it online.) 

Does anyone have a clue what is going on here? Thanks in advance!

---

### Post by krazyj on 2008-01-16
Hey there, Im trying to get the same problem fixed. Heres a link to my thread so you can follow it and hopefully it can be of help to you:
[http://ubuntuforums.org/showthread.php?t=668902](http://ubuntuforums.org/showthread.php?t=668902)

---

### Post by PuleX on 2008-01-17
Krazyj, thanks for the link. 
I'll subscribe to your thread, maybe that will provide me with a fix for my issue.   :)

---

