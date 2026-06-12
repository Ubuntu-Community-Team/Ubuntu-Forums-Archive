---
title: "Ubuntu 12.04 LTS Internet could not connect internet"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by Berkan_ on 2015-07-20
Hello everyone,

I'm new user for Ubuntu LTS also whole Unix platform,

My issue is, I did setup process with using Ubuntu 12.04 alternate iso i386 then I configured my network properties with using GUI, 

I'm trying to prepare a VNC server or something like that which will be used for educational purposes at office. What I want is there will be Terminal Server for Ubuntu and other windows users will use it remotely from their PC's that is why I try to setup Ubuntu LTS

I set my Subnet, NetMask, IP and Gateway I'm pinging successfully the other Pc's in my network( also pinging 8.8.8.8 DNS succesfully) but I cannot reach the internet via using Mozilla or I cannot do system updates which I see them ( 28 Updates 283 Mb etc.) 

I hope I translated my issue well any given information about my purpose or my  issue will be used gladly.

Thank you for your patience

---

### Post by SeijiSensei on 2015-07-20
If you can ping the Google DNS server at 8.8.8.8, you have full connectivity to the Internet.

Perhaps you don't have the DNS resolver configured correctly on the machine?  Does your office have an internal DNS server?  Is that the one you've told the machine to use?  If not, try setting it to use 8.8.8.8 and see if that helps.

---

### Post by Berkan_ on 2015-07-21
We donot have DNS server server in the office. As I undrestand I will check resolve.conf.

---

### Post by lzeimet on 2015-07-22
If youve set a static ip i recommend this as a way of adding a nameserver/ configuring your static ip

auto eth0
iface eth0 inet static

address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
dns-nameservers 8.8.8.8

also you just want to have a way to host files that other windows users can have access to? 
I recommend samba.

**Install Samba**

[LIST]	
[*]	*sudo apt-get install samba*

[*]Edit	the **smb.conf	**file

[LIST]		
[*]		*sudo nano /etc/samba/smb.conf*
[/LIST]
	
[*]	Add a share folder somewhere on the bottom

[LIST]		
[*]*[Share*]

[*]		*Path = Type/directory/path/here*

[*]		*Valid users = root*

[*]		*Guest ok = no *		

[*]*Writable		=		yes*

[*]		*Browsable = yes*
[/LIST]
	
[*]	Add/assign root a password

[LIST]		
[*]		*sudo smbpasswd -a root*
[/LIST]
[/LIST]

---

