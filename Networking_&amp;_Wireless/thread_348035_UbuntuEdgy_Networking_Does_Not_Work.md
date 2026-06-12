---
title: "Ubuntu:Edgy Networking Does Not Work"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by pyrofire on 2007-01-28
I cannot get my Local Area Network to work.

i'm a new user to ubuntu, just installed it today. unfortunate problem here though.

please help.

---

### Post by highneko on 2007-01-28
Where's the router located? Are you trying for a wireless connection? Good luck.

---

### Post by pyrofire on 2007-01-28
the router is located approx. 1-2.5 meters away from the computer.

am attempting a wired connection.

am using d-link g604t

i cannot share files, it displays "nfs" or "samba" is not installed/found.

---

### Post by RandomJoe on 2007-01-28
Ah, so you DO have network connectivity?  You're getting an IP and all that?

The necessary items for NFS aren't installed by default.  Search for NFS in the package manager (I use Synaptic) and for a client install 'nfs-common', for a server install 'nfs-kernel-server'.

I don't use samba, but checking Synaptic it appears it should be default have client stuff ('samba-common') installed, to run a server you will need to install 'samba' as well.

---

### Post by pyrofire on 2007-01-28
no network connectivity whatsoever.

i am not getting an ip either (i think..) how do i check if im getting an ip from my router?

---

### Post by RandomJoe on 2007-01-28
Simplest is to open a terminal window and type 'ifconfig'.  If you have a connection, you will have (usually) an eth0, and the second line will show the 'inet addr:'.

If it only shows 'lo', then that means it didn't detect an Ethernet card, or it is disabled.

Do you have an Ethernet connection showing in System -> Administration -> Networking?

---

### Post by pyrofire on 2007-01-28
yes. both of them show correctly. ill have a look at ifconfig next time im in ubuntu trying another method to get on the net.

---

### Post by pyrofire on 2007-01-28
Update: Yes... it does display inet addr: --bunch-o'-numbers-- scope: link

edit:

Yes i do have network connectivity yay! cuz when i used the ip of the comp im currently using (this is a 2nd comp i decided to use.. much easier) it displayed an error that there are multiple users on the ip!

so can you tell me how to config my router?

it is: d-link g604t

---

### Post by RandomJoe on 2007-01-28
No, unfortunately I'm not at all familiar with configuring that sort of router as I don't personally use them.  It should just be a web-based config menu.

If your ethernet port is set to DHCP, you should be getting the IP from the router, so if it gives you (for example) 192.168.0.xxx then try browsing to 192.168.0.1 (most routers will be at x.x.x.1 for whatever network they give out) and see if you get a login screen.  You'll need the password (if any by default) to get in, though.  Each of the vendors are different on their defaults...

If you are using fixed IPs on your computers because DHCP doesn't work, it may have the DHCP server turned off.  In that case, just try setting the IP of the computer to 192.168.0.10 and connecting to 192.168.0.1.  You have to be on the same subnet, which means the first three numbers must match whatever's in the router.  (An oversimplified description, but for this issue is close enough!)  If that doesn't work, increment the third number for both IPs - e.g. 192.168.1.10 and 192.168.1.1.

Looking at my 'ifconfig' output, I think the line you are looking at (that ends in Scope:Link) is the inet6 (IPv6) addr.  There should be a line _above_ that with the regular (IPv4) address.  Here's mine:
```

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:28:DB:CB
            inet addr:192.168.144.2  Bcast:192.168.144.255  Mask:255.255.255.0
            inet6 addr: fe80::2c0:9fff:fe28:dbcb/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:46554192 errors:0 dropped:0 overruns:0 frame:0
            TX packets:62771891 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:2352315122 (2.1 GiB)  TX bytes:611223318 (582.9 MiB)
            Base address:0xecc0 Memory:fe320000-fe340000

```
I'm using the subnet 192.168.144.x here.

---

### Post by pyrofire on 2007-01-29
inet addr:192.168.144.2  Bcast:192.168.144.255  Mask:255.255.255.0

this line is not displayed.

            inet6 addr: fe80::2c0:9fff:fe28:dbcb/64 Scope:Link

this one is.

oh and i have worked with my router before. i know the password and everythin like that.

i know:

DHCP server IS enabled
The password
the ip (10.1.1.1)
the range (10.1.1.2-254)

---

### Post by pyrofire on 2007-01-29
so is anyone going to help?

---

### Post by Lil_Eagle on 2007-01-29
you can verify easily enough if DHCP is working by going to a terminal and typing

sudo ifdown -a && ifup -a

You should see the DHCP requests and answers.

---

### Post by pyrofire on 2007-01-29
im not entirely sure why its not working.. anyway, im uninstalling ubuntu, then trying again. maybe that might fix it. =)

---

### Post by Lil_Eagle on 2007-01-29
You can do that, but most of the time it isn't necessary to reinstall.  But if you're determined to reinstall, then make a separate partition for /home.  Then if you have to reinstall, most of your settings (ie. Destop Preferences) will be saved.

---

### Post by pyrofire on 2007-01-29
a new cd didnt make any difference.... there must be something wrong with my router/config that is stopping it from working.

after all.. it works fine on windows..

---

### Post by Lil_Eagle on 2007-01-29
Is your windows set to aquire its IP address automatically?

If so, then your file /etc/network/interfaces should have a lines that looks like these:
```

auto eth0
iface eth0 inet dhcp
```
If your windows uses a specific address then the file should contain this:
```

auto eth0
iface eth0 inet static
address 192.168.1.2  # or whatever your ip address should be
netmask 255.255.255.0

```
Hope that helps.

---

### Post by pyrofire on 2007-01-30
yes it is set to automatically recieve its ip.

---

### Post by spd106 on 2007-01-30
First try grabbing an ip address manually with **sudo dhclient eth0**.

If that fails with  "No DHCPOFFERS received.", try setting the ip address statically with **sudo ifconfig eth0 10.1.1.36**, then ping the router **ping 10.1.1.1**.

If this fails then you may have to look into a misconfigured driver, try **sudo lshw -C network**. It might also be useful to know what make/model of network card it is.

---

