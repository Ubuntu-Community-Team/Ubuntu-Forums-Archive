---
title: "[SOLVED] ssh/port forward/ static ip problem"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by mangoes on 2008-03-12
Hi all, I'm a noob and have a ubuntu gutsy 64 box and internet connection with dynamic ip.

This is the problem : I've done what I think all the right steps to make this box open to outside through ssh, but no joy so something must be mising.

THIS is what I've done:

1. Make double sure my ISP does not block port 22 (They don't).
--------------------------
2. Set up dynamic DNS

- Get a host name with dyndns 
- Install and configure ddclient
- Put dydns account detail in my netgear-wgt624v3 router
- Test if ddclient updates properly by
(i) ddclient -daemon=0 -verbose -noquiet -debug
(ii)get the router to also test the update (there's a 'test' button)
- Result : 
-Router and ddclient tests show the update is going normally.
- checking my ip address with [dyndns CheckIP serve]("http://checkip.dyndns.com:8245/")r yields and external IP address.
-------------------------
3. Get a static IP for my box by

(i) Assigning it through the router:
static ip 192.168.1.4
router ip 192.168.1.0
subnet mask 255.255.255.0
change the dhcp ip range to( 192.168.1.5 until 192.168.1.254)

(ii) do this in /etc/network/interfaces (I'm not on my box now so this is how I remembered it, but it's
based on this [howto]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")
=========
remove this : iface eth0 inet dhcp
append this:
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1 
network 192.168.1.0 # don't think this is necessary
broadcast 192.168.1.254 # don't think this is necessary
===========
-------------------
4. Forward port 22 through my router
service: SSH1
ip: 192.168.1.4
------------------
5. Restart the network by
sudo /etc/init.d/networking restart

THESE are the results:

- I could ssh into the box from a computer within my network, but ssh from outside the network returns
ssh: connect to my.dydns.host port 22: No route to host 
- Testing port 22 on this address, using [dyndns open port tool]("http://www.dyndns.com/support/tools/openport.html"), yields "Connection timed out" which suggests the port is blocked by
firewall, router or ISP.

CONCLUSION:
- Assuming my ISP was right in saying that they don't block port 22, and knowing that I don't have firewall installed in gutsy yet, the problem
is most likely in my router/port forward setup. 

Any help will be most appreciated. I need to go away next week and be able to ssh occasionally to my box to see if those fortran codes are still running!

THANKS!!
ps:  there are two lines in /etc/network/interface about something like  lo and loopback,  I can't remember exactly, but I left them there because no clue what they're for.  However typing  ifconfig  yields information on eth0 and lo.

---

### Post by TwoWordz on 2008-03-12
Hi, 

log on to dyndns, look at your host. Is the IP address right? Can you access your box using the IP on the site?

TW

---

### Post by jcwmoore on 2008-03-12
> **mangoes said:**
> 
CONCLUSION:
- Assuming my ISP was right in saying that they don't block port 22, and knowing that I don't have firewall installed in gutsy yet, the problem
is most likely in my router/port forward setup. 


agree, something with your router, OR your IP address could have change.  Not very likely, i know but you did say you have a dynamic ip address, and from my experience it can change while you are using it...

---

### Post by lnxr00t on 2008-03-13
to make sure you have the router set correctly check out [http://portforward.com](http://portforward.com).

Also I am not too familiar with dyn DNS but make sure you can use the hostname to tunnel to port 22 at your specific IP 

Ive setup remote SSH just by using my actual IP address, for security I just changed the port that SSH listens on in the sshd config file.

heres some usefull links that helped me out ...

[http://www.zunta.org/blog/archives/2005/08/29/sshirking_work/](http://www.zunta.org/blog/archives/2005/08/29/sshirking_work/)  <---- creating a SSH tunnel & proxy

[http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)  <--- basic ssh stuff

[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)  <--- VNC over SSH

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)   <----  Putty (for access from Windoze)

---

### Post by mangoes on 2008-03-13
> **TwoWordz said:**
> Hi, 

log on to dyndns, look at your host. Is the IP address right? Can you access your box using the IP on the site?

TW

Yes I checked them and they matched.  I ssh from my laptop within my network using the ip on the site.
Thanks

---

### Post by Iowan on 2008-03-13
Hopefully, my information is out of date... Thought I read that SSH-server wouldn't work with dynamic IP address.

---

### Post by mangoes on 2008-03-13
> **Iowan said:**
> Hopefully, my information is out of date... Thought I read that SSH-server wouldn't work with dynamic IP address.
Hmm if this is true I'll be positively wretched. Will find out.
Thanks.

---

### Post by Iowan on 2008-03-15
I'm still trying to find where I got the info - here's another interesting tidbit I learned from the sshd_config **man** page:>  **HostKey**...Note that sshd will refuse to use a file if it is group/world-accessible.
[This article]("http://os.vault9.net/forums/lofiversion/index.php/t19479.html") suggests folks are using sshd with dynamic IP.
[Another link]("http://whirlpool.net.au/forum-replies-archive.cfm/936868.html") that might be helpful.

---

### Post by mangoes on 2008-03-17
OK I've solved the problem.
It was the modem not forwarding the port to the router.

However my modem was very temperamental. So in the end I just got a modem/router. Worked like a charm.

If you are in the same situation, this [portforward.com link]("http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841") may be useful.

Thanks everyone!

---

