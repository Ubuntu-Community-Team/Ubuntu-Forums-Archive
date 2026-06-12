---
title: "Transfer on Samba at 250 KB/s  with 3945ABG"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Lantius on 2008-08-06
Hello:

   I have Ubuntu Hardy and a samba service in another computer on my lan network. I can use this share undo Windows without problems, I can see movies in real time without problems. Nevertheless in Ubuntu if I am watching the movie it is stopping all time. 
  I made a copy of a file to my computer and It showed a transfer speed of 250 KB/s. Sometimes it gets 800 KB/s and it works ok but it is very unstable. 
  If I do ping to the host i receive that:

```

4 bytes from zipi.lan (192.168.1.75): icmp_seq=13 ttl=64 time=2.14 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=14 ttl=64 time=2.21 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=15 ttl=64 time=2.39 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=16 ttl=64 time=3.30 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=17 ttl=64 time=3.27 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=18 ttl=64 time=2.75 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=19 ttl=64 time=2.97 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=20 ttl=64 time=3.16 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=21 ttl=64 time=2.03 ms
64 bytes from zipi.lan (192.168.1.75): icmp_seq=22 ttl=64 time=1.98 ms

```

  I used EtherApe to see if some process were using the network. But there is nothing until I began to copy the file. 

  I looked up for information in Ubuntu I found [it]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html"), so I remove the IPV6 but it continues with problems. 

  I have a:

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:18:de:6e:65:e5
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.65 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

  The driver is iwl3945 and It is made by Intel so I think it is ok. Moreover I did a transfer from winzip and it goes at 300KB/s what is my maxim speed. 

  Maybe something is wrong with samba. I don't know what to do. I hope some help 

  Sorry about my english

Greetings.

PD:

I have seen that if you turn off wireless, doing second click upper right in gnome and turn on again it began to works again ok. Nevertheless I would like to solve this problem.

---

### Post by szale9001 on 2008-08-10
I have the exact same problem with the exact same network card. With Windows everything seemed to be fine. Lately however I get 500k to 1MB LAN transfers tops and can't watch movies without stuff stopping either. To be quite honest, downloading files from the internet goes faster than my lan transfer speed does. I too would like to solve this problem. A little while ago I read an older article about how to switch the iwl driver back to the ipl for hardy. Some of the symptoms they were listing about the iwl driver seemed a bit extreme but as I said it was an older article (as in shortly after hardy's release). The driver seems to have improved, but these problems still exist to some degree.
[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html")
Hopefully someone else has a better solution??

---

### Post by cariboo on 2008-08-10
Samba under hardy doesn't seem to transfer files very fast, If your server is linux based I would suggest using NFS there is a howto located here:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Leave your samba setup as it is so you can still access the server from windows and setup nfs. BTW I use a web bowser to watch movies located on my server, and I can stream to all three of the computers located in my den, including my HP laptop on wireless, at the same time, with no stoppage or stuttering. The server is just an old 1GHz AMD64 with 512MB ram that I inherited from a former employer.

Jim

---

