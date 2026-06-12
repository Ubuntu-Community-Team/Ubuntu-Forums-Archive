---
title: "No access via internet?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by ThomThom on 2008-06-17
I'm running Ubuntu 8.04 on an old Epia SP 13000 which I plan to use as a file server.

I tried to connect to Remote Desktop via the internet, but I just get error messages saying UltraVNC/TightVNC can't connect to server.

When I connect using local IP it works perfectly. But it's the internet access I can't seem to get working.

I've forwarded the port I use for Remote Desktop to the Ubuntu machine. [http://www.canyouseeme.org/](http://www.canyouseeme.org/) says that it can see my service on the port I've set up.

I also have the same problem with Twonky. I can access the web interface via local IP, but not when I use my public IP address.

Again, I've forwarded the port that Twonky uses.

Is there some configuration I  have to do in Ubuntu?

It's a pretty fresh installation of Ubuntu. And I'm coming from years and years of Windows use. I'm not very familiar with Linux.

---

### Post by superprash2003 on 2008-06-17
are you able to ping your computer ip from the internet? do you have firestarter or anything similar installed?

---

### Post by ThomThom on 2008-06-18
Yes, I can ping my IP.

I didn't have Firestarter installed initially. But I did eventually as I thought it was a GUI for Ubuntu built-in firewall. When I launched Firestarter and it asked me to set up a firewall I just cancelled it. 
I'm still confused whether Ubuntu comes pre-installed / pre-setup with a firewall or not.

---

### Post by superprash2003 on 2008-06-18
yes it does.. iptables.. does your port respond to this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by ThomThom on 2008-06-18
> **superprash2003 said:**
> yes it does.. iptables.. does your port respond to this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

Yes. For the port I set Remote Desktop it use it says:
*<IP-ADDRESS> is responding on port 6000 (x11).*
(Does Remote Desktop use any ports other than the one set up in the config window?)


For the TCP port Twonky uses it says:
*<IP-ADDRESS> is responding on port 9000 (cslistener).*

However, for the UDP ports that Twonky uses (1030, 1900 and 9080):
[I]<IP-ADDRESS> isn't responding on port 1030 (iad1).
<IP-ADDRESS> isn't responding on port 1900 (ssdp).
<IP-ADDRESS> isn't responding on port 9080 (glrpc).[/I]


Is there a visual config for iptables? I'm used to typing commands from the days of DOS, but I prefer visual aids.

---

### Post by superprash2003 on 2008-06-18
firestarter..
  did you set remote desktop to listen to port 6000?? 5900 is the default port.

---

### Post by ThomThom on 2008-06-19
> **superprash2003 said:**
> firestarter..
  did you set remote desktop to listen to port 6000?? 5900 is the default port.

Yes, since I had problems initially I tried some other ports for the take of testing.


Are you saying that Firestarted is a frontend for iptables?

---

### Post by superprash2003 on 2008-06-19
Yes

---

