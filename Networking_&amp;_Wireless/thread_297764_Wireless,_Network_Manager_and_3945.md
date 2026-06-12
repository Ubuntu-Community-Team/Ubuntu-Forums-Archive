---
title: "Wireless, Network Manager and 3945 ?"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by rvickers on 2006-11-11
I've been tackling wireless the last two days and got it so messed up that I had to reload ubuntu. I have a Toshiba Satellite with a PRO/Wireless 3945ABG.
Questions:

1. Does Network Manager allow static IP's yet?
2. I've read a lot of threads where people have had a lot of issues with edgy and the 3945. Does anyone have it working?
3. How risky is it to load Network Manager and if it doesn't work then go back to System-<Networking and wired?
4. I loaded WiFi Radar before I loaded Network Manager, could that have been a mistake?

Thanks :)

---

### Post by wieman01 on 2006-11-11
Don't know all answers to your questions, but here we go anyway:

1. No, not yet. You need to use Wifi-Radar or configure your network manually (my preferred option).
2. No idea...
3. No problem at all. You can uninstall it at anytime you want. No interference with networking as far as I know.
4. You cannot run both at a time. Install either of them.

What's the output of:
> iwlist scan
Does your card see other wireless networks around you?

---

### Post by rvickers on 2006-11-12
rvickers@rvickers-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:B7:3F:1E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=77/100  Signal level=-57 dBm  Noise level=-57 dBm
                    Extra: Last beacon: 52ms ago

sit0      Interface doesn't support scanning.


Thx :)

---

### Post by rvickers on 2006-11-12
Loaded Wifi radar and it sees my wireless and displays at the bottom:
Connect to eth1(127.0.0.1) 
but I can't edit or disconnect and I can't access the Internet.
Any interesting thing, if I enable the wired connect, at the bottom of WiFi Radar I see:
eth1( 198.192.0.1 ) 
which is my dns. :confused: 
Thx

---

### Post by wieman01 on 2006-11-13
Wanna try to set it up manually then? If you uninstall NetworkManager as well as Wifi-Radar & post the contents of this file (run this from command line/terminal):
> sudo gedit /etc/network/interfaces
_**EDIT:**_
Then replace with contents with this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]linksys[/COLOR]
Then restart your network (_after_ unplugging the Ethernet cable):
> sudo /etc/init.d/networking restart
Then do this from command line:
> route
Please post the results.

Are you able to browse the Internet?

---

### Post by louistan3 on 2006-11-13
i have an intel 3945 too.. i got it working with network manager.. i just took out all of the contents of my /etc/network/interfaces file except for the loopback.. so that all my networking connections are handled by the network manager.. im not sure about the static ip's though.. i use dhcp on mine.. 

the 127.0.0.1 is the loopback ip.. at least i thnk so.. 

hope this helps.. il try and help some more.. just ask me the right questions  cause im not sure about what you really need.. :)

---

