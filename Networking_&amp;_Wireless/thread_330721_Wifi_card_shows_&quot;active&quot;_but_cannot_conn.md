---
title: "Wifi card shows &quot;active&quot; but cannot connect"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by Schowie on 2007-01-03
Hi, 
I have a Level One WIFI card with an Atheros driver and when running iwconfig I get: 
ath0      IEEE 802.11g  ESSID:"xxxxxxxx"
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx: xx: xx: xx: xx: xx
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key: xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:restricted
          Power Management: off
          Link Quality=25/94  Signal level=-70 dBm  Noise level=-95 dBm
          Rx invalid nwid:10881  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

- where the ESSID and the Encryption key have the right data.
But the card will not connect - I hope someone can help:

---

### Post by jblebrun on 2007-01-03
When you say "the card will not connect" do you mean that you tried to browse to a web page and it didn't work?

Does ifconfig show an IP address for you?

Try typing **dhclient ath0** in a terminal, to get a new IP adddress from the wireless router. If it gives you an IP address, try a website again.

---

### Post by Schowie on 2007-01-03
Hi,
Thank you - Yes I cannot connect to the internet with the Wifif card / cannot browse a web page. When running dhclient ath0 I get:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by c.dric on 2007-01-03
I've checked the list of supported cards and there is only one entry : the WPC-0300 (ver. 3) which should work out of the box. Now are you sure you're using the exact same card & version ?

It can happen that a card works well enough with one driver to load or connect but not good enough to use some other function like wep ... i would check the exact version with the following command if you haven't already : 

**sudo lshw -C network**

If that's alright, you should recheck all your settings one last time ... 

Finally take a look at the output of 

**dmesg**

after trying to connect, you might spot an error message that leads us to the cause of the problem.

Just a few ideas :-?

---

### Post by Schowie on 2007-01-04
Hi,
I have been checking around in the forum to get ideas. 
Typing 'sudo lshw -C network' gives the following:
*-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@ 02: 00.0
       logical name: ath0
       version: 01
       serial: 00: 12: 6c: 60 :f7 :dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:22000000-2200ffff irq:11

Then I have also installed Wireless Assistant via add/remove program and the WA detects my wireless network - but connection fails?? When  starting WA it asks whether I have started it as "sudo" - how do I do that.
Still :confused:

---

### Post by jblebrun on 2007-01-05
Is there a button on your laptop that enables/disables wireless? I am using a compaq nc6000, and I was unable to scan networks or get an IP address. I hit the little wireless button, and suddenly everything worked. 

It's a bit tricky, because when my wireless card is deactivated, it still looks like its there and working, but it doesn't work. 

It may be a separate button, or it may be Fn-something.

---

### Post by Schowie on 2007-01-05
Hi,
No unfortunately no button to help here - I use an IBM T20 laptop.
Anyhow the netcard is "working", meaning that when I run Wireless Assistant it finds all existing networks in the area. I have also tried to turn off web key on the router and the Wireless Assitant recognises that there is now no web key - but, but it still cannot connect and give access to the internet.
It seems to be so close and then still :confused: ](*,) 
Hope still somebody has *the* good idea.

---

### Post by Schowie on 2007-01-05
Hi again,
I have now also installed wifi radar and kwifi Manager. When  running these it shows, that the card connects to network, gets the accesspoint, signal strength is Top - but gets no IP address back. If this is the problem how could it be solved??

---

### Post by Schowie on 2007-01-06
Hi,
Just wanted to tell that case is solved.
I went to go to System \ Administration \ Networking, clicked the Properties button and then changed to static IP address and typed in the data from my router. Bingo :)

---

