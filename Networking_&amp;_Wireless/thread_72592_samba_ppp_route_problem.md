---
title: "samba ppp route problem"
date: 2005-10-06
forum: Networking &amp; Wireless
---

### Post by desleep on 2005-10-06
Im new to kubuntu, I had a some trouble setting up the modem but eventually got it to work but... I need to delete the default route everytime I boot to allow traffic over ppp0. I can live that as I hope to get dsl soon but samba seems to rely on the default route being eth0 and fails to see the local network when i have deleted eth0 as the default. I can still ping the other hosts. 
How do I set this up, I had mandriva 10.2 and it didnt have this issue, I even used my old mandriva smb.conf but it didnt solve it either.
 thanks in advance for any clues on how to fix this!

Paul.

---

### Post by mlomker on 2005-10-07
> thanks in advance for any clues on how to fix this!


That's odd because DHCP (dhclient) should reset your default route once you login by PPP.  Are you using a static IP address for your modem connection?

---

### Post by desleep on 2005-10-07
I have dynamic ppp address from my isp. I had the same route problems on mandriva. It seems that if eth0 is running first it becomes the default route.. I have done hours of googling with no success which seems to suggest I am overlooking something very basic.

 thanks Paul

---

### Post by desleep on 2005-10-07
my samba setup

Processing section "[printers]"
Processing section "[print$]"
Processing section "[pdf-gen]"
Processing section "[SHARE]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = HOMENET
        server string = Varuna
        security = SHARE
        map to guest = Bad User
        log file = /var/log/samba/log.%m
        max log size = 50
        server signing = auto
        socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
        printcap cache time = 60
        printcap name = cups
        preferred master = No
        domain master = No
        dns proxy = No
        ldap ssl = no
        remote announce = 192.168.0., 127.
        printer admin = @adm
        hosts allow = 192.168.0., 127.
        printing = cups
        print command =
        lpq command =
        lprm command =

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        guest ok = Yes
        printable = Yes
        print command = lpr-cups -P %p -o raw %s -r   # using client side printer drivers.
        use client driver = Yes
        browseable = No

[print$]
        path = /var/lib/samba/printers
        write list = @adm, root
        inherit permissions = Yes
        guest ok = Yes

[pdf-gen]
        comment = PDF Generator (only valid users)
        path = /var/tmp
        printable = Yes
        printing = bsd
        print command = /usr/share/samba/scripts/print-pdf "%s" "%H" "//%L/%u" "%m" "%I" "%J" &
        lpq command = /bin/true
        lprm command = lprm -P'%p' %j

[SHARE]
        comment = home
        path = /home/paul
        valid users = paul
        wide links = No

ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:7B:F2:DB
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe7b:f2db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metr

ppp0      Link encap:Point-to-Point Protocol
          inet addr:219.88.128.233  P-t-P:192.168.251.42  Mask:255.255.255.255

route;

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.251.42  *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.251.42  0.0.0.0         UG    0      0        0 ppp0


thanks!

---

### Post by w9wi on 2007-02-25
> **desleep said:**
> Im new to kubuntu, I had a some trouble setting up the modem but eventually got it to work but... I need to delete the default route everytime I boot to allow traffic over ppp0.

18 months later(grin) but I seem to have run into more or less the same problem.  

My modem installed just fine, everything was working nicely.  Then I installed the samba server.  (I already had the client working properly)  I could no longer reach the Internet.  /var/log/messages said ppp connected successfully and received an IP address & DNS info.  However, I couldn't reach the DNS servers, and [FONT="Courier New"]route -n[/FONT] showed eth0 was the default route.   So did the Networking GUI configuration tool - and it didn't allow me to change it.  [FONT="Courier New"]setdefaultroute[/FONT] is already in my ppp configuration.  

I ended up creating a script I called [FONT="Courier New"]setroute[/FONT] and putting it in [FONT="Courier New"]/etc/ppp/ip-up.d[/FONT].  It seems to work.  

Quite frustrating.  Wish I knew what happened - did samba really do this? - and if so, where?

---

