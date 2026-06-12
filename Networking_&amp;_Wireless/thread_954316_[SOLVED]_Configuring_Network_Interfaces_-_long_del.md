---
title: "[SOLVED] Configuring Network Interfaces - long delay during startup"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by infinitejones on 2008-10-21
I'm running Intrepid on an HP Pavillion dv6000 with an Intel wifi card. It's dist-upgraded from Hardy. 

Ever since I first did the dist-upgrade, there's a long delay during start-up while it's "configuring network interfaces". Long as in 3-4 minutes. Not the end of the world because all I have to do is wait, and everything else (before and after) is absolutely fine. However it's annoying and obviously something is wrong.

Makes no difference if an ethernet cable is connected, and once it gets past the delay, there are no issues with connectivity at all.

Has anyone else noticed this? I can't find anything on Launchpad and googling doesn't bring up anything either. I'm hoping it's just a symptom of Intrepid's beta-ness but given that I can't find any bugs filed, should I file one? Where and how would I do that?

---

### Post by infinitejones on 2008-10-22
Anyone?

---

### Post by jimv on 2008-10-22
Edit /etc/network/interfaces and comment out everything except:

```
auto lo
iface lo inet loopback

```

---

### Post by infinitejones on 2008-10-22
Great! Thanks!

---

### Post by SuA on 2008-11-05
That is not the absolute solution. If you do this, your internet connection is gone.

---

### Post by infinitejones on 2008-11-05
It worked perfectly for me! I backed up the file before I edited it, just in case, but it solved the problem which is why I set the thread to "solved"...

---

### Post by jokker on 2008-11-05
This solution is for dhcp. I need static IPs on my machines with a bridge from eth1 to 4 virtual devices tap. I uninstalled network-manager because it is a mess ! then I edited interfaces like that:


auto lo
iface lo inet loopback

## eth0
auto eth0
iface eth0 inet static
        address 192.168.0.22
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

## Original eth1
auto eth1
iface eth1 inet static
        address 192.168.0.21
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1



## Virtual interfaces for bridged VirtualBox network

# Taps should be before br0
auto tap0
iface tap0 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.30
uml_proxy_ether eth1

auto tap1
iface tap1 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.31
uml_proxy_ether eth1

auto tap2
iface tap2 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.32
uml_proxy_ether eth1

auto tap3
iface tap3 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.33
uml_proxy_ether eth1

auto tap4
iface tap4 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.34
uml_proxy_ether eth1

## Actual bridge for eth1 to tapx virtual devices
# Ip address is the same as eth1 would have been.
auto br0
iface br0 inet static
address 192.168.0.21
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth1 tap0 tap1 tap2 tap3 tap4
bridge_maxwait 0

This is working great only I DO NOT HAVE DNS!
I can ping my router, but can't get out!
all the devices have the right IPs though, all the taps are functional, but NO DNS!
thanks

---

### Post by Diffusr on 2008-12-09
Had the same issue and the fix worked for me too. Using wicd I am still able to set static IP's and specific DNS's if I so wish.

---

### Post by John Jason Jordan on 2008-12-12
> **jimv said:**
> Edit /etc/network/interfaces and comment out everything except:

```
auto lo
iface lo inet loopback

```

This solved my problem too, except that after booting my ethernet was not working. I had to uncomment the lines:

iface eth0 inet dhcp
auto eth0

Afterwards things are back to normal. Dunno how the upgrade from Hardy to Intrepid managed to muck this up, but thanks for helping me fix it!

---

### Post by Kladaradatsj on 2009-01-19
Worked like a charm! It even solved a little problem I had with conflicting network managers: now the one I can see is also the one that handles the connection. Great, thanks, jimv! :)

---

