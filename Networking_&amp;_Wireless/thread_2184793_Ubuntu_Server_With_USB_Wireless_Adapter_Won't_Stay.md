---
title: "Ubuntu Server With USB Wireless Adapter Won't Stay Connected"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by samalex1014 on 2013-10-30
Hey, I'm currently running a Ubuntu Server 12.04.  I had to move it into a room separate from the modem, so I installed a Kubuntu GUI and plugged in a Linksys USB Wireless Adapter.  Due to hardware restrictions, I either have to use Kubuntu in failsafe mode or simply use command line, but I'm not sure how to use networking from the terminal.  I would just install and connect via the adapter, then uninstall kubuntu, but whenever I connect to my network, which the server can see, it will stay connected for a few minutes, then kick itself off.  I'm not sure if this has something to do with the failsafe mode, or not installing anything with the wireless adapter.

My main question is: Why is it automatically disconnecting itself?

If it is due to failsafe mode: How do I go about connecting to the network from the command line?

If it is due to uninstalled drivers: Would they still be functioning and set to automatically connect to my network once I remove Kubuntu?

Thanks in advance!

---

### Post by chili555 on 2013-10-30
*Doc Chili emerges from the back room amongst the jeers and laughter of all the usual suspects; Wild Man, Varun, Hadaka, et al. "We feel sorry for you, Doc. Here's an easy one!"*

The usual way that networking is handled on any desktop environment including kubuntu, is Network Manager. When you remove or even don't boot into kubuntu, NM doesn't start and doesn't control networking. After a few minutes, your wireless, drifting around unassisted, decides to take the afternoon off. 

Let's get set up as a proper server without a desktop environment. Boot up and temporarily within kubuntu, open a terminal and do:```
sudo apt-get install vim ssh kate
```After they are installed, do:```
iwconfig
```Is your wireless interface wlan0? We'll need that in the next step. Next do:```
sudo kate /etc/network/interfaces
```Make the file look something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <my_network>
wpa-psk <my_secret_key
dns-nameservers 8.8.8.8 192.168.1.1
```Be sure to pick an address outside the DHCP pool in the router. Of course, substitute your relevant details here. Proofread carefully, save and close kate. 

Now you can remove kubuntu. Reboot to the command line. Get the system to read the file and use the changes:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```If all goes well, you will see something like:> wpa_supplicant: wpa-ssid "my_network" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.1.100/255.255.255.0 broadcast 192.168.1.255 	  dev wlan0 label wlan0
ip link set dev wlan0   up
 ip route add default via 192.168.1.1  dev wlan0 
See if you are connected to the world:```
ping -c3 www.google.com
```If you get ping returns you are all set!

Now you can, from another machine, ssh into the server to work at any time:```
ssh -l <username> 192.168.1.100
```Once that's working, you can probably detach the display and let the server hum away in the closet or, as mine does, the garage! vim is a text editor you can use from the command line. It looks difficult but is easy.

---

