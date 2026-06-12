---
title: "Wireless Access Point"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2014-07-23
This question is about what entry to put in as the gateway for an access point. 

I have a security cameras that is hard wired to a DVR. The DVR has an ethernet socket, which is connected to a Netgear WN604 which converts the ethernet to wifi and acts as  an access point. 

I assume I should reset the WN604 and set it up again via a direct connection from the computer. To do this I have tried to set up a new Network connection in Ubuntu. 

Went to Wired tab --add new connection--- 
Tabs:
wired left alone with MTU automatic
IPv4 -manual- add address. At this point I am confused:
     Address: 162.168.0.230
     Netmask 255.255.255.0
     Gateway ?? don't know what to put in


This is what the manual says:

> The default configuration of the WN604 is for a static IP address of 192.168.0.230 and a
subnet mask of 255.255.255.0 with DHCP disabled. Make sure your network
configuration settings are correct.
If you are using the NetBIOS name of the access point to connect, ensure that your
computer and the access point are on the same network segment or that there is a WINS
server on your network.
If your computer is set to obtain an IP address automatically (DHCP client), restart it.
If your computer uses a fixed (static) IP address, ensure that it is using an IP address in
the range of the WN604. The access point default IP address is 192.168.0.230, and the
default subnet mask is 255.255.255.0.



I will also need help on how to configure the router so that camera output  can accessed  remotely. 
 


Robin

---

### Post by Hadaka on 2014-07-23
Hi Robbyx
 Please open a terminal ctrl/alt/t then
COPY and paste the following,,,
```
ifconfig | grep Bcast | awk '{print$2}'
```
post the output.
thanks.

---

### Post by varunendra on 2014-07-24
> **Robbyx said:**
> Tabs:
wired left alone with MTU automatic
IPv4 -manual- add address. At this point I am confused:
     **Address: [COLOR="#FF0000"]162[/COLOR].168.0.[COLOR="#FF0000"]230[/COLOR]**
     Netmask 255.255.255.0
     Gateway ?? don't know what to put in

Assuming "162" is a typo above, actually it is 192, the address "...**[COLOR="#FF0000"]230[/COLOR]**" is already being used by your Netgear AP. Assigning the same to your computer will cause an IP conflict and they won't connect to each other. Change this IP to something like "**192.168.0.[COLOR="#0000CD"]200[/COLOR]**".

Gateway is fundamentally not necessary, but Network Manager (at least the version I have) has a bug due to which it doesn't let you complete the configuration until you define the gateway. So you can put any other IP there. The role of a Gateway is to connect you to the 'External' network - the Internet in other words. Usually, **it is the IP of the router/access-point** to which you are connected (directly or via a switch) and is going to connect you to the internet.

So, if you are going to leave the IP address of the Netgear AP to what it currently is (192.168.0.230), you can use the same IP as the gateway - 192.168.0.230

But if you are planning to change its IP during configuration, use that planned IP as the gateway.

Lastly, if you are not planning to connect this computer to internet at all, just put any random (but valid) IP address, even "0.0.0.0" should do.

Keep in mind that in order to connect to Internet, a Gateway MUST be defined _for the interface using which you would connect to internet_.

Also keep in mind that having more than one gateway (for different interfaces - ethernet and wifi for example), and using both interfaces at the same time can also cause a gateway confusion - thus causing internet connectivity issues. Usually it is the Gateway of the ethernet interface that is preferred by the system. But there are ways to overcome such problems, if occurred.

---

### Post by Robbyx on 2014-07-24
> **Hadaka said:**
> Hi Robbyx
 Please open a terminal ctrl/alt/t then
COPY and paste the following,,,
```
ifconfig | grep Bcast | awk '{print$2}'
```
post the output.
thanks.

 ifconfig | grep Bcast | awk '{print$2}'
addr:192.168.1.5
 
This was done without the WN604 being connected. At present only the ADSL router is connected

Robin

---

### Post by Hadaka on 2014-07-24
Hi, the address you got with that command
is the IP adderss for your wireless card in the computer.
192.168.1.5 this means your computers modem/router IP address is
192.168.1.1 This is the addresss you need for your gateway.

now lets look at the access point you are trying to add
you say its IP is Address: 162.168.0.230 That needs to be changed.
it will conflict with your current system. so disconnect your computers modem/router
and put the cable in the accesspoint's router,,,follow the instructions on how to
access the unit.  once inside change 162.168.0.230 to 192.168.1.230
while in there makeing that change also give it an ssid name.,,like cam1 or what ever.
once you make these changes,,,save them, and replug your computer modem/router
back in ...turn the access unit on,,.not plugged in,,,,and you should be able to see
the ssid,,,cam1 in your network access choices, then come back here and i will work
with you getting the 1pv4 configuration like it should be.

