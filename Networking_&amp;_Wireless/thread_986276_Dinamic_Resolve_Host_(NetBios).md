---
title: "Dinamic Resolve Host (NetBios??)"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Sda1986 on 2008-11-18
Hi all, I'm new user of linux, and I am from Italy because sorry for may poor English and my poor knowledge.

I have Ubuntu (8.10) installed on my pc and I have 4more hosts in my house.

1. Sister PC (Windows)
2. Father PC (Windows)
3. Nas (Debian + Samba)
4. PrintServer

With windows i remember i can write **//sister** or ping **sister** and automatically my Pc resolve **sister** with the Ip of my sister pc. I search something and i understand, if i am not wrong, this is called Netbios.

In Linux i don't can do that! I know i have the hosts file but the ip in my net is assigned by DHCP, because i need something can do what windows do...
I search a lot but nothing i can't be able to find a program or something to config.

Can you help me?
Thanks!
Stefano

---

### Post by captaintrav on 2008-11-18
first of all, install the "winbind" package.  This service provides Windows-specific name resolution support, for WINS, and NetBios broadcasting. (synaptic or 'sudo apt-get install winbind'

After you install that package, you'll have to tweak name resolution a little to make it work.

From a terminal, try 

```
sudo gedit /etc/nsswitch.conf
```

Find the line that starts with 'hosts:'   You should see "dns files, " and so forth.  Add 'wins' somewhere on this line.  Save this file, and you should be able to resolve windows hosts more easily.  In nautilus, if you want to browse to a specific machine manually, enter smb://computername to do so.  ( click the little paper/pencil icon under the back button in nautilus to manually enter a location )

Here's what my /etc/nsswitch.conf looks like:

```
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          dns wins files mdns4_minimal [NOTFOUND=return] mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

Regards, and good luck!

---

