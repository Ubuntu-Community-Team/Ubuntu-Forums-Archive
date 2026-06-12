---
title: "Wireless access to NAS is slow and unreliable"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by AndyC_772 on 2007-01-27
My laptop has a Broadcom (BCM4306) based 802.11g wireless card. I did a clean install of Edgy last week, including nsidwrapper, and my wireless access to the Internet seems fine.

However, I also have a NAS drive on my local network, mounted over NFS. If I plug in an Ethernet cable and access it that way, it's very fast and reliable. However, if I use the wireless network instead, throughput is poor and keeps freezing for no apparent reason. (I've tried accessing it over Samba too, same problem).

Given time, transfers always seem to complete eventually, but in the meantime the wireless activity LED can go out for seconds at a time. System Monitor shows little CPU activity - it's as though the machine is just sitting there waiting for something to happen. I have a good signal - booting into Windows and checking the network status shows a connection speed of 48 or 54Mbit/s. Accessing the NAS in Windows seems fine too, even over the wireless network.

I can, however, download large files from the Internet over wireless with no problem, the intermittent freezing just doesn't happen.

Any ideas please?

Andy.

---

### Post by AndyC_772 on 2007-01-28
Nobody? Good job I found the answer eventually myself, then.

As per the advice on numerous web pages about NFS setup, I had my /etc/fstab specifying rsize=8192 and wsize=8192, which is fine for a wired network. However, with the slow wireless network in the way, it just doesn't work. The fix is to set rsize=1024 on the laptop, which causes the laptop to read data in chunks that are just one Ethernet packet in size, avoiding the overrun problem described [here](http://ftp.utcluj.ro/pub/docs/diverse/freeBSD/FreeBSD-handbook/handbook178.html).

Hopefully this will at least help anyone else doing a search for the same problem :)

---

### Post by tyres on 2007-02-20
Hi Andy,

I've hit the same problem. seems to be ok if just small files are being transferred, but bigger ones result in a total lock-up (apparently) on the server side, and the client-side process hangs, although you can still do other stuff on the client.

It's reassuring in  a way that it's not just me, or my system, but a wider issue. If I find a solution i'll let you know. Do you manage to run your wired and wireless systems together?My attempts to do that have been unsuccessful, it seems to have to be one or the other. I'd like the NFS server to be accessible via the wireless network, but I guess a second-best would be to have it only accessible to the other computer it's wired to, if I can do that via ethernet and yet still run the wireless access on the client as well.

Cheers,

Colin

---

### Post by AndyC_772 on 2007-02-26
Hi,

I don't have any problem accessing the NAS drive from multiple computers. In case it helps, my setup is pretty straightforward: I have an ADSL modem/router which includes a 4 port Ethernet switch, and the NAS drive, desktop PC and wireless base station are connected directly to it. On the wireless network I have a laptop, a PDA and a Squeezebox.

The fourth port on the router is usually spare, but I sometimes plug the laptop into it to troubleshoot wireless problems or get a better connection speed.

Andy.

---

### Post by hairy on 2007-03-27
I have found a (possible) solution to some people's wireless samba/nfs problem.

I have no idea why this affects ubuntu (i've not had a problem with windows or slackware) but with ubuntu if you do not specify a low receive buffer size, then you get slow transfers! 

Something that worked for me.......

sudo mount -t smbfs //server/video /mnt/video -o rsize=1024

This enables each chunk to be placed into a ethernet frame without fragmenting it. I've seen some other stuff relating to mac's that suggests turning off delayed acks (couldn't find a similar option in ubuntu) I wonder whether ubuntu is collecting fragments before sending acks, which leads to samba throttling the connection. 

if anybody who knows better than me can dis/prove that i'd be grateful =)

---

### Post by jcr1 on 2008-04-06
Hi,

How did you edit the fstab to get this to work please? I have the same issue.

Many thanks

Jon

---

### Post by AndyC_772 on 2008-04-06
Just open a terminal and type:

sudo gedit /etc/fstab

...then scroll down to the lines that specify the NFS shares and add '-o rsize=1024', as per hairy's post above.

---

### Post by jcr1 on 2008-04-07
Thats what I thought...but when I opened the file, I could see no lines to do with NFS shares. Is it something I need to add perhaps?

I will tell you whats in there once I get home and have a look.

(must find out how to login to my machine at home, via browser from windows machine in work)

Cheers

Jon

---

### Post by netztier on 2008-04-07
> **hairy said:**
> 
```
sudo mount -t smbfs //server/video /mnt/video -o rsize=1024
```

This enables each chunk to be placed into a ethernet frame without fragmenting it. 

The basic idea is correct. Wireless networks are particularely prone to packet loss. 

A 8192 byte sized NFS request needs at least 6 ethernet frames to be transported in (provided we are using the common ethernet frame with 1500bytes of payload).  Losing just one of them kills the entire NFS request which has to be repeated. If you can make sure that each request only needs one ethernet frame to be transported, you can get a lot better performance in a highly lossy network.

However, the **-o rsize <bytes>** and **-o wsize <bytes>** options only apply to NFS, not to SMB. Check man smb.conf (section about "socket options") to see options available for SMB.

regards

Marc

---

### Post by him610 on 2008-04-07
FWIW, I built my own NAS using a ten-year old Dell, three spare hard drives, and freenas which can be downloaded from [http://www.freenas.org/](http://www.freenas.org/) also comes with an excellent guide that can be downloaded.
The accessibility is basically a non-issue if freenas is properly configured; all you need to do is set up freenas to be a Samba server as well as a NFS server. I found that the freenas seems to be easier to access using Samba than NFS; don't know why; it just seems easier. Your installation of Ubuntu comes with a Samba client. You may have to tinker with the settings a little bit to be able to access it. I am able to access my own freenas from any one of three XP systems or three Ubuntu systems from anywhere on my home network, either wireless or wired.

---

### Post by jcr1 on 2008-04-09
Hi,

Not sure how I need to change fstab to get rid of this problem?

When i look at my fstab all i have in it is this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=29e54a86-71d2-4332-8a94-464638734489 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1b435b00-84f5-41d2-bb08-5a40f9d24abb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by jcr1 on 2008-04-10
Any ideas guys, as I really can't start using my nas properly until this is sorted.

Cheers,

Jon

---

