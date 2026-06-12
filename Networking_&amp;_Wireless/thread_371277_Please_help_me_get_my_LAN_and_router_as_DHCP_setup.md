---
title: "Please help me get my LAN and router as DHCP setup"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by dryder on 2007-02-26
Hi,
Please have patience with this embarrassingly long Linux newbie post - thanks.

I admit defeat trying to configure ubuntu 6.10 connected to a Netgear FVS318 router which acts as a DHCP server. I have (for some years) used the router's LAN IP addressing to reserve IP addresses for different computers on the LAN. (My LAN is hard wired.)

All computers connect through the router which in turn connects to tha adsl modem/router. The adsl modem/router is setup in bridge mode so in effect the modem is acting only as a modem, not a router.

In Network Settings I have 'Wired connection' (enabled) and 'Modem connection' (disabled).

For the 'Wired connection'>Properties I see the 'Settings for interface eth0' are: Configuration: Automatic (DHCP). But I don't want that as I want the router to be the DHCP. The alternative is Staic IP Address. I don't want that either for the same reason.

So I looked in the Netgear Administration and, yipes, the linux computer is not  even seen as Attached (but it is when I boot into Windows and it also has the correct IP address so obviously the MAC number is correct).

Under the General tab the Host name is correct. The Domain is blank as I use Woorkgroups not Domains in Windows. Automatic service discovery is ticked.

Under the DNS tab 'DNS Servers' - wo! - it shows the router address so it must be able to assign the IP address I want - if I can get help on this post, of course. 'Search Domains' lists 'Type' and 'address' which mean nothing to me ... (help please?)

Moving to the 'Hosts' tab I see ther IP address 127.0.0.1 is Alias localhost and the same address is this linux computer (ouch!)

So I look at 'Network Tools'. It is set to 'Loopback interface [lo]) Protocol IPv4 (I want TCP/IP don't I?) with IP Address 127.0.0.1 mask 255.0.0.0. Hmmm. But changing it to the option Ethernet Interface (eth0) I get the Protocol IPv4 ... but ... with the IP Address and mask that I assume came from my router and the IPv6 is fe80::20c:6eff:fec6:3d83. And [2]0c[:]6e[ff:fe]c6[:]3d83 just happens to contain my MAC address (00.0C.6E.C6.3D.83). Now I'm really tearing my hair out. I connect to the internet without any problem so it must be going through the router - so why doesn't the router see it?

Please bear with me ...
So I try to Configure Ethernet Interface (eth0) but am denied permission. Dead end.

After a lot of gurgling, sorry, googling and reading as many HOWTOs and posts as I can I seem unable to connect Ubuntu 6.10 to my LAN let alone have my router 'see it'.

To summarize:
1. I want the router to be the DHCP and supply the IP Address - it is setup to do so.
2. I want to see and be seen on the LAN even though at this stage the rest of it is Windows. I need to be seen on the LAN so my UPS can shut me down on power failure.
3. I want to share some folders/drives and devices such as printers. Yes, I have the Windows app installed so Windows can see Linux partitions and file system.

Please can anybody help me? I would be very grateful.

Very many thanks,
David

---

### Post by Gerard Barberi on 2007-02-26
If you want the router to be DHCP, then eth0 should be set to (automatic)DHCP.  This does not mean it will assign an IP, only that it will accept an IP to be assigned to it.  In order for your PC to assign an IP, you would have to install a DHCP server on it.

Try turning off the modem and then back on.  It should see your PC.  It having windows or Ubuntu on it should not be affecting your router's ability to "see" the PC.  It records mac addresses and not Operating Systems.

If you want to share files and folders on the LAN, then you need to learn how to use SAMBA.

see this thread

[http://www.ubuntuforums.org/showthread.php?t=202605&page=29](http://www.ubuntuforums.org/showthread.php?t=202605&page=29)

---

### Post by dryder on 2007-02-26
Thanks Gerard Barberi - reading that guide has got me a long way and you explaining 

> ... set to (automatic)DHCP. This does not mean it will assign an IP, only that it will accept an IP to be assigned to it.

cleared a lot of things up.

One thing I am stuck on following the HOWTO though, I wanted my >path = /media/samba/ to be /home/networkshare/samba (the guide says the path can be to a folder). Trouble is, 'networkshare' and 'samba' folders were created as separate folders under / instead of /home.

I can not get permission to move them (nor to delete a folder I created by misspelling it) ... I used sudo and gksudo nautilus but was still denied permission.

But - I can see the network now in linux -I have yet to test the other way round and DHCP ...

David

---

### Post by slayerboy on 2007-02-26
you really shouldn't have "/home/networkshare/samba", as the home folder is strictly for users.  you could create a link to the /networkshare and /samba folders in your home directory, otherwise it's easier for all users to just be able to navigate to the /networkshare or /samba folders.

what if you tried:
```
sudo rm -r /"your-directory-name-you-don't-want-here"
```

---

### Post by dryder on 2007-02-26
Hi slayerboy,

I am assuming that
networkshare
netshare
and samba (all empty) are folders I created rather than folders created by the system?

If so, /networkshare deleted OK, /netshare gives me a warning "rm: remove write-protected directory `/netshare'?"
and /samba I haven't tried to delete in case either are folders the system created, not me. (when creating the folders I mistyped netshare for networkshare but one never knows all the names of system created folders).

Would it be better to create the folder tree under my username david? But that is /home/david which ubuntu created on setup? > the home folder is strictly for users

Many thanks

GREAT - after rebooting the Windows network is still seen, its workgroup, computers and drives and linux appears in the workgroup - AND the router sees this linux box  and has allocated the correct IP! . You are a great help.

Much gratitude to all 'helpers' (in all fora),
David

---

