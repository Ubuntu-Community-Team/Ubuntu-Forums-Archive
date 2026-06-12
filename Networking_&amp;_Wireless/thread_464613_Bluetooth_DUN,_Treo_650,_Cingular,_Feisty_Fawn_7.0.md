---
title: "Bluetooth DUN, Treo 650, Cingular, Feisty Fawn 7.0.4"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by byunique on 2007-06-04
[SIZE="3"]**[COLOR="Blue"]The whole point of this was to use install a bluetooth USB adapter in my Xubuntu/Ubuntu laptop, connect to the Treo 650 via bluetooth and use the Internet connection on the Treo. [/COLOR]**[/SIZE]

Figure I would share my setup, since I found it hard to find documentation of this same setup.

I mainly followed this document, but things didn't follow 100% of course. And thats 1 big reason I would like to share my experiences. I will copy the same steps, and make comments as necessary.
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)
[B]
1. Installation of Bluetooth and Dialup Packages[/B]

"sudo apt-get intall bluez-tuils ppp"

I don't think the bluez-pin was needed since I never seemed to configure it. Other documents led me to think there was a /etc/bluetooth/pin file, but chose not to configure one.

**2. Listing Bluetooth Devices**
"hcitool scan"

this listed the mac address of my treo phone.

I then went into the treo 650 configuration for bluetooth configuration:
a. went into bluetooth, changed it from off --> on, gave it a device name, turned discoverable from no --> yes, dial up networking from off --> on. 

then did a hictool cc your-phone-mac-adress to connect to make pairing connection...

**3. Pairing**

Once this was run, my phone's bluetooth dialogue passkey would show up. I used the default passkey of 1234 and it seemed to take.

"sudo hcitool auth your-phone-mac-address"

This didn't result in anything useful it seems. I would constantly get "not connected". And so it seems, it doens't have to be connected in order to work.... 

Although the auth command didn't seem to work, the connection seemed to be made by running "hcitool con", where it displays active connections.

**4. Configurting the rfcomm device**
sdptool browse your-phone-mac-address

this would return "connection timed out". I just guessed cingular would use "channel1" and was lucky it did!

Edited /etc/bluetooth/rfcomm.conf

refcomm0  {
 bind yes;
 device your-phone-mac-address
 channel 1;
 comment "treo650 PPP connection";
}

Edited /etc/bluetooth/hcid.conf 
passkey "chosemyownpasskey";

sudo /etc/init.d/bluez-utils restart
didn't run this because it didn't exist, yet package was installed...dunno!!!

sudo /etc/init.d/bluetooth restart 
[B]
5. Configure PPP, edited /etc/ppp/peers/cingular[/B]

debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/cingular"
usepeerdns
/dev/rfcomm0 115200
defaultroute
noipdefault
crtscts
lcp-echo-interval 0
lcp-echo-failure 0
ipparam cingular

edited /etc/chatscripts/cingular

TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=1,"IP","WAP.CINGULAR"'
OK      ATD*99***1#
CONNECT ""

I ran "pppconfig" at first, but went around in circles for a hour with it trying to connect and failing. I just  pasted the two config files, allowed it to connect right after that.

**6. Connecting....**

"pon cingular"

Once the connection was initated, here's what showed in var/log/messages:

