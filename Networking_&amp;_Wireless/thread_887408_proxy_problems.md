---
title: "proxy problems"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by boblemur on 2008-08-12
hey all, my question is something that i would have thought would seem a common thing to need...

i have my laptop running ubuntu 8.04/8.10 (dual) and i take it to uni every day to take notes... the problem is, that the uni uses a proxy (obviously) and dont use that proxy at home (obviously) so i was wondering if i could have almost like profiles... where i could chose where i am... ei uni or home and it will change all my proxys over.

now this is ok if i only need to change the FF proxy but, i end up needing to change:

FF proxy
pidgin proxy + use html method
system > prefs > proxy
synaptic's proxy
(apt-get install dosen't work)

now this is a real pain to do twice a day and i was wondering if ubuntu has an easy way of making this simpler, because it seems like something that alot of laptop users would need...


i had 2 ideas:

1) make a second user.. and have one with all my uni settings and one with all my home settings. However the problem with this is then my data is scattered and i have two sets of /home files for everything :S which is stupid...

2) hack up some script that goes through and changes them all...which is something that will be hard... because i don't know how they all store their settings.

any help is much appreciated... and i dont mind using 3rd party tools if they exist

---

### Post by adewale on 2008-08-12
Well i shuffle between proxies also. So i installed foxyproxy for firefox which enables me to switch between proxies by rightclicking (That can't be hard). 
Okay now for gnome i use the network proxy application under preferences. 
Now for terminal it stores the proxy in the bashrc file so i use the export command

---

