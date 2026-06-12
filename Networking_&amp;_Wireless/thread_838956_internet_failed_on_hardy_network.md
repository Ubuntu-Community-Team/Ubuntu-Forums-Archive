---
title: "internet failed on hardy network"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by nagaraj on 2008-06-24
hi, 
recently upgraded all five pcs s at my office to hardy. liked the look and feel of it and all started working fine. two days back one of the pcs ( the only dual boot pc) was run on windowsxp. since then _no pc on the network is connecting to internet_. the wired network has pcs connected through switches and a pppoe broadband modem is connected to one of the switches. all pcs are detected from all other terminals and can be pinged. modem is 192.168.1.1 and even that can be pinged and is the primary DNS server on all pcs. can anybody help me in this? any further info i'd b glad to furnish. thanks in advance.

---

### Post by wormser on 2008-06-24
Sound like you are getting IP address and you can ping on the local internet.  Have you tried pinging over the internet by domain and IP address?

```
ping ubuntuforums.org
```
```
ping 91.189.94.12
```

If you can ping by IP and not by domain then it is a DNS issue.  [Open DSN]("https://www.opendns.com/start/ubuntu.php") should fix that.  Another thing to try is unplug your router for 10 seconds.

---

### Post by nagaraj on 2008-06-24
thanks, 'll try that and get back. i m away from my workplace rt now.

---

### Post by nagaraj on 2008-06-24
thanks a lot - changing to open DNS solved the problem but everytime i reboot the DNS needs to be changed. i added DNS 208.67.222.222 by editing the DNS tab of *network*from *system>administration>*. how do i change the DNS settings permanantly?

---

### Post by wormser on 2008-06-24
Permanent settings directions are at the bottom of that link.

> To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:[INDENT]    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0 [/INDENT]You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

