---
title: "How to remote access from Outside the LAN"
date: 2019-09-20
forum: Networking &amp; Wireless
---

### Post by webmiester on 2019-09-20
Hi everyone,

Ive been experimenting with remote access.  Aside from the obvious team viewer and anydesk, there are other alternatives such as nomachine, VNC viewer, etc...

Doing this over LAN is easy.  Just put the IP address of the computer we want to control in the viewer PC and viola!  It works.  However, when we want to access the computer from outside the LAN, I am confused.

The instructions on sites such as Nomachine says just put in the IP of the machine...  some of the VNC viewers say the same thing too. However, my computer's IP is merely the result of what my DHCP server tells it. It is a local IP address and many other computers around the world might have the same local IP.

So I used google to look up "what is my IP", and I get some sort of global IP... However, the computer beside mine also has the same global IP result when I look it up there.  And this IP also doesnt work.

So what value should I put so that remote access can work for a computer through the internet?  Thank you.

---

### Post by CatKiller on 2019-09-20
[https://portforward.com/](https://portforward.com/)

---

### Post by Skaperen on 2019-09-20
if your computer gets a "private" IP address like 192.168.X.X or 172.12-31.X.X or 10.X.X.X then this can be difficult but not impossible.  the way it would be done in this case is the configure your firewall or border router to translate a public address to the private address.  if your computer has a public IP address, then it should be ready to go.  can you describe your network in more detail?

*edit*:

well there.  CatKiller has provided a link.

---

### Post by fragglebliss on 2019-09-21
You kind of answered your own question in your original post. ie. TeamViewer.

---

### Post by TheFu on 2019-09-21
Warning.  Lots of opinions follow.

Remote access needs to be secured at the network layer. That means both authentication AND encryption.  For the network authentication, if passwords are used, then we've already lost.  Encryption should be handled by tools that are known to be trustworthy and actively maintained - ssh, openvpn, IPSec.  Of someone claims they don't need one of those, they are selling snake oil. Run away.

I'd never trust teamviewer and any other similar service.  It just isn't necessary. Why would you want someone at a 3rd party to have access to your internal LAN?  

Use **ssh**.  As a "webmiester", that should be the main tool of choice for any needed remote management of any Unix-like system.  The internal IP really needs to be static for port forwarding/translation to be used. Modifying the IP that the router uses all the time to track down some changing DHCP IP is not useful time.

[https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)  is mostly for home users.  Inside an enterprise, I'd only do that for desktops.  Servers need to have static IPs, manually setup, always.  There are different opinions about that, but if you have a dead DHCP server and have to reboot any other server, life sucks.
If you have more than a few machines, then you'll want to use an ssh "jump server" for external connection into the LAN, then just from that machine to the machine you need to access.  A full VPN setup, like provided by openvpn can do this as well.  
If you use ssh, then each internal machine needs to be connected through a different port on the WAN IP (assuming there is only 1 WAN IP).  Modern routers support port translation.  This is a good way to drastically reduce the logs that attacks from the outside world will cause. For ssh:   
```
Internet -->  WAN IP:Port/tcp --> LAN IP:Port/tcp  --> ServerIP:Port/tcp
```
So an exact example would be:
```
Internet -->  ra.example.com:**63022**/tcp  --> 10.1.1.1:22/tcp  --> 10.1.2.**99**:**22**/tcp
```
The router takes DNS+port and translates it into a LAN connection on 10.1.2.99:22/tcp. Inside, the default ssh port is used. From outside, a non-standard port is used.  If there is another internal server you want to access using ssh, then setup port forwarding/translation like this:
```
Internet -->  ra.example.com:**63024**/tcp  --> 10.1.1.1:22/tcp  --> 10.1.2.**98**:22/tcp
```

There are all sorts of security reasons that VNC and RDP tools shouldn't be enabled.  VNC has a -localhost option, which prevents any remote access, thus effectively requiring that an ssh tunnel be configured from the client machine to the VNC server machine before the VNC connection is allowed.  But this is beyond most non-admin people to configure.  Plus x2go (NX protocol) uses ssh for network authentication and feels 2-3x faster than any VNC or any linux-based RDP, so why not just use x2go?

---

### Post by webmiester on 2019-09-21
Hi thefu, I actually tried x2go.  I installed it.  The viewer side is asking me to put an IP address.  If the viewer is within the LAN it is as easy an entering the local IP address, but through the internet, I can't figure out what IP to put in.  Hence, this thread.

I like the term "jump server", its basically the setup that I'm doing.

Ok...  Someone mentioned that there will be lots of opinions, and I'm glad cause there is more than one way of doing this.

First of is port forwarding, with x2go, do I still need to turn on port forwarding? I have the impression that opening port forwarding can make my system more vulnerable to hackers.  So if I can keep this off, I would.

Next, you sent these codes:
Internet -->  ra.example.com:63024/tcp  --> 10.1.1.1:22/tcp  --> 10.1.2.98:22/tcp

Where do I write or find these codes?  Are they on a file on the jump server?

Then lastly, where do I get the values that you have in the code?  The "ra.example.com".  Where does it come from?  Will this work even if I don't have a DNS server giving my server  local DNS name yet?

Thanks so much

---

### Post by webmiester on 2019-09-21
> **fragglebliss said:**
> You kind of answered your own question in your original post. ie. TeamViewer.

I'm looking for something without 3rd party subscription.

---

### Post by webmiester on 2019-09-21
> **Skaperen said:**
> if your computer gets a "private" IP address like 192.168.X.X or 172.12-31.X.X or 10.X.X.X then this can be difficult but not impossible.  the way it would be done in this case is the configure your firewall or border router to translate a public address to the private address.  if your computer has a public IP address, then it should be ready to go.  can you describe your network in more detail?

*edit*:

well there.  CatKiller has provided a link.

What I meant by "private IP" is that it is the IP given to my computer by my router or dhcp server.  Our connection has 1 static IP provided by the ISP, then the ISP's router provides the IP to another router which everyone connects to and it gives a different IP to everyone else.

Come to think of it, I don't think I have access to the settings of the ISP's router.  They so far havent allowed us to touch it.

---

### Post by TheFu on 2019-09-22
x2go uses only ssh ports.  There are thousands of how-to guides on the internet for explaining how to setup ssh access from the internet to a LAN.  
If your networking knowledge is lacking, search for episodes 25-27 of Security Now! podcast.  These are "how the internet works" episodes and should fill in any knowledge gaps sufficiently.  There are audio and transcribed versions available.
Securing ssh is a well-worn path.  There are many different methods.  [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) is one.  The main methods are:
* use a non-standard port for WAN ssh connections
* never use passwords - don't even allow them for ssh authentication
* limit which IPs can attempt to connect via ssh using highly restrictive firewall rules
* if any remote IP tries to connect to ssh and fails more than 3 times, block that IP for a week, automatically.

---

