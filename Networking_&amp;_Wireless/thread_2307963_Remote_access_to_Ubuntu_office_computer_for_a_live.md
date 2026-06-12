---
title: "Remote access to Ubuntu office computer for a live session, from a laptop"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by flucoe2 on 2015-12-29
Hi,

I need to have access to the computer that I have in my office as it is pretty powerful and I can run some stuff there that I can't in my laptop. For example, I want to run some simulations in R that because of the amount of memory, I can't run in my laptop. My idea was to set up remote access and connect to the computer. However, I'll need to do this in some "live session" manner, meaning that I'll need to remotely open R, Matlab, etc, and run any files I need to run in that live session. So, a couple of questions. First, how should I set this up? Second, does it matter if the laptop is running Ubuntu or OSX? If so, how should I proceed for each case?

Thanks,

---

### Post by TheFu on 2015-12-30
Can't help with OSX. Sorry.

If the commands can be run from a terminal, use ssh. This is really easy to setup and millions of ssh connections criss-cross the world right now. ssh is how Unix/Linux admins work and manage remote systems. Install the **openssh** package on the client and openssh-server on the server.  There are at least 1000 how-to setup ssh articles on the web. Firewalls, routers, port forwarding are likely needed, depends on your situation. Also, on the "server", please install a brute-force attack protection tool like **fail2ban**. If the ssh-server is configured with defaults, then fail2ban defaults automatically protect you, but it must be installed.

Last time I checked Apple called ssh something else, but it is built-in. Hate it when companies "brand" common tools. Seems like they want to keep their users uninformed of interoperability options.

If you need a remote GUI, there are some limitations you need to know.  Any GUI that needs an accelerated GPU (2D or 3D graphics) won't work. That means Unity doesn't work or if it does, it works poorly.  Use a lighter GUI - something like LXDE or XFCE for the remote connections. VNC is popular, but doesn't properly secure the network traffic, so it is easier for most people to use the NX protocol, which uses ssh. 
After you get ssh working as described above, nothing more needs to be done to open firewalls, forward ports, or routers. NX uses the same ssh as regular ssh.  Which NX protocol tool should you use? Cannot say. I've used freenx and x2go.  x2go has a pretty, integrated, interface and it is very stable. NX is about 2-3x faster than VNC or RDP, so there really isn't any question.  The x2go website has install instructions. You need/want to use their PPA. There is a server and a client. The x2go client for Ubuntu and Windows is very solid. I would expect the OSX client is as well, but don't know.  Web search for "x2go install" to find instruction.

ssh is the swiss-army-knife for system-to-system connectivity for everyone except Microsoft.  For over-the-internet connections, be certain to use key-based authentication, never passwords.   [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

### Post by flucoe2 on 2016-01-01
Thanks! I'll start working on this. I think I can do most things without a GUI so I'll just focus on ssh for now.

---

### Post by flucoe2 on 2016-01-05
I was able to set everything to get ssh working, with fail2ban and ufw allowing a single IP, from within the network at my office. Then, when trying at home, things didn't work.

I first connected to my office via vpn. I was able to turn on the desktop from my house (I realized it had worked once I got to the office today) and 'ping' the desktop. However, I couldn't ssh to it. I thought it would be a matter of IP changing, and yes, the IP according to whatismyip.com has nothing to do with the one that I specified as an exception in ufw. However, the one I used on ufw was what ifconfig labels as "inet addr:", and that remains to be the same this morning when I was able to connect from within the network at my office. I checked two more times in an interval of 3 hours and the IP address reported by whatismyip changed in both cases. 

So, I'm able to connect from within the network and I'm also able to turn on the desktop from my house once I connect via vpn to the office.  However, I can't ssh in. I don't know if it is a matter of IP or not (even though the seems to change, but it could be something else too). How should I fix this? Or at least get a complete diagnosis before trying to make it work? I know I could get rid of the exception as I need to be within the network via vpn to connect. However, I would like to keep this exception to only allow my laptop to ssh in.

Thanks.

---

### Post by TheFu on 2016-01-09
The best way I know to figure out this stuff is to draw a diagram and label all the IPs and ports for each of the devices in the chain.  Private LAN addresses aren't useful except for the port forwarding at the edge router protecting the LAN from the big-bad-internet (unless you are tunneling that connection thru a VPN).  If the WAN IP is jumping around on the "server-side", you'll want a dynamic DNS service (there are free ones) that the router updates whenever the WAN IP changes. no-ip is popular and I used dyndns back in the day before I got some static IPs for home. If your workstation at work has a dynamic IP, you'll need to get a static IP from the network guys for it. Without that, this will be much too hard, though not impossible.

Anyway - draw the diagram, label all the parts, ensure the router ports are open and forwarding to the internal IPs (usually on private subnets) correctly.  If it is possible, setting up ssh at home for connections from cafes around the world is pretty easy. Usually the main limitation is a lack of network understanding. I recall way back in the mid-90s when my understanding was weak and I couldn't get ssh working. This is common.  I drew a diagram, took it into to work and asked for help. They quickly pointed out that I didn't correctly setup port forwarding on my router and hadn't setup a static IP for the internal ssh-server machine, so it would be very hard for any of this to work. Setting up ssh is easier for me today than setting up **any** other service. The only difficulty is whether that traffic will be blocked from where ever I am.  Usually, I have to switch the ssh port to be 443 (luckily I have a few static IPs), to get passed corporate proxies. Some hotels block outbound ssh as well, but by using port 443 and their proxy, I was able to get traffic through.  If they require a CA loaded from the company for SSL traffic to work, then ssh won't work, since they won't be able to look inside the packets and decide how safe the traffic is.  When it comes to encrypted connections, I don't trust any where a public CA is used.

Back to ssh ... with fail2ban installed and working, I don't bother with specific firewall rules to limit ssh access. That's what fail2ban handles.

Also - if you are using passwords for ssh authentication, you've already lost the security battle. Setup ssh-keys and disable password-based authentication for anyone outside the LAN. Many how-tos for this.

Draw the diagram.

---

### Post by flucoe2 on 2016-01-09
That's great, thanks!

---

