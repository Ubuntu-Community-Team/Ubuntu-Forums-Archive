---
title: "denied browsing 16.04 ubuntu shares from any machine in the lan"
date: 2016-07-26
forum: Networking &amp; Wireless
---

### Post by cedo.maric on 2016-07-26
So, there is some really "weired" problem with ubuntu machines. Actually I'd rather blame our, (and with this I am prone to blame myself, as well), ignorance about IP networking. 
Slightly explained situation :
In the moment, I am having situation like this one :

- there are two pc's that I am currently observing in this post, (pc1 and pc2)
- in addition to it there are some android devices that should be able to browse any of those two 
- all those are connected to the same wlan router-repeater

------------------------------------------------------------------------------------------------------------
the tricky part:
a pc2 is connected to this router via usb cable, but Ubuntu is treating this as standard ethernet cable and gave it a interface name "enx001e101f0000". Router is standard huawei gsm wlan router which can give wlan repatin service as well and in this situation this is what I have handy at the moment. 
The pc2 pc plays some kind "logon and keep link alive" role since ISP in the place where I am residing in the moment is restricting access to ony one MAC address and for shameless ammount of money, so I decided to relay the internet to other guys in my surroundings sharing, though, a expenses for this one. 

A pc2 is some kind of file sever too, and to this job I assigned one of my netbooks sitting unused uder the table. 
PC1 is my comp which is used for any other purpose, and also need beeing able to access all the shares on pc2 as well as beeing able to share all files from it's dedicated folders as well. 

Rest of this small "enterprize" users are standard internet users, and those who like to access files and folders shared over the, (let's say hiddennet). 
I some ocasions this net should be able to serve some android devices in very same way. 

PC1 and PC2 are both ubuntu 16.04 machines with enabled and running smbd services. 
----------------------------------------------------------------------------------------------------------------

Here is what happend:

After installation of latest ubuntu 16.04 release, system worked perfectly until the moment where I had to reset it due to ubuntu "have frost" on PC1. All over the sudden, I lost filesharing ability of PC1 while I was able to browse and share all on tne PC2 . 

-------------------------------------------------------------------------------------------------------------------
That gave me a challenge to dig out what could went wrong and here is what did after several days of digging through all other sollutions found on the net:
I have connected computers to the AP not paying much attention to the IP configuration. The internet still have worked even after all other stalled. 
For some reason, PC1 have prioritzed IPV6 rather then IPV4 which was taken before all stopped. This caused some missconfiguration issues in the network, preventing me to access shares on the PC1. 
--------------------------------------------------------------------------------------------------------------------
Sollution:
Just disabled IPV6 in all of network participating computers. 


coclusion:
To all who may encounter similar problem, 
since IP management of any network, (no matter how big and complex this one could be), is rather systematic topic, it would be good to pay attention to this detail. 
In addition to this, one wanting to implement similar situation, should consider assigning IP adresses manually, or at least dedicate own IPV4 pool to the local network, hence avoiding a missconfiguration that happend in my situation. 

All comments on this matter are more than welcome.

---

