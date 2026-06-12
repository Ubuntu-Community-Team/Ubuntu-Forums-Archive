---
title: "Why Two Icons for same computer in Files Browse Network"
date: 2018-06-09
forum: Networking &amp; Wireless
---

### Post by Axis Mann on 2018-06-09
When looking at the LAN using browse network in the Files (aka nautilus) sidebar on old computer running ubuntu 16.04, I get two separate icons for my new Ubuntu 18.04 computer.  For one icon, the properties indicate smb://hostname.local/ and the properties for the other indicate smb://hostname/.  The one for hostname.local goes away if I turn off the avahi-daemon on the 18.04 machine.  But, I want to run both avahi-daemon and use samba to share files from my 18.04 public directory for both my linux computer and windows 10 computer.  Looking for samba solution to eliminate the superfluous icon.

---

### Post by Morbius1 on 2018-06-10
> But, I want to run both avahi-daemon and use samba to share files from  my 18.04 public directory for both my linux computer and windows 10  computer.  Looking for samba solution to eliminate the superfluous icon. 
They are both samba but two different methods of host name resolution. The reason you get two icons is because the 18.04 machine is "broadcasting" it's samba server two different ways: the old netbios way ( smb://hostname ) and the avahi / mDNS way ( smb://hostname.local ).

You can turn off either mechanism in smb.conf in 18.04 by adding one of these under the workgroup = WORKGROUP line:

**multicast dns register = no **<-- This will disable the avahi mechanism.[B]
disable netbios = yes       [/B]<-- This will disable the netbios mechanism.

You would have to restart the smbd and nmbd services after each change: ```
sudo service smbd restart 
```
```
sudo service nmbd restart
```
 But that will limit how each client machine can "discover" your server.

Some possibilities:

[1] Probably the easiest thing to do if you are sure that the other machines / devices on your network only run Linux, macOS, or Win10 is to disable netbios on your server with **disable netbios = yes **in its smb.conf. Win10 will not be able to "discover" your 18.04 host but it will be able to connect to using avahi by running this in explorer:
```
\\hostname.local
```
Since this is a server with a public share you can even map it in WIn10 using that same method: [B]\\hostname.local\public
[/B]
The only other solution I can think of will still result in duplicates but with different names:

[2] disable the avahi mechanism in smb.conf but recreate it with something that allows you to change how the server is seen:

** Disable avahi in smb.conf ( **multicast dns register = no** )

** Restart smbd: **sudo service smbd restart**

** Then recreate it by adding a file /etc/avahi/services/samba.service with this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```

You will see two icons on your Linux / macOS clients. One will be "hostname" but the other ( avahi  way ) will be "hostname SMB"

If you don't include the avahi samba.server file you can still access the server from Linux / macOS since avahi-daemon is still runnng. You will just have to access it explicitly smb://hostname.local and you can even map ( Bookmark ) it in Linux: smb://hostname.local/public

---