Jun  1 16:37:21 lattitude pppd[8917]: pppd 2.4.4 started by root, uid 0
Jun  1 16:37:24 lattitude chat[8920]: timeout set to 35 seconds
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nBUSY\r)
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nERROR\r)
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nNO ANSWER\r)
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nNO CARRIER\r)
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nNO DIALTONE\r)
Jun  1 16:37:24 lattitude chat[8920]: abort on (\nRINGING\r\n\r\nRINGING\r)
Jun  1 16:37:24 lattitude chat[8920]: send (^MAT^M)
Jun  1 16:37:24 lattitude chat[8920]: expect (OK)
Jun  1 16:37:24 lattitude chat[8920]: *MRDY: 1^M
Jun  1 16:37:24 lattitude chat[8920]: ^MAT^M^M
Jun  1 16:37:24 lattitude chat[8920]: OK
Jun  1 16:37:24 lattitude chat[8920]:  -- got it
Jun  1 16:37:24 lattitude chat[8920]: send (AT+CGDCONT=1,"IP","WAP.CINGULAR"^M)
Jun  1 16:37:25 lattitude chat[8920]: expect (OK)
Jun  1 16:37:25 lattitude chat[8920]: ^M
Jun  1 16:37:25 lattitude chat[8920]: AT+CGDCONT=1,"IP","WAP.CINGULAR"^M^M
Jun  1 16:37:25 lattitude chat[8920]: OK
Jun  1 16:37:25 lattitude chat[8920]:  -- got it
Jun  1 16:37:25 lattitude chat[8920]: send (ATD*99***1#^M)
Jun  1 16:37:25 lattitude chat[8920]: expect (CONNECT)
Jun  1 16:37:25 lattitude chat[8920]: ^M
Jun  1 16:37:25 lattitude chat[8920]: ATD*99***1#^M^M
Jun  1 16:37:25 lattitude chat[8920]: CONNECT
Jun  1 16:37:25 lattitude chat[8920]:  -- got it
Jun  1 16:37:25 lattitude chat[8920]: send (^M)
Jun  1 16:37:25 lattitude pppd[8917]: Serial connection established.
Jun  1 16:37:25 lattitude pppd[8917]: Using interface ppp0
Jun  1 16:37:25 lattitude pppd[8917]: Connect: ppp0 <--> /dev/rfcomm0
Jun  1 16:37:25 lattitude pppd[8917]: Remote message: PAP access OK
Jun  1 16:37:25 lattitude pppd[8917]: PAP authentication succeeded
Jun  1 16:37:27 lattitude pppd[8917]: local  IP address 10.11.145.103
Jun  1 16:37:27 lattitude pppd[8917]: remote IP address 10.11.145.0
Jun  1 16:37:27 lattitude pppd[8917]: primary   DNS address 209.183.48.10
Jun  1 16:37:27 lattitude pppd[8917]: secondary DNS address 209.183.48.11

**7. Other messages:**
I could then ping [www.yahoo.com](www.yahoo.com)

PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (209.191.93.52) 56(84) bytes of data.
64 bytes from f1.[www.vip.mud.yahoo.com](www.vip.mud.yahoo.com) (209.191.93.52): icmp_seq=1 ttl=53 time=593 ms
64 bytes from f1.[www.vip.mud.yahoo.com](www.vip.mud.yahoo.com) (209.191.93.52): icmp_seq=2 ttl=52 time=563 ms
64 bytes from f1.[www.vip.mud.yahoo.com](www.vip.mud.yahoo.com) (209.191.93.52): icmp_seq=3 ttl=52 time=607 ms
64 bytes from f1.[www.vip.mud.yahoo.com](www.vip.mud.yahoo.com) (209.191.93.52): icmp_seq=4 ttl=53 time=663 ms
64 bytes from f1.[www.vip.mud.yahoo.com](www.vip.mud.yahoo.com) (209.191.93.52): icmp_seq=5 ttl=53 time=555 ms

"netstat -nr"

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.11.240.0     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0

"ifconfig -a"

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:267 (267.0 b)  TX bytes:267 (267.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.11.240.193  P-t-P:10.11.240.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:6783 (6.6 KiB)  TX bytes:3087 (3.0 KiB)


Once the USB bluetooth adapter was inserted in the laptop, here's the relevant /var/log/messages:
Jun  4 18:26:30 lattitude kernel: [111958.520000] usb 1-1: USB disconnect, address 2
Jun  4 18:26:33 lattitude kernel: [111961.052000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jun  4 18:26:34 lattitude kernel: [111961.216000] usb 1-1: configuration #1 chosen from 1 choice


**8. Comments**
to disconnect the connection: "poff cingular"
all the commands were entered in "terminal as root". I used vi to edit files, so you can chose your own editor, like "gedit" in the tutorial. If you don't use root, 
then use sudo.

Good Luck!

---

### Post by digitalbenji on 2007-06-05
That is a great resource!  This worked marvelously for me.  I'm so pleaed, I now have DUN working through bluetooth and my treo on cingular.  You ROCK!  I had all but given up, but your tutorial was a breeze

Thanks again,

---

### Post by byunique on 2007-06-05
Glad it worked! Anything advice you have for others? Was there anything a bit not right about the document or unclear? I wrote the document w/o taking notes, so I doubt it was exact.

---

### Post by digitalbenji on 2007-06-06
Everything worked without a hitch.  I replaced all instances of the term cingular with treo, but that's just me.  I also changed:
Edited /etc/bluetooth/hcid.conf
passkey "chosemyownpasskey";
to the passkey that I used when I paired my devices.

---

### Post by grndslm on 2007-06-06
This is an awesome guide... but does anyone know how the sprint chatscript && /etc/ppp/peers/sprint files should look??

I just found out my vision username & pass...but don't know the syntax for these 2 files!

---

### Post by digitalbenji on 2007-10-21
this worked for me in Gutsy as well!

---

