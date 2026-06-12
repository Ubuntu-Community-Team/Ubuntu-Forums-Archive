---
title: "Trying to get my 14.04 box to access a windows server thru VPN"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by pollywog on 2015-07-04
So here's my situation. I have  a new job working for a tiny company, and I need to get access to a VPN to access a windows server at my boss's house. He's given me the IP address, my username and password. On a windows box this was enough to get me to connect to the VPN. Once connected he had me use the Start search box to enter his computer's name (which is a word, not a number)“\\computername”. After I did this a window popped up with a bunch of folders which exist on the server. I right clicked on the one I needed and selected “map this drive” option.  After that I had access to the needed folder on a windows computer. 
	I'm trying to accomplish the same thing on my 14.04 box, since it's the main computer I use. I copied screenshots of the VPN connection properties to use as a guide to connect my linux box. By doing this I have gotten as far as having a VPN connection show up under my network tray icon. When I connect to it, it takes a moment trying to connect, then it indicates that I'm successfully connected. Great! Now I need to search \\computername for the folder that I need in order to map it. Any ideas how I should do this? I assume I need some combination of samba, mount commands, and maybe fstab edits, but I hit a brick wall here. Any help would be appreciated.

---

### Post by SeijiSensei on 2015-07-04
Some Linux file managers support the smb://server/share form of address. KDE's Dolphin does so, and I think Nautilus might as well.  So rather than connecting with "\\servername\sharename" as in Windows you'd use "smb://servername/sharename" instead.

You may need to add an entry to /etc/hosts with the name and IP address of the server in order to use the hostname rather than an IP.

You can also use smbclient from the command prompt; e.g., "smbclient -U username //servername/sharename".  Again an entry in /etc/hosts might be required.

---

### Post by pollywog on 2015-07-04
Thanks SeijiSensei! I'm close but so far no cigar. Trying cmd line, but so far exits with timeout error. If I get it working I'll be sure to share. Till then it looks like I have to work from windows :(

---

### Post by SeijiSensei on 2015-07-05
With the VPN up, can you ping the server's IP address?  If so, try "telnet server_IP 139" to see if you can connect to the port that handles file-sharing connections.

---

