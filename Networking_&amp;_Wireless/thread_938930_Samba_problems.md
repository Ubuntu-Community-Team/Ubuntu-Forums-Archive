---
title: "Samba problems"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by NoWayBill on 2008-10-05
I have 2 archival drives on my desktop (8.04).
I have been sharing them with my laptop, dual XP/8.04
Samba dropped one of them today.
When I try to re enable the /storage share I get the following Samba error....
> 'net usershare' returned error 255: [2008/10/05 12:17:02, 0] lib/util_sock.c:read_socket_with_timeout(497)
  read_socket_with_timeout: timeout read. read error = Connection reset by peer.
[2008/10/05 12:17:02, 0] libsmb/clientgen.c:cli_receive_smb(111)
  Receiving SMB: Server stopped responding
net usershare add: cannot convert name "Everyone" to a SID. NT_STATUS_INVALID_NETWORK_RESPONSE.

At first I was able to read the contents, but couldn't copy a file from it.
After I left the share I was unable to get back in as Samba had dropped the share.
Laptop was in XP at the time.

The other drive, /archive, and a folder in my Windo$e drive are still working fine.
Don't understand what happened.

My process is to "sudo nautilus"
Then enable sharing through GUI.

---

