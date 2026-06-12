---
title: "How do I set up an RT61 wireless card on feisty?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by mrmonday on 2007-04-21
Hi all.

As the title asks: How do I set up an RT61 wireless card on feisty?

I have used these guides:

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

Which worked on edgy, but all they did on feisty was to make it stop detecting my wireless card. What can I do?

Thanks.

---

### Post by jogege on 2007-04-21
My edimax pci card works without any problem on Feisty without any modifications. ONly thing is that DHCP does not work and I have to configure the IP address using networking. If you are trying to use network manager, it might not work.

---

### Post by mrmonday on 2007-04-25
Apparently, here is going to be a new guide for this chipset on the wiki soon which includes how to do it on feisty :D Anyone know who is doing it, so I can get in touch with them?

Thanks.

---

### Post by Smokersroom on 2007-04-25
> **jogege said:**
> ONly thing is that DHCP does not work and I have to configure the IP address using networking.

I'm a noob, how do you configure the IP, and how do I find out what it is?

Thanks in advance!

---

### Post by stadt on 2007-04-25
Make sure to use ra61.ko not ra61pci.ko (both are deliverd with feisty, no need to compile anything from outside)

1. disable Network Manager

either by removing it it, or - more elegant - by disabling it:

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus/event.d/25NetworkManager stop

create two files (named 'NetworkManager' and 'NetworkManagerDispatcher') containing only 'exit' in

/etc/default/NetworkManager
/etc/default/NetworkMangerDispatcher

Step 2:

edit /etc/network/interfaces 
Note: replace 'n' by the number reported on your system, e.g. on mine it's ra1
Note: static is ways more reliable that using dhcp, with dhcp you have sometimes to wait several minutes until you get a valid connection.

Quote:

auto ra'n'
iface ra'n' inet static
address 192.168.x.x (replace x by the necessary address)
netmask 255.255.255.0 (have a look at your router if thats correct)
network 192.168.x.0 (replace x with correct subnet)
broadcast 192.168.x.255 (replace x with correct subnet)
gateway 192.168.x.x (your router address)
pre-up ifconfig ra'n' down
pre-up iwpriv ra'n' set AuthMode=WPAPSK (or any other authenication method you have set-up in your router, e.g. WPA2PSK)
pre-up iwpriv ra'n' set EncrypType=TKIP (or AES, as choosen in your router)
pre-up iwconfig ra'n' essid MYESSID (your SSID as set in your router)
pre-up iwpriv ra'n' set WPAPSK=MyEncryptionKey (Encryption passphrase as set in your router)
pre-up ifconfig ra'n' up
wireless essid MYESSID (your SSID as set in your router)

step 3:

reboot and never touch NetworkManager

works here perfect with a RA61 based MSI card, more stable and faster than XP with latest Ralink drivers.

---

### Post by Smokersroom on 2007-04-25
Great thanks!

How do I find out the correct subnet? Sorry, I'm new to this...

---

### Post by stadt on 2007-04-25
> **Smokersroom said:**
> Great thanks!

How do I find out the correct subnet? Sorry, I'm new to this...


Maybe my terms where not quite correct (I'm no native spaeker).

But e.g. if you have set your router (or your router ist set ...) to an ipaddress

all according ipaddresses inside your local network must be inside the same range.

e.g:

your router is set to 192.168.0.1

the you can select for your network-card 192.168.0.2, or 3 or 5 (up to 254)

all other settings (e.g network, broadcast ...) must follow the scheme 192.168.0.....

Example B:if your router is set to 192.168.159.1

your cards can range from 192.168.159. 2 up to 254

all other settings (e.g network, broadcast ...) must start with 192.168.159.

---

### Post by Smokersroom on 2007-04-30
None of the above works...

Thanks for your help, but windows is calling me back.

---

### Post by Clang on 2007-04-30
[wicd]("http://wicd.sourceforge.net/") is the only thing that works for me, you'll have to uninstall network manager.

---

### Post by tiuito on 2007-05-01
Hi,

after 2 weeks of hard work i've finally set up my wireless net:)  Like you i've read many tutorials but i only had success after reading this: 

[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709)


In my case the problem was with my dns, wich was not responding, because i was giving the wrong adress. 

Read this HOWTO and say something.

tiuito

---

