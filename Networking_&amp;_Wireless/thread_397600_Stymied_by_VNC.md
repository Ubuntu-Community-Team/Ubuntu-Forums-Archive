---
title: "Stymied by VNC"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by ZaphodNE on 2007-03-30
Any assistance will be MASSIVELY appreciated!!

-  Running up-to-date Edgy
-  Using VINO as VNC server on Edgy box
-  Using RealVNC VNC viewer version 4 on WIN XP Home box
-  Router is Netgear (wired) with Port 5903 forwarded to Edgy box
-  NO firewall on Edgy box

I can connect from WIN to Edgy, but only within the LAN.  Cannot connect to Edgy box when coming through WAN (ISP).  I have another box with another distro of Linux where coming in through the WAN is no big deal.  The error that gets thrown is "10061    Unable to connect to host"  (very informative).  I'm using the IP that my ISP has assigned to me followed by ":3" to try to get into the Edgy box.  IP followed by ":5903" does not work either.

I thought I knew how to make this work.......I clearly do not.  If someone has any ideas I would greatly, greatly appreciate your help!

---

### Post by dbott67 on 2007-03-30
Vino listens on 5900 by default.  Are you forwarding 5903 on the router to 5900 on your Ubuntu box?

Can you please post the output of:
```
dbott@thedrake:~$ **netstat -l**
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
[COLOR=Red]tcp        0      0 *:5900                  *:*                     LISTEN
tcp        0      0 *:5901                  *:*                     LISTEN[/COLOR]
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 *:5400                  *:*                     LISTEN
tcp        0      0 localhost:51801         *:*                     LISTEN
tcp        0      0 localhost:47290         *:*                     LISTEN
tcp        0      0 *:5500                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
udp        0      0 192.168.1.10:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 192.168.1.1:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
udp        0      0 *:xdmcp                 *:*
udp        0      0 *:bootpc                *:*

```

-Dave

---

### Post by ZaphodNE on 2007-03-30
As requested.  I didn't know that about VINO, although (I'm probably mistaken on this) I thought I had success using 5901 on Vino.....bad memory I'm sure.  Thank you very much fjor taking interest here.....very much appreciated!!

 netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 localhost:59171         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
udp        0      0 192.168.1.6:netbios-ns  *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.6:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:bootpc                *:*                                
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     8700     /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     8757     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10911    /tmp/ssh-FvQmTg4522/agent.4522
unix  2      [ ACC ]     STREAM     LISTENING     10935    /tmp/orbit-dmccoll/linc-11d3-0-4de9d1f3bf948
unix  2      [ ACC ]     STREAM     LISTENING     8972     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10945    /tmp/orbit-dmccoll/linc-11aa-0-3efb7a3dd0f9a
unix  2      [ ACC ]     STREAM     LISTENING     11195    /tmp/.ICE-unix/4522
unix  2      [ ACC ]     STREAM     LISTENING     11204    /tmp/keyring-0bBKPA/socket
unix  2      [ ACC ]     STREAM     LISTENING     11227    /tmp/orbit-dmccoll/linc-11d9-0-eaa66c27986
unix  2      [ ACC ]     STREAM     LISTENING     11254    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     12017    /tmp/orbit-dmccoll/linc-126b-0-1eb0852014223
unix  2      [ ACC ]     STREAM     LISTENING     11303    /tmp/orbit-dmccoll/linc-11ef-0-3377ca146650f
unix  2      [ ACC ]     STREAM     LISTENING     11334    /tmp/orbit-dmccoll/linc-11f4-0-626fc745f0c84
unix  2      [ ACC ]     STREAM     LISTENING     11367    /tmp/orbit-dmccoll/linc-11f8-0-547ee8c51a6ff
unix  2      [ ACC ]     STREAM     LISTENING     11374    /tmp/orbit-dmccoll/linc-11f6-0-547ee8c51bc2a
unix  2      [ ACC ]     STREAM     LISTENING     11405    /tmp/orbit-dmccoll/linc-1200-0-6765d4503db77
unix  2      [ ACC ]     STREAM     LISTENING     11460    /tmp/orbit-dmccoll/linc-1208-0-547ee8c494c23
unix  2      [ ACC ]     STREAM     LISTENING     11462    /tmp/orbit-dmccoll/linc-120c-0-604e440950fa
unix  2      [ ACC ]     STREAM     LISTENING     11625    /tmp/orbit-dmccoll/linc-1212-0-6bf779f54291e
unix  2      [ ACC ]     STREAM     LISTENING     11653    /tmp/orbit-dmccoll/linc-120a-0-6bf779f597813
unix  2      [ ACC ]     STREAM     LISTENING     11700    /tmp/orbit-dmccoll/linc-1225-0-5d9c946d64fdf
unix  2      [ ACC ]     STREAM     LISTENING     11721    /tmp/orbit-dmccoll/linc-1228-0-5d9c946d72d5b
unix  2      [ ACC ]     STREAM     LISTENING     11751    /tmp/mapping-dmccoll
unix  2      [ ACC ]     STREAM     LISTENING     11774    /tmp/orbit-dmccoll/linc-1239-0-4c09139761429
unix  2      [ ACC ]     STREAM     LISTENING     11827    /tmp/orbit-dmccoll/linc-124c-0-71e7e92552e54
unix  2      [ ACC ]     STREAM     LISTENING     11857    /home/dmccoll/.beagle/socket
unix  2      [ ACC ]     STREAM     LISTENING     11850    /tmp/orbit-dmccoll/linc-124e-0-71e7e925a9321
unix  2      [ ACC ]     STREAM     LISTENING     11956    /tmp/orbit-dmccoll/linc-1262-0-703eac06c704
unix  2      [ ACC ]     STREAM     LISTENING     12174    /tmp/orbit-dmccoll/linc-120f-0-10583d715ada3
unix  2      [ ACC ]     STREAM     LISTENING     21031    /tmp/orbit-dmccoll/linc-13d0-0-2d10afe7df78e
unix  2      [ ACC ]     STREAM     LISTENING     140691   /tmp/orbit-dmccoll/linc-2774-0-67fd80dca6dd4
unix  2      [ ACC ]     STREAM     LISTENING     21472    /tmp/orbit-dmccoll/linc-1426-0-189d56959d133
unix  2      [ ACC ]     STREAM     LISTENING     21478    /tmp/orbit-dmccoll/linc-1424-0-7dccc25a9d71d
unix  2      [ ACC ]     STREAM     LISTENING     21519    /tmp/orbit-dmccoll/linc-142d-0-5dd954c6a79a1
unix  2      [ ACC ]     STREAM     LISTENING     21643    /tmp/orbit-dmccoll/linc-1460-0-4ea728b962fde
unix  2      [ ACC ]     STREAM     LISTENING     22518    /tmp/orbit-dmccoll/linc-1617-0-61b6e5c325a6d
unix  2      [ ACC ]     STREAM     LISTENING     8991     @/tmp/hald-runner/dbus-lqj4HapEE3
unix  2      [ ACC ]     STREAM     LISTENING     8862     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10916    @/tmp/dbus-YIThpciXqo
unix  2      [ ACC ]     STREAM     LISTENING     10669    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     8990     @/tmp/hald-local/dbus-uMXvLTbn8s
unix  2      [ ACC ]     STREAM     LISTENING     4372     @/com/ubuntu/upstart/logd
unix  2      [ ACC ]     STREAM     LISTENING     8444     /var/run/acpid.socket

