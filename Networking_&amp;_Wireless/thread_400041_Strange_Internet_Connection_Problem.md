---
title: "Strange Internet Connection Problem"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by rugby471 on 2007-04-03
I have a strange problem regarding my internet connection in Ubuntu. To test everything out on Ubuntu, I used the live  cd and realized in Firefox I had to disable ipv6 in the about:config for my to be able to browse. I then installed Ubuntu and installed all the updates successfully. But now I have a problem. When I try to connect to the internet using a system app ( eg Add/Remove Programs, Synaptic, Automatix ( not necessarily a sys app ) ) My internet connection fails. I have realized that I can sometimes access the net using these apps by browsing on Firefox at the same time. It is very weird and the Firefox thing only works sometimes. Can anyone help me ? 

Ps : I am connected to the internet via an ethernet cable to my origo wireless broadband router and I am running Edgy Eft

Plz help, I don't want to end up having to move to another distro as I really like Ubuntu :(

---

### Post by heimo on 2007-04-03
Hi! Did you disable ipv6 in just Firefox's "aboud:config" settings, or also under /etc/modprobe.d? You need to reboot after the change. See this:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by rugby471 on 2007-04-03
Before I go on, thank you for your help so far . So here it is :

about:config - network.dns.disableIPv6 - true
I have disabled ipv6 in the link you gave above, and in /etc/modprobe.d/aliases

I don't know what else to do, is there another thing I need to edit ?

BTW when I did the thing In the link you gave me this came up as well as the file being loaded :

> (gedit:4885): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I don't know if that means anything ?

---

### Post by heimo on 2007-04-03
Double check that you don't have ipv6 enabled by running:
```
ip a | grep ipv6
```and then:
```
lsmod | grep ipv6
```Do you get any output from those commands?

---

### Post by rugby471 on 2007-04-04
When I enter those in the terminal there is no output.

---

### Post by heimo on 2007-04-04
> **rugby471 said:**
> When I enter those in the terminal there is no output.

Ok, shouldn't be about ipv6 then. What happens, if you run something like:
```
sudo aptitude update
sudo aptitude upgrade

```
First line updates package lists / database and the second one upgrades your computer to the latest packages. Do those work? This seems a bit strange problem. Any other information you could give us? Is it systematic, happens every single time? How do you recover, reboot? If so, next time you could try something like:

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```
And if you use DHCP (you network settings are automatically detected, you could try):
```
sudo dhclient eth0
```
This assumes you've only one ethernet port (eth1 would be your second interface).

---

### Post by rugby471 on 2007-04-04
The first two lines of code you gave me worked, to reset it ? I don't really reset it, I just don't try that thing for that session and then next time I go on I try again, so I guess I restart it, but it doesn't work everytime I restart it. I also put in the last line of code, but it made no difference. BTW It is not systematic.

---

### Post by heimo on 2007-04-04
I'm lost. Sorry, at the moment I have nothing else to suggest. Maybe someone else who sees this?

---

