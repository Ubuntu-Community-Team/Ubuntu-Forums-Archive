---
title: "Configuring samba and dell wireless 1450 usb 2.0 adapter"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by james.pinkerton on 2007-12-14
Hello everyone. I am new to linux so this is my first post. I need people to explain things on a lower level.

I just recently downloaded ubuntu 7.10 and I am using gnome. When I purchased my dell PC I got a wireless 1450 USB adapter. I also got a dell router that did not work at all so I got a rangemax 240 router from netgear. When I first got onto linux I had some connection problems so I followed this link's [http://ubuntuforums.org/showthread.php?t=327098&highlight=dell+1450](http://ubuntuforums.org/showthread.php?t=327098&highlight=dell+1450) instructions on configuring the drivers with the installation CD. I did what silentvoice said to do. The problem I currently have is that when I log into ubuntu the internet connection will be stead, but then it will suddenly say 0% connection. It then says there is no connection a few minutes later and it will try to reconnect without success. The only way to get back onto the internet is to either restart the computer or disconnect the adapter and then plug it back in. On xp I think instead of suddenly failing it will "searching for IP address"

My second question is how to configure my home network with linux. I can see other workgroup computers inside the network, but I cannot access their shared folders. I got the impression that this is what samba is for? I went to this link for some installation instructions   [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)  and I got as far as the part on static and dynamic IP addresses. I don't understand how to check what kind of IP address I have. Do I want the router's IP address or the computer with the 1450 adapter's address? I typed sudo dhclient twice in the terminal and got the following:


james@james-desktop:~$ sudo dhclient
[sudo] password for james:
There is already a pid file /var/run/dhclient.pid with pid 6107
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/wlan0/00:90:4b:cd:f7:41
Sending on   LPF/wlan0/00:90:4b:cd:f7:41
Listening on LPF/eth0/00:11:11:c1:b8:5d
Sending on   LPF/eth0/00:11:11:c1:b8:5d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 42232 seconds.
james@james-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6556
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:11:11:c1:b8:5d
Sending on   LPF/eth0/00:11:11:c1:b8:5d
Listening on LPF/wlan0/00:90:4b:cd:f7:41
Sending on   LPF/wlan0/00:90:4b:cd:f7:41
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 36448 seconds.
james@james-desktop:~$ 


He goes on to talk about making a partition?


-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

Code:

sudo mkdir /home/samba

... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:

Code:

sudo chmod 0777 /media/samba

NOTE: Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...

Sorry about the long post thanks for the help

James

---

### Post by jebber on 2007-12-14
James,
Samba is for exactly connecting to Windows shares.  I haven't been in the details or at the command line for years, but I remember a command line interface different than what you posted.  I have psubuntu loaded, and when I connect it is effectively the same as a windows share.  When I go to "places/ network" I get a list of windows servers in my workgroup.

I didn't catch your entire question about DHCP vs Static IP addresses, so I'll answer briefly.  DHCP is a dynamic address.  You can configure a client to connect to a network using a dynamic address or a static address.  Dynamic addresses are provided by servers.  If you can browse the web from all of your clients then you should be able to communicate between them.  (DHCP is at the IP layer and is much lower than whether or not Samba works.)

Try setting all of your clients up for the same workgroup.

---

