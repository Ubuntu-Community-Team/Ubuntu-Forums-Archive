---
title: "Killer E2205 NIC"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by Tristan_Cormier on 2015-10-07
Hello,

I am experiencing issues with my Killer Network E2205 NIC (Atheros QCA8172) on Ubuntu Vivid Vervet (15.04) and would greatly appreciate any help in resolving them.
_The wireless-info text dump is attached within._

Thank you for your valuable time and consideration.


**EDIT: The problem was resolved thanks to chili555's [suggestion]("http://ubuntuforums.org/showthread.php?t=2297839&page=2&p=13373793#post13373793").**

---

### Post by Tristan_Cormier on 2015-10-09
I'm still not able to connect to the internet or my router via the LAN. Any help would be greatly appreciated.

---

### Post by fillchiam on 2015-10-09
I'm not sure if I can help much, but I think others might be able to help more readily if you include the output of the wireless-info script from [this pinned thread](http://ubuntuforums.org/showthread.php?t=370108). :)

Specifically, these commands:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by Tristan_Cormier on 2015-10-09
> **fillchiam said:**
> I'm not sure if I can help much, but I think others might be able to help more readily if you include the output of the wireless-info script from [this pinned thread]("http://ubuntuforums.org/showthread.php?t=370108"). :)

Specifically, these commands:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

I've updated my original post with the wireless-info dump file. Thank you.

---

### Post by chili555 on 2015-10-10
It looks like you are well and truly connected to me:> eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd91:c69a:a544:0:90a:4e0a:d4d4:a493/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fd91:c69a:a544:0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98112 (98.1 KB)  TX bytes:116844 (116.8 KB)
          Interrupt:19 Are you able to ping?```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by Tristan_Cormier on 2015-10-10
> **chili555 said:**
> It looks like you are well and truly connected to me:Are you able to ping?```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

I am able to ping my own addresses and my ISP's but nothing else.
[www.google.com](www.google.com), [www.ubuntu.com](www.ubuntu.com) return unknown host errors.

Could it be a problem with my ISP? Everything works fine on my Windows 10 partition.

---

### Post by chili555 on 2015-10-10
It may be a DNS issue. According to your wireless-info, you have:> IP4.DNS[1]:                             207.134.193.189
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             192.168.1.1Are those numbers you plugged in to Network Manager? How do they correspond to the same data on your Windows partition? No typos??

---

### Post by Tristan_Cormier on 2015-10-10
> **chili555 said:**
> It may be a DNS issue. According to your wireless-info, you have:Are those numbers you plugged in to Network Manager? How do they correspond to the same data on your Windows partition? No typos??
IPv4 DNS servers are the same on Windows. I don't know what the hell is going on.

---

### Post by Tristan_Cormier on 2015-10-10
> **chili555 said:**
> It may be a DNS issue. According to your wireless-info, you have:
> IP4.DNS[1]:                             207.134.193.189
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             192.168.1.1
Are those numbers you plugged in to Network Manager? How do they correspond to the same data on your Windows partition? No typos??

I have finally been able to resolve my problem by manually setting my DNS servers under the Network Manager.
Thank you very, very much for your valuable time and continued support.

[B]EDIT: It turns out I was only able to connect to the internet for roughly 30 seconds, before experiencing issues again. Could it be my ISP that is at fault here?
How do I go about asking them for help, knowing that they have no trained technician and will likely be unable to understand even what an IP address is?[/B]

---

