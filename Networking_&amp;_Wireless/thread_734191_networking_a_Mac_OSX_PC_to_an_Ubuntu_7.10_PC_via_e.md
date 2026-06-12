---
title: "networking a Mac OSX PC to an Ubuntu 7.10 PC via ethernet using an ADSL modem w/route"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by vilppu on 2008-03-24
I have an Adsl modem that is connected to the Internet. The modem has a local network router for four computers via ethernet connection. I have a windows 2000 computer and several Macintosh OS X computers on the network. The Fujitsu Ubuntu machine is connected to the ADSL modem and works fine with the internet, and I can Ping _some_ of the other devices from it and I am able to ping it from the other computers.- However it will not ping my "main" computer and I have not been able to connect _to_ the Ubuntu device nor _from_ it to the other devices. I would like to be able to transfer files to and from the Ubuntu to my main computer as freely as I can with the other computers. The apple computers use afp:// protocol and the windows one uses smb:// protocol is there a specific protocol for linux?

the ADSL/router uses DHCP and assigns the IP addresses more or less randomly. the first device to open the connection gets the lowest IP number.
the Network settings (on 7.10) is set for "line connection". (not bluetooth or WLAN)
I should be able to choose "connect to server" from the apple menu Go> Connect to Server and type in the ubuntu machine's Ip address and then click the connect button and get the password dialogue box. Unfortunately that is not happening.

Pinging the Ubuntu Machine(UM) IP address from the main computer works successfully. Pinging the Main computer from the UM does not work although the UM can ping the other computers and itself. When i try to connect (to UM) with smb - (smb://1.1.1.1) I get a password error message (could not connect to the server because the name or password is not correct) When I try to connect using nfs - (nfs://1.1.1.1) the connection panel just keeps rolling and rolling. I suspect that there may be a misconfiguration in the networking settings on the Ubuntu machine, or on the Main computer. So far the OSX macs will connect over to each other and win2k (and 98) without a problem. 

When I go the "places" route and use the "connect to server" option I get icons for the other machines to mount but when I try to open the mounted "servers" I get an error message: 
Couldn't find ./1xx.xx8.x.3x

strange. 

vilppu

---

### Post by Eiríkr on 2008-03-24
There is no specific protocol for Linux sharing.  That's one of the happy things, there are several, and you can choose from among them to pick the one that's best suited to your situation.  

With a mixed environment like this, Samba is probably your best bet for sharing in all directions.  If your Macs are running OSX, you can change them over to using the SMB protocol pretty easily.  Open System Prefernces -> Sharing, and enable Windows Sharing in the list.  

What OS does your "main" computer run?  Do you have a firewall running?  That's all I can think of that might be blocking pings.  

For connecting from the Macs to your Ubuntu machine, provided you have your Samba server configured and running, pull up the Connect to Server dialog and type in:
```
smb://IP.ADD.RE.SS
```
Leaving out the "smb://" prefix won't work.  

Also remember that, even after properly configuring Samba, you still need to add the Samba users to the Samba password file for access to work properly:
```
sudo smbpasswd -a USERNAME
```

HTH,

Eiríkr

---

