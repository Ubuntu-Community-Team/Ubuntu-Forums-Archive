---
title: "Samba issues with winbindd... also gigabit issues."
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by lordofduct on 2007-10-23
So I have had MAJOR network issues over the last month... and they got horribly worse this last week. I've spent the entire week fixing everything up...

I literally had to replace my router, switch and reconfigure my samba server... on a ubuntu linux server hosted as a file/print server on my network... it also performs local remote desktopping for me from my bedroom.

the MAIN issue that was occuring with samba was that it 'net groupmap' wasn't associating "Domain Users" to the unixgroup "users" (same with admin's and guests).

I fixed this all, and I've checked the /var/log/daemon.log file and most of the errors have stopped. BUT one of the errors that was occuring rather frequently before (about every 10 seconds) is now still occuring... just less frequently (like every 5-10 minutes only once).

Wondering if anyone has any ideas why...
the error output is:

Oct 23 22:23:00 server1 winbindd[10025]: [2007/10/23 22:23:00, 0] libsmb/clientgen.c:cli_receive_smb(112) 
Oct 23 22:23:00 server1 winbindd[10025]:   Receiving SMB: Server stopped responding 

keep in mind, I'm no longer getting dropped connections to the server anymore, I just still receive this error a little less often and have NO idea what it means.


ALSO:
I have the ASUS P5NSLI motherboard, using nForce4 gigabit ethernet controller for this server. I check /var/log/syslog and it says that my eth0 and eth1 (I have 2 ethernet ports) are being set to 1000Mbit, but on my network it only get's recognized as 100Mbit and is served so (my house is wired appropriately with all gigabit switches and router through out). Is it possibly the driver I'm using (I'm using the generic one that Ubuntu gave it on install... don't know the name)

Oct 23 04:55:46 server1 kernel: [   36.939919] sky2 eth1: Link is up at 1000 Mbps, full duplex, flow control both

This has occured on every build of Ubuntu I've used in the last year (Dapper, Edgy, and the latest Gutsy). I've googled it and found other people with the problem, but alas none of the people ever posted about how to fix it.

I even have a very old thread about it here:
[http://ubuntuforums.org/showthread.php?t=287357](http://ubuntuforums.org/showthread.php?t=287357)

thanks in advance anyone

---

### Post by lordofduct on 2007-11-12
I still don't know what is going on with libsmb/clientgen.c

Still today I have issues with it and it restarts samba every 2 or 3 minutes which doesn't allow me to grab files off my server for a couple seconds every once in a while. (yeah the issue returned)



I don't mean to sound like a prick, but it appears of the three threads I've ever created on here (after doing a ton of searching on the internet) I get zero responses. Where as other's get responses for nonsense... should I be giving you more information or does no one even want to assist at all? If that is so, then well... I'll just bugger off and think twice before I ever offer help again to anyone on any forum.

---

### Post by DeusEx on 2007-11-12
Hi,
try setting the samba log level to a different number to generate some more relevant info
e.g.  
```

log level = 10

```

in the *Global* section

---

### Post by lordofduct on 2007-11-12
in /var/log/samba/log.nmbd I continually get this over and over:
_______________________________________________

[2007/11/12 16:03:35, 4] nmbd/nmbd_workgroupdb.c:find_workgroup_on_subnet(171)
  find_workgroup_on_subnet: workgroup search for WORKGROUP on subnet UNICAST_SUBNET: found.
[2007/11/12 16:03:35, 4] nmbd/nmbd_workgroupdb.c:find_workgroup_on_subnet(171)
  find_workgroup_on_subnet: workgroup search for WORKGROUP on subnet UNICAST_SUBNET: found.
[2007/11/12 16:03:45, 4] nmbd/nmbd_workgroupdb.c:find_workgroup_on_subnet(171)
  find_workgroup_on_subnet: workgroup search for WORKGROUP on subnet 192.168.0.100: found.
[2007/11/12 16:03:45, 10] nmbd/nmbd_sendannounce.c:announce_myself_to_domain_master_browser(382)
  announce_myself_to_domain_master_browser: t (1194901415) - last(1194901310) < 900
[2007/11/12 16:03:45, 4] nmbd/nmbd_workgroupdb.c:dump_workgroups(282)
  dump_workgroups()
   dump workgroup on subnet   192.168.0.100: netmask=  255.255.255.0:
  	WORKGROUP(1) current master browser = SERVER1
  		SERVER1 408c9b0b (server1 server (Samba, Ubuntu))
  		DEVMACH 40011003 ()
  		TRIATAMI 40011003 (andy)
  		EVILGENEVA 40011203 ()
  		BEDROOM 40011003 ()
[2007/11/12 16:03:45, 4] nmbd/nmbd_workgroupdb.c:dump_workgroups(282)
  dump_workgroups()
   dump workgroup on subnet  UNICAST_SUBNET: netmask=  192.168.0.100:
  	WORKGROUP(1) current master browser = UNKNOWN
  		SERVER1 40899b0b (server1 server (Samba, Ubuntu))
____________________________________________________________


and in /var/log/daemon.log I still get the same thing over and over... along with some info about packets and stuff I'm accessing... like this:

__________________________________
Nov 12 16:02:02 server1 smbd[8089]:                           path                     : '/home/share/allusers/_orbital_/Blade3D/C#Solutions/LoDCombineExtensionLibrary/LoDCombineExtensionLibrary' 
Nov 12 16:02:02 server1 smbd[8089]: [2007/11/12 16:02:02, 0] librpc/ndr/ndr.c:ndr_print_debug_helper(203) 
Nov 12 16:02:02 server1 smbd[8089]:                           path_len                 : 0x00000068 (104) 
Nov 12 16:02:02 server1 smbd[8089]: [2007/11/12 16:02:02, 0] librpc/ndr/ndr.c:ndr_print_debug_helper(203) 
Nov 12 16:02:02 server1 smbd[8089]:                           private_data             : 0x8493078 
Nov 12 16:05:15 server1 winbindd[5383]: [2007/11/12 16:05:15, 0] libsmb/clientgen.c:cli_receive_smb(112) 
Nov 12 16:05:15 server1 winbindd[5383]:   Receiving SMB: Server stopped responding 
Nov 12 16:05:28 server1 winbindd[5383]: [2007/11/12 16:05:28, 0] libsmb/clientgen.c:cli_receive_smb(112) 
Nov 12 16:05:28 server1 winbindd[5383]:   Receiving SMB: Server stopped responding 
Nov 12 16:05:40 server1 winbindd[5383]: [2007/11/12 16:05:40, 0] libsmb/clientgen.c:cli_receive_smb(112) 
Nov 12 16:05:40 server1 winbindd[5383]:   Receiving SMB: Server stopped responding

---

