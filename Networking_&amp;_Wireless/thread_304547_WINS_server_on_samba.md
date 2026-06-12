---
title: "WINS server on samba"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by livestockPimp on 2006-11-21
hi, i have tried to set up a wins server and i cannot seem to get it to work, all the computers connect via dhcp, the ipconfig on thier machines points to my server as the wins server, i cant find any error messages in the logs...
i have set up the smb.conf with the lines:
workgroup = nsh
wins support = yes
wins proxy = yes
name resolve order = wins lmhosts bcast host
they are probably the specific ones for the wins setup.
i looked at the /var/lib/samba/wins.dat
and it is only recognising the local server in there...
also, all the client machines can connect to the samba shares EXCEPT the windows 98 machines, all the xp ones are fine... any ideas?
thanks in advance....

---

### Post by dmizer on 2006-11-22
you cannot use a wins server in a dhcp network.

---

### Post by livestockPimp on 2006-11-22
yes you can, i have seen it configured before but this is the first time i have tried doing it, there are websites too that say you canb also..

[http://www.clarkconnect.com/wiki/index.php?title=Howtos_-_Samba_and_WINS](http://www.clarkconnect.com/wiki/index.php?title=Howtos_-_Samba_and_WINS)

---

### Post by speedman on 2006-11-22
You can absolutely provide wins name resolution services with dhcp.  Normal DNS via bind is preferable, but if you want to use wins follow my brief instructions below.

=====

sudo apt-get install winbind

=====

sudo vi /etc/nsswitch.conf

hosts:          files dns ldap wins

=====

sudo vi /etc/samba/smb.conf

wins server = 192.168.0.1 #(replace with your server IP)
wins support = yes

=====

sudo vi /etc/dhcp3/dhcpd.conf

option netbios-name-servers 192.168.0.1; #(replace with your server IP)

=====

sudo /etc/init.d/samba restart && sudo /etc/init.d/dhcp3-server restart

=====

Hope that helps.


Regards,

SM

---

### Post by livestockPimp on 2006-11-22
cheers, i will give that a shot tomorrow and post back

---

### Post by livestockPimp on 2006-11-22
i thought that if you had 
wins support = yes 
and
wins server = 192.168.1.1
then when you try and do a testparm on it it flagged as a conflict...
i will still give it a shot though...

---

### Post by dmizer on 2006-11-22
sorry ... let me rephrase.

you cannot have a wins server on a dhcp network unless the dhcp server and wins server are in different subnets.

---

### Post by speedman on 2006-11-22
> **dmizer said:**
> sorry ... let me rephrase.

you cannot have a wins server on a dhcp network unless the dhcp server and wins server are in different subnets.

Pardon?  You can run them on the same box bound to the same network device.  We have dozens of production boxes doing so.


REgards,

SM

---

### Post by dmizer on 2006-11-22
> **speedman said:**
> Pardon?  You can run them on the same box bound to the same network device.  We have dozens of production boxes doing so.

really?  everything i've found indicates that's not possible.  when i tried it, i always got ip conflicts.

---

### Post by speedman on 2006-11-22
> **dmizer said:**
> really?  everything i've found indicates that's not possible.  when i tried it, i always got ip conflicts.

winbind typically just caches netbios names that are being broadcast on the network.  The winbind daemon doesn't assign hostnames, or IP addresses.  dhcp3-server on the other hand not only delegates IPs it can also be used to set the wins server for clients to query using the netbios-name-servers option that I referenced above.

All of that being said wins stinks.  It isn't reliable and it's no wonder MS deprecated it with the release of Win2k.  It is much better to use a DNS server in conjunction with DHCP that allows clients to be registered in DNS when receiving a DHCP assigned IP.


Regards,

SM

---

### Post by livestockPimp on 2006-11-23
hi, i still am having problems, i will paste out my smb.conf files...
[global]

   log level = 3
   workgroup = NSH
   netbios name = NS
   netbios aliases = NS-B
   interfaces = lo 127.0.0.1/24 eth0 192.168.10.1/24
   hosts allow = 127. 192.168.
   bind interfaces only = yes
   server string = Server
   load printers = yes
   enable privileges = yes
   printing = cups
   printcap name = cups
;   printcap name = /etc/printcap
;   printing = lprng
;   print command = /usr/bin/lpr -P%p -Z%m %s
   guest account = nobody
;   invalid users = root
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = share
   encrypt passwords = true
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   local master = yes
   os level = 99
   hide dot files = yes
;   veto files = /.*/
   hide files = /.DS_Store/desktop.ini/DESKTOP.INI/Thumbs.db/*.tmp/
   domain master = no
;   domain logons = yes
   logon drive = H:
   logon home = \\%N\%U
   logon path = \\%N\profiles\%U
   logon script = logon.bat
;   logon script = %G.bat
   preferred master = yes
   time server = yes
   wins support = yes
;   wins server = 192.168.10.1
;   remote announce = 192.168.10.1 192.168.12.1
;   remote browse sync = 192.168.10.1 192.168.12.1
;   wins proxy = yes
   dns proxy = no
   name resolve order = wins lmhosts bcast host
;   preserve case = yes


that is my global section and here is my dhcpd.conf...


ddns-update-style none;

option domain-name "ns.server.com";
option domain-name-servers 192.168.10.1;
option netbios-name-servers 192.168.10.1;
option netbios-node-type 8;
default-lease-time 60000;
max-lease-time 720000;
authoritative;

log-facility local7;

subnet 192.168.10.0 netmask 255.255.255.0 {
 range 192.168.10.20 192.168.10.200;
 option routers 192.168.10.1;
}

host ns-hostmachine {
 hardware ethernet 00:03:47:2E:A9:20;
 fixed-address 192.168.10.205;
}

host jim {
 hardware ethernet 00:17:31:BE:51:67;
 fixed-address 192.168.10.206;
}



any ideas?

---

