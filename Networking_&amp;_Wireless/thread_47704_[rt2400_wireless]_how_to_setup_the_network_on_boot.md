---
title: "[rt2400 wireless] how to setup the network on boot"
date: 2005-07-09
forum: Networking &amp; Wireless
---

### Post by roblubbers on 2005-07-09
hello everybody,

I downloaded the drivers for the rt2400 from sourceforge.
I compiled the module and it works great.
The module is loaded automatically because i made the entry  rt2400 in /etc/modules.
I also made a line in the aliases file where it says ra0 = rt2400 so that is no problem either
To /etc/network/interfaces i added the line  'iface ra0 inet dhcp' 


But to get the network started i have the execute a selfmade script which contains this:

sudo ifconfig ra0 up
sudo iwconfig ra0 channel 11
sudo iwconfig ra0 essid NETWORKNAME
sudo iwconfig ra0 mode managed
sudo ifup ra0

if this is executed my network connects to my wireless router and i have a connection. The ip is set through dhcp

how can i have my network configured (for all users)at boot without having to run any script myself.

(the options under the kde control center do not help at all)

---

### Post by leperisland on 2005-07-09
[QUOTE=roblubbers]hello everybody,

I downloaded the drivers for the rt2400 from sourceforge.
I compiled the module and it works great.
The module is loaded automatically because i made the entry  rt2400 in /etc/modules.

I also made a line in the aliases file where it says ra0 = rt2400 so that is no problem either
To /etc/network/interfaces i added the line  'iface ra0 inet dhcp' 


But to get the network started i have the execute a selfmade script which contains this:

sudo ifconfig ra0 up
sudo iwconfig ra0 channel 11
sudo iwconfig ra0 essid NETWORKNAME
sudo iwconfig ra0 mode managed
sudo ifup ra0

if this is executed my network connects to my wireless router and i have a connection. The ip is set through dhcp
[/QUOTE]
[COLOR=Red]Hello - I am a REAL newbie here so excuse the probably stupid questions... Please tell me how you do this selfmade script and how it is excecuted - I have no idea! Thanks so far though this looks really useful[/COLOR]

---

### Post by roblubbers on 2005-07-10
that's the problem, i have to execute it by hand.

i made the script in nano (but gedit also works)
and saved it as ra0.sh

i execute it by typing
sh ra0.sh

---

### Post by roblubbers on 2005-07-10
I've got it!

i added the following lines to /etc/init.d/bootmisc.sh

ifconfig ra0 up
iwconfig ra0 channel 11
iwconfig ra0 essid NETWORKNAME
iwconfig ra0 mode managed
ifup ra0

i added it to the end of the file but *before* the last line which contains something like :exit

when i boot my computer automatically connects to the network

---

### Post by sigvartb on 2006-08-21
Thanks, works for me. I had to add a dhcp-request at the end of /etc/init.d/bootmisc.sh (dhclient ra0). Now the only snag is that I have to wait for the network to come up before I gain control of the machine after boot.

---

