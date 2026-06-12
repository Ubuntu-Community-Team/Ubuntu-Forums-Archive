---
title: "RaLink RT2500 Problems In Heron"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by redDEADresolve on 2008-05-29
My wireless network card, a Linksys WMP54G, is a listed under [COLOR="Blue"]lspci[/COLOR] as:
> 
Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

I have used it since Dapper Drake and not had any problems, but since installing Hardy Heron my internet speeds have been considerably slower. 

When I output [COLOR="Blue"]iwconfig[/COLOR], I get:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point:
          [COLOR="Red"]Bit Rate=1 Mb/s[/COLOR]   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I noticed my Bit Rate was set at 1Mb/s.

I found that I could change my bit rate speed by using this command
> [COLOR="Blue"]sudo iwconfig wlan0 rate 54M[/COLOR]

[COLOR="Blue"]iwconfig[/COLOR] now outputs:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point:
          [COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My internet connection is still slow and I am still getting the same speeds. The changes also do not "stick" after a reboot, I have to manually change the bit rate after each login.

Other Computers and Devices connected to my router are not experiencing this problem. Please help, I built this box specifically with parts that worked 100% in Linux and now I'm unable to do anything productive and my main computer.

---

### Post by kwacka on 2008-05-30
its unlikely you'll get the full 54Mbs rate (unless you are within a couple of feet of the source) and forcing your card to operate at this speed can slow it down.

Try the usual default of ```
sudo iwconfig wlan0 rate auto
``` to see if there's any improvement.

---

### Post by mschering on 2008-06-06
Follow this howto and it will work as expected:

[http://ubuntuforums.org/showthread.php?t=766724&highlight=rt2500&page=2](http://ubuntuforums.org/showthread.php?t=766724&highlight=rt2500&page=2)

---

