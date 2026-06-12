---
title: "ndiswrapper problems with acer 1670"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by crazycucumber on 2007-10-26
hi all , linux / ubuntu newbie so please be kind ! I have done my fair share of reading and trying to work it out myself , here is my issue so far:- 

using acer aspire 1670wlmi  ive done a lspci::

02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

so assume i need to get the windows driver for it and load it using ndiswapper. 

if so ..I did a apt-get install on ndiswrapper-common  and it seemed to install

when i try to use it though I get the error 

mark@ubuntu-laptop:~$ ndiswrapper -i neti2220.inf
Error: no ndiswrapper utils found!

So I am stuck !!!! Thanks for any help

---

### Post by crazycucumber on 2007-10-26
ok figured the first bit , installd the utils from synaptic ,  now get the following error:- 

mark@ubuntu-laptop:~/wifi$ ndiswrapper -i neti2220.inf
couldn't create /etc/ndiswrapper/neti2220: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.


thanks for any help

---

### Post by mve-lamb on 2007-10-26
WELCOME! You need a lot of patience with UBUNTU and LINUX,  and of course a lot of reading but, I'll give you hint: you need SUDO i.e. administrator privilege to run most of network commands.
Be carefull Linux make sence with CAPITAL and small letter!

Try:>  sudo ndiswrapper -i neti2220.inf  :)

and after that ndiswrapper --help to know more...

Lamb

---

### Post by crazycucumber on 2007-10-26
oh dear , school boy error ! 

still more problems though : this is the output now - 

it must be something else i have done wrong. 

mark@ubuntu-laptop:~/wifi$ sudo ndiswrapper -i neti2220.inf
driver neti2220 is already installed
mark@ubuntu-laptop:~/wifi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

 Maybe i should start a new thread for this .

---

### Post by kevdog on 2007-10-26
Cant install the driver twice.  Delete everything and start again

sudo rm -rf /etc/ndiswrapper/*

---

### Post by crazycucumber on 2007-10-29
Thanks , got that working now , + shows up in hardware and software functioning correctly. 
just need to wait till I get back home to try it out on my wireless. 

Should I install anything else to help me, or indeed change any settings from the Roaming one set.  , as I will be travelling to client sites and wanting to attach to some open and wep , wpa networks , I installed the SWS scanner utility and it just keeps crashing. 

thanks again

---