---

### Post by ZaphodNE on 2007-03-30
Just dawned on me that I have torn everything down, so the the netstat I posted is probably worthless.  But I think I get where you are coming from, so I'll try to proceed on my own.  Else "I'll Be Back".  Again, thanks for you interest!!

---

### Post by ZaphodNE on 2007-03-30
Not to be a pain, but is it possible to get Vino to accept on some other 59xx port.....not just 5900????

---

### Post by dbott67 on 2007-03-30
Strange... I don't see anything listening on 5900.

Can you verify that vino is running?
```
dbott@thedrake:~$ **ps aux | grep vino**
dbott     3163  0.1  0.7  17260  6708 ?        S    21:38   0:02 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=42
dbott     4054  0.0  0.0   2876   800 pts/1    S+   22:02   0:00 grep vino

```

-Dave

---

### Post by dbott67 on 2007-03-30
> **ZaphodNE said:**
> Not to be a pain, but is it possible to get Vino to accept on some other 59xx port.....not just 5900????

I've looked into this before but I do not think Vino supports any port other than 5900.  You could install VNC4server or better yet, try installing NX from [www.nomachine.com](www.nomachine.com).

It's free, it's far faster than VNC, it's secure (it runs over SSH on port 22).  

If you need a hand with NX, just let me know.  I used to use VNC religiously, but I've converted to NX and think it's far superior for remote access.

-Dave

---

### Post by ZaphodNE on 2007-03-30
I trashed vino in a effort to start over......the netstat I posted was worthless.  Can vino accept on ports other than 5900??  If so, how?

---

### Post by Mr. C. on 2007-03-30
Use:

netstat -ln -A inet

instead; you don't care about the unix socket listings, and numeric port output is easier for debugging.

There is nothing listening on your VNC port (590[0-9]).

Before you change ports, get your connection working.

After that, see gconf-editor, key /desktop/gnome/remote_access/alternative_port and use_alternative_port.

MrC

---

### Post by ZaphodNE on 2007-03-30
Reinstalled vino on Edgy box.  Forwarded 5900 to Edgy.  All is well.  I thought I understood VNC but was completely wrong.  Many, many thanks for your time....truely.  I hope I have the chance to help you some day, but something tells me that won't ever happen :-)

Again, thank you for educating me a little tonight

Dave McCollum

---

### Post by dbott67 on 2007-03-31
> **Mr. C. said:**
> After that, see gconf-editor, key /desktop/gnome/remote_access/alternative_port and use_alternative_port.

MrC

Hi Mr.C.

I don't seem to have the key present on my Dapper machine.  Can I just create a new key type (string), call it 'alternative_port' and then plunk in a new port #?  I've attached a screen shot after creating the key for reference.

If so, are there any other values/settings that I need to be aware of (i.e. **set as default** or **set as mandatory**).

Also, is this a default key in newer versions of Ubuntu (Edgy/Feisty)?

Just wondering....

Thanks,
Dave

---

### Post by Mr. C. on 2007-03-31
I'm sorry, I should have been more clear.  I currently have Feisty running, and do not know where the settings are configured for Dapper, nor if adding the key is sufficient.  I would suspect not.

The default in Feisty is to *not* use the alternate port (so vino will default to the built-in 5900), and the alternate port setting contains port 5900.

I ran a "locate" command to find all things "vino", and started the discovery from there.  I knew there was a port specifier somewhere.

I don't believe I have a dapper disk around; if I do, and you have not already found the locate of the port specification, I'll post when I find it.

MrC

---

