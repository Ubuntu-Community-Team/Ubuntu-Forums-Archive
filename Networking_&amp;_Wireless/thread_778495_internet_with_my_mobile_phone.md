---
title: "internet with my mobile phone"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by dboira on 2008-05-02
I'm tryng connect my laptop to internet with my mobile phone. I have read that I must create a file like this
[Dialer YoigoUSB] 
Modem = /dev/ttyACM0 
Phone = *99***1# 
Username = '' 
Password = '' 

and exec the command
sudo wvdial YoigoUSB

but I also want tunning the mtu of my device with
sudo ip link set 'device' mtu 'value'

my problem is which device select; I obtain the devices with
ip l
but I don't know which is the correct of the list I obtain

---

### Post by plastichero on 2008-05-02
hey buddy ...
wanna get connected by your mobile phone?
it's only the matter of 3 commands.

1. connect your mobile using USB
2. open a terminal and run
[COLOR="DarkOrange"][FONT="Courier New"]sudo wvdialconf /etc/wvdial.conf[/FONT][/COLOR]
it'll show you all available modems (also the modem no. of the cell)
3. open this file and edit the username and password with this command:
[COLOR="#ff8c00"][FONT="Courier New"]sudo mousepad /etc/wvdial.conf[/FONT][/COLOR]
or [COLOR="#ff8c00"][FONT="Courier New"]sudo gedit /etc/wvdial.conf[/FONT][/COLOR] 
4. get connected:
[COLOR="#ff8c00"][FONT="Courier New"]sudo wvdial[/FONT][/COLOR]


if you need further in-depth help .. you can visit:
[http://shubuntu.blogspot.com/](http://shubuntu.blogspot.com/)

---

