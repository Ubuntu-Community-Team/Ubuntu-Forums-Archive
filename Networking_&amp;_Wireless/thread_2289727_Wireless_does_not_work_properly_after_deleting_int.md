---
title: "Wireless does not work properly after deleting interfaces file"
date: 2015-08-06
forum: Networking &amp; Wireless
---

### Post by Farhad.plasma on 2015-08-06
hi, today I accidentally removed /etc/network/interfaces and then I recreated it, after that my lan interface works just fine but wireless DOES NOT, and its going to make me crazy cause I did almost anything on the Internet but no luck, I even reinstalled network-manager. In this forum I tried this [http://ubuntuforums.org/showthread.php?t=1836867](http://ubuntuforums.org/showthread.php?t=1836867) but again no luck. I don't want to reinstall my os please help if you can. Thank you in advance.

---

### Post by Hadaka on 2015-08-06
Hi,please post your network interface file..
```
cat /etc/network/interfaces
```
thanks.

---

### Post by Farhad.plasma on 2015-08-06
hi, this is the content of my interfaces file:

> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.120
mask 255.255.255.0
gateway 192.168.1.1
dns-nameserver 8.8.8.8


auto wlan0
allow-hotplug wlan0
iface wlan0 inet dhcp




---

### Post by Hadaka on 2015-08-06
Hi, etc/network configuration and Network Manager do no work well together
i would suggest you do this,,
open an editor
```
sudo gedit /etc/network/interfaces
```
comment out every thing except the first 2 lines.
```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
#auto eth0
#allow-hotplug eth0
#iface eth0 inet static
#address 192.168.1.120
#mask 255.255.255.0
#gateway 192.168.1.1
#dns-nameserver 8.8.8.8


#auto wlan0
#allow-hotplug wlan0
#iface wlan0 inet dhcp

```
then go to NETWORK MANAGER
select MANUAL and click ADD
and configure like attached..
[ATTACH=CONFIG]263691[/ATTACH][ATTACH=CONFIG]263692[/ATTACH]

*******************************************************OR
OR YOU COULD
delete NETWORK MANAGER
and leave your etc/network/interfaces..  as is

---

### Post by Farhad.plasma on 2015-08-07
hi, thanks for the solution but for the first method when I commented out everything and configured eth0 in network manager with a different address the network went down and just eth0 came up with the command: ifup eth0 --force, and the it was interesting it has the previous address not the new one.
about the second method I should say that I've tried it before but again no luck.
thank you anyway, is there any other solution???

---

### Post by chili555 on 2015-08-07
I don't really know the purpose of the hotplug declaration. I haven't used it or seen it required in a few years. Also, it's netmask, not mask. Also, dns-nameserver[COLOR="#FF0000"]s[/COLOR]. Therefore, I suggest:```
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#allow-hotplug eth0
iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1


auto wlan0
#allow-hotplug wlan0
iface wlan0 inet dhcp

```

---

### Post by matt_symes on 2015-08-07
Hi

Chili555 and hadaka are very competent and can help you recreate the settings you had.

I do have a question though. 

Why are you mixing both the interfaces way and network managers way of managing your network interfaces ?

It's not like you are aliasing multiple IP addresses on a single interface or setting up some esoteric bridge configuration so why not just let network manager handle it for you ?

I'm just interested.

Kind regards

---

### Post by Farhad.plasma on 2015-08-08
hi, sorry for my late response, I'm a little busy these days. Thank you chili555 your solution worked, the list of APs apeared again but when connected no ping and no page on the browser not even with cable when disabling the wifi interface. The interesting part is when I switch to another AP of mine it stocks at releasing the ip it got from the previous AP, actually the same problem showed itself when I deleted the interfaces file. so I think it should be about dhcp or something. I think we're close but I cant figure it out by myself.
and to matt: the reason was that when using network manager the static ip of wired interface is not used for me and by terminal I cant see the ssid of APs and connect to them easily.

---

### Post by chili555 on 2015-08-08
> when using network manager the static ip of wired interface is not used for meI'm not quite sure I understand this. Please explain a little more.

Your interfaces file implies that you want to use ethernet and wireless both and at the same time. That is surely not what you intend, is it? I assume you want to use ethernet somewhere with a static IP address and some other place, wireless with DHCP, but not both at the same time. Is that correct? 

If so, as Hadaka and matt_symes both say, this can easily and simply be done within Network Manager alone.

Please help us understand.

---

### Post by Farhad.plasma on 2015-08-08
yes you are right and I intend to do what you said sometimes wired and sometimes wifi, but the problem is I could not manage the network manager to work properly, I mean when I set an static ip address on my wired interface it gets an ip address again from dhcp. so I decided to do what you saw to interfaces file.

---

### Post by Farhad.plasma on 2015-08-08
Finally, it worked, I used the configuration bellow for interfaces:
> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#allow-hotplug eth0
iface eth0 inet static
address 192.168.1.120
mask 255.255.255.0
gateway 192.168.1.1
dns-nameserver 8.8.8.8


#auto wlan0
#allow-hotplug wlan0
#iface wlan0 inet dhcp

actually I left the wifi to be managed by network manager and wire to be managed by interfaces file.
Thank you so much for your efforts and consideration.

---

### Post by chili555 on 2015-08-08
Awesome! Glad it's working.

I still suggest, however:```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#allow-hotplug eth0
iface eth0 inet static
address 192.168.1.120
[COLOR="#FF0000"]net[/COLOR]mask 255.255.255.0
gateway 192.168.1.1
dns-nameserver[COLOR="#FF0000"]s[/COLOR] 8.8.8.8


#auto wlan0
#allow-hotplug wlan0
#iface wlan0 inet dhcp
```

---

