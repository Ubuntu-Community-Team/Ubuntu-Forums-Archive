---
title: "Network security."
date: 2015-12-18
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2015-12-18
My network has been slowing down the last few month. My ISP suggested that I bypass the router a Dlink DSR 250 and connect directly to the cable modem.
I connected the cable from the cable modem to a switch port on the DSR 250, doing this doubled my down load speed.

> With router connected
Download Speed: 14356 kbps (1794.5 KB/sec transfer rate)
Upload Speed: 1954 kbps (244.3 KB/sec transfer rate)
Latency: 29 ms
Jitter: 2 ms

Direct into the router switch
Download Speed: 23477 kbps (2934.6 KB/sec transfer rate)
Upload Speed: 2149 kbps (268.6 KB/sec transfer rate)
Latency: 22 ms
Jitter: 2 ms


My question is would I be compromising my network of 4 computers a wireless, 2 NAS by bypassing my router this? 



Thanks
Paul

---

### Post by praseodym on 2015-12-18
Please run the wireless-script from the sticky-thread and show the outputs

---

### Post by uwe-bungto on 2015-12-19
There was no script, instead a speed test from my ISP
[http://speedtest-east.eastlink.ca/](http://speedtest-east.eastlink.ca/)

My internet connection is very sluggish at times. My ISP tech support told me about the link to their test page.

I shut down everything except one computer and ran the test 6 times with the router connected to the cable modem and 6 times with the computer connected direct to the cable modem.
As you can see from my first post there is an enormous speed difference 

I was in contact with the tech service since I wrote the first message, they assured me that the router was not necessary and the switch part of it could be used, my network would be safe from intrusion.

Is it possible that the router is failing?

If I go with out the router I have no idea how to get 4 computers 2 printers and a NAS to communicate with each other.

---

### Post by uwe-bungto on 2015-12-20
> **praseodym said:**
> Please run the wireless-script from the sticky-thread and show the outputs

here is the output There is a wireless attached that is only used for cell phones or tablets. the rest laptops, boxes, NAS are wired.
[ATTACH]266280[/ATTACH]

---

### Post by bashiergui on 2015-12-20
> **uwe-bungto said:**
> My network has been slowing down the last few month. My ISP suggested that I bypass the router a Dlink DSR 250 and connect directly to the cable modem.
I connected the cable from the cable modem to a switch port on the DSR 250, doing this doubled my down load speed.

My question is would I be compromising my network of 4 computers a wireless, 2 NAS by bypassing my router this?
Some cable companies provide modems that also function as a router. Find out if yours is by either asking the cable company or looking up your IP on a device connected to the modem by typing ```
ifconfig
```If your IP is 10.x.x.x or 192.168.x.x then you know the modem is functioning like a router.

---

### Post by uwe-bungto on 2015-12-20
> **bashiergui said:**
> Some cable companies provide modems that also function as a router. Find out if yours is by either asking the cable company or looking up your IP on a device connected to the modem by typing ```
ifconfig
```If your IP is 10.x.x.x or 192.168.x.x then you know the modem is functioning like a router.

The cable modem's IP address is 195.168.100.1
I can connect the modem directly into one of the 8 switch ports on the DSR 250 bypassing the router. As long as my computers network connection are set to DHCP I have internet.
Where I am lost is having access to printers, NAS and an interconnection to each computer on my network. I have been using /etc/fstab and /etc/hosts and a fixed address to to mount my two NAS. I tried it with DHCP and do not know to mount them or even find their IP.
eg:
/etc/hosts
192.168.0.14    dlink-01
192.168.0.15    dlink-02

/etc/fstab
dlink-01:/volume1            /mnt/dlink01          nfs defaults 0 0
dlink-02:/volume1            /mnt/dlink02          nfs defaults 0 0

How would I proceed?

---

### Post by bashiergui on 2015-12-27
Why can't you plug everything into the switch ports of the DSR 250.

If you gave your NAS a static IP on your old network you'll have to adjust it to be in the new subnet. 
192.168.100.x is a different subnet from 192.168.0.x. They won't talk to each other if the mask is 255.255.255.0. 

This means that you need to change your static IP assignments to 192.168.100.x. You'll have to check with the cable company or the user's manual on how to set a static IP on the cable modem. Then you'll also have to change your mount points in fstab and hosts to match the new IPs.

If you can't find the IPs of the NAS boxes which I presume are plugged into the switch ports and are getting IPs from the modem, then you could use nmap. ```
nmap -sS -O 192.168.100.0/24 >nmap.txt
``` that will run for a little bit and will identify all the devices plugged into the modem. The -O will identify the operating system of each. The bit after the > will dump the results into a text file which will be much easier to read and search.

---

