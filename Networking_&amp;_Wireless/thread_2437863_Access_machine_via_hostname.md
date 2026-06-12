---
title: "Access machine via hostname"
date: 2020-03-02
forum: Networking &amp; Wireless
---

### Post by sim085 on 2020-03-02
I have two ubuntu servers which I had installed at different times, one of these is 16.04 (machine1) and the other one is version 18.04 (machine2). When I use the command hostname both give me the hostname correctly, with machine1 hostname being "machine1" and machine2 hostname being "machine2".

The problem is that while I can access machine1 over the network using the hostname "machine1" or "machine1.local", when it comes to machine2 I can only access this through the IP Address, if I try to ping using "machine2" or "machine2.local" I am told that the machine cannot be accessed. I have checked my router and I can see in the DHCP settings page that both machine1 and machine2 are registered and that machine1 has the name "machine1" and machine2 has the name "machine2".

So given on router both machines look to have the correct name, what might I have different on machine2 from machine1 such that I can access machine1 via the hostname (machine1, machine1.local) but I cannot do the same for machine2?

btw - ping is not the only way I tried to test access to machine2 via hostname, I have also tried via putty (for machine1 I can access via hostname but not the same for machine2).

---

### Post by TheFu on 2020-03-02
a) servers shouldn't use DHCP.  They need static IPs.
b)There are 3 ways to have machines resolve names[LIST]
[*]/etc/hosts entries on all machines
[*]DNS server for the network.
[*]Avahi zeroconf server
[/LIST]

host1.local uses the 3rd method, avahi.
All hosts know their own name. That because the /etc/hosts file has it added during install, but only for the localhost IP 127.0.0.1 (or any 127.0.0.x can be used, doesn't matter.)

Some home routers have the ability to be DNS servers and may enable this with using DHCP reservations. Or you can run a DNS server somewhere on your network and have the DHCP-reservation server point to the new-to-you DNS server.  

An article about DHCP reservations: 
   [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

IMHO, servers shouldn't use Avahi, but that's mainly because the early releases of that tool had problems sucking 100% of the CPU on a system. That was a long time ago.

I manage my network carefully.  Every system on it has an effective static IP.  Any non-portable system that has a keyboard gets a manually configured static IP.  Portable devices, like tablets, smartphones, laptops, and some IoT devices get static IPs using that "DHCP Reservation" method.  Guest devices aren't allowed on my network. They get placed onto a guest network which is treated like the internet from a security standpoint. 

Clear as mud?

---

### Post by sim085 on 2020-03-02
> **TheFu said:**
> 
Clear as mud?

I have done some further experiments. It looks like only my Windows machine can access machine1 as "machine1" or "machine1.local". On an Apple machine I can only access machine1 using its IP address. However the host file on my Windows machine does not have any entry for machine1.

I have also tried to see if Avahi is installed on machine1 but it looks like not as when I try to stop/start the service it says that the service cannot be found.

---

### Post by TheFu on 2020-03-02
Avahi has to be installed on all the systems (or another zeroconf implementation) for the names to be shared.

For under 5 systems, putting the IP -to- name records for the LAN IPs into the /etc/hosts files is usually easiest. This assumes all have static IPs.

---

### Post by Morbius1 on 2020-03-02
Something doesn't add up here.

Win10 can access it with it's mDNS host name yet avahi is not found?

Are you doing a:
```
sudo service avahi status
```
Or are you doing a:
```
sudo service avahi-daemon status
```

There is no "avahi.service". There is an "avahi-daemon.service" And you would have had to install avahi-daemon on your servers since it's not installed by default on the server edition.

By any chance are all of these machines not on the same router?

---

### Post by sim085 on 2020-03-02
> **Morbius1 said:**
> Something doesn't add up here.

All machines are connected to the same router. I can confirm avahi is not installed on any of the machines (Unit avahi-daemon.service could not be found).

Another strange thing I noticed is the following;

Following steps provided here: [https://linuxize.com/post/how-to-change-hostname-on-ubuntu-18-04/](https://linuxize.com/post/how-to-change-hostname-on-ubuntu-18-04/)

If I change the hostname of machine1 from "machine1" to for example "mymachine1" and restart the machine my router correctly reports the Client Name of machine1 as "mymachine1".

If I change the hostname of machine2 from "machine2" to for example "mymachine2" and restart the machine my router reports the Client Name of machine2 as "Unknown". 

Only difference I can see is that machine2 has a cloud.cfg file (this was an Ubuntu 18.04 installation) while machine1 does not have this file (this was an Ubuntu 16.04 installation).

---

### Post by TheFu on 2020-03-02
hostnames have ZERO, nothing, nada, to do with network names.  
DNS doesn't care what the hostname is.  
/etc/hosts doesn't care  what the hostname is.  
I haven't any clue about zeroconf/avahi if it cares about the hostname.

Does your router have a DNS capability? Is it enabled?  DHCP may or may not be connected  (tied) to DNS.  I've not see that connection automatically setup on any router before, but perhaps newer routers do it?  Check the manual for your router to be certain.

With only 4 machines, I would use the /etc/hosts method and be done with this in 10 minutes.

---

### Post by Morbius1 on 2020-03-03
> I can confirm avahi is not installed on any of the machines (Unit avahi-daemon.service could not be found).
How about installing it:
```
sudo apt install avahi-daemon
```

---

### Post by Morbius1 on 2020-03-03
This is another "by any chance" question I'm afraid.
>  Only difference I can see is that machine2 has a cloud.cfg file (this  was an Ubuntu 18.04 installation) while machine1 does not have this file  (this was an Ubuntu 16.04 installation).                 

When you downloaded the server iso did you go here: [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

It would have been a reasonable thing to do and you would have downloaded a ubuntu-18.04.4-[COLOR=#0000cd]**live**[/COLOR] ... iso.

Or did you go here: [http://cdimage.ubuntu.com/releases/18.04/release/](http://cdimage.ubuntu.com/releases/18.04/release/).

That would have downloaded a ubuntu-18.04.4-server-amd64 iso.

I did the first one myself in the beginning and I ended up with a pretty wacky install. Then I read LHammonds post ( [https://ubuntuforums.org/showthread.php?t=2390785](https://ubuntuforums.org/showthread.php?t=2390785) ). After I installed the non-Live version from the second link things went back to normal.

---

### Post by sim085 on 2020-03-03
> **Morbius1 said:**
> I did the first one myself in the beginning and I ended up with a pretty wacky install.

I still have the ISO image used for the install, it the the live version; "ubuntu-18.04.2-live-server-amd64.iso"
Will read the post you linked to.

---

### Post by sim085 on 2020-03-03
> **TheFu said:**
> With only 4 machines, I would use the /etc/hosts method and be done with this in 10 minutes.

I will probably go for this method.

---

