---
title: "Can't get static IP to work"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by texasrsx on 2008-09-27
I am a newbie to linux and am trying to set up a file server on my home network.  I installed xubuntu on an old computer and with auto DHCP it works fine.  I can set up a shared drive that my other computers can see but it does't have a static IP.  Every time I try to set a static IP an error that it doesn't recognize the host server.  I have been searching the forums for days and have tried everything I can find and nothing works.  I don't need to have this computer connect to the internet, just to be visible to the other computers.
These are the values that I am using

auto eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254

I also edited the resolv.conf file and made it say
search gateway.2wire.net

nameserver 68.94.156.1
nameserver 68.94.157.1

I got the nameservers from my router and am not sure if they are correct.  I am also assuming that the gateway address is the same as the router IP, and am not sure that is right.
Any help would be greatly appreciated.

---

### Post by Iowan on 2008-09-27
You  will probably need an "auto lo" line (or edit line to read "auto lo eth0".  Beyond that, I remember a thread/post that mentioned that a static address in DHCP environment behaved somewhat strangely... name didn't get registered, so it couldn't be seen.  I've edited the **hosts** file on my DHCP/DNS server so it knows the IP/name of my static addressed machines.

---

### Post by casper_2095 on 2008-10-07
I'm *not* a new linux user and sympathise. I'm having the similar difficulty setting a static IP. Ordinarily a little tweak of "/etc/network/interfaces" would be enough but this two minute job is turning into hours.  I'm still working on it but it looks like there are several "helpful" layers of other stuff which are interfering: "NetworkManager" and "avahi" are on the 'persons of interest' list.

Different approach solutions are not helping: the DHCP server on this network is not controllable and xubuntu does not seem to have a gui for this.

---

### Post by casper_2095 on 2008-10-07
Found the gui - click/right click on the network icon in the top right of the tray and wander around in there (ipv4 tab).

It applies immediately but i'm still having trouble with it hanging indefinitely on boot after doing this.

Sorry to hijack the thread: as for the original poster, did he get his static ip? If he has avahi running ok the machine should answer to {hostname}.local shouldn't it?

---

