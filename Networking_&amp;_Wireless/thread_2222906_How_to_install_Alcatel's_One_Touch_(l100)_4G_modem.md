---
title: "How to install Alcatel's One Touch (l100) 4G modem in a Ubuntu 14.04?"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by smigmh on 2014-05-08
I've tried using Alcatel's [One Touch 4G USB modem]("http://www.alcatelonetouch.com/global-en/products/mobile_broadband/one_touch_l100v.html#.U2u-TPldWaQ") on a newly installed Ubuntu 14.04, but with no luck. The carrier is Portugal's Optimus Kanguru.

Following suggestions online, I've installed usb-modeswitch, usb-modeswitch-data, wvdial and comgt.

When I plug it in, NetworkManager's applet adds the option to enable Mobile Broadband. I enable it, but when I try to create a new connection, the combo box has no devices in it. Only the "Any device" option. I set it up anyway with a multitude of all possible APN's I could find (incl. none) but when I try to connect, it immediately fails.

Following instructions online, I've also attempted to connect with wvdial, by running:

sudo wvdialconf
sudo wvdial

with the following result:

Sending: ATDT*99#
Waiting for carrier.
Timed out while dialing. Trying again.
Sending: ATDT*99#
Waiting for carrier.
Timed out while dialing. Trying again.

(and so on...)

I also tried using different APNs in /etc/wvdial.conf to no avail.

lsusb shows the device as:

Bus 001 Device 010: ID 1bbb:011e T & A Mobile Phones

usb-devices shows this:

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=011e Rev=00.00
S:  Manufacturer=USBModem
S:  Product=Mobile Broad Band
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan

---

### Post by jfilipemo on 2014-06-23
Não testei em ubuntu, mas em Mac e em Windows e no router só consigo fazer a ligação manualmente quando o led pisca verde (uns 7 segundos). Se não acertar no alvo durante esse momento, tenho de aguardar mais 36 segundos enquanto pisca laranja, até voltar a ter uma nova oportunidade. No APN e restantes configurações não é preciso por nada, pode ir tudo em branco. O problema é fazer a ligação no momento certo.

---

