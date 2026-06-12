---
title: "LAN can't show computers but shows the router"
date: 2018-04-25
forum: Networking &amp; Wireless
---

### Post by gleble on 2018-04-25
I am trying to access other machines on our home network. Samba is installed on  all laptops and sharing is enabled on the Shared folders. When opening Windows Network I get to Home but on opening that I only find my router. No sign of the other machines or the printer. It all worked fine before upgrade to 16.04. What could be wrong?

---

### Post by sdowney717 on 2018-04-26
> **gleble said:**
> I am trying to access other machines on our home network. Samba is installed on  all laptops and sharing is enabled on the Shared folders. When opening Windows Network I get to Home but on opening that I only find my router. No sign of the other machines or the printer. It all worked fine before upgrade to 16.04. What could be wrong?

It will work if you switch or try out linux Mint.
Same problem here, no network discovery. For me its been like that a long time, problem is still in version 18.
In Mint it will show the other lan connected devices.

In Ubuntu, if you know the IP address,  you*** MIGHT*** be able to use the 'connect to server' option.

---

### Post by gleble on 2018-04-26
Thanks for your suggestion. I am using Ubuntu, 16.04. I cannot see what knowing the ip address of other computers on the network has to do with 'connect to server'. I can communicate with other machines e.g.
root@neil-ThinkPad-T430:/home/neil# nmap -v -sn 192.168.1.101

```
Starting Nmap 7.01 ( https://nmap.org ) at 2018-04-26 14:03 BST
Initiating ARP Ping Scan at 14:03
Scanning 192.168.1.101 [1 port]
Completed ARP Ping Scan at 14:03, 0.23s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:03
Completed Parallel DNS resolution of 1 host. at 14:03, 0.00s elapsed
Nmap scan report for neil-Lenovo-ideapad-110S-11IBR (192.168.1.101)
Host is up (0.0030s latency).
MAC Address: 60:14:B3:7E:31:2D (Unknown)
Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.31 seconds
           Raw packets sent: 1 (28B) | Rcvd: 1 (28B)

```

But I cannot see them in the Network to access them.

[IMG]http://frackfreecleveland.co.uk/img/shares.png[/IMG]

Why not?

---

### Post by gleble on 2018-04-26
I've worked it out. I made changes to /etc/samba/smb.conf as follows: 
in [global]  at the top
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME
```
in Share Definitions near the bottom add
```
[share$]
   comment = Shares
   path = /home/neil/Shared
   browseable = yes
   read only = no
   guest ok = yes
```
My Shared folder is now available on the network. I can see this work is supposed to be done when /var/lib/samba/usershares/Shared was created. 
If anyone can explain why I have had to do this I would be interested.

---

### Post by Morbius1 on 2018-04-26
You did more than change your workgroup name.

** From your output the two hosts mentioned are **neil-ThinkPad-T430** and [B]neil-Lenovo-ideapad-110S-11IBR

[/B]If  you are going to use the netbios mechanism to discover hosts ( and that is what you do when you go to Network > Windows Network ) those names are too long. It can only be 15 characters long or less so it's unresolvable. You must have added a: netbios name = xxxx somewhere in smb.conf.

** As for the userhsare comment I have no idea. Run the following command to see if the share definition was created:
```
net usershare info --long
```

** You might want to refrain from ending your share name with a "$" sign. To a Windows box that is a hidden share.

** If this is an all Linux or Linux / macOS network let me get you ready for living with Ubuntu 18.04.

[1] Create a new file at [B]/etc/avahi/services/samba.service 

[/B][2] Add this to the empty file:
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
Just in case restart avahi:
```
sudo service avahi-daemon restart
```

If you add that file to both your machines they will show up as **neil-ThinkPad-T430 SMB **and** neil-Lenovo-ideapad-110S-11IBR SMB **It's using host names and they will show up under Network not under Windows Network because you are no longer using the Windows method of host discovery and the 15 character limit no longer applies.[COLOR=#0000cd][I]
Note: When you do your next install you might want to shorten your host names a bit.[/I][/COLOR][B] ;)

Adding the samba.service file is unnecessary in Ubuntu 17.10 and 18.04. Ubuntu finally enabled Multicast in samba on those two releases so the whole avahi thing is automatic the instant you install samba.
[/B]

---

