---
title: "[SOLVED] Wireless connectivity challenge"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by daggerx on 2008-07-05
I cannot connect to my home network via wireless

```
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:52:f7:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.106 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:0f:ea:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

I did what i was told to do via [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction") mine was the 2e. I can see my network and other networks. i can connect to the neighbor's "netgear" (unsecured) but I cannot connect to mine (wpa2-aes). I tried my network broadcast and non-broadcast (I got nothing). Please assist me in any way you guys/gals can. Thanks in advance. God bless.

I have a Dell Inspiron 1525. I can use my ethernet. That works.

---

### Post by Sam Lars on 2008-07-05
I've got a 1525, too, connected with WPA-TKIP.  Sounds like the WPA is the barrier for you.  Are you using network-manager to connect?  It works fine for me.

---

### Post by daggerx on 2008-07-05
> **Sam Lars said:**
> I've got a 1525, too, connected with WPA-TKIP.  Sounds like the WPA is the barrier for you.  Are you using network-manager to connect?  It works fine for me.

yeah, im using network manager, this is a fresh install (like last night fresh):cry:

---

### Post by Sam Lars on 2008-07-05
So when you go to connect to your network, you type in the passkey, it tries to connect but doesn't?

---

### Post by daggerx on 2008-07-05
> **daggerx said:**
> yeah, im using network manager, this is a fresh install (like last night fresh):cry:

freakin weird - just connected (using wireless now) freakin weird...

---

### Post by daggerx on 2008-07-05
> **Sam Lars said:**
> So when you go to connect to your network, you type in the passkey, it tries to connect but doesn't?


Yup, the first green bubble lights up and the second one doesnt and then from there it proceeds to connect me to the netgear network

---

### Post by daggerx on 2008-07-05
spoke too soon, still having issues with this...

---

### Post by daggerx on 2008-07-06
any more advice on this

---

### Post by Sam Lars on 2008-07-06
So did it ever connect?
If you right click on the applet, and Edit Wireless Networks, does it all look alright?  The key should be the really long hex thing, not the passkey...

---

### Post by daggerx on 2008-07-06
> **Sam Lars said:**
> So did it ever connect?
If you right click on the applet, and Edit Wireless Networks, does it all look alright?  The key should be the really long hex thing, not the passkey...

:( i've been putting the passkey all this time...
i just redid my ubuntu install where to i get the hex from - getting ready to redo the ndiswrapper and wpa supplicant again from that "no fluff" page...

---

### Post by Sam Lars on 2008-07-06
When it pops up it needs to be the passkey, but in the edit wireless networks, it should show as the hex key.
You can get the hex key like so:
> 
```
wpa_passphrase <your_essid> <your_ascii_key>
```Resulting in an output like...
```
Quote:
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
```Copy the "hex_key" (next to "psk=...")This is from [here]("http://ubuntuforums.org/showthread.php?t=202834"), you might want to also check that out for setting up WPA.

---

### Post by daggerx on 2008-07-06
fair enough,
here is some more weird stuff
i put in wpa-tkip info when I tried to login to my network and it worked immediately, I do have my network accepting both protocols (linux tomato firmware). So its connected as WPA-TKIP...im gonna reboot and see if it holds..


ok it didnt hold....i got the hex though...

---

### Post by daggerx on 2008-07-07
ok still no wifi juice, at least from my home network that is...empty out my net interface file
my nm still sees wifi networks I connected to a school open network while I was at work. I think was it happening now with me is that im getting a little confiused with some of the material.

for example in my case, do i need to setup a wpa supplicant conf file? I just want the thing to work via nm, thats all. Should I post screens of my current setup (which is really nothing). All I did so far was the ndiswrapper and the 2e driver setup from the no fluff page. I think my lack of familiarity in this part is frustrating me a little - This is the only challenge I have and I hope I can get this info in my head and apply to my ubuntu soon  - this is driving me bonkers - ](*,)](*,) Please help - if I need to do a iwlist and go step by step to get the end result  - please help in any way u can....I like the world without walls and fences.

---

### Post by Umar07 on 2008-07-07
i also can't connect to my wireless and need help

---

### Post by daggerx on 2008-07-07
Ok, not sure if this matters or anything but I was looking around and i tripped over some online guide via google and it talked about the wpa supplicant and to make sure that the "Enabled=0" line was in the wpa supplicant. So I got to thinking and I doublechecked my wpa sup and the "Enabled=0" was in there 2x. Could that have been my issue all along. Would I have challenges connected via wpa if I had that entry in the wpa supp file twice. Please advise and thanks. specifically the admin gave these instructions:

> Procedure to enable WPA Wireless in Ubuntu

To update the source list run the following command

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command

sudo /etc/init.d/dbus restart

The instructions specifically says add entry and not "entries" and when I checked my  /etc/default/wpasupplicant, it was in there 2 times. Please comment and advise. didn't test my wpa network yet (not home yet)

---

### Post by Sam Lars on 2008-07-07
I guess it *could* be your problem.  You could try that and see.
The whole point of network-manager is to make connecting to the network easy.  You should just need lo in your /etc/network/interfaces, and nm should do the rest.
I think that guide may help you getting WPA to work with network-manager, you can try it out.  I'm going to try it myself to see if it does anything for me.
I have issues with WPA myself.  Sometimes I get disconnected, and it takes a few tries to get connected again.  So if you haven't already, try connecting a few more times if it fails the first time.

---

### Post by daggerx on 2008-07-24
I was able to connect  - I'm currently using the new network manager, everything is going good. Thanks for all your help.

---

