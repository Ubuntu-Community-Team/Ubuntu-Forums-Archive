---
title: "[SOLVED] Ubuntu Network (Daisy-chaining networked devices) help"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by sj01 on 2008-11-25
Hi. I'm trying to set up a file server box, with two NICs, and I would like to know if there is a way to have one of the NICs connected to my home's network, with the other NIC connected to a nearby computer, causing the file-server to act as a network switch/hub. I am assuming the hardware set up would kind of look similar to daisy-chained power bars. I would like the PC connected to the file server to be available on the network as any other computer would be, with the router (not the file server) assigning a separate IP address to each machine.

The network layout I am trying to acheive looks something like this:
Internet -> Linksys Router -> D-Link Switch/Hub -> File Server -> PC where the file server acts similarly to the D-Link switch.

I have no idea where to start, so any help would be appreciated.

By the way, the file server is running Ubuntu Intrepid Server, so no GUI tools are available (CLI is all I need).

Thanks,
Stephen

---

### Post by SpaceTeddy on 2008-11-26
you want to bridge your network cards together. There was a similiar thread a few days back where i posted how to do it... found it... [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=992250")

you want to do the same thing... bridge your network cards together and then configure the br0 device as the network card of your fileserver - this ip will apply to both network cards. If you have no firewall software installed nothing else is needed, as the standard here would be to let anything bounce of the computer...

if you need more specific instructions, please tell me the ip's all computers involved (if they have multiple i need to know the ip of each network card) and on the fileserver the names of the network cards... 

hope it helps :)

---

### Post by sj01 on 2008-11-26
Thanks for your help. It worked. I would have searched for the answer myself, but I could not remember the networking term that meant what I was trying to do: bridging. Either way, both of my computers now have a connection to the network. Thanks.

---

