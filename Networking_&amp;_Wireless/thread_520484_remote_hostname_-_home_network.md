---
title: "remote hostname? - home network"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by mickeythecat on 2007-08-08
I am still trying to hook up a simple ubuntu home network (desktop and wireless laptop, both running ubuntu).

I found a number of sites with info, however I cannot figure out what each computer's "remote hostname" is.  Most of the sites in their tutorials quote something like "modify these to match your environment".

Specifically, what is the default ubuntu hostname for a desktop computer. (i.e. what should I substitute for 'ubuntu2' in the last line below?
Should this be 127.0.1.1 which is what shows up in BOTH computer's /etc/host file?
[I]
"Next enter the command to mount to the remote folder (in this example we use ubuntu2 as the remote hostname and /home/demo as the remote path - modify these to match your environment):

sudo mount ubuntu2:/home/demo /home/demo/demo-folder"[/I]

---

### Post by spd106 on 2007-08-08
When they say your network settings they mean in terms of domain name. This will only matter if you have a DNS server on your network and if you want to access the machine from outside of the LAN. For instance if you had a domain called example.com, each machine would have a name such as ubuntu2.example.com. This is overkill for a simple home network.

The 127.0.1.1 or 127.0.0.1 addresses are the loopback addresses for the local machine and will not be routed out onto the LAN, that means only the machine you are using will see it.

You can see the hostname in the System -> Admin -> Network capplet, under the general tab, or simply type *hostname* into a terminal. You won't be able to ping the hostname without setting up a DNS server, configuring samba/netbios/WINS or maintaining hosts files. Though since we now have [Zeroconf ]("https://help.ubuntu.com/community/HowToZeroconf")(service discovery) turned on by default, you can use hostname.local instead.

So getting to your problem, the two simplest choices are

1) Set static IP addresses on all PCs and add each PC to every other's /etc/hosts file. Where you have lines to map hostnames to addresses. This is a bother to begin with and means lots of updates if you make any changes, but it works well and lookups are fast.
e.g the hosts file on ubuntu1 would look like this
```
~$ cat /etc/hosts 
127.0.0.1       localhost
127.0.1.1       ubuntu1
192.168.0.5       ubuntu2
192.168.0.6       ubuntu3
192.168.0.7       ubuntu4

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


2) Ensure avahi-daemon is running on all PCs and just use hostname.local instead of hostname. You can keep the DHCP server running as the mapping takes place on demand. This way is simple to get working, but lookups are a little slower (almost unnoticeable). This won't work outside of the LAN, so you will have to make sure all PCs are on the same network (not usually an issue). On Windows PCs you can install the Bonjour for Windows package from Apple.

Other than these two options you will have to start installing extra software such as a DNS server.

---

### Post by mickeythecat on 2007-08-08
Your option 1 with static IP address looks the easiest (and once this is set-up, that is it – never should have to be changed).  If I follow your logic with /etc/hosts file, then my network will look like this (at work now so will try this tonight).  Do you agree?

Thanks in advance, this has been extremely frustrating.

Scott (San Francisco, CA)


_Simple network consisits of_:
- Single house just two ubuntu computers (desktop and wireless laptop)
- cable from street to wireless rounter
- ethernet from wireless router to ubuntu 7.04 desktop (mickeythecat, /home user ID - mickeythecat)
- ubuntu 7.04 laptop (cynmac, /home user ID =cyn) connects via wireless router
(internet works fine on above without any network stuff below, just not networked together yet)

To get the network to work, I have three files to screw around with on both computers:
/etc/hosts
/etc/fstab
/etc/exports

**For the desktop (mickeythecat)**:

_For /etc/hosts, add following lines_:
127.0.1.1 mickeythecat (should already be in /etc/hosts)
192.168.0.5 cynmac (new line to add)

where 192.168.0.5 is a number I am making up myself and therefore this number I also have to define as a static IP address on the laptop (cynmac)


_In /etc/fstab, add the following_:
cynmac:/home/cyn /mnt/mac nfs defaults 0 0

where I already created /mnt/mac on the mickeythecat machine (desktop)

_In /etc/exports, add the following line_:
/home/mickeythecat cynmac/(rw)



**For the laptop (cynmac)**:

_For /etc/hosts, add following lines_:
127.0.1.1 cynmac (should already be in /etc/hosts)
192.168.0.4 mickeythecat

Where 192.168.0.4 is a number I am making up myself and therefore this number I also have to define as a static IP address on the desktop (mickeythecat)

_In /etc/fstab, add the following_:
mickeythecat:/home/mickeythecat /mnt/pc nfs defaults 0 0

where I already created /mnt/pc on the cynmac machine (laptop)

_In /etc/exports, add the following line_:
/home/cyn mickeythecat/(rw)

---

### Post by spd106 on 2007-08-08
As long as you've install all of the relevant NFS packages and have permissions/user accounts worked out, that looks ok to me.

There is a better, more detailed description of the steps to configuring NFS on this wiki page [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) 

I use mostly ssh and samba and I have yet to do any tinkering with NFS, so I'm a little inexperienced in that aspect of networking.

---

### Post by mickeythecat on 2007-08-10
Darn,  Still cannot get this to work.  I made all the changes above to the three /etc files on both machines.  After rebooting or after sudo mount -a command, both machines respond with "unable to mount cynmac (or mickeythcat), server is down".

The problem is likely me not understanding how to "Set static IP addresses on all PCs".  I went into the system/network panel and since I have cable internet, I already had the appropriate non-static boxes checked.  If I find my particular ip address (via a website that tells me what my address is), and if I change my network settings to just be that number (by me typing it in), then the internet does not work.

It seems like I am almost there.  If anyone has any ideas, let me know.

Thanks.

---

### Post by spd106 on 2007-08-11
The wireless router is your presence on the Internet so it has the only public viewable IP address, it's assigned by the ISP and should not be changed by you.

The wireless router also has a private address on your LAN, usually in the 192.168.x.x range, you must make sure that all the PCs on your LAN match the first three octets of this address. It varies between manufacturers, Belkin use 192.168.2.x, Linksys use 192.168.1.x etc So you'll have to check which one you have before you assign static addresses to the other PCs. Once you think it's set up, ping them to make sure it works.

You can use the System -> Admin -> Network capplet, or edit the /etc/network/interfaces file with a text editor.

---

