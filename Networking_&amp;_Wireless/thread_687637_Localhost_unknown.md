---
title: "Localhost unknown"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by snifferharris on 2008-02-04
Just installed LAMP and cannot get Apache to serve up the "It works" page from [http://localhost](http://localhost) - only [http://127.0.0.1](http://127.0.0.1) and [http://synapse](http://synapse) (machine name) seem to work.

I have checked the following from the terminal:

xxxx@synapse:~$ nslookup localhost
Server:         192.168.1.254
Address:        192.168.1.254#53

Non-authoritative answer:
Name:   localhost
Address: 127.0.0.1

xxxx@synapse:~$ ping localhost
ping: unknown host localhost
xxxx@synapse:~$ 

Here is my /etc/hosts file contents:

xxxx@synapse:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost   synapse

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here is my /etc/network/interfaces contents:

xxxx@synapse:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

and finally an ifconfig output:

xxxx@synapse:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fec7:79d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8580730 (8.1 MB)  TX bytes:1347057 (1.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92709 (90.5 KB)  TX bytes:92709 (90.5 KB)

It's not too much of a big deal as Apache is working of sorts, but I don't understand why this is happening. Any help would be appreciated.

---

### Post by jetsam on 2008-02-04
I think that you're getting a negative response from a dns server, which is what causes ping to say localhost is unknown.  nslookup defaults to search further when this happens, and apparently ping and most other programs just take it as "there is no localhost."

Check your /etc/nsswitch.conf file.  If I'm right, I think you can fix this by making sure that "files" is the first entry in the list on the "hosts:" line.  This will cause name service lookups to check the hosts file before they move onto name servers or wins or whatever else is on that line.

---

### Post by snifferharris on 2008-02-05
This did the trick - I had changed the /etc/hosts file in the past and for some reason commented out the hosts: prefix leaving just the config. Thanks again for the prompt response.

---

