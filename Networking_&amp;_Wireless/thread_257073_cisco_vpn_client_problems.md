---
title: "cisco vpn client problems"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by bbbbbtony on 2006-09-14
&#65279;i've tried four different software versions of the cisco vpn client, 32bit and 64 bit versions. i even used the version that was in www.popey.com's tutorial and i get this. my headers should be the same because i have not done an update or upgrade. i have a fresh install of ubuntu, did apt-get to get the headers and it pulled it off the cd that was in the drive. so the headers are the same version as the kernel.

Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".

running amd64 with 64 bit version of ubuntu
intel pro wireless 2200bg wireless card

if you need more info let me know.

---

### Post by spin2cool on 2006-09-14
I had problems with the Cisco client too, and ended up using vpnc instead.  I've had no problems with it.

---

### Post by dermdaly on 2006-09-14
Make is a standard utility for running builds.  Looks like you don't have make installed.
Install the package "build-essential".
Do this:
 sudo apt-get install build-essential

to get make.
Actually, to install the cisco vpn, there's a couple of other things you'll need:
This client must be built against your current kernel headers. However its written against an older version of the kernel(At least, 4.7 my version was), and will now have build errors. Fortunately these have been found out there, so there's some well known fix.:(see [http://www.redhat.com/archives/fedora-list/2005-November/msg02105.html](http://www.redhat.com/archives/fedora-list/2005-November/msg02105.html))

Get your headers using the following command:
sudo apt-get install linux-headers-`uname -r`
The patch needed can be applied to the cisco client using these commands:
cd vpnclient
patch < (patch file name)
sudo vpn_install

Hope this helps
Dermot.

---

### Post by Spankmaster79 on 2006-09-15
I have just installed version 4.8 of the client with no problems. The patch isn't needed as it seems. But I get a different error.

It says:
> 
Secure VPN Connection terminated locally by the client
Reason: Failed to establish VPN connection.
There are no new notification messages at this time.


What can I do? I use a D-Link DWL-650 that works, since I get a connection to the Wireless Network and can use it. I need the VPN to get a connection to the company servers.

So what could be wrong? Using the same .pcf under Windows works.
The serice is started with /etc/init.d/cisco-blainit start.

Anyone able to help?

---

### Post by routerstu on 2006-09-15
i have installed 4.8 in dapper but needed build-essential and kernel headers.  maybe it is time for a new dapper howto?  also you have to run in sudo.

---

### Post by ret3 on 2006-09-15
I've navigated the installation and cofiguration fun with the Cisco VPN client, but now that I can connect, I have no idea what do in order to use the connection. After connecting, it does not return a command prompt; is that right? How do I view the network or navigate to a particular pc? How do I open a browser "through" this tunnel?

---

