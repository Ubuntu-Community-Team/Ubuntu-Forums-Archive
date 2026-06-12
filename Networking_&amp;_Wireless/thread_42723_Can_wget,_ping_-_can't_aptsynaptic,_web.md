---
title: "Can wget, ping - can't apt/synaptic, web"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by pompomtom on 2005-06-19
Using Ubuntu Hoary, I have no problem using the machine as a Samba and ssh server on the local net. I can also ping domains from it, and ftp the outside world, no worries. What I cannot get working is web (no real problem, the box is my local storage a server), or apt or synaptic (which IS a problem). The bizarre thing, which has prompted this post, is that I can actually retrieve web pages using wget. I only found this out when I'd forgotten about the grief I'd been having - used wget without thinking and it worked fine.

So WTF is wrong here?

I've disabled ipv6, as I've read posts suggesting this has caused problems with Ubuntu and dsl. I've tried dropping the MTU to 1000 (well, I've gone down as low as 500), as I gather this has been an issue for some with dsl, where the modem tacks something on to the packet and then chokes. This was no help. Also, I can get web using a knoppix CD (with an MTU of 1500). 

Oh, yeah, on the hardware side, the box itself is a P4, 3ghz, 512Mb RAM, going into a linksys wrt54g router, going into a netcomm nb5 dsl modem. I've got windows and macOS machines on the same network working fine. 

So can anyone suggest where I should be looking? I'm considering installing knoppix instead, but would prefer not to. Is there some other setting I could compare between the what knoppix is doing and ubuntu? 


(Happy to provide ifconfig or dmesg or apt (or whatever) output if anyone thinks it'll help, but didn't want to make the post massive....)

---

### Post by DaturaX on 2005-06-19
what is the error u get when u type apt-get update and show us what ifconfig says.

---

### Post by pompomtom on 2005-06-19
ifconfig says:

```
eth0      Link encap:Ethernet  HWaddr 00:11:5B:C4:C3:2C  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256461321 (244.5 MiB)  TX bytes:7456575 (7.1 MiB)
          Interrupt:23 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2552 (2.4 KiB)  TX bytes:2552 (2.4 KiB)

 
``` 

apt-get update starts off like this:

```
Err http://security.ubuntu.com hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://au.archive.ubuntu.com hoary Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security Release
Err http://au.archive.ubuntu.com hoary-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://au.archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security/restricted Packages
Ign http://au.archive.ubuntu.com hoary-updates Release
```

....there's more, but it's still going and I'm just on my way out...

(thanks for looking!)

---

### Post by mila80 on 2005-06-20
Hi...
   I had a similar problem... 
Try with it:

Chance  your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp
...

 \\:D/ 

Then tell me... 
Bye

---

### Post by pompomtom on 2005-06-20
Well Mila80, that took the box off the net completely, no eth0 at all.

It seems you've made the same post in three threads here. Are you having some sort of joke?

---

### Post by pompomtom on 2005-06-20
Okay, I've sussed it out.

For others' reference, it was stuffed DNS. Resolv.conf was pointing to my modem, which works on every other box in the house, but not on Ubuntu. 

Specifying a proper DNS server, and locking it with the 'sudo chattr +i /etc/resolv.conf' as mentioned in other threads here fixed it all (these other threads also say that will only work on an ext2 or ext3 FS, btw).

Hope that can help someone.

---

### Post by pompomtom on 2005-06-20
Okay, I've sussed it out.

For others' reference, it was stuffed DNS. Resolv.conf was pointing to my modem, which works on every other box in the house, but not on Ubuntu. 

Specifying a proper DNS server, and locking it with the 'sudo chatter +i /etc/resolv.conf' as mentioned in other threads here fixed it all (these other threads also say that will only work on an ext2 or ext3 FS, btw).

Hope that can help someone.

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=mila80]Hi...
   I had a similar problem... 
Try with it:

Chance  your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp
...

 \\:D/ 

Then tell me... 
Bye[/QUOTE]
 don't do this. It will only take your network/internet down as soon as /etc/network/interfaces  is loaded again (for example after a reboot). 

mila80 please don't give this advice anymore

---

