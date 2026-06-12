---
title: "need help with basics  of a simple home network"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by engineer85 on 2008-09-14
Hey everyone,

I am very new to linux, and networking, but not computers in general.  

I ultimately (as of now) want to create a file/print sharing network between 2 computers each running only Ubuntu 8.04.  Could anyone provide a link to some basic documentation on both the physical and software setup on how to do this?

To give you some information on how things are currently setup (NOT using wireless):

Computer 1 (which I want to be the "main computer or server, I guess)
Computer 2 (client computer)

I have a cable line for internet coming from the wall, it enters the cable modem, which has CAT6 running to my NETGEAR wireless router.  The router I suppose is acting as a switch with 1 CAT6 cable running to each of computers 1 and 2.  Computer 1 is using eth 1 to connect to the internet (which is working) and Computer 2 is using eth 0 to connect to the internet (which is also working).  How can I make each computer "see" and recognize the other's existence so that I can set up my file sharing network between the two?

Thank you so much,

Steve

---

### Post by unca.paka on 2008-09-14
You can just right-click on any folder/file, and click on Share, that will open up the folder/file to any machine on the network. You can allow guest access so you wont have to setup another user on each machine.
Same thing w/the printer, open the printer control panel, and choose to share the printer. Pretty straight-forward stuffs.
Plenty of info on the forums and google too, just throw in 'home networking linux' 'home networking ubuntu' etc etc.

Also, you might want to try and ping the other machines on the network, just to make sure they are seeing each other. Pop open a terminal and throw in
```
ping -c3 <machine ip here>
```

---

### Post by engineer85 on 2008-09-14
Thank you for replying so quickly.  I tried that option but it says that I need to setup windows sharing network, but I don't have any windows systems.  Is this referring to windows in a more general sense?

Also, did the setup I gave make any sense/sound correct?  I don't know if I need to give some specific name to each computer or something but I can't seem to establish connectivity between the two.  I am trying to confirm that the netgear router I am using can indeed be used as a network switch.

Thanks again,

Steve

---

### Post by bab1 on 2008-09-14
> I tried that option but it says that I need to setup windows sharing network, but I don't have any windows systems. Is this referring to windows in a more general sense?

Ubuntu in a general way directs the user towards using the CIFS/SMB protocol to "share" files and printers".  This is a Windows convention.  Hence, Ubuntu refers to it as "Windows sharing network"  When you setup this sharing you are actually setting up Samba.  If you are using Ubuntu 8.04, you will have lots of problems as the Gnome/Nautilus window and file manager is broken.  This might be repaired in the next release (8.10 Intrepid Ibex).

> I am trying to confirm that the netgear router I am using can indeed be used as a network switch.

I believe the netgear device is both a router and a switch.  The router is what connects the network to the internet (via TCP/IP) and the switch is the part that connects the 2 computers together (Ethernet).  In networking the connectivity is a 7 layer contrivance.  Ethernet is the layer that connects the physical to the software (OS and such); also know as layer 2.  TCP/IP is the networking part; IP addressing and such.  It is known as layer 3.

---

### Post by lisati on 2008-09-14
> **engineer85 said:**
>  I am trying to confirm that the netgear router I am using can indeed be used as a network switch.
The device I have from Netgear (a WGR614v7, wireless [b & g], 4 regular ethernet ports plus 1 dedicate ethernet connection for my ADSL router/modem) can happily tackle the challenge.....

---

### Post by gregphil on 2008-09-14
There are many protocols that can be used to share.  The Windows version of sharing protocol is supported on linux boxes by a service called Samba (smbd and nmbd services).  These can do true "peer-to-peer" sharing (no master server).  If you plan to ever connect a windows machine to your network (a laptop maybe?) I would just go ahead and install Samba.

Like all packages these days this is very easy, open the package manager (update manager) and look down the list of un-installed  packages until you find samba (and probably samba-docs).  click on those to mark for install and then click apply.

Once samba is installed the other menus you mentioned should start working.  Samba is configured at the nuts and bolts level by a file "/etc/samba/smb.conf".  If you are going to edit this directly make a back up copy first.  After each edit run "testparm" to check for typo's in your smb.conf edit, and it all looks OK (no error messages) you can restart samba to make it take effect.  This is done (with root privledge, use sudo) with /etc/init.d/samba restart.  There are various GUI packages that will attempt to make it easier to edit the smb.conf file, you could use your package manager to search for the word samba to find them.

Finally, in a peer-to-peer network, there is a broadcast discovery time (after a samba restart) before all the shares are known about and usable.  This can be up to 12 minutes.  This applies to browsing, if you know the exact destination share name you can connect near immediately.

There are other sharing protocols like NFS, but if you come from a Windows background samba will seem the most "normal".

Your little network will need some sort of name resolution (something that converts share computer names to IP addresses) but if you are using a router with DHCP turned on, the router will normally do this within your sub-net.

Good Luck.

---

### Post by engineer85 on 2008-09-14
Also, you might want to try and ping the other machines on the network, just to make sure they are seeing each other. Pop open a terminal and throw in
```
ping -c3 <machine ip here>
```[/QUOTE]

Can I ask how to find the IP addresses of the machines I am using? :)

Thanks so much!

---

### Post by lisati on 2008-09-14
> **engineer85 said:**
> 
Can I ask how to find the IP addresses of the machines I am using? :)

Thanks so much!

My netgear router has an admin page that can tell you the attached deviced - yours probably has something similar. On my setup I start up Firefox, and type in ```
routerlogin.net
``` in the address line. It then asks for a username (defaults to "admin") and a password (defaults to "password", change it a.s.a.p). I then click on the "Attached devices" link which tells me which machines are currently connected and the ip addresses they have been assigned on my home network.

If it's the internet address you're after, check out [http://whatismyipaddress.com/]("http://whatismyipaddress.com/")

---

### Post by engineer85 on 2008-09-14
Ok, great info.  I checked out the website and was able to determine the internet IP addresses for the two machines.  Also, routerlogin.net works for me too, I set that up a while back, and it allowed me to determine the IP addresses of the devices attached.

If I understand correctly, the Inet IPs are those which the router uses to send me to the Inet, and the device IPs are those which my personal network uses for file sharing purposes?  Any clarification would be most helpful.

Steve

---

