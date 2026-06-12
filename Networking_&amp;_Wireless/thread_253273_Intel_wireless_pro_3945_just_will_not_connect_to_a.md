---
title: "Intel wireless pro 3945 just will not connect to access point"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by hepkat63 on 2006-09-08
Hi All,
I have been reading the forum with interest as I just cannot get my wireless to connect. I too have a Dell Inspiron 6400 with the Intel Wireless chip. I can certainly see my access point - 5/5 signal, but it just will not connect no matter what I do.
I have tried WEP 64 bit, 128 bit - no luck. Open system, shared key - even no passwords at all - but it just will not connect up.
So, I cracked it and rebuilt the laptop back to windows spec (yuk) and of course it worked perfectly @#$$#!
so, rebuilt the laptop again with latest ubuntu 6.06 , downloaded all the updates and patches and tried again - still the same.
Stupid thing is, i bought the laptop to use wireless and it is the only thing not working.
Can some one please point me in the right direction as I am going crazy here. If the wireless card can see the access point, there must be something really silly and simple I can do to connect. I am just using gnome interface. I did download the kde wireless assistant and tried to connect using that - but same ' connection failed ' error. Is there a log or something in ubuntu that you can view to see WHY it is not connecting?
thanks
Steve

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

### Post by jbmech006 on 2007-11-20
Hi,
I am also having trouble connecting to my wireless-b access point. I have the same card wireless pro 3945. My wireless can see the network but it wont connect. Other computers can connect to the access point so I'm pretty sure its this card. I tried modifying the /etc/network/interfaces but it didn't work. 

Here's what my network adapter sees:

eth1      unassociated  ESSID:"Matrix"  Nickname:"Matrix"
            Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:68:08:A4   
            Bit Rate:0 kb/s   Tx-Power:16 dBm   
            Retry limit:15   RTS thr:off   Fragment thr:off
            Encryption key:148A-2EDE-683E-BBB7-5B2T-EA8F-97  Security mode:open
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:734   Missed beacon:0

The access point is a Linksys, not sure if that matters though.

---

