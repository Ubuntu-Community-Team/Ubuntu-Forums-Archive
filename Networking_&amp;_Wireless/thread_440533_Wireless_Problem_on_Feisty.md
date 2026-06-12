---
title: "Wireless Problem on Feisty"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by USR612 on 2007-05-11
Hi,
I just installed Feisty on my computer, and I'm having trouble connecting to my network with my linksys WUSB54GC adapter.  I can't connect to my network after turning the computer on, but if I reboot from the Vista partition into the ubuntu partition, it will connect fine for an undefined period of time, before disconncecting, reconnecting, and then disconnecting permanently.  With some help on the 'absolute beginners forum' I ran the commands "sudo killall NetworkManager" and "sudo NetworkManager --no-daemon" which resulted in many pages that mean nothing to me.  As the lines became somewhat repetitive, I'll just post the first page:
NetworkManager: <information> wpa_supplicant(5977): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 39 35 31 2d 32 00 
NetworkManager: <information> wpa_supplicant(5977): Cancelling scan request 
NetworkManager: <information> wpa_supplicant(5977): WPA: clearing own WPA/RSN IE 
NetworkManager: <information> wpa_supplicant(5977): Automatic auth_alg selection: 0x1 
NetworkManager: <information> wpa_supplicant(5977): WPA: clearing AP WPA IE 
NetworkManager: <information> wpa_supplicant(5977): WPA: clearing AP RSN IE 
NetworkManager: <information> wpa_supplicant(5977): WPA: clearing own WPA/RSN IE 
NetworkManager: <information> wpa_supplicant(5977): No keys have been configured - skip key clearing 
ioctl[SIOCSIWAUTH]: Operation not supported 
WEXT auth param 5 value 0x0 - NetworkManager: <information> wpa_supplicant(5977): _set_drop_unencrypted 
NetworkManager: <information> wpa_supplicant(5977): State: SCANNING -> ASSOCIATING 
NetworkManager: <information> wpa_supplicant(5977): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
NetworkManager: <information> wpa_supplicant(5977): WEXT: Operstate: linkmode=-1, operstate=5 
NetworkManager: <information> wpa_supplicant(5977): wpa_driver_wext_associate 
NetworkManager: <information> wpa_supplicant(5977): Association request to the driver failed 
NetworkManager: <information> wpa_supplicant(5977): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 39 35 31 2d 32 00 

I'm not sure if the first few lines are here, if needed I can run the command again and get them.
I believe one said something about the driver being supported using 'something'. The only lines farther down that jumped out at me were:

NetworkManager: <information> wpa_supplicant(5977): Trying to associate with SSID 'default' 
ioctl[SIOCSIWMODE]: Device or resource busy 

NetworkManager: <information> wpa_supplicant(5977): State: ASSOCIATING -> DISCONNECTED

Note: This is my first linux system so I know absolutely nothing about it.  I have no idea what ndiswrapper &c. do exactly, I just installed ubuntu and it seemed to see my network, so I assumed the driver was okay.  Now I can always see the network, but can't usually connect.

Thanks, any help is very appreciated!

---

### Post by zshall on 2007-05-14
I'm also having a problem with wireless and the same adapter. I would do ifdown and ifup for wlan0, try to connect using the network icon, it would find the network even, the LED would flash, it would say connecting, then...
nothing.

I couldn't find ndiswrapper on the Feisty CD, but after getting my old CD I found and installed it, added the driver, it said driver present, hardware present. Then I unplugged it, the 2 wireless interfaces went away, plugged it in again, they came back, and only checked wlan0. I tried ifdown again, then iwconfig wlan0 essid mynetwork and then ifup... nothing again.

It just seemed to work in the old version with another card. I wonder if i used that card...

---

### Post by USR612 on 2007-05-20
I've been searching, and can't seem to find a solution.  This site "http://funcation.blogspot.com/" shows how to connect on a Debian 2.6.8 kernel, it might have some useful information, I haven't tried any of it yet.  I'll let you know if I find a fix, but you probably are much more knowledgable with Linux then me, so I doubt if I'll find something you haven't.

---