### Post by chili555 on 2015-10-10
I'd try setting my DNS nameservers to:```
8.8.8.8
192.168.1.1
```I suggest you also try:```
sudo ip route delete 169.254.0.0/24 dev eth0
```Then try again.

I doubt it is your ISP. All your ISP sees at its end is the router. By the way, most run a very small version of Linux.

---

### Post by Tristan_Cormier on 2015-10-10
> **chili555 said:**
> I'd try setting my DNS nameservers to:```
8.8.8.8
192.168.1.1
```I suggest you also try:```
sudo ip route delete 169.254.0.0/24 dev eth0
```Then try again.

I doubt it is your ISP. All your ISP sees at its end is the router. By the way, most run a very small version of Linux.

sudo ip route delete 169.254.0.0/24 dev eth0
RTNETLINK answers: No such process

It however seems to be working for the moment, as I have disabled IPv6. Could this be the problem?

---

### Post by chili555 on 2015-10-10
> It however seems to be working for the moment, as I have disabled IPv6. Could this be the problem?Anything is possible. Please keep us posted.

---

### Post by Tristan_Cormier on 2015-10-10
> **chili555 said:**
> Anything is possible. Please keep us posted.
It worked once again for a short time and then stopped working again. I'm not sure what's going on but is there any diagnostic I could ask my ISP for? It's a very small company and I have direct access to the technicians, and even the owner.

---

### Post by chili555 on 2015-10-11
I couldn't begin to guess what to ask the ISP. As I said, all he sees from his end, is the router. Assuming that other devices connect to it correctly, then what the ISP sees, the router, isn't likely the issue.

I'd check your own log first:```
cat /var/log/syslog | grep -e eth0 -e alx | tail -n25
```Ideally, run this immediately after a connection and drop.

As it will be lengthy, post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by Tristan_Cormier on 2015-10-11
> **chili555 said:**
> I couldn't begin to guess what to ask the ISP. As I said, all he sees from his end, is the router. Assuming that other devices connect to it correctly, then what the ISP sees, the router, isn't likely the issue.

I'd check your own log first:```
cat /var/log/syslog | grep -e eth0 -e alx | tail -n25
```Ideally, run this immediately after a connection and drop.

As it will be lengthy, post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)
Here it goes: [http://paste.ubuntu.com/12756872/](http://paste.ubuntu.com/12756872/)

I'd also like to mention that my ISP is somehow splitting connection requests in two. One of the two switches handles all port 80 traffic, while the other handles the rest. I have two IP addresses. Could that cause issues? I realized earlier my connection seems to be working but it just continually drops and I have to refresh pages like 100 times before it reaches. Same thing for apt-get update/upgrade.

---

### Post by chili555 on 2015-10-11
> I'd also like to mention that my ISP is somehow splitting connection requests in two. One of the two switches handles all port 80 traffic, while the other handles the rest. I have two IP addresses.I don't understand why you or the ISP would want this, although I freely admit that there is much in networking that I don't understand.

For me, with only ten or twelve devices attached at any one time, it works perfectly well to have:

chili's computer -->  router -->  DSL modem --> ISP

Your log shows nothing very interesting except:> Registering new address record for fd91:c69a:a544:0:468a:5bff:fe9e:761 on eth0.*.That's an IPv6 address. I thought you had set IPv6 to 'Ignore.'

---

### Post by Tristan_Cormier on 2015-10-11
I once again manually set everything and it worked flawlessly until I restarted the computer to complete the installation of some updates.
What I don't understand is how every single site on the planet and beyond isn't working when all my ISP's addresses load in less than 300 ms.

[B]EDIT: I have finally found a solution!
After Googling around, looking for diagnostics I could run on my own, I stumbled upon 'dhclient'. I have now been able to consistently connect to various websites without interruption for a few hours upon running 'sudo dhclient' upon booting.

Is there any way to automatically run the command every time the computer boots?
[/B]

---

### Post by Tristan_Cormier on 2015-10-14
I have still not been able to find a way to resolve the issue automatically yet. Any ideas? I also happen to be having a problem with some USB devices. Should I open a new thread about it?

---

### Post by chili555 on 2015-10-15
> Is there any way to automatically run the command every time the computer boots?I suggest you add to /etc/rc.local:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="#FF0000"]dhclient eth0[/COLOR]

exit 0
  
```> I also happen to be having a problem with some USB devices. Should I open a new thread about it?  Yes, please.

---

### Post by Tristan_Cormier on 2015-10-16
> **chili555 said:**
> I suggest you add to /etc/rc.local:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR=#FF0000]dhclient eth0[/COLOR]

exit 0
  
```Yes, please.

Thank you, chili555.
I've applied your suggested edit to /etc/rc.local and it worked perfectly. Now my only remaining problem seems to be a hardware one and I suspect it may be due to a faulty motherboard...

I'll mark the thread as resolved.

---

