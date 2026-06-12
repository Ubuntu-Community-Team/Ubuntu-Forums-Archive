---
title: "Problems with connecting to IRC, torrents, other stuff"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by UltraDavid on 2008-02-18
So I'm using Gutsy, and I can't get onto IRC and can't track torrents.  I also just found out that I can't connect to a url with GOM player (which I installed via wine), and it says "Make sure you're not blocked by a firewall."  When I try to configure Azureus and get to the port testing part, no matter what number I put in, it always says, "Connect attempt to ...your computer) timed out after 20 seconds. This means your port is probably closed."  In trying to find answers I read about people opening ports with Firestarter, so I installed it to see if I could do that, but I can't get the firewall to work.  I'm totally confused.

I don't think it's a router problem; my roommate uses XP and has no problems with any of this, and I've had the same problems (and people with Windows have had no problems) at my school, my friends' house, and my parents' house.  I also had no problems before I switched from XP to Ubuntu.

Sorry if I'm not being explicit enough, I'll supply any info needed to help solve this problem (as long as you can tell me how to get it!).

---

### Post by SpaceTeddy on 2008-02-18
ok... i am pretty confused by what you are saying :) At the moment, it does not make much sense to me... anyway

what services are you trying to connect to exactly ? Do any of these programms requite a direct connection to you ? can you open websites ? does a ping to the servers you want to connect to (IRC or Azureus) go through and give you replies ?

i know that IRC sometimes requires a connection back to the user, but you stated that you could use it before and have changed nothing - which confuses me again :)
Azureus also needs a direct connect to your computer, which means it needs a portforwarding in your router... that this fails is no real surpise without port forwarding... again, you said it worked before...

so please tell me first if you internet connection in general works, then we'll figure it out for  the other applications. 

Quick breeze through the brain - have you used anything like UPnP in windows ? that could be the answer to the problem...

[EDIT]
also, can you please post the output of *sudo netstat -lnp |grep LISTEN* as well as *sudo iptables -L -vn* and *sudo route -n*

---

### Post by UltraDavid on 2008-02-19
Sorry for being unclear!

I can get on web pages just fine like always, but I can't get anything out of IRC servers or Azureus.  My internet connection works well generally, but not in the case of IRC or torrents.

I could use IRC and track torrents back when I still ran XP, but that changed when I switched to Ubuntu, and I haven't been able to do that kind of stuff ever since.  I completely removed Windows from my computer, I now have Ubuntu only.   

Here's the output for that stuff:

