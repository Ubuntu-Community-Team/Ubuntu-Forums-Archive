---
title: "problem with Linksys Wifi-N Broadband"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by joel_gil on 2007-02-23
hello everyone, as the title say, im havin trouble with the linksys router.

I can get the normal wireless of my college with no problems, the one on my house (2wire modem), but now ive changed internet provider and got the linksys Wireless-N Broadband Router.

I do all the normal things, set the name of the connection, type in th epassword but nothin happens =S

i have no problems at all with any of the other connections. Ive look around in the forums but the other post have problems with their wireless cards or sth, but since all the otehr connections work im sure it isnt that...

please i hope someone can help me.

---

### Post by joel_gil on 2007-02-24
noone who can help yet?

please please help.... T_T

---

### Post by handaxe on 2007-02-24
Forgive if you have covered this... you do know that this router works?

i.e you can connect to it under W'doze? I once spent hours troubleshooting a "linux" wifi problem only to have my wife tell she too was getting dropped under Windows :) Issue was the router.

HA

---

### Post by joel_gil on 2007-02-24
unfortunately my router works completely fine, i hav eno trouble usin it under windows, other friends also connnect to it perfectly (under windows) but it wont work on linux.

Also the wifi card seems to b fine, as i said in the 1st post i can connect to other wireless networks with no prolbem... 

i also downloade the 'network manager' package but didnt do any difference.

please plase heeeelp!!!

---

### Post by Floppyjoe on 2007-02-24
Does your network interface also support the wifi-n protocol? Is the router set to only one speed or mixed?

---

### Post by handaxe on 2007-02-24
I will try to help  but it is 3 am here!

As a previous poster wrote about [SIZE=-1]802.11**n **protocol, ensure your card supports it. Google is your friend..

If not or you are not sure, then change the router to [/SIZE][SIZE=-1]802.11b or g (or mixed b&g)[/SIZE]

If still with trouble:

```
sudo iwconfig "interface" (replace "interface" with whatever eth1, ath1 etc)
```This should produce something like:

```
eth1      IEEE 802.11g  ESSID:"bohlinyates"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:18:39:D3:78:84   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxx   Security mode:open
          Power Management:off
          Link Quality=73/100  Signal level=-66 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9180   Missed beacon:0

```In my case, my essid and AP is seen. 

alternatively, try ```
sudo iwlist "interface" scanning
```

(there are other useful modes under iwlist)


If essid seen, then set router to open security (ie no passphrase).  Test connect. Once ok, try wep and work to wpa if thats what you want.

If this is all known to you my apologies. My guess is the [SIZE=-1]802.11[B]n bit.

HA
[/B][/SIZE]

---

### Post by joel_gil on 2007-02-27
hello, thanks for the help until now although it didnt solve the problem i learn a bit more about linux.

Anyways, i tried both the commands u said and i dont geet the essid from the network i want.i get others on the area but nt mine.

About what u said of the -n protocol... well if in windows it works i dont see why wouldnt it on linux, so my guess is the card is fine...

maybe theres an exrta config i have to do on linux so it supports the -n thing... ?

all comments are useful, ill try everything...

thanks in advance

---

### Post by joel_gil on 2007-02-27
hey so this is what i get now with sudo iwlist "eth1" scanning:
------------------------------------------------------------------------------------------
          Cell 03 - Address: 00:18:F8:81:68:93
                    ESSID:"Nextel"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=69/100  Signal level=-64 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 124ms ago
------------------------------------------------------------------------------------------
and with iwconfig "eth1":
------------------------------------------------------------------------------------------

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4957   Missed beacon:0
------------------------------------------------------------------------------------------

i hope this info can tell someone what my problem is so they can help me =S

thanks in advance again!!

---

### Post by Floppyjoe on 2007-02-27
Is your wireless adapter a USB or Built in one?
Post the output of :
```
lspci
```
and:
```
lsusb
```

This will show you if your wireless card supports the -n protocol.
If you are dual booting and it works on Windows, it may be using a slower b or g protocol when connecting in Windows.

It might be worth having a look at your /etc/network/interfaces file too.
```
sudo gedit /etc/network/interfaces
```

---

### Post by joel_gil on 2007-02-28
my wireless is built in...
i have a dell inspiron 6400... i dont know if tahts any help.

the output of lspci:
------------------------------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
------------------------------------------------------------------------------------------

the output of lsusb:
------------------------------------------------------------------------------------------
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
------------------------------------------------------------------------------------------

i dont use any usb except of my wireless mouse hehe.

and my interface file is like this:
------------------------------------------------------------------------------------------
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
------------------------------------------------------------------------------------------

it does seems strange that it says "eth2" instead of "eth1" which is my wireless interface... but again im not very fluent with codes language =S

hope this info can help


again thanks in advance, and thanks for the help uve already given me!

---

### Post by Floppyjoe on 2007-02-28
This is your wireless card here:
> 0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Notice that it supports A B G protocols but not N. You should still be able to use this interface device but it will not use your router to its fullest speed capacity.

I also noticed that you had network-manager installed. For network-manager to work you need to disable all the network interfaces in System/Administration/Networking and comment out all but the lo interface in /etc/network/interfaces. That means to put a # in front of the lines in /etc/network/interfaces except for the ones that have the word lo in it.

---

### Post by handaxe on 2007-02-28
Hi,

First off, I have a ipw3945 and it works on 802.11b&g.

If it works in Windows then indeed it potentially should work under linux. BUT remember, hardware without a driver is useless, SO the real question is not so much about the card but whether the intel linux driver (a closed binary) support 802.11n? Clearly the Windows driver does.

Did you try the router on 802.11b or g? Feel this is NB.

(For your info: 802.11n is a specification under development that some card makers brought out "prematurely". As far as I know it is not really production ready but the forces of commerce ......)

Secondly,

Assuming that you have driver & other hardware issues sorted out, you might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Deb install. Also installs a tray icon BUT does not put an entry is startup. Do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

Wicd has its own forum (details in link above). Use that if you will.

Judging by my experience, wicd may not reconnect automatically for you after a resume (suspend/hibernate) but that is a minor inconvenience IMO.  The developer actively works on these problems.

HA

---

### Post by spotman on 2007-02-28
a little OT, but I have the same router.  And the same wireless nic in my laptop.

I use ssh a lot and the router tends to just drop tcp connections after spurious amounts of time, no matter what your doing or if its idle, etc..  

I searched for a solution and came to the world of running linux on the router.  The distribution im using is suuuper easy, and as long as you read a wiki for 15 minutes, its probably not going to destroy your router.  It comes with a web interface to control everything, and my router has been stable for weeks now.

cheers, and GL

dd-wrt link: 
[http://www.dd-wrt.com/dd-wrtv2/index.php](http://www.dd-wrt.com/dd-wrtv2/index.php)
(the v24 betas are compatible with your router)

---

### Post by handaxe on 2007-03-02
Hi,

A small matter - note that using open-wrt
 likely will void your warranty....
HA

---

### Post by joel_gil on 2007-03-07
heey WICD is great
connected me in few mins

thanks u all for ur patience with me hehe and for ur help, all of em were very useful...

i learn more thanks to the commuity =)

---

### Post by handaxe on 2007-03-08
Not to be picky, but it is a huge help if you could reveal what exactly worked.  Kind of gives closure....:)

HA

---

### Post by joel_gil on 2007-03-08
hehe sorry.
i thought it was clear but ur rught.


hehe i installed the WICD and i detectad isntantly all the wireless LANs around... icludin the one id been tryin to make work.

i jsut typed in the router passsword and that was it!

=)

thank u all again

---

