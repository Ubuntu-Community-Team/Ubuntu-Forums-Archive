---
title: "NFS Share Slow"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Deathmoon on 2007-10-30
I've searched the forums and the web and I haven't found too much concrete evidence regarding the slowness of NFS.  I have an all Ubuntu network at home that I have shares setup on one of the computers.  

I have the NFS share working and it works ok, it's just painfully slow.  This isn't a new issue and I've had it since 6.06, but I'm just now wondering what I can do to resolve it.  

I've looked at OpenAFS, but I haven't had much luck setting it up; and from what I've read it's more secure but not much faster.  Furthermore, I've read (and tested once) Samba and it too was slow, possibly slower.

So...What are the options available?  What does a linux server utilize to share files, and why is that technology not slow?

Finally, if the answer to my questions have already been posted please direct me to the thread.  I searched and found nothing concrete.

Thank you!!!

---

### Post by Jose Catre-Vandis on 2007-10-30
What does slow mean? How long to copy 100 x 1mb files or 1x 100mb file? i can shift 700mb file in about 2 minutes.

What network setup do you have? wired/wireless? How fast are the NIC's? 10/100? are they running full duplex?

What settings do you have for your NFS shares?

---

### Post by Deathmoon on 2007-10-30
A 62mb file took 83 seconds to copy; another example is just using image viewer to change between JPG in my pictures directory take a few seconds (the images are 1-2 mb in size).

I have a Linksys router (WRTP54G); and yes I'm running both machines via a wireless connection.  Now via, updates, downloads, etc. from the Internet I've seen 400kbps+.

**NFS Share on Server: (/etc/exports)**
/home/USERNAME/PICTURES 192.168.15.103(ro,sync,all_squash)

**NFS Share on Client: (/etc/fstab)**
sudo mount SERVERNAME:/home/USERNAME/PICTURES /var/music
SERVERNAME:/home/USERNAME/PICTURES /var/music nfs r,hard 0 0


The one item that I do not know is the full duplex / half duplex question.  I ran sudo ethtool wlan0 and the results came back as "no data available".

---

### Post by Jose Catre-Vandis on 2007-10-30
Try this setting in your fstab:
```
SERVERNAME:/home/USERNAME/PICTURES /var/music    **nfs rsize=8192,wsize=8192,timeo=14,intr,bg**
```

---

### Post by Jose Catre-Vandis on 2007-10-30
I use this in /etc/exports
```
/home/USERNAME/PICTURES 192.168.15.1/24(rw,no_root_squash,async)
```
(you will have to re-export your share and probably restart nfs server)
and this in /etc/fstab
```
SERVERNAME:/home/USERNAME/PICTURES /var/music nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

(sorry for the double post, not concentrating :))

---

### Post by Deathmoon on 2007-10-31
I made the changes, and it took 83 seconds; same as the original time.

on the server, after making the changes, I executed 
> 
sudo exportfs -ra

and restarted the computer.

On the client, I made the changes to the fstab file; and restarted the computer.

No luck.

---

### Post by netztier on 2007-10-31
> **Deathmoon said:**
> I have a Linksys router (WRTP54G); and yes I'm running both machines via a wireless connection.  Now via, updates, downloads, etc. from the Internet I've seen 400kbps+.

Running a file server and the client both on wireless via the same AccessPoint leads to a race for bandwith, explained in this thread (last posts):

[http://ubuntuforums.org/showthread.php?t=534370](http://ubuntuforums.org/showthread.php?t=534370)

"54mbps" is a blunt marketing lie. An 802.11g WLAN will yield at most 25Mbps real-world throuhput, of which half is used for server<->AP, the other half is used for client<->AP traffic. So we have at best 1Mbyte/sec. 

Now let signal quality suffer just a little bit, and you restart this calculation with 18 or 20Mbit/s to start with, and you result with the roughly 750kByte/s you are seeing.

Solution as suggested by that thread: the server-to-client traffic must be "transit" (WLAN <-> LAN) for he AccessPoint, not WLAN<->WLAN. Ergo: run the server on the wired part of the LAN.

> **Deathmoon said:**
> The one item that I do not know is the full duplex / half duplex question.  I ran sudo ethtool wlan0 and the results came back as "no data available".

Full/Half Duplex issues don't apply to wireless. WiFi is half duplex only by design.


best regards

Marc

---

### Post by Deathmoon on 2007-10-31
thanks netztier for the reply; I read the thread and did the same test in iperf; I was getting 7.19 from client to server on average and 7.90 from server to client.

The wired test on the server easily doubled the output of the server.  

I guess that this is "normal"...it does seem that before I switched to Linux in my old operating environment that this was not an issue.

Regardless, I'll get a NAT device I suppose to resolve the problem.

Thank you for your help!  It is very much appreciated.

---

### Post by Jose Catre-Vandis on 2007-10-31
I learnt something too :)

---

### Post by netztier on 2007-11-01
> **Deathmoon said:**
> 
Regardless, I'll get a NAT device I suppose to resolve the problem.


I doubt that NAT  will help in this scenario. You'd have the same problem if you didn't have a router at all, but only a LAN switch together with an WLAN access point.

All these common "Wireless Broadband Routers" are three devices in one. From a logical point of view, they are:

[LIST]
[*] a 6-port LAN switch, of which 4 ports have connectors to plug cables in. 
[*] a WLAN access point connected to one of the internal switch ports
[*] a Router/Firewall with two interfaces: one connected internally to the LAN switch, one with a connector most often labelled "WAN"  (sometimes this is an Ethernet port, sometimes it's an  integrated DSL Modem)
[/LIST]
[SIZE="1"](I know that the actual internal mapping of e.g. a Linksys WRT54G is a bit different, but standard firmware configures the device to behave as outlined above).
[/SIZE]

The problem you are looking at has nothing to do with the router part of the device, but it's only about the WLAN part. So NAT (which is is a function of the router part) most probably won't help there. 

What could help: Use two distinct WLAN APs (with non-overlapping WiFi Channels!) and make sure that the server connects to one while the client connects to the other. Then make sure that the APs are connected to the same LAN (in your case: get a simple WLAN access point device and connect it to the LAN switch integrated in your wireless broadband router). Now traffic from server to client is "transit" for the APs, not "reflected",  --> No bandwith race --> better throughput.

best regards

Marc

---

### Post by Deathmoon on 2007-11-01
My bad...I meant to say **NAS** (network attached storage).  I can plug the NAS device into the router which would reduce the wireless activity (server and client on a wireless connection).

As was stated in the thread that you referred to, this would be just like placing the server on the router wired.  It should improve performance to some degree.

Thanks again for the guidance.

---

