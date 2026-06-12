---
title: "Access A VISTA share"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by itzabo on 2007-09-22
Here is my setup..

Linux Server (Running ClarkConnect)
This server handles DHCP, Firewall, Routing etc....
2 XP Systems
1 Vista System

I can access any share on the XP and Linux Server from my Ubuntu system
When I try to access the Vista share  (which has all of my music & Pics) I just
get "The folder Contents can not be displayed" error.

I can acces this share from any windoze PC, and I don't have a monitor and keyboard on the server to test it from there. 

I already setup my smb.conf with the correct workgroup.
I've been running Linux servers for the past 10 years. 
They just work!!

Suggestions?

TIA

Bo

---

### Post by ddrichardson on 2007-09-23
Yes there was a change in Vista, NTLMv2 is enabled by default which is not in older Samba versions. (more [here]("http://www.linux-watch.com/news/NS4434907782.html")).

Basically you need to:
1. Start/Run secpol.msc
2. Open Local Policies/Security Options, find "Network Security: LAN Manager"
3. Change it to "Send LM & NTLM - use NTLMv2 session security if negotiated."

This is a pain in the **** with file servers using an embedded non-upgradeable samba version.

---

### Post by itzabo on 2007-09-25
Tried that and no luck. But Here is how I got it to work

In synaptic Package Manager
Install SMBCLIENT & SMBFS

restart samba  (or reboot)

to manually mount a drive

Assume here Windoze & Linux user is fred, password is fredpass
vista system ip = 192.168.1.105
vista share is   music
Folder to mount on Unbuntu system    /home/fred/music

sudo mount -t smbfs -o username=fred,password=fredpass //192.168.1.105/music /home/fred/music

This will mount the vista share to /home/fred/music

To make it automatic every time you boot use this....

create a text file in your home directory with 2 lines
username=fred
password=fredpass

save it as .smbpasswd     (the . makes it hidden)

in a terminal:

chmod 600 .smbpasswd

then backup your fstab using
sudo cp /etc/fstab /etc/fstab.bak

sudo gedit /etc/fstab

add this line to the bottom

//192.168.1.105/music /home/fred/music smbfs credentials=/home/fred/.smbpasswd,uid=fred,gid=users 0 0
(The line above should read  ,gid=users 0 0 (NOT use rs 0 0 )
save and exit

test it with 
sudo mount -a

If all goes well it will now be mounted and the next time you reboot the share will be mounted automatically.

Good Luck!!!
I've spent 2 days figuring this one out.
I tried uisng the system's network name and it just wouldn't work. I had to us the IP address.

Bo

---

