---
title: "Can't set static IP"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Buuntu on 2010-07-01
Ugh... sometimes Linux drives me crazy.
Anyways, I've been trying to set a static IP for hours so I can have an SSH server on my computer.
I've tried everything from changing the settings in network-manager to manually editing /etc/network/interfaces. 
I don't know much about networking to be honest so maybe I'm missing something. 
I'm typing this from my fedora partition because I deleted network-manager and now can't get it to start up again in Ubuntu (so no internet), even though I managed to get it reinstalled from a live CD.

Anyways, if anyone can help or give ANY suggestions I'd really appreciate it.  Please...

---

### Post by oldfred on 2010-07-01
You cannot use any numbers within the range auto assigned for DHCP by your router. 

My router assigns 50 numbers starting at 100, so I could not use 100 or 101 even though under DHCP those were the address' normally used.

Attached are the settings I used.

---

### Post by jonobr on 2010-07-02
Hello

If you can (and you dont mind sharing) , could you post the results of ifconfig as well the results of 
/etc/network/interfaces
when you changed the settings, its important to check that ifconfig shows the new ip address has taken affect.
If it has and you have say a dns issue you may think its a static IP address problem when it is not.

---

### Post by Buuntu on 2010-07-02
> **oldfred said:**
> You cannot use any numbers within the range auto assigned for DHCP by your router. 

My router assigns 50 numbers starting at 100, so I could not use 100 or 101 even though under DHCP those were the address' normally used.

Attached are the settings I used.

That's not the problem, I realized that and discovered that my router assisgns 100-200 under DHCP so I was using low numbers such as .5 or .6.


I'll post the results of ifconfig and /etc/network/interfaces tomorrow when I get on my Ubuntu partition.

By the way, I managed to get a static address to work under Fedora.

---

### Post by Buuntu on 2010-07-02
So this is the output of both commands after setting it to manual by editing connections graphically (through network-manager).

My settings are:
IP: 192.168.1.5
Mask: 255.255.255.0
Gateway: 192.168.1.1
DNS Servers: 24.140.1.2, 24.140.1.3

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 04:4b:80:80:80:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:fd:d5:21  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fefd:d521/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2069 (2.0 KB)  TX bytes:7991 (7.9 KB)

~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by Iowan on 2010-07-02
You *should* be able to set up a static address via Network Manager, but I like to set up a static lease on my DHCP server that grants a lease based on MAC address. The machine always gets the same address, but it can be left set up as DHCP client.

---

### Post by oldfred on 2010-07-02
Is this a wireless connection? You have set up wlan0 not eth0.

---

### Post by Buuntu on 2010-07-03
Yes it's wireless.

---

### Post by Buuntu on 2010-07-05
bump

---

### Post by Buuntu on 2010-07-07
No one knows of a solution?  Ugh... I guess I have to use Fedora then

---

### Post by jonobr on 2010-07-07
Hello


I did not see this post til now, sprry for not replying sooner.

Looking at your ifconfig , it appears your wireless seems to have an ip address assigned,
In fact if you ping 192.168.1.5, im sure it will work.
If you ping 192.168.1.1 your default gateway, i reckon that would also work.

I dont know if 24.140.1.2 is pingable but you could try that also, 

also a ping to google or similar might show resolution to dns is working, or maybe not.

Anyway, im probably too late and your on your way back to fedora,

---

### Post by Buuntu on 2010-07-08
Thanks for the reply

Yes you're right, I can ping my gateway and my own computer when I have those settings.  I can't ping google however and my DNS server is "unreachable", so it seems to be a DNS issue.  
In that case, what can I do about it?

It's weird though because I have the exact settings in Fedora and it works fine...

---

### Post by jonobr on 2010-07-08
So what happens if you put

65.55.175.254

into your browser,
what do you see? If anything

---

### Post by oldfred on 2010-07-08
In Ubuntu I configure DNS as the router. 192.168.1.1 

The router finds the correct DNS on its own using its DHCP. I only see the DNS addresses if I check the router status.

---

### Post by jonobr on 2010-07-08
Like Oldfred, in my case, my dns is my default gateway however putting the ip address in the browser should prove misconfigured dns

---

### Post by Buuntu on 2010-07-08
Setting the DNS servers to my gateway address worked!  

Thanks a bunch everyone

---