---

### Post by Robbyx on 2014-08-04
I am not able to access the WAP.

I have reset the WAP.

Created a new internet connection
IPv4 setting:
Address: 192.168.0.210
Mask 255.255.255.0
gateway: 192.168.0.1

I have not entered the device mac address or cloned mac address. MTU: automatic.
No dns servers entered. 

the manual says:

> Log In to the Access Point

The access point is set, by default, with the IP address of 192.168.0.100 with DHCP disabled.
To log in to the access point:
1. Prepare a computer with an Ethernet adapter.
a. If this computer is part of your network, record its TCP/IP configuration settings.
b. Configure the computer with a static IP address of 192.168.0.210 and 255.255.255.0
for the subnet mask.
2. Connect an Ethernet cable from the access point to the computer.
3.Power up the access point.
a. Connect the power adapter and plug it into an electrical outlet.
b. Make sure that the Power On/Off button on the rear panel is in the On position
(pressed in).
Verify the following:
 The Power LED is on.

 The LAN LED is on for the LAN port that is connected to your powered-on computer.

 The WiFi LED is blinking.
Launch a web browser and enter [http://192.168.0.230](http://192.168.0.230) in the address field. You are
prompted to log in:


When I was connected to the WAP the internet connection worked. It showed the two arrows. I just could not find the device and login via my browser.

---

### Post by Robbyx on 2014-08-05
I have managed to get in to the Wireless AP. Now what do I do?

---

### Post by varunendra on 2014-08-08
Sorry for not responding earlier (reason [here]("http://ubuntuforums.org/showthread.php?t=2237796&p=13093195#post13093195")), and I think Hadaka didn't reply because things are getting a bit confusing here.

Please clarify the following, and I hope Hadaka would be available to get you through the rest of the configuration, if I go amiss again -

**1)** How many devices in total are currently involved? I think the following four -

[indent]The router/modem (connected to internet) with IP **192.168.1.1** -------> The Ubuntu laptop --------> the access-point with IP **192.168.0.230** --------> The camera itself[/indent]

**2)** How are you connected to the router/modem that is connected to Internet? Via Ethernet cable or wifi?

**3)** What do you mean by "WAP"? Which device do you refer to when you say "WAP"?

**4)** If you have manually changed some settings, what are they now and in which of the involved devices (the laptop, the wifi access-point, the modem??)?

Apart from the answers to the above, an output from the following commands may also make things a bit clearer -
```
route -n
nm-tool
```
Run these when you are connected to both the router/modem and the wifi access-point, and post back their outputs here.

---

### Post by Robbyx on 2014-08-09
> **varunendra said:**
> Sorry for not responding earlier (reason [here]("http://ubuntuforums.org/showthread.php?t=2237796&p=13093195#post13093195")), and I think Hadaka didn't reply because things are getting a bit confusing here.

Please clarify the following, and I hope Hadaka would be available to get you through the rest of the configuration, if I go amiss again -

**1)** How many devices in total are currently involved? I think the following four -

[indent]The router/modem (connected to internet) with IP **192.168.1.1** -------> The Ubuntu laptop --------> the access-point with IP **192.168.0.230** --------> The camera itself[/indent]
**Yes, except that the camera is connected to the DVR and the IP connection is to the DVR not the camera.**

**2)** How are you connected to the router/modem that is connected to Internet? Via Ethernet cable or wifi?

**ethernet**

**3)** What do you mean by "WAP"? Which device do you refer to when you say "WAP"?
**Wireless Access Point**

**4)** If you have manually changed some settings, what are they now and in which of the involved devices (the laptop, the wifi access-point, the modem??)?
**A friend tried to set up the WAP so that it was being used as a bridge. I believe this was a way in which other people could also access the camera output.**


Apart from the answers to the above, an output from the following commands may also make things a bit clearer -
```
route -n
nm-tool
```
Run these when you are connected to both the router/modem and the wifi access-point, and post back their outputs here.
At the moment I can not connect by wireless to the WAP via my router, so the best I can do at present is the following which does not show a connection to the WAP

```
/dev/sda2
robins@robins-EP35-DS3L:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
robins@robins-EP35-DS3L:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1D:7D:0A:01:3E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```


Thank you for your reply.

R

---

