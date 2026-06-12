---
title: "ubuntu studio 8.04, slackware 12 &amp; Realtek 8201CL PHY"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by spamhippy on 2008-05-13
hello & greetings-

well- just upgraded to 8.04... here's the story...

got a lan built into my motherboard- it's hooked up to the dsl.

(here's my motherboard...)

[http://www.newegg.com/product/product.aspx?Item=N82E16813135028](http://www.newegg.com/product/product.aspx?Item=N82E16813135028)

also have a 'network everywhere' network card model# nc100u-wm

internet worked before upgrading to 8.04.. during upgrade internet stopped working (possibly new software installed caused problems..) pulled out old 'network everywhere' card i had laying around from an old computer- put it in the machine & ubuntu reconized it.. was back online. after several problems.. i ended up doing a fresh install of 8.04 off a disk. the lan worked fine after that & i was using that for the dsl. check for updates- there were a bunch.. downloaded them & now i can't connect to the internet again. there is no microsoft software on this machine-- it's ubuntu studio 8.04 & slackware 12... NO WINDOWS. i'm currently thinking the problem is either....

1) software update is causing the internet not to work. (probably the lan?)
2) when i'm switching between slackware & ubuntu some sort of setting in the motherboard is getting changed (like the 'wake on lan' bug..)

basically- the light is on for the lan & when i try to connect to the internet the lights on the dsl modem blink..BUT.. no internet.. no pidgin.. etc (lol) the only setting for the lan in the bios is enable or disable. ubuntu 8.04 doesn't seem to reconize the network card (gutsy did...) & slackware isn't set up for that card either- BUT slackware reconizes the lan built into the motherboard just fine & has connected to the internet without any problems this whole time.

soooo-- there's 2 different ways you could help me... (lol..) either 

A) help me trouble shoot the lan in the motherboard & get that working..

or...

B) help me get ubuntu 8.04 & slackware 12 (for bonus points..lol..) to use the 'network everywhere' network card model# nc100u-wm


is there a way to 'wake on lan' - in ubuntu or slackware? (might be on the wrong track here too... i don't know...lol)

(some possibly useful information...)

exspastic@monster:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:37:b9:5e  
          inet6 addr: fe80::219:21ff:fe37:b95e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5060 (4.9 KB)  TX bytes:12602 (12.3 KB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136800 (133.5 KB)  TX bytes:136800 (133.5 KB)    


well.. ideas.. requests for more information ect.. all would be welcomed-

thanks for the help...

---

### Post by spamhippy on 2008-05-13
bump!

---

### Post by spamhippy on 2008-05-13
bump! x2

---

### Post by spamhippy on 2008-05-13
bump again... anyone?

---

