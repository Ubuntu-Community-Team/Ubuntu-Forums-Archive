---
title: "Wireless broken after using wvdial"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by macking on 2007-07-04
I got my Nokia 6300 up and running as a GPRS modem using wvdial, but now my wireless is broken. I use network-manager to handle the wireless connection. The connection is established alright but I cannot ping any address or find any site in Firefox. It looks like an DNS issue to me, but I don't know where to fix it.

Any help greatly appreciated.

Martin

---

### Post by limbourg31 on 2007-07-04
check the DNS tab and ensure the modem is actually active in the modem tab of the networking manager

---

### Post by macking on 2007-07-04
Sorry I wasn't clear. The Nokia/wvdial works fine. It is the wireless ethernet connection that is broken. Normally network-manager will let me hook up to any open access point and everything just works, but now I just get the connection but cannot ping anything or find any sites in Firefox. I have disconnected the phone and stopped wvdial when trying to use the wireless connection.

Martin

---

### Post by limbourg31 on 2007-07-04
eth0 is probably not active try and activate ethernet in netowrk manager ... if there is just a connection that means that there is a problem in the actual setup of the ethernet port or the cards

---

### Post by macking on 2007-07-04
The card is active and working, I get an IP address and everything. Is there any way wvdial can interfere with the DNS set-up used by network-manager. The resolv.conf has the info I would expect and I can acces the homepage of the router I am connected to, but nothing else.

Martin

---

### Post by limbourg31 on 2007-07-04
are you trying to access network throu ethernet or wirelessly? DNS would be only important if you are trying to log in through an intranet to a larger network or host through a modem which is what you are doing right? 

[http://staff.xiaoka.com/smoku/2007/05/10/networkmanager-and-gsm-dial-up-over-bluetooth/](http://staff.xiaoka.com/smoku/2007/05/10/networkmanager-and-gsm-dial-up-over-bluetooth/) might be useful since it gives a really detailed howto

if you don't want to read it here it is condensed:

1. hcitool scan and locate the id of the device
2. sdptool browse "this id"
3.  If dialup networking service is present, set up the rfcomm port for it in /etc/bluetooth/rfcomm.conf:
      rfcomm0 {
     bind yes;
     device "this id"
     channel 1;
     comment "Smocza N80 DUN";
     }
4. echo > /dev/rfcomm0 to test if it works, a BT connection should exist
5. Add the modem to your devices in network manager and then add the init string for your GPRS provider to /etc/wvdial.conf

---

### Post by macking on 2007-07-04
The GPRS modem is working fine. It is the connection through my WLAN card that is the problem. It used to work flawlessly, but ever since I used wvdial to hook up the GPRS modem, its broken.

Martin

---

### Post by limbourg31 on 2007-07-04
did you make sure all your settings were right, i.e. accidentaly putting DHCP instead of static IP? post the lspci output so we can see if the device is even recognized now

---

### Post by macking on 2007-07-04
I have this when running lspci:

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

I do not have to choose btw DHCP and static when using NetworkManager ([http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)) - that is handled automatically.

Martin

---

### Post by limbourg31 on 2007-07-04
are you in edgy or feisty? your card is being recognized but not functioning so it may not be activated... try configuring the wlan0 or wmaster0 on network manager and also try to install the windows drivers through ndiswrapper and modprobe ndiswrapper

---

### Post by macking on 2007-07-05
limbourg31,

I am Edgy. Thanks for trying to help out, but your advice simply does not make sense. The card is working, as NetworkManager is able to get a connection and bring up the routers homepage. My issue is resolving other sites.

Martin

---

### Post by limbourg31 on 2007-07-05
Sorry for the confusing advice

Let me try again, when you say the router's homepage does it load a site on the http:// protocol or one on file:///? Edgy has a problem with cards, so if the site is on file:/// that just means the sites are loading from the router's own memory, not from the network... which results in you having  to download ndiswrapper

---

### Post by macking on 2007-07-05
It is me who is sorry. The network admin at the library where i was trying to connect has just informed me that their dns was broken yesterday and he was trying to reinstall it - nothing wrong at my end. Sorry for the inconvenience - very nice of you to try and help out.

Martin

---

### Post by limbourg31 on 2007-07-05
thats fine, and good luck with your DNS

---

