---
title: "xbox 360 to laptop"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by mgmz on 2009-01-31
How would connect my xbox 360 to the internet by connecting it to my laptop which then accesses my home wirless network?

---

### Post by apothecaryaaron on 2009-02-01
> **mgmz said:**
> How would connect my xbox 360 to the internet by connecting it to my laptop which then accesses my home wirless network?

 I have not done this in Linux, but the concept should be the same as Windows.  You have to bridge the wireless connection to the wired connection.  In Ubuntu it requires doing some command line work as far as I know.  I'll try to find the guides, if you want to search some I think the package is bridge-utils.

---

### Post by mgmz on 2009-02-01
i was able to set a bridge between my laptop and the xbox with bridge-utils but when i test the connection on the xbox it says 

IP address: confirmed
DNS: failed

as well i can't access the internet on my laptop even though it says it's connected

any ideas?

---

### Post by apothecaryaaron on 2009-02-02
> **mgmz said:**
> i was able to set a bridge between my laptop and the xbox with bridge-utils but when i test the connection on the xbox it says 

IP address: confirmed
DNS: failed

as well i can't access the internet on my laptop even though it says it's connected

any ideas?

You can take the bridge down for internet access like this:

```
ifconfig <bridge name> down
brctl delbr <bridge name>
```

As far as getting it all working, this page is old, but I used it in 7.10 when I was playing with bridging.

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

---

### Post by mgmz on 2009-02-02
i followed the link you gave and im still getting the "DNS: failed" error, i think it has something to do with the DNS i have put in for the xbox:

xbox 360.
ip: 192.168.0.10
subnet: 255.255.255.0
gateway: 192.168.0.111
primary DNS: 192.168.0.111
secondart DNS: 0.0.0.0

laptop.
ip: 192.168.0.111
subnet: 255.255.255.0
gateway: 192.168.0.1 
DNS: The ones the ISP provides

is that right? 
      - i think that's why it's giving me DNS: failed.

---

### Post by mgmz on 2009-02-03
Finally i got it working, i used the firestarter method, i'll just share my setup in case it is useful to someone else
xbox 360 -> ethernet cable -> laptop -> wireless -> router...

- installed firestarter
```
sudo apt-get install firestarter
```
- followed the wizard, checked on the second screen "ip assigned by DHCP" and also set up ICS in the wizard.
- edited firestarters preferences in ICS and checked "enable DHCP for local networks"
- got an error referring to device eth0 (wan interface i think) being not ready, so ran
```
sudo ifconfig eth0 up
sudo ifconfig eth0 192.168.0.120
```

and then the settings for eth0, eth1 and xbox
eth1 (wireless) -- had it set on automatic - DHCP , in network settings
[INDENT]ip: 192.168.0.111
subnet: 255.255.255.0
gateway: 192.168.0.1
primary dns:...
secondary dns: 192.168.0.1[/INDENT]

eth0 -- set it manually in network settings
[INDENT]ip: 192.168.0.120
subnet: 255.255.255.0
gateway: 0.0.0.0[/INDENT]

xbox 360:
[INDENT]ip: 192.168.0.121
subnet: 255.255.255.0
gateway: 192.168.0.120 (eth0 ip)
primary dns: dns the isp provides
secondary dns: 192.168.0.1[/INDENT]

---

