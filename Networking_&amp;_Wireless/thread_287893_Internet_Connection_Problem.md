---
title: "Internet Connection Problem"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by badguyanil on 2006-10-29
ok to make it simple ans short: "I dono how to connect to internet using my NIC + Modem". Cant figure out what to do!

Well finally i could install ubuntu on to a seperate HDD with lots of help posted on this forum. Here is the next problem hope i get  similar help so that i can migrate from windows to linux. I will explain how i connect to net in windows. Please let me know wht shld i do in ubuntu.

Here goes:
System has (H/W):
1. NIC card (Realteck RTL8139/810X Family PCI Fast Ethernet NIC).
2. Sterlite ADSL modem connected to the NIC card and to my phone line.

How do i connect:(DHCP)
1.Once NIC card is detected by Win XP i get an icon in control panel\Network Connections as "Local Area Connection".
2.I create a "new cnnection".. and set these parameters.
          a.General tab\ Servive name : abcd
          b.Options tab\ set the dialing options to :
                i. Display progress while connecting.
                ii.Promt for name and password, certificate etc.
            Options tab\ set the re-dialing options to :
                i. Redial once line is dropped.
          c.Networking tab:
                i.Type of broadband connection to make: PPPoE (Point to Point Protocol over Ethernet)
                ii.Connection uses the fllwoing items:
                    Internet Protocol (TCP/IP)
                    QoS Packet Scheduler

And so i get one more icon in control panel\Network Connections as "abcd". To connect to internet all i need to do is to double click on the abcd icon and enter the login id and password and press on connect.

ohhhh that took some typing! :mrgreen: 
Now the big question! How do i do this in ubuntu 6.10!

Plese reply coz none of my frnds work on linux... so i have to do all by myself. And i planning to say good bye to windows! But all imp thing is this shld work out!

---

### Post by badguyanil on 2006-10-30
i guess no one understood the question ! anyways can u tell me how to ping my nic card and check if it is installed and working under 6.10! if not where do i get the NIC drivers from!

---

### Post by stream303 on 2006-10-30
To see if your card has picked up and IP address, run ifconfig in a terminal and look at eth0 and see if it has an address.  (Typically eth0 for your default nic)

From what you describe, it looks like you'll need to load PPPoE if your dsl modem is a modem only, and not a combo modem/router.

What some people do to simplify the process is to hook an inexpensive router to their dsl modem, even if it is just one computer, and let them speak PPPoE to each other in hardware, leaving you to deal with just standard ethernet without having to mess with PPPoE.  Make sure this is ok with your system admin.

Might be something to look into - especially since I have NO PPPoE install experience....

---

### Post by mips on 2006-10-30
Why make life difficult for yourself. You say you are connecting via ethernet. You have an ethernet router, use it as such and not as a modem.
 
 Configure the router via it's web interface. Take it out of bridged mode and into routed mode, set the encapsulaion type & VPI/VCI values, enter userid&passwd.
 
 Configure pc for dhcp and off you go. No need for pppoe. The same for windoes, you wont need that login client anymore.

---

### Post by badguyanil on 2007-09-09
Was using ```
pppoeconf
``` to configure and connect to internet. But lately i am not able to do so. the following are some observations. hope this is useful. Well i am a total novice in internet connectivity and all. Please help.......

```
amit@amit-desktop:~$ pon dsl-provider 
Plugin rp-pppoe.so loaded.
amit@amit-desktop:~$ plog
Sep  9 19:20:37 amit-desktop pppd[8435]: Plugin rp-pppoe.so loaded.
Sep  9 19:20:37 amit-desktop pppd[8437]: pppd 2.4.4 started by amit, uid 1000
amit@amit-desktop:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.93.53.40  P-t-P:59.93.48.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2858 (2.7 KiB)  TX bytes:54 (54.0 b)

amit@amit-desktop:~$ poff -a
/usr/bin/poff: /bin/kill failed.  None stopped.
amit@amit-desktop:~$
```

when i give the pon dsl-provider, it does not connect to the net and i keep getting no page found error .anything else you guys need to diagnose the problem let me know. After quite some time i had to come back to windows for this!! kindly help!

--2 days and not a single reply is strange in this forum...any help would be appriciated !

---

