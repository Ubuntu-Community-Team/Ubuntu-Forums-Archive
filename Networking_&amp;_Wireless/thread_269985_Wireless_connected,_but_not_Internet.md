---
title: "Wireless connected, but not Internet"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by on~namas~ganga on 2006-10-02
](*,) Well, I already posted a message about this issue and I keep on reading mroe and more people having the same issue, seeing a network around, send/receive packages and still no Internet...
Does anyboy out there now what is going on? 
I would suggest to the gurus around to give a hand... 

That is my case: 

```
root@ganga:/home/daniel# lshw -C network

  *-network:0 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5901 100Base-TX
... ... ...
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 01
       serial: 00:20:e0:97:d0:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.7.2 ip=192.168.1.15 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:f8000000-f8000fff irq:11


root@ganga:/home/daniel# lspci | grep chipset
0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```


```
root@ganga: /home/daniel# iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:02:6F:37:41:A0
                    ESSID:"TrAir7"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:18/153  Noise level:9/153
                    Encryption key:off
                    Bit Rates:11 Mb/s

Seems that its detected and with a driver that seems to work, let's see what it does if...


root@ganga:/home/daniel# iwevent
Waiting for Wireless Events from interfaces...
19:00:31.443404   eth1     Scan request completed
19:09:10.170370   eth1     New Access Point/Cell address:00:02:6F:37:41:A0
19:09:10.185915   eth1     Tx packet dropped:00:02:6F:37:41:A0
19:09:11.111384   eth1     Tx packet dropped:00:02:6F:37:41:A0

root@ganga:/etc# iwconfig eth1 essid TrAir7
root@ganga:/etc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"TrAir7"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:37:41:A0
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=24/92  Signal level=143/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:0   Missed beacon:0


root@ganga:/home/daniel# ifconfig eth1 192.168.1.15 netmask 255.255.255.0


root@ganga:/home/daniel# ifconfig eth1 down

root@ganga:/home/daniel# ifconfig eth1 up 

dmesg | tail  

[17180255.504000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180255.808000] eth1: New link status: Connected (0001)
[17180255.808000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180266.744000] eth1: no IPv6 routers present
[17181079.192000] eth1: New link status: AP Out of Range (0004)
[17181141.748000] eth1: New link status: AP In Range (0005)
[17181594.116000] NET: Registered protocol family 17
[17181756.452000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181804.648000] eth1: New link status: Association Failed (0006)
[17181809.864000] eth1: New link status: Connected (0001)
[17181809.864000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17181820.836000] eth1: no IPv6 routers present
```

](*,) 

It might be that last line on dmesg: no IPv6 routers present

Any ideas? Million thanks

---

### Post by fehja on 2006-11-05
BUMP.

I am having the exact same problem. It's driving me crazy. And i thought the hard part was going to get the pcmcia card visible and have it connect to the router...

I have only just recently been using linux (4 days). I've checked all your same commands and i get the same results. It sees it, it sees the router, everything is fine, except no internet. I've searched these forums for anything relating.

One interesting thing, dunno if you're having the same thing. It sends packets just fine, however it has not recieved 1 single packet. Any ideas for that?...

---

### Post by yet another newbie on 2006-11-05
> **fehja said:**
> BUMP.

I am having the exact same problem. It's driving me crazy. And i thought the hard part was going to get the pcmcia card visible and have it connect to the router...

I have only just recently been using linux (4 days). I've checked all your same commands and i get the same results. It sees it, it sees the router, everything is fine, except no internet. I've searched these forums for anything relating.

One interesting thing, dunno if you're having the same thing. It sends packets just fine, however it has not recieved 1 single packet. Any ideas for that?...

I also have the same problem. Sends packets, does not receive. I see numerous post for various fixes, but after trying so many similar problem fixes I would really like to know which will really work.

---

### Post by matt_b on 2006-11-05
I have exactly the same problem as the OP. I receive an IP address, DNS server and gateway address from my D-link wireless router (as expected).

I can ping the router, I can ping by domain (*ping [www.google.com](www.google.com)* produces results) but whenever I open firefox I cannot get out on the web - the page times out. I can access the router config page, but no other page.

I have exactly the same problem in Suse 10.1, using both wired and wireless connections.

I am running 6.06 on a Sony TR1MP laptop (Intel pro 100 wireless).

Any ideas?

---

### Post by McLaughysSN on 2006-11-05
Im having the same problem and im sure its a DNS error. I double checked the DNS addresses in the network utiity and everything checked out. I entered the address for google (72.14.207.99) menually into the firefox andress bar and low and behold results.. 

Usually deleting the profile and reentering all the information will work half of the time, the other half i just shut down and wait until im less frustrated

My problems started after trying other network utilities as Ubuntu's is, sub par

---

### Post by somersetsimon on 2006-11-05
I struggled for weeks trying to get my wireless network working with Dapper. With all the linux drivers and my windows driver (zd1211 card) I could see my wireless network, but couldn't make a connection. With help from the ever helpful and patient 'wieman01', I tried everything. Eventually, I searched on the net for new drivers. I found a really recent windows driver (only a few months old), used ndiswrapper and it worked perfectly. So my tip would be to make sure you have absolutely the latest version of your driver for your chipset (not necessarily just the latest driver from your vendor) and the latest version of ndiswrapper.

It's confusing when you can see the network, but can't connect. It doesn't seem obvious that the driver is the problem.

Simon

---

### Post by stream303 on 2006-11-10
Ah, pinging but no browsing by url might point to dns issues.  I have NO wireless experience, but plenty of bodged dns routers...

Does your **/etc/resolv.conf** have any of your isp's dns nameservers listed at the top of the file?  If not, you may want to check out:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Let's see if this helps.

---

### Post by brenx on 2006-11-10
My wireless card (airport) refuse to work properly if I don't use 11th channel on my access point.

---

### Post by FrodoB on 2006-11-10
on~namas~ganga;

What is your output from:

$ netstat -rn

---

