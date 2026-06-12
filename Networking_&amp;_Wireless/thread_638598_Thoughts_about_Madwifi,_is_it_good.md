---
title: "Thoughts about Madwifi, is it good?"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2007-12-12
My wireless isn't working but I manage to find some driver (I think) on madwifi [http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG) .

Question is if it worth installing them, did find somewhere that madwifi can sometimes cause problems.

what do you thing about installing madwifi drivers?

EDIT:
I did deactivate the drivers that come with ubuntu in restricted drivers since they didn't work

---

### Post by Junglizer on 2007-12-12
Yes, the madwifi drivers are excellent. Though you will need to be able to use the command line.

---

### Post by Junglizer on 2007-12-12
Since you do not accept PMs I will just post it here:

I have used them quite a bit as nearly all of my wireless cards have an Atheros chip in them. NDIS and some of the other, default Ubuntu drivers that you mentioned, may work but usually do not give you the full functionality of your cards features, things like powersaving and such, it varies from card to card, but most of these features do work with the madwifi drivers. You will need to use the command line (console, xterm, konsole, etc..) to configure your device with these drivers, but it isn't too difficult. If you need any help with them let me know, thats mostly what respond to on these forums anyways.

---

### Post by SpinningAround on 2007-12-13
> **Junglizer said:**
> Since you do not accept PMs I will just post it here:

I have used them quite a bit as nearly all of my wireless cards have an Atheros chip in them. NDIS and some of the other, default Ubuntu drivers that you mentioned, may work but usually do not give you the full functionality of your cards features, things like powersaving and such, it varies from card to card, but most of these features do work with the madwifi drivers. You will need to use the command line (console, xterm, konsole, etc..) to configure your device with these drivers, but it isn't too difficult. If you need any help with them let me know, thats mostly what respond to on these forums anyways.

First: Thanks for the info about PM, think it will work now :)

I have looked a little on madwifi and found two guides

[http://madwifi.org/wiki/Requirements](http://madwifi.org/wiki/Requirements)
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I'm a little unsure about those do you know if there are any ubuntu guides?
Is the requirements standard for ubuntu 7.10 or do i need to install something extra?



This is a little off topic but hope someone can answer me.
I have tried to get the wlan working with ndiswrappers but have been unsuccesful, so since i did install the latest version with make & install. How do I uninstall these?

EDIT:
this confuses me.
the guide say
> 
ifconfig ath0 down
ifconfig wifi0 down
#Repeat these 2 ifconfig lines for every MadWifi device you have


but my ifconfig return
> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:60:7F:D4:FE  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe7f:d4fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67864162 (64.7 MB)  TX bytes:2648794 (2.5 MB)
          Interrupt:22 Base address:0x6400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


should i becuase of this use
ifconfig eth0 down
ifconfig lo down

???

---

