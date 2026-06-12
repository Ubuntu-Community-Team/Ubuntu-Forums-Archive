---
title: "[ ipw2100 ] :: can't connect"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by JackosKing on 2006-10-09
Hello,

I have a Acer travelmate 370 centrino, on dapper drake.

> root@nono-laptop:/home/nono# lspci | grep Wire
0000:02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:02:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
root@nono-laptop:/home/nono#


I loaded ipw2100 module:
> root@nono-laptop:/home/nono# modprobe ipw2100
root@nono-laptop:/home/nono# lsmod | grep ip
ipv6                  265728  6
ipw2100                88628  0
ieee80211              37064  1 ipw2100


Then I tried to connect with gnome network configuration -> failed.
With the consol:
> 
root@nono-laptop:/home/nono# ifconfig eth1
eth1      Lien encap:Ethernet  HWaddr 00:0C:F1:02:14:62
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:10 Adresse de base:0x2000 Mémoire:e0200000-e0200fff

root@nono-laptop:/home/nono# ifup eth1
ifup: interface eth1 already configured
root@nono-laptop:/home/nono# iwconfig eth1
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@nono-laptop:/home/nono# iwconfig channel 11
Error : unrecognised wireless request "11"
root@nono-laptop:/home/nono#


Someone can help me?

thx.

---

### Post by wieman01 on 2006-10-10
What happens if you do this?
> iwlist eth1 scan
Please ensure that your router is turned on & post the output of this command. Equally post the contents of this file:
> sudo gedit /etc/network/interfaces

---

### Post by JackosKing on 2006-10-10
Hello!
So:
> 
root@nono-laptop:/home/nono# iwlist eth1 scan

eth1      No scan results

root@nono-laptop:/home/nono# iwconfig

lo        no wireless extensions.



eth1      unassociated  ESSID: off/any  Nickname:"ipw2100"

          Mode:Managed  Channel= 0  Access Point: Not-Associated

          Bit Rate= 0 kb/s   Tx-Power: off

          Retry min limit: 7   RTS thr: off   Fragment thr: off

          Encryption key: off

          Power Management: off

          Link Quality: 0  Signal level: 0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc: 0   Missed beacon:0



eth0      no wireless extensions.



sit0      no wireless extensions.

And the content of the intefaces file is:
> auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp

I hope I can use this card without windows drivers emulation:/

---

### Post by wieman01 on 2006-10-10
Please update your "interfaces" file so that I looks like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR="Red"]**wireless-essid ipw2100**[/COLOR]
Using this terminal command:
> sudo gedit /etc/network/interfaces
Then restart the network & please post the output:
> sudo /etc/init.d/networking restart
Am I right in that you are using DHCP, no encryption/authentication (e.g. WEP) with your ESSID being "ipw2100"? Have you installed a firewall such as Firestarter?

Last but not least, please post the output of these commands:
> ifconfig
> iwconfig
> route
This will help a lot if this solution does not work out.

---

### Post by pierko on 2006-11-05
I also have IPW2100.
I can scan the essid around. But I can't connect as kwifimanager says that I'm "out of range" and every essid have "no signal".
How can I solve it ?

---

### Post by Sponge34 on 2006-11-29
> 
root@nono-laptop:/home/nono# iwconfig eth1
eth1 unassociated ESSIDff/any Nickname:"ipw2100"
Mode:Managed Channel=0 Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power:off


The Tx-power:Off is your clue.... the wireless card is switched off...
on this dell inspiron 8500 <fn><f2> toggles the wireless power on and off.

so with the power off i get
eth1      unassociated  ESSID:"2WIRE332"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   

and with power on I get 

eth1      unassociated  ESSID:"2WIRE332"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   


OK - so I still cant get my card to associate with the router - possibly cos of where the router is..... but that is another issue.

S.

---

