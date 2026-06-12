---
title: "No Network Connection Before Login"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by jgambleii on 2008-07-31
Hello,

I think this may be a "feature" of Ubuntu, but is there any way to have the network connect prior to login? It appears as if the network only gets an IP address from DHCP after someone logs in and this is causing problems for an application that I use.

---

### Post by ChumleyEX on 2008-07-31
It should get the IP before you login, as the system boots it loads everything. I can do everything with my computer remotely without logging in. Of course I'm somewhat new to all of this so there might be something I don't know. Try pinging your computer from another one on the network if you can/.


Are you using wireless?

---

### Post by jgambleii on 2008-07-31
No, it's a wired connection. For some reason, after a fresh install, I can't ping the computer until I'm logged in.

---

### Post by terces on 2008-11-15
I have the same problem; fresh install of Kubuntu 8.10 on nVidia nforce4 chipset with AMD X2 processor.

The network manager stinks as far as holding any settings... but I am having much more of a headache with not being able to communicate with the computer via networking before login... this doesn't prove useful as I log in remotely via SSH or VNC.

Any ideas?

---

### Post by ToshiBoy on 2008-12-02
Same issue here. Once I've logged in locally, I can log out and the network is there. I suspect it has something to do with the way network manager works but I'm in the same boat. I don't know enough about it to fix this and am hoping someone out there may know. Is it maybe possible as a work around to create a boot script that will log an unprivileged user in, waits for the network manager to create the network connection and then log out?

I'm sure there is a way. Just another bug, I guess... along with Static IPs and VPNs, it really seems that we've gone backwards with networking in this release. 8.04 was rock solid on all these accounts, and I've been running it happily on most of my boxes. 8.10 with the new network manager does a lot of fancy and nice things... but unfortunately has broken a few of the fundamental basics.

---

### Post by metale on 2008-12-02
Same here, no network until the first login, even tho the service "basic network" comes in as [ok].

This is preventing likewise-open to work until I login as local first.

---

### Post by Iowan on 2008-12-02
Anyone checked the [bug list]("https://bugs.launchpad.net/ubuntu") or filed a report?

---

### Post by metale on 2008-12-02
There we go

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/304496](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/304496)

---

### Post by metale on 2008-12-04
Hey guys, try this

On the network manager, edit the auto eth0 connection and remove the check from "connect automaticaly" and "system settings". Go to your connection and check those boxes.

Worked for me (but I use a static IP).

---

### Post by zika on 2008-12-04
Using following command
(sudo to use Your admin priviledge)(You will be prompted for password)
(nano is editor)
(/etc/network/interfaces is the file where You configure Your networking if You do not want Network Manager to do that for You, but only after You are successfully logged in)

> 
sudo nano /etc/network/interfaces
make that file look like:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
That way You'll get rid of Network Manager and You will have network as soon as You boot.

The example above is for the case where You use DHCP. If You use static address then it is:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address ............
netmask ...........
gateway ...........


---

### Post by Biased turkey on 2008-12-04
Thanks to all the members who contributed to that thread and particularly metale and zika.
I installed Ubuntu 8.10 AMD64 yesterday and , except for that network manager bug, I'm very satisfied with that 8.10 iteration.

As mentioned the fix has 3 steps:
1) in network manager, uncheck "connect automatically" and "system settings"
2) Edit /etc/network/interface
3) In my case I had to edit /etc/resolv.conf too and add my ISP DNS server IP addresses.

Jacques

---

### Post by zika on 2008-12-04
I think You do not even need step 1. Network manager will give-up as soon You make connection other than lo in /etc/network/interfaces. 

Glad I could be of any help.

---

### Post by nZain on 2010-06-18
Works perfectly.

First, I added my static eth0 configuration to ```
/etc/network/interfaces
``` as explained by zika. This way my computer was available in the LAN before login, which is especially usefull, when using wakeonlan without auto login :)

However, I couldn't access the internet - for this to work, I had to add my router's IP to ```
/etc/resolv.conf
```

Thanks to zika & biased turkey

---

