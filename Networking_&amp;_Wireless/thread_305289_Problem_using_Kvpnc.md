---
title: "Problem using Kvpnc"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by dudds on 2006-11-23
Hi Guys I hope someone can help. I have installed vpnc and kvpnc packages. I then setup all the relevant details in Kvpnc and then try to connect. The only problem is that I get the message "loading of module tun failed".

I really don't know where to go from here. Can anyone give me a few pointers.

Thanks,
David

---

### Post by dudds on 2006-11-23
following the below instructions from another post seems to work. Why doesn't the Kvpnc client work then?

Hello,

after struggling to get the cisco vpn client working under hoary for a few weeks, I found vpnc a saviour - both easy to configure, and easier to run.

I assume you have already 'sudo apt-get install vpnc resolvconf'

Now you want to create a file, with <name of connection profile> being something easy to remember, and short to type out

Code:

/etc/vpnc/<name of connection profile>.pcf

then, enter the following details into that file

Code:

IPSec gateway <ip of server> IPSec ID <group name> IPSec secret <group password> Xauth username <username>

save the file, and then after ensuring you have enabled your wireless connection and have an IP, at a prompt type

Code:

sudo vpnc-connect <name of connection profile>

It will then prompt for your user password, enter that in, and you should be good to go.
Reply With Quote

---

