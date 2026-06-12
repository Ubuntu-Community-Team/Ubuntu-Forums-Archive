---
title: "dhcp not working"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by topoftheworld on 2005-07-05
hello all...
I just installed ubuntu a day or 2 ago, and I have been trying to get my internet to work. 

I am using cable behind a router (wired), and am connecting to a switch before that. 

the NICs that I have been using are realtek 8139 (built into mainboard), and 3com 3c905 (yes, i disabled the onboard LAN when I used the 3com card.)


I have tried using 2 NIC's, neither seems to be operating dhcp correctly. I have ran dhclient using either NIC, 
and it always goes thru the whole thing, and says

No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

after a bunch of DHPDISCOVER on eth0 to 255.255.255.255 port 67  (various intervals and various interfaces)


strangely enough, yesterday I was messing around and I put a static IP in, with the correct gateway and DNS information, and it worked! but then, I rebooted, and now that dosn't work anymore. 

any help is greatly appreciated!

---

### Post by topoftheworld on 2005-07-05
ok update... 

after I have entered a static IP, 192.168.0.105

now in dhclient, I am getting some messages that say

ip length 314 disagrees with bytes recieved 534.
accepting packet with data after udp payload. 

this happens like 10 times? i think
then it says

DHCPOFFER from 192.168.0.1

and then continues to do the 255.255.255.255 thing until "No DHCPOFFERS recieved"

---

### Post by topoftheworld on 2005-07-06
ok, i figured some things out here.

it is only getting the packet size message when i use the 3com NIC.

i am going to just install slackware and see if that alleviates the problem since no one seems to know why my dhcp isnt working. if that dosn't work, back to windows :-/

---

