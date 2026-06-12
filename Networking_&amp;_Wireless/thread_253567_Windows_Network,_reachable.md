---
title: "Windows Network, reachable?"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by SvanteH on 2006-09-08
I can see the folders but I can't access them and I am trying to find a solution for that ;)

Please note that I am sitting at a LAN so I can't change any settings on their computers.

I can see but I can't access, also 

timeout connecting to xxx.xx.xxx.xxx:139
Error connecting to xxx.xx.xxx.xxx (Operation already in progress)
cli_start_connection: failed to connect to MAKS<20> (xxx.xx.xxx.xxx)
        \\MADFORCE                      madforce

Operation already in progress during excecuting smbtree command.

---

### Post by SvanteH on 2006-09-08
Also it tries connecting to the "global IP" we got, so basically it doesn't recognize them as LAN ips (192.168.xxx.xxx)

---

### Post by tbonius on 2006-09-08
I am afraid you might want to be a bit more specific.  You are attempting to access SMB shares on remote Windows computers from a Ubuntu computer?  Using the Gnome SMB browser?

Try pinging the machines first by IP address.  Are they accessible?  Then try accessing them via the SMB browser by IP address :

smb://192.168.x.x

or whatever the IP address is.  Also.. are these Windows machines a member of a Windows domain?  Are the shares open to anyone outside of the domain?

T

---

### Post by SvanteH on 2006-09-08
I can't ping them as I don't know the network IP range, smb:// gives me the Windows Network content but as said, I still can't actually connect to the computers. 

I'm not trying to access SMB shares;
Basically I am trying to read the content of each specific person (In Windows I just open Network ~ and connect to their computer (can't do that now :p))

---

### Post by spd106 on 2006-09-08
So, does smbtree work then?
Have you installed the smbclient package? It should enumerate all netbios aware PCs on the same network. You must remember that netbios isn't routable without a CIFS/SMB forwarder. So if you're alone on the network you won't see anyone.

What about using nmblookup to resolve ip addresses? Do you have a DNS/WINS server?

---

### Post by tbonius on 2006-09-08
Browsing the contents of a share IS using SMB.  Make sure you have the samba package installed.. (which I assume that you do).

Also.. as I stated before.. find out if these Windows machines are on a Windows Domain or not and are configured to allow access on their shares to computers not joined to the Windows Domain.

Verify a couple of IP addresses of Windows machines you want to brose and try connecting directly to them.

Verify you are a member of the same Workgroup name so that you can browse within that group of computers.

Verify that you are using the correct DNS and (if needed) WINS serers for the network

T

---

