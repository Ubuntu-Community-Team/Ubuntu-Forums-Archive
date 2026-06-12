---
title: "Compaq WL110 PC Card dont work"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by Norberg on 2006-08-13
Hello i have Compaq WL110 PC Card Ubuntu manage to find my network but i dont get any internet connection but in knoppix 3.8 it works grate, could i copy something from knoppix to get ubuntu to work?


iwconfig eth1 in ubuntu gives me:
eth1      IEEE 802.11b  ESSID:"Mellby"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:05:5D:25:6A:3D
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/92  Signal level=-58 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lsmod|grep orinoco in ubuntu gives me:
orinoco_cs             17928  1
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
pcmcia                 40508  2 hostap_cs,orinoco_cs


iwconfig eth1 in knoppix gives me:
eth0      IEEE 802.11b  ESSID:"Mellby"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:05:5D:25:6A:3D
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/92  Signal level=-58 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:10
          Tx excessive retries:17  Invalid misc:0   Missed beacon:0


lsmod|grep orinoco in knoppix gives me:
orinoco_cs             10504  1
orinoco                43664  1 orinoco_cs
hermes                 11904  2 orinoco_cs,orinoco
pcmcia                 21776  5 orinoco_cs
pcmcia_core            42272  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic


Could someone please help me?

---

### Post by Norberg on 2006-08-14
BUMP
The orginal post have been updated whit more info.

---

### Post by flightless bird on 2007-05-09
I am having similar problems, although I am rather newbie so don't really know where to go to from here. pccardclt informs me that the pc-card is recognised and that orinoco is associated with it, and the network manager seems to believe that I have a wireless card, but I have no way of finding networks - it doesn't scan for them and doesn't seem to make any effort to connect.

---

### Post by chili555 on 2007-05-10
Pleae let us see the results of:```
lsmod | grep prism2
lsmod | grep hostap
lsmod | grep orinoco
```Thanks.

---

