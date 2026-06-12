---
title: "Network LAN transfer slow"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by capdog on 2007-02-09
Greetings everyone

I've got a problem I hoped someone could shed some light on. My LAN connection from my Edgy Eft laptop to other computers is much slower than it should be, noticeable when sharing files.

When I boot my laptop into Windows, the network connection sits at about 85 - 95 % utilization when copying a file, or just under the theoretical maximum of 12.5 MBytes/sec. 

In Edgy, I only get about 3 - 4 MBytes/sec. I've tried a number of random things suggested on the forum, from disabling IPV6 to editing the smb.conf file to add socket options= SO_RCVBUF=8192 SO_SNDBUF=8192, but they don't work.

My network adapter is a Broadcom BCM4401-B0 100Base-TX.

Laptop is a HP Compaq NX7300, relatively new with Intel Core 2 Duo.

Can anyone please help? Or point me in a sane direction?

The other strange thing is that the processor usage goes up quite high to about 33%, the culprit is nautilus...

Thanks
capdog

---

### Post by Yuzem on 2007-02-09
Same here but worse.
In XP I get about 4 MBytes/sec and in Edgy I only get about 1,5 MBytes/sec
I also want to know what can I do to improve the network speed.

---

### Post by capdog on 2007-02-10
Hi Yuzem

Have you tried any solutions? Maybe there is something that you have done that may help me?

I've searched everywhere and I can't find any answers! I wonder if it's a bug in the kernel, or samba, or nautilus... it really is a blow!

Regards,
capdog

---

### Post by Jnex26 on 2007-02-10
Try looking at your network history in the system monitor is it doing this (See attached image) 

If so we are all in the same boat.

---

### Post by Yuzem on 2007-02-10
> **Jnex26 said:**
> Try looking at your network history in the system monitor is it doing this (See attached image) 

If so we are all in the same boat.
It isn't doing that to me.

> **capdog said:**
> 
Have you tried any solutions? Maybe there is something that you have done that may help me?

Now I am getting more speed.I have set the devices to full duplex
It is still too slow.
On XP I am getting 6 MBytes/sec and on Edgy 2,5
If your network card is eth0 you can type this on the terminal:
```
sudo mii-tool eth0 --force=100baseTx-FD
```
To view the status type:
```
sudo mii-diag
```
or
```
sudo ethtool eth0
```

I have managed to get more speed (still slow) in the following way:
I have an apache server on the server computer. I can access the server from firefox by typing the computer address on the address bar.
Then with a download accelerator manager (I use an extension for firefox: [downthemall]("https://addons.mozilla.org/firefox/201/")) I can transfer a file from the server computer to the client and I get more speed but not much more.

The apache thing isn't an option for me. I only tried that to see if the speed was different.
Tell me if any of this worked for you. I am still looking for an answer.

---

### Post by Jnex26 on 2007-02-10
sudo mii-tool eth0 --force=100baseTx-FD

That's a invalid command on my system. 


Using the default interface 'eth0'.
Basic registers of MII PHY #0:  3100 792d 02a8 0380 0de1 45e1 0007 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

here is my config. 

I have recently removed my wireless network card and it made the internet respond a little faster but it's still not great.

---

### Post by capdog on 2007-02-11
Thanks for the screenshot, I can't check at the moment but I'll let you know. Although I'm not sure if it is jumping like that, it seems to be more consistent but just slow.

---

### Post by Yuzem on 2007-02-11
> **Jnex26 said:**
> sudo mii-tool eth0 --force=100baseTx-FD

That's a invalid command on my system. 



Maybe you dont't have mii-tool installed. It seems that you already have  100Mbps Full Duplex.
You can check that by typing:
```
sudo ethtool eth0
```
An alternative to mii-tool to set Full Duplex:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

---

### Post by Jnex26 on 2007-02-15
> **Yuzem said:**
> Maybe you dont't have mii-tool installed. It seems that you already have  100Mbps Full Duplex.
You can check that by typing:
```
sudo ethtool eth0
```
An alternative to mii-tool to set Full Duplex:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Here is the results from the sudo ethtool eth0 command 

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

---

### Post by Yuzem on 2007-02-15
You have it set to 100m/s Full Duplex, you have to be sure that all devices in your network are working in the same mode.

---

### Post by dmizer on 2007-02-15
let's take a step back here ...

you say your lan connection is much slower than it should be.  what kind of protocol are you using, and by what means are you connecting?

for example ...
http?
ftp?
ssh/scp?
samba?
nfs?

this is just a SHORT list of a few of the different protocols available for handling various kinds of file sharing traffic across your lan, but i don't see where you indicate what kind of connection you're using, and it's difficult to try to narrow a problem down without knowing exactly what the trouble is in the first place.  this is especially true when you consider that there are various methods and techniques for managing all of the above protocols.

for example:
while mounting samba shares via nautilus (as with: places > connect to server) is painfully slow and (in my opinion) unusable, mounting samba shares via smbfs is much faster and more stable.  furthermore, mounting samba shares via cifs is even faster and more stable than smbfs.

so ... how do you have your shares mounted?  have you tried other protocols like nfs, cifs, or smbfs?

---

### Post by Yuzem on 2007-02-15
I'm using smbfs and the speed is about 2,5MB/s while in XP is about 6MB/s
I have just tried cifs and it is not better than smbfs. It starts at 3MB/s but then goes to 1,7MB/s.
I get the faster speed (about 4,8MB/s) using wget to download a file from a http server over the lan.

---

### Post by dmizer on 2007-02-16
something else is wrong here.  have you disabled ipv6?

add:
blacklist ipv6

to the end of this file:
/etc/modprobe.d/blacklist

also, make sure that your router (eg 192.168.x.x) is NOT listed as a dns server.  try working through this thread: [http://www.ubuntuforums.org/showthread.php?t=282034&highlight=howto+fix+dns](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=howto+fix+dns)

---

### Post by Yuzem on 2007-02-16
Thanks for the help

ipv6 is disable on my system
I dont have a router or my XP machine is the router. My computer (ubuntu edgy) is directly connected to the XP machine that act as a dhcp server (on XP: ICS internet connection sharing)

(edgyPC) -----> (XP-PC) -----> (cablemodem)

---

### Post by dmizer on 2007-02-16
in which case, your xp machine is your router.  either way, you still need to make sure that the dns servers in edgy are set to either your providers or set to opendns.org servers instead of set to your xp address (most likely 192.168.0.1).  this really is critical in order to make sure that speed is optimized.

so i still suggest you try the link i gave above.

also what are you running for an xp firewall?  and are you sure that the firewall on the network adapter connected to your edgy pc is off?  almost every xp update that comes down the pipe turns that ics firewall back on and messes up the whole works again.

---

### Post by Yuzem on 2007-02-19
I did the open dns thing but I don't see any changes on the speed.
My XP firewall is Sygate and it is configured to allow network traffic to the network adapter connected to my edgy pc.
The default XP firewall is off.

I noted something else: When I copy a file (smbfs) to an ext3 partition it goes faster (3,1MB/s) than doing the same to an ntfs-3g partition (2,5MB/s)

The last time that I checked the speed on XP it was about 4MB/s it is practically the same (or a little less) than using wget to download a file from the server on my other computer.
Wget is also faster when downloading to an ext3 partition.

---