> sudo netstat -lnp |grep LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5200/cupsd          
unix  2      [ ACC ]     STREAM     LISTENING     28671    5200/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     17481    5160/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18066    5613/gnome-keyring- /tmp/keyring-9VhDC9/socket
unix  2      [ ACC ]     STREAM     LISTENING     18149    5655/ssh-agent      /tmp/ssh-KYLijY5616/agent.5616
unix  2      [ ACC ]     STREAM     LISTENING     18165    5657/gconfd-2       /tmp/orbit-ultra/linc-1619-0-1fead95986027
unix  2      [ ACC ]     STREAM     LISTENING     18175    5616/x-session-mana /tmp/orbit-ultra/linc-15f0-0-704e6fd5a2901
unix  2      [ ACC ]     STREAM     LISTENING     18345    5616/x-session-mana /tmp/.ICE-unix/5616
unix  2      [ ACC ]     STREAM     LISTENING     18383    5663/gnome-settings /tmp/orbit-ultra/linc-161f-0-7f1d0f7ea2df6
unix  2      [ ACC ]     STREAM     LISTENING     18437    5677/gnome-volume-m /tmp/orbit-ultra/linc-162a-0-208dcb3dd7efa
unix  2      [ ACC ]     STREAM     LISTENING     18471    5671/gnome-panel    /tmp/orbit-ultra/linc-1627-0-531ad2f5dc44
unix  2      [ ACC ]     STREAM     LISTENING     18522    5669/metacity       /tmp/orbit-ultra/linc-1625-0-7f82d55c4d658
unix  2      [ ACC ]     STREAM     LISTENING     78028    11728/gedit         /tmp/orbit-ultra/linc-2dd0-0-344186c31d6bd
unix  2      [ ACC ]     STREAM     LISTENING     18547    5673/nautilus       /tmp/orbit-ultra/linc-1629-0-531ad2f5c0b4e
unix  2      [ ACC ]     STREAM     LISTENING     18570    5685/gnome-vfs-daem /tmp/orbit-ultra/linc-1635-0-2fd9b68990ed1
unix  2      [ ACC ]     STREAM     LISTENING     18668    5690/bluetooth-appl /tmp/orbit-ultra/linc-163a-0-4e4474da6fb57
unix  2      [ ACC ]     STREAM     LISTENING     78032    11728/gedit         /tmp/gedit.ultra.2696594967
unix  2      [ ACC ]     STREAM     LISTENING     18718    5689/vino-session   /tmp/orbit-ultra/linc-1639-0-77f3344038dac
unix  2      [ ACC ]     STREAM     LISTENING     78612    11790/soffice.bin   /tmp/orbit-ultra/linc-2e0e-0-a5f89a4f263f
unix  2      [ ACC ]     STREAM     LISTENING     18719    5692/update-notifie /tmp/orbit-ultra/linc-163c-0-77f3344038dc9
unix  2      [ ACC ]     STREAM     LISTENING     78618    11790/soffice.bin   /tmp/OSL_PIPE_1000_SingleOfficeIPC_e5f81e5831e01f667f9ca0901d7e62
unix  2      [ ACC ]     STREAM     LISTENING     18732    5705/nm-applet      /tmp/orbit-ultra/linc-1649-0-590de2563db4a
unix  2      [ ACC ]     STREAM     LISTENING     18752    5711/gnome-power-ma /tmp/orbit-ultra/linc-1645-0-590de2567cfa1
unix  2      [ ACC ]     STREAM     LISTENING     18761    5682/bonobo-activat /tmp/orbit-ultra/linc-1632-0-4a7185fecbc3c
unix  2      [ ACC ]     STREAM     LISTENING     17437    5154/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18826    5737/gnome-screensa /tmp/orbit-ultra/linc-165b-0-26c7376343829
unix  2      [ ACC ]     STREAM     LISTENING     18833    5699/evolution-alar /tmp/orbit-ultra/linc-1643-0-118bde2a38cfa
unix  2      [ ACC ]     STREAM     LISTENING     18843    5732/mapping-daemon /tmp/mapping-ultra
unix  2      [ ACC ]     STREAM     LISTENING     19046    5750/evolution-data /tmp/orbit-ultra/linc-1676-0-27b265b4950f5
unix  2      [ ACC ]     STREAM     LISTENING     202800   20340/firefox-bin   /tmp/orbit-ultra/linc-4f74-0-1ee99b74bd8d
unix  2      [ ACC ]     STREAM     LISTENING     20379    5764/evolution-exch /tmp/orbit-ultra/linc-1684-0-6d17c18e71270
unix  2      [ ACC ]     STREAM     LISTENING     20554    5809/trashapplet    /tmp/orbit-ultra/linc-16b1-0-3a7129ba9a9f2
unix  2      [ ACC ]     STREAM     LISTENING     20723    5826/notification-d /tmp/orbit-ultra/linc-16c2-0-f8fcf082fe7b
unix  2      [ ACC ]     STREAM     LISTENING     218426   21391/gnome-termina /tmp/orbit-ultra/linc-538f-0-4bd2cc3183040
unix  2      [ ACC ]     STREAM     LISTENING     20762    5836/mixer_applet2  /tmp/orbit-ultra/linc-16cc-0-73ce96d94b49e
unix  2      [ ACC ]     STREAM     LISTENING     15884    5031/dbus-daemon    @/tmp/dbus-e7vLwtJE11
unix  2      [ ACC ]     STREAM     LISTENING     17743    5393/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17825    5440/bluetoothd-ser @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     15907    5051/hald           @/var/run/hald/dbus-RHdliCYDuM
unix  2      [ ACC ]     STREAM     LISTENING     17818    5428/hcid           @/var/run/dbus-tk4khSktm0
unix  2      [ ACC ]     STREAM     LISTENING     15503    4779/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     17816    5428/hcid           /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     15904    5051/hald           @/var/run/hald/dbus-TKEqBFbYa8
unix  2      [ ACC ]     STREAM     LISTENING     15827    4988/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18359    5661/dbus-daemon    @

>  sudo iptables -L -vn
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

> sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0


Hope that helps!

---

### Post by SpaceTeddy on 2008-02-19
ok, your logs indictae that you do not need port forwarding (if you had your programs running at the time when you took the logs), Otherwise, the forwarded ports should show up with your printer server in the netstat command, right up the top. The only thing that is there is port 631,which is cups mangement interface.

furthermore, iptables is not blocking anything, (all Chains are on ACCEPT, which means, everything pass though) and therefore, it should work aswell...

lastly, you do have a firewall/router between your computer and the internet, but since you do not need outgoing connections this should really not matter at all.

In other words, your network configuration looks just fine and ready to do anything on the net. So i'd suspect it has to do something with the programms themselves rather than your internet connection. I personally have never used azureus so i would now know how exactly they work...

*[idle]*

just installed azureus on my computer (i assume you got it via synaptic) and done the setup. As i suspected, Azureus needs an incoming port (one that other people from the internet can connect to) and that one is blocked by your router. you will have to run the azureus setup again, and when you get to the question for the server/nat port you should NOT run the test right away.

Note down the port, open your management interface for your router (most likely to be found at [http://192.168.1.1]("http://192.168.1.1") and configure the port that azureus shows to be forwarded to your machine. Without that, Azureus will NOT work correctly, whatever you do. Why it worked in windows i don't know, but there must be some kind of port fowarding involved here. This is machine independant ! 

after the port forwarding is setup, the test should succeed. if it does not, check it again until the test is done. I had to setup port-forwarding here aswell to make the test go through.

now, for IRC... what client are you using ? ( i cannot debug without knowing the client... sorry :) )

hope this helps so far

PS: this [link]("http://www.peerevolution.com/forums/showthread.php?t=3679") explains roughly why you need port forwarding and what it does (i am too lazy to type it all up :)

---

