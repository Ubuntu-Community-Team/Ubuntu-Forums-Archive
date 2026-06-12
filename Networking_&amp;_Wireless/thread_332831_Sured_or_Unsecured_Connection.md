---
title: "Sured or Unsecured Connection"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by clemkonan on 2007-01-06
My objective is to get a PC on my second floor connected to the internet. My network consist of:
1) Bell Sympatico Speedstream 6520 modem / router
1) 2 PC's  running XP wire to router
1) 2 PC's running Linux in remote locations and using Linksys WURT 54G ver 4 routers 

My Steedstream is using :

1) my name as the SSID
2) set to channel 11
3) no passphrase
4) 64 bit encryption consisting of a 5 by 4 matrix where the first row is something like ao 73 b6 c8 2a ( not the actual numbers

I do not know if row 1 is to be assigned to the fist remote pc, row 2 to the second and so on.

In other words each row is equivalent to a 10 character key.

My queastion is this, am I correct in stating that I am a candidate for an out of the box set up since the Speedstream already has me behind a firewall with what I think is WPA encryption.

I cannot recall the inputs to terminal but here is some output I am sure you will recognize:

auto eth1
i face eth1 inet dhcp

auto eth2
i face eth2 inet dhcp

auto wlan 0
iface wlan0 inet dhcp

iface rausbo inetdhcp
wireless essid clemkonan
wireless key s
auto rusb o

sudo if down rao
ifdown: interface rao not configured

sudo ifup rao
Ignoring unknown information rao=rao

In basic terms how shoould I proceed?
 
Sorry I am using  Ubuntu Edgy

Thanks


:twisted:

---

### Post by tturrisi on 2007-01-06
64 bit encryption = WEP = weak security, you are not using WPA.
If your dsl modem-router also has a built in access point then why use these: Linksys WURT 54G ver 4 routers?

---

### Post by clemkonan on 2007-01-06
I do not understand your point about WUSB54G. If 64 bit = WEP thats fine I will switch to WPA. As to why I am using a wireless adapter, there is no other way I can connect a remote PC, or is there? This PC is located upstairs and my access point is in the basement.

Now if truth be known, I have a Linksys Broadband Wireless G WRT54G but I do not know if it can replace the Speedstream as it needs to accept a phone line. I was using the WRT54G with my cable provider (Rogers)

---

### Post by tturrisi on 2007-01-06
> 1) 2 PC's running Linux in remote locations and using Linksys WURT 54G ver 4 routers
This is why I asked what I did.

---

