---
title: "Bittorrent blocked"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2007-10-10
I am having problems successfully using bittorrent on my Fiesty UB. I have firestarter installed and a NAT firewall in my adsl router. This is a picture of the setup. Can anyone comment on what is wrong:

[[img]http://img3.freeimagehosting.net/uploads/th.01fe687f3b.png[/img]](http://img3.freeimagehosting.net/image.php?01fe687f3b.png)

Robin

---

### Post by Robbyx on 2007-10-11
Please could someone reply. The image above is clickable so that the full screen becomes clear.

R

---

### Post by Boomy on 2007-10-11
You might need to open udp 4444. I'm pretty sure you need to forward those ports to your host's IP as well.

---

### Post by Robbyx on 2007-10-12
> **Boomy said:**
> You might need to open udp 4444. I'm pretty sure you need to forward those ports to your host's IP as well.

Could you please explain further. Are you advising that I open a new range of ports in the router ie 4444 and in firestarter. Is it an incoming or outgoing range. I am also unclear as to what you mean by "forward to your host's IP". 

I am actually trying to use Bittorrent as a means of transferring a private large file to another company. The advice was in:

[http://www.poromenos.org/tutorials/bittorrent](http://www.poromenos.org/tutorials/bittorrent)

I failed to make it work in Ub, so I thought the first step would be to set up BT and see if it would download a publically available file in a public tracker. So far I have not succeeded with that first step. Your reference to host's IP  holds out hope that the  advice I receive here  will eventually enable me to use   BT to transfer a  file using a private tracker file sent to the other company, as per the tutorial in the url  above.

Robin

---

### Post by Boomy on 2007-10-12
Try clicking "assign a game or application to a local network device" in the control panel. Right now your ports 6881-6889 are open and translated to the same ports on your private network, but they are not forwarded to your pc, so when they are triggered, the router just discards the data. The ports need to be forwarded to your computer via the router.  I'm not sure if 4444 needs to be opened or forwarded, but it's worth a try.

Forwarding basically means that any data recieved on the forwarded port is sent directly to the ip you select for forwarding.  For example if you forward port 20 to ip 192.168.1.10, any traffic going to your router on port 20 gets directed to the pc with the ip 192.168.1.10. If that port was not forwarded, any data on port 20 that was not destined for the mac address of the machine with ip 192.168.1.10 would be discarded.

---

### Post by Robbyx on 2007-10-14
In my current set up I have removed the Bittorrent standard connections and made a high port access. The port range is 53000-53000 and that is translated to the same range. However  I have also asigned the application to robin-desktop. This is my ethernet port and it has a static Ip address assignment  with an ip address of 192.168.1.201. When I wish to access my modem's set up page I go to 192.168.1.254 so it looks as if I have assigned the incoming trafic t to my machine. 

Not withstanding the above BT does not work.

Robin

---

