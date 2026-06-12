---
title: "wireless almost set up, but i need help for the rest please"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by shockertwin on 2005-08-07
Ok, so this is my first day on linux and i am having a problem. I had the smc2802-ca wireless adaptor, which doesnt work at all in linux, so i went and got a d-link DWL-g510rev.b. After this i downloaded the needed packages:

sudo apt-get install linux-source-2.6.10 linux-headers-2.6.10-5-386 gcc

Then i download ndiswrapper and installed it. As per the install instructions i download the windows dirvers from the d-link website and did

sudo ndiswrapper -i "NetA3AB.inf"

which gave me an error of already installed. I navigated to ndiswrapper and deleted the folder neta3ab and tried the command above once again. SUCCESS!!

After this i ran

iwconfig  (and this was the output)
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

i ignored this message and ran 

iwconfig wlan0 essid (MY SSID)
iwconfig wlan0 key open XXXXXXXXXXXXXXXXXXXXXXXXXX

Both ran perfectly.

then i did 
ndiswrapper -l <-(that being an L not an i)
and got happy results.

next i did
modprobe ndiswrapper
and once again got the required results produced when running: "dmesg"

now when i run iwconfig again this is what pops up

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:"brad-megan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:42/100  Signal level:-63 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So this is telling me that my wireless i "working", but i cant actually use it at this point. I tried going into the network settings and activating wlan0 and deactivating eth0, but when i try to browse it doesnt work.

[B]i notices at the bottom of the ndiswrapper installation that i needed to 
1) set up the firewall to allow for the external interface wlan0 to do its thing
2) set up the network paramters for interface wlan0

then type one of the following three:
ifconfig wlan0 up
dhclient wlan0
dhcpcd wlan0
[/B]

If needed, the router i use is a netgear wgr614v5

the bold part is what i need help with. Can anyone give me a hand here? Runnig ubuntu 5.04. Thanks.

OMG stupid me. just needed to do

sudo ndiswrapper -m

But how do i set it up to use wlan0 and run that command as soon as i reboot? thanks.

---

