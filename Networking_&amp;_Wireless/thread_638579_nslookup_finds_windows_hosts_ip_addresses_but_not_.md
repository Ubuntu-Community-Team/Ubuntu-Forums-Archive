---
title: "nslookup finds windows hosts ip addresses but not linux ones"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by amitst on 2007-12-12
On my local company LAN, nearly all machines are Windows ones. I know of two Linux machines, one, my laptop with Ubuntu and second a test machine with Fedora7. Both machines are reachable on the net and have their DNS server configured as per the IT department's instructions. However the funny thing is nslookup only returns the IP address binding for Windows host. But it is not returning the IP address for the Linux hosts.

Here is the output,
```
$ nslookup ps4439
;; Got SERVFAIL reply from 10.44.0.100, trying next server
Server:         4.2.2.2
Address:        4.2.2.2#53

** server can't find ps4439: NXDOMAIN

$ nslookup lap432
;; Got SERVFAIL reply from 10.44.0.100, trying next server
Server:         4.2.2.2
Address:        4.2.2.2#53

** server can't find lap432: NXDOMAIN

```

Any other (Windows) names are resolved correctly. I guess the DNS server is also the Windows one (and not in my control). Any pointers regarding why this is happening and how can I overcome this limitation?

Also I am seeing my machine name (and domain) under System->Admin->Network->General tab

Thanks in advance,
Amit

---

### Post by handaxe on 2007-12-12
My guess: Probably a wins server issue.

Install SAMBA, and configure it to point to the local WINS serve i.e. update the /etc/samba/smb.conf "wins server = " entry with your networks  WINS server addresses. NB:  be sure not to enable "wins support = yes" as that will make your box a WINS server and someone will prolly get cross.

Lets see....

HA

---

### Post by amitst on 2007-12-21
I checked the corresponding Windows configuration,
- There are no entries in the WINS setting
- The check box "enable LMHOSTS lookup" is ON
- Another radio button "enable NETBIOS over TCP/IP" is selected

Any suggestions?

---

### Post by handaxe on 2007-12-21
You are correct when you id the dns server as the problem as it has no knowledge of the link between your linux box hostname and the dynamically assigned ip. This is a common problem in mixed *nix and Windows environments and usually devolves down to the use of netbios and /or wins servers by windoze.

One way is to get your Network Admin to serve fixed ips to the linux boxes via the dns and then make the appropriate host entries for the linux boxes on the dns.

Alternatively, try this:

edit /etc/nsswitch.conf  and make the hosts line as such:

hosts: files dns wins


You may have to install winbind via synaptic for this to work. (Edit: I should have read your original posting better - the linux boxes do pick up the windows host names so I am unsure if this will help. cannot hurt though. The samba bit below may be the best bet besides the dns entry route).

Also install samba server on your box and in the config file enable NetBIOS Hostname by entering your linux hostname. Check this out for 2 different network scenarios:

[http://www.terminally-incoherent.com/blog/2007/10/03/access-linux-workstation-by-hostname-on-a-windows-network/](http://www.terminally-incoherent.com/blog/2007/10/03/access-linux-workstation-by-hostname-on-a-windows-network/)

HA

---

### Post by amitst on 2007-12-24
Both of my machines use static IPs. I tried adding the "netbios name" to the smb.conf but that didn't help the Fedora7 machine. However, I did a lot of things (I remember for sure  putting DNS IP in the WINS server param, restarting smb and then again commenting out the entry and restarting smb) and suddenly the DNS started giving proper IP for my Ubuntu laptop name. Though I am not able to replicate the same thing with the Fedora7 machine. Isn't there a way to send the Linux box host name everytime it boots to the DNS server?

---

### Post by handaxe on 2007-12-24
The netbios smb entry was precisely to announce the linux hostname to the network. It seemed (somehow?) to have worked for the Ubuntu box and so it should if samba is configured correctly on the Fedora box.

Beyond that I know not... except that you (apparently) can set up a dns server on the linux boxes to do the job.  Google around is all I can suggest.

BTW, "fixed" IPs can be served in 2 ways.  1) you set a static ip for your interface or 2) the dhcp server delivers the same IP to you based on the MAC everytime your box requests a dynamic address. I guess you mean 1)?

HA

---

### Post by amitst on 2007-12-25
How does the samba server send the netbios name entry to the correct DNS? I could successfully connect to /tmp directory of the Fedora from my Ubuntu desktop by connecting through Windows share facility. So samba is working fine. I also did "/sbin/service iptables stop" to ensure that the firewall isn't coming in the way.

Currently I have put (in /etc/samba/smb.conf),
workgroup = <domain e.g. ubuntu>
netbios name = <this machine name>
realm = <domain name e.g. ubuntu.com>
dns proxy = no

Other than the above there aren't any other params that looked of interest to me.

Also through Fedora's UI I couldn't share a new directory using a specific user name as there wasn't a provision to add a new user name (K Menu->System Settings->Samba->Add Share->Access tab->Select "Only allow access to specific users", but there is no way to add a user name to the list.).

---

### Post by handaxe on 2007-12-26
This has reached the limits of my knowledge - how samba interacts with the local  and remote dhcp/dns processes.

AFAIK, in the absence of a WINS server (aka a Netbios NS) netbios is a broadcast service that announces the presence of a PC name on the network; with a wins server present the pc adds its netbios name to wins database and the wins serves up the IP:netbiosname info to other pcs. With the entries you made in the conf file, does samba pass on the netbios info to the wins server, or does it broadcast it? 

Did you put ```
send host-name "my_hostname"
``` into /etc/dhcp3/dhcp.conf? Might help if the dns is set to update info each time and your machines might be resolved via the hostname? Chances are it is enabled already tho'....

As far as user goes. you realise that the user needs to be an existing user of the *nix system running samba? Also, under Gnome in Ubuntu, the gui method of enabling sharing is not enough in the case of share level access, as I always need to edit samba.conf. Is he same true for KDE / Fedora so that you need to tweak the conf file?

HA

---

### Post by amitst on 2007-12-27
The "send host-name" statement is present in the /etc/dhclient-eth0.conf file. The /etc/dhcp3/dhcp.conf file is not present on the Fedora7.

The Gnome/KDE is not showing any user in the dialog box. I guess the /etc/samba/smbuser file is used for this? The content of this file read as follows
```

root = administrator admin
nobody = guest pcguest smbguest

```
But none of these users or any Unix users are listed in the dialog box.

---

