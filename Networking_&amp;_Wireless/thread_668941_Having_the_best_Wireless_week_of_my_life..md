---
title: "Having the best Wireless week of my life."
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2008-01-15
Helo.

I swear to God I've had enough of Gusty's networking! It's much worse than Edgy ever was!
/rantoff


I would really appreciate some help with sorting out a wireless issue. I run DHCP on my network. I have 2 Ubuntu Desktops, a couple windows ones and 1 Ubuntu Laptop. All Desktops have access via ethernet and the Laptop uses a Netgear AP.

My Ubuntu Desktop(10.0.0.3) cannot talk to the the Laptop(10.0.0.9) and the Laptop won't talk to the Desktop but both can see the 2nd Ubuntu machine, my file server.:
I'm pasting the output for the desktop but the results are exactly the same from the laptop to the 10.0.0.3 Desktop.

> 
rudolf@Rudolf:~$ tracepath 10.0.0.50
 1:  10.0.0.3 (10.0.0.3)                                    0.271ms pmtu 1500
 1:  10.0.0.50 (10.0.0.50)                                  4.623ms reached
     Resume: pmtu 1500 hops 1 back 1 


rudolf@Rudolf:~$ tracepath 10.0.0.9
 1:  10.0.0.3 (10.0.0.3)                                    0.232ms pmtu 1500
 1:  no reply
 2:  no reply


rudolf@Rudolf:~$ ping 10.0.0.3 -s 2048
PING 10.0.0.3 (10.0.0.3) 2048(2076) bytes of data.
2056 bytes from 10.0.0.3: icmp_seq=1 ttl=64 time=0.062 ms
2056 bytes from 10.0.0.3: icmp_seq=2 ttl=64 time=0.063 ms
2056 bytes from 10.0.0.3: icmp_seq=3 ttl=64 time=0.062 ms
2056 bytes from 10.0.0.3: icmp_seq=4 ttl=64 time=0.065 ms
2056 bytes from 10.0.0.3: icmp_seq=5 ttl=64 time=0.067 ms
2056 bytes from 10.0.0.3: icmp_seq=6 ttl=64 time=0.066 ms

--- 10.0.0.3 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4996ms
rtt min/avg/max/mdev = 0.062/0.064/0.067/0.005 ms




NOTHING except a ping gets through. I desperatly would like to copy files from one to the other without having to dump the files on the backup server and theb copy from there but neither Samba, Shh or Scp works so I'm flat out of ideas.

Is there a way to test link quality on Wifi? but then why does the rest of the network work with the laptop and no the 1 desktop?

I have  had trouble trying to access Samba shares on the desktop(10.0.0.3) and also SHH server has never worked. 

So just to sumerise:

i) 10.0.0.3 Desktop can see all but the laptop on network
ii) 10.0.0.9 Laptop can see all but the Desktop @ IP 10.0.0.3
iii) SSH server never worked on the Desktop and I have had endless samba troubles.
iv) The Samba troubles started as soon as I installed VMware but I can't uninstall this as it's more important in my life than Samba but I will remove it temporarily if  you think it's necessary to prove or test something.
v) Have had 3 reinstalls of Gusty on the Desktop and never had a stable Samba Solution. 

Any Random advice will greatly be appreciated! If you need any info, please don't hesitate to ask.

Thanks in advance for any replies,

Rudolf

---

### Post by mimada on 2008-01-16
Try disabling the iptables firewall on all Ubuntu machines. Easiest way is to install the Firestarter front end for iptables.

---

### Post by RudolfMDLT on 2008-01-16
Cool - will try. The one PC is a server - and I have asked this before :) - how do I turn iptables off in bash?

Thanks for the reply,

Rudolf

---

