---
title: "IP Address is all 000's"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-08-14
I have been having some strange issues with my internet access. I am using a SONY VAIO VGN FE780G Notebook. The wireless connection with the Linksys WRT54G 2.4Ghz router has always been sketchy at best. It finally gave up & only accessible using a LAN cable. The router is working fine with other computers. Last year I addressed the issue with Sony when the problem first began with the wireless. They informed me they would not support the hardware use with Ubuntu Linux. Ok, we all know that's lame. I refuse to go back to windows.

However, now the problem has progressed to an overall failure using the LAN cable as well. When I click on 'Connection Information' Everything dealing with the IP address has a listing of 000's. Is this fixable or is the computer finished ? Thanks Cal

---

### Post by aesis05401 on 2009-08-14
It is best to start by ruling out simple causes.

Start by verifying the physical connection to the router.  Address information is zeroed following failed dhcp renewals, so if your connection has a physical fault that is interrupting communication with the router and you were using dhcp then you would be seeing this behavior.

First try plugging into a different port on the router and attempting to enable your network connection.  If that doesn't work then try a different cat5 cable etc... 

At least this will help rule out simple causes.

---

### Post by mapes12 on 2009-08-14
> **aesis05401 said:**
> It is best to start by ruling out simple causes.

Start by verifying the physical connection to the router.  Address information is zeroed following failed dhcp renewals, so if your connection has a physical fault that is interrupting communication with the router and you were using dhcp then you would be seeing this behavior.

First try plugging into a different port on the router and attempting to enable your network connection.  If that doesn't work then try a different cat5 cable etc... 

At least this will help rule out simple causes.Yep! Then start the process of making sure your machine can access the other adapters in your network. I would start by pinging the laptop network adapter itself. Terminal: ```
ping 127.0.0.1 -c4
```This is what I get back from a fully functioning adapter in my machine: > PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.082 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.076 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.073 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.080 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.073/0.077/0.082/0.011 ms
mark@test-ubuntu:~$  Then we move on to querying your router but post back first please.

Mark

---

### Post by scorp123 on 2009-08-14
> **CoCoKnots said:**
> When I click on 'Connection Information' Everything dealing with the IP address has a listing of 000's. Is this fixable or is the computer finished ? Thanks Cal Why not boot a live CD?  Like this we'd at least know if it's really the hardware or rather --what I suspect-- your software setup.

---

### Post by scorp123 on 2009-08-14
> **mapes12 said:**
> ```
ping 127.0.0.1 -c4
```  That's the loopback. You can ping it all day long, it has nothing to do with the Ethernet interfaces. The loopback will be there even if there are no other interfaces whatsoever. ;)

---

### Post by egalvan on 2009-08-14
> **scorp123 said:**
> **Why not boot a live CD? ** Like this we'd at least know if it's really the hardware or rather --what I suspect-- your software setup.

I second this, you could use the LiveCD you used to install...

or download Puppy or PartedMagic, either one has excellent network support.

This would help eliminate the hardware...

---

### Post by CoCoKnots on 2009-08-14
> **mapes12 said:**
> Yep! Then start the process of making sure your machine can access the other adapters in your network. I would start by pinging the laptop network adapter itself. Terminal: ```
ping 127.0.0.1 -c4
```This is what I get back from a fully functioning adapter in my machine:  Then we move on to querying your router but post back first please.

Mark

Thanks Mark,
In the terminal I entered ping 127.0.0.1 -c4 as instructed & received a similar response,

ping 127.0.0.1 (127.0.0.1) 56(84) bytes of  data.
64 bytes from 127.0.0.1: 1cmp_seq=1 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: 1cmp_seq=2 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: 1cmp_seq=3 ttl=64 time=0.023 ms
64 bytes from 127.0.0.1: 1cmp_seq=4 ttl=64 time=0.026 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/mdev = 0.023/0.029/0.035/0.006 ms


I assume this looks to be working Ok???

MAPES12,
I am trying a different cable & router port next.

Thanks,
Be back in a few...

---

### Post by CoCoKnots on 2009-08-14
> **scorp123 said:**
> That's the loopback. You can ping it all day long, it has nothing to do with the Ethernet interfaces. The loopback will be there even if there are no other interfaces whatsoever. ;)

I tried booting from the original Ubuntu CD. It did not change the access to the internet... Still unable.

---

### Post by CoCoKnots on 2009-08-14
> **aesis05401 said:**
> It is best to start by ruling out simple causes.

Start by verifying the physical connection to the router.  Address information is zeroed following failed dhcp renewals, so if your connection has a physical fault that is interrupting communication with the router and you were using dhcp then you would be seeing this behavior.

First try plugging into a different port on the router and attempting to enable your network connection.  If that doesn't work then try a different cat5 cable etc... 

At least this will help rule out simple causes.

I tried another port on the router with the same results... No connection after searching. It appears that the cable is functioning correctly. It does begin to search once connected.

---

### Post by juancarlospaco on 2009-08-14
**You are "The Internet"**

:)

---

### Post by scorp123 on 2009-08-14
> **CoCoKnots said:**
> I tried booting from the original Ubuntu CD. It did not change the access to the internet... Still unable. OK, and you checked cables and all that?

What if you reboot the router? Maybe it's hanging? I have a Linksys WRT-54GL too and from experience I know that those things can hang sometimes. Or behave oddly. So what if you unplug it from power for like 20 seconds? And then plug it back again?

Also --very important-- do you have any other working systems? Can you check on that Linksys router if DHCP service is on and if it sees any leases given to any client computers?

---

### Post by CoCoKnots on 2009-08-14
> **scorp123 said:**
> OK, and you checked cables and all that?

What if you reboot the router? Maybe it's hanging? I have a Linksys WRT-54GL too and from experience I know that those things can hang sometimes. Or behave oddly. So what if you unplug it from power for like 20 seconds? And then plug it back again?

Also --very important-- do you have any other working systems? Can you check on that Linksys router if DHCP service is on and if it sees any leases given to any client computers?

Yes, I have rebooted the router & restarted the dish receiver. I have run two other computers off the same router. With all of this in mind, it make me think perhaps the system card/board may have gone south.

---

