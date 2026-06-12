---
title: "[SOLVED] Signal strength:93%, but no wifi access..."
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by pognonec on 2007-03-10
Hi from a brand new beginner (bad start, right?). I installed UBUNTU 6.10 on a Dell Inspiron 8100. I really like the look and feel of it, after Mandriva.
 I configured my internet connections as usual (I use fix IPs, I know my DNS, gateaway and all). 
I want to use my wifi connection (ra0 with my card), and after entering all requested information in connection properties, great, I get a good signal!
But no access to the internet :( 

Here are some info I got from my terminal, in case it would help:

daddy@daddy-laptop:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


ra0       RT2500 Wireless  ESSID:"colombo"
  
        Mode:Managed  Frequency=2.452 GHz  Access Point: 00:07:CB:53:78:83
   
       Bit Rate:54 Mb/s   Tx-Power:0 dBm
   
       RTS thr:off   Fragment thr:off

          Link Quality=66/100  Signal level=-53 dBm  Noise level:-192 dBm
          
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sit0      no wireless extensions.



daddy@daddy-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


ra0       Scan completed :
          
          Cell 01 - Address: 00:07:CB:53:78:83
                    
                    Mode:Managed
                    
                    ESSID:"colombo"
                    
                    Encryption key:on
                    
                    Channel:9
                    
                    Quality:65/100  Signal level:-50 dBm  Noise level:-193 dBm


sit0      Interface doesn't support scanning.


Thanx in advance for any help/suggection!

Philippe

---

### Post by spd106 on 2007-03-10
Can you post the output of **ifconfig** and **ip route** please?

Are you able to ping the gateway?

---

### Post by jml on 2007-03-10
After you post the output of the commands suggested by spd106, there are a few more things to consider.  If your wireless access point has any encryption runnig, temporarily turn it off and see if you can connect.  If you can, then you know its just a configuration problem.

I have also read on this forum that Ubuntu does not do well with fixed ip addresses (especially if you are using network manager,) many suggest using DHCP.

If you have a separate broadband modem (either cable or DSL,) connected to your access point, try turning both off for about five minutes.  Then plug in first the modem and then the access point.  My Carter Cable modem will at times loos its ability to connect.  Power cycling the device seems to help.  Hope this helps.

Joe

---

### Post by pognonec on 2007-03-11
> **spd106 said:**
> Can you post the output of **ifconfig** and **ip route** please?

Are you able to ping the gateway?
Thanx for your help. 
I can ping the whole world without any problem.
Here are the info requested

daddy@daddy-laptop:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


ra0       RT2500 Wireless  ESSID:"colombo"
  
        Mode:Managed  Frequency=2.452 GHz  Access Point: 00:07:CB:53:78:83
   
       Bit Rate:54 Mb/s   Tx-Power:0 dBm
   
       RTS thr:off   Fragment thr:off

          Link Quality=66/100  Signal level=-53 dBm  Noise level:-192 dBm
          
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sit0      no wireless extensions.



daddy@daddy-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


ra0       Scan completed :
          
          Cell 01 - Address: 00:07:CB:53:78:83
                    
                    Mode:Managed
                    
                    ESSID:"colombo"
                    
                    Encryption key:on
                    
                    Channel:9
                    
                    Quality:65/100  Signal level:-50 dBm  Noise level:-193 dBm


sit0      Interface doesn't support scanning.

---

### Post by mrmonday on 2007-03-11
in firefox, type about:config, type ipv6 in the filter bar, and double click the only value... Can you get online now? if so post again... you need to do something else so you can do updates.

---

### Post by pognonec on 2007-03-11
> **jml said:**
> If your wireless access point has any encryption running, temporarily turn it off and see if you can connect.

Yes, I'd like to... But I am connected via a "Freebox" (a broadband DSL modem, in France, that also works as a router). This system does not accept open wireless settings... 

> **jml said:**
>  I have also read on this forum that Ubuntu does not do well with fixed ip addresses (especially if you are using network manager,) many suggest using DHCP.

I have a server running behind my router.This is why I have to go with fixed IP.

> **jml said:**
>  If you have a separate broadband modem (either cable or DSL,) connected to your access point, try turning both off for about five minutes.  Then plug in first the modem and then the access point.  My Carter Cable modem will at times loos its ability to connect.  Power cycling the device seems to help.  Hope this helps.
Joe

I tried that too, but to no avail.

Ooops, one detail: when I configured my Ubuntu, I accidentally entered the same IP for eth0 and ar0 (wifi) settings. I fixed that now (but it still does not work, even after reboot).
Actually, I just tried the wired connection on this machine too (I am using others for these posts), and I got the same symptoms: I can ping, but Firefox is not able to connect to any site!!! 
Is that suggesting a more general connection problem??

---

### Post by pognonec on 2007-03-11
> **mrmonday said:**
> in firefox, type about:config, type ipv6 in the filter bar, and double click the only value... Can you get online now? if so post again... you need to do something else so you can do updates.

Did as you said, got:
preference name: network.DNS.disabledIPv6
Status: default
Type: boolean
Value: false

After double clicking on the text, it became bold fonts, and said:
[B]preference name: network.DNS.disabledIPv6
Status: user set
Type: boolean
Value: true[/B]

After reboot, still no Firefox working :(

---

### Post by mrmonday on 2007-03-11
Try 64.233.167.99 does it get you to google?

---

### Post by pognonec on 2007-03-11
Actually no. I tried in Firefox, and as a ping in a terminal window. None worked (but a control ping to another outside address worked fine).

---

### Post by mrmonday on 2007-03-11
[Try this]("http://www.ubuntuforums.org/showthread.php?t=358749#post2226758"). Hope it helps

---

### Post by pognonec on 2007-03-11
I entered my DNS addresses as explained, rebooted, and ... still nothing.
But I appreciate you guys trying to sort out that mess with me.

---

### Post by pognonec on 2007-03-13
Hi everybody!
After spending quite a lot of time, and reading/trying things suggested in reply to my post, I finally got one of my laptop to work on wifi with Ubuntu 6.10: a HP Pavilion zd8000 (the one I am using right now), which is equiped witha Broadcom card.
I "simply" followed that post:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
activated my card in the System/Administration/Networking panel, and there it goes!
Thanx to all of you for your help.

---

