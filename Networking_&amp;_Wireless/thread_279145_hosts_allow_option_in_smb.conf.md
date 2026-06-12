---
title: "hosts allow option in smb.conf"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2006-10-17
I just figured something out that may be hanging up a lot of users with there samba setups. I have tried using the guide that I found within this forum titled peer to peer samba setup or something or another and it just wouldn't work. Then I figured, what the hell, I am gonna read the entire man page on smb.conf. Ok, I didn't read the entire thing but I did find something out that is conflicting with what the man page states. Here's a quote, "hosts allow (S) 
A synonym for this parameter is allow hosts. 
This parameter is a comma, space, or tab delimited set of hosts which are permitted to access a service. 

If specified in the [global] section then it will apply to all services, regardless of whether the individual service has a different setting. 

You can specify the hosts by name or IP number. For example, you could restrict access to only the hosts on a Class C subnet with something like allow hosts = 150.203.5.
The full syntax of the list is described in the man page hosts_access(5). Note that this man page may not be present on your system, so a brief description will be given here also. 

Note that the localhost address 127.0.0.1 will always be allowed access unless specifically denied by a hosts deny option. 

You can also specify hosts by network/netmask pairs and by netgroup names if your system supports netgroups. The EXCEPT keyword can also be used to limit a wildcard list. The following examples may provide some help: 

Example 1: allow all IPs in 150.203.*.*; except one 
hosts allow = 150.203. EXCEPT 150.203.6.66 

Example 2: allow hosts that match the given network/netmask 
hosts allow = 150.203.15.0/255.255.255.0 

Example 3: allow a couple of hosts
hosts allow = lapland, arvidsjaur 

Example 4: allow only hosts in NIS netgroup "foonet", but deny access from one particular host 
hosts allow = @foonet
hosts deny = pirate 

Note 
Note that access still requires suitable user-level passwords. 
See testparm(1) for a way of testing your host access to see if it does what you expect. 

Default: hosts allow = # none (i.e., all hosts permitted access) 

Example: hosts allow = 150.203.5. myhost.mynet.edu.au "
so after reading all this you would think that I line line:
hosts allow = 192.168. EXCEPT 192.168.0.20
would work right? WRONG, this is what I get when I type smbtree and enter my password,         \\UBUNTU                        Dans Linux Desktop
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
failed tcon_X with NT_STATUS_INVALID_NETWORK_RESPONSE. 
but when I make the hosts allow line like this:
hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20
then I get the desired results of all the shares on my ubuntu box. This just goes to show, the man pages aren't always correct. Who know, the man pages were probably written prior to Samba 3.0.22 also. Just wanted to point this out for everyone.
Security = user is the default security setting in Samba 3.0 so you really don't need to have it there. I have read that it is recommended that you use smbpasswd, though larger networks may require tbdsam so I wonder why this guy is suggesting to use tbdsam as the password backend? ANd 1 last important thing that some people may forget, 
Firewall Configuration
The following should apply to most (if not all) Linux distributions, and is an easily forgotten part of Samba configuration. If your samba shares do not show up in windows network environment the firewall configuration is one of the probable causes.
The following ports will need to be allowed through your firewall to enable Windows to connect to the Linux Samba server. It follows a format of Port Number:Protocol. 
  445:tcp
  139:tcp
  138:udp
  137:udp

---

