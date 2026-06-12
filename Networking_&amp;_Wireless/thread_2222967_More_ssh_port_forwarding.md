---
title: "More ssh port forwarding"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by HeartBT on 2014-05-08
Thanks for reading.

I have pulled hair trying to solve this.  I'm pretty linux savvy, but networking; not-so-much.
I've had the home network set up for years, and as old as it is, it's working and I really don't want to upgrade hardware until I can start yanking wires and doing it proper: again.(waiting for IPV6 rollout to go equipment shopping).  My office is setup recently, newer equipment, and a lovely high speed line.

I would like to have the transmission-daemon running on my home media pc, and use the work router as a proxy, or similar.  Yes, I understand it's slower there, etc. Thing is, sometimes I don't go to the office for a week or two and work from home, and I'm fine with the slower speeds transmission gets over the wisp since my QOS moves it out of the way as needed.  What I hate is not being able to connect to but a small amount of peers, and seeding to 100%? yeah. not often, and leads to bad JuJu. (Due to the double NAT)

What do I need to do to create a route or tunnel, or whatever to make this work?  I've spend 2 days playing with ssh port forwarding and think I've only gotten older. 
what I have:
|---------------------------------100MB---------------| 1.5 MB     |-------------------------------| 1GB-------->
<-----------------Home--------------------------------| isp equip. | -----------inet----------------| office lan ---------------->
xbmcbuntu running transmission --> (old)ddwrt router--->  WISP AP-------->the great beyond---------> (new, nice)DD-wrt router ----> all my personal/work PCs, etc.

What I want: (preferably)
xbmcbuntu running transmission--->(old) ddwrt router======================================>(new, nice)DD-wrt router------> inet
or
xbmcbuntu running transmission=======================================================>(new, nice)DD-wrt router------> inet

Oh, and ISP assistance = 0. They will not open ports, put the AP in bridge mode, nadda.  Not helpful.
Advice, options, or even (gasp) opinions are welcome.

---

### Post by Lars Noodén on 2014-05-09
Looking at Transmission's settings, it appears to not support any proxying.  It would be more efficient to run Transmission from your office net anyway, if that is possible.  You can still access it remotely.

Other alternatives include setting up either OpenVPN or using SSH as a VPN.  That would route all your traffic through your office including your Transmission traffic.

---

### Post by redrumrogue on 2014-05-09
Deluge supports SOCKS 5 proxy (with Authentication).  You could use that on your xbmcbuntu (although i've never tried installing it on xbmcbuntu).  I use Deluge on my Ubuntu box at home and have it pointed at a BtGuard ([https://btguard.com/](https://btguard.com/)) annonymous proxy service which is a SOCKS5 proxy.  If you want to create an SSH tunnel to your office you'll need a device there running an SSH server, and that would have to be accessable from the internet.  You would need to setup port forwarding in your office gateway router to forward your SSH port (default port 22) to the SSH server within the office network.  I would highly recommend setting up public key authentication between the SSH client and SSH server.  Once you have client and server setup you can SSH from xbmcbuntu to SSHServer like this:

**ssh <user>@<hostname>**

<hostname> would be the external IP address of the office gateway router, or the external hostname if you have one.  I use No-Ip ([http://www.noip.com/](http://www.noip.com/)) for a free hostname to access my ubuntu machine at home.

If you setup your SSH server to use a non-standard port then your ssh command would be:

**ssh -p <ssh port> <user>@<hostname>**

If you can connect to the SSH server in this way then you either use it as a SOCKS 5 proxy server itself with this command:

**ssh -p <ssh port> -D <proxy port> <user>@<hostname>**

<proxy port> can be any port number you like above 1025 (or there abouts).  Then you would configure your torrent client to connect to SOCKS 5 proxy server at **localhost:<proxy port>**

If you have an HTTP proxy server in your office network then you can connect to it like this:

**ssh -p <ssh port> -L <local proxy port>:<ip address of HTTP proxy server>:<HTTP proxy server port> <user>@<hostname>**

<local proxy port> can be any port number you like above 1025 (or there abouts).  Then you would configure your torrent client to connect to the HTTP proxy server at **localhost:<local proxy port>**

Hope this all makes sense!  I've spent FAR too much time researching this stuff ... 

Cheers,
JB

---

### Post by HeartBT on 2014-05-09
Thanks for the response.
Lars Noodén : I would consider running transmission on the office net, IF the torrents could be stored at home, .part and all.  Reasons: any copy of completed torrents would have a huge long transfer time, and not be so friendly to data shaping (QOS). It would also require 2x the storage space, at least temporarily.  This would also suck if I needed a reboot and were unable to ssh.  AND although I know it's possible, I have no idea how, or the implications of, remote mounting of drives.  
I will look at open VPN, and have attempted ssh as vpn, but I'm missing something. I have set up keys, and started a tunnel with ran on home router:
```
ssh -nNT -R 15000:IPo'MediaPC:15000 user@IPo'WorkRrouter -p xxxx    #(mostly manpage and guessing to get there)
```
But this does nothing no matter how I configure transmission.  I would be fine with sending all traffic from xbmcbuntu through the tunnel, but not any other.

---

### Post by HeartBT on 2014-05-09
Yes, that is what I was thinking of how it would work!!  So, what I did wrong above was set the tunnel from home router to work router, where I need to run it MediaPC to work router...  got it!

Transmission apparently does NOT support proxy in itself(removed ~2 versions ago. OT, but lets make our software LESS functional??), so I will have to route all MediaPC(xbmcbuntu) traffic through the work router, am I right? BTW, I'm rather committed to transmission as I have gobs of input and output scripting for it and I really don't want to redo any of that at this time.

So, my new tunnel ran from MediaPC is:
```
ssh -p <WorkRouterSshPort> -D <proxy port> <user>@<IPo'WorkRouter>
```

I will give that a stab when the desk clears.  

Thanks tons!

---

### Post by redrumrogue on 2014-05-09
Not sure that would work as you've got it, unless your work router has it's own ssh server running?

Wouldn't it be more like this:

xbmcbuntu ==========> gateway router (which forwards ssh port) ==========> internal machine running ssh server -------->  back out to internet.

I use this setup all the time for routing all web browser traffic from my laptop via my ubuntu machine at home.

---

### Post by HeartBT on 2014-05-09
yes, work router is DD-WRT v24-sp2 std Release: 04/18/14 (SVN revision: 23919). It has server up and running.  This server has a weird issue with randomly spitting out ```
ssh_exchange_identification: read: Connection reset by peer
``` but it's apparently a dd-wrt issue, and (at least I think) not related.  

I executed ```
ssh <IPo'WorkRouter> -p 18232 -D 44000
```

and am now working on setting xbmcbuntu to proxy localhost:44000

Still on the right track?

---

### Post by redrumrogue on 2014-05-09
Ok cool - I'm not familiar at all with the type of router you've got by the sounds of it.  I only tinker with my own home router.  Sounds like you're on the right track anyway.  Looks like you're stuck routing all traffic through system proxy.

---

### Post by HeartBT on 2014-05-09
Maybe... I'm not sure this will work.  I just realized that if all traffic went through the tunnel, my remotes (ip) and transmission RPC will also.. maybe not a big deal, but I cannot test.  Stupid router is not allowing connections often enough to test effectively..

Thanks for the help!

---

### Post by HeartBT on 2014-05-10
UPDATE: I've abandoned this for the time being.  Thank you redrumrogue you have been a great help. The tunneling commands above worked, and I finally got DD-wrt to accept ssh connections (ssh_config had no options set by default).  So I will mark this solved in that regard.  However, I have run into the limitations of transmission.  See 
[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCsQFjAA&url=https%3A%2F%2Ftrac.transmissionbt.com%2Fticket%2F3817&ei=vkluU5vCOc-YyASG5ILIDQ&usg=AFQjCNFY-gov8dKp2eNmeFWGD2pZ7gBZCA&sig2=oF834aHh8O9X0NDJuoL2eg&bvm=bv.66330100,d.aWw]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCsQFjAA&url=https%3A%2F%2Ftrac.transmissionbt.com%2Fticket%2F3817&ei=vkluU5vCOc-YyASG5ILIDQ&usg=AFQjCNFY-gov8dKp2eNmeFWGD2pZ7gBZCA&sig2=oF834aHh8O9X0NDJuoL2eg&bvm=bv.66330100,d.aWw") where some fishstick decided to remove proxy support instead of improving or fixing it 3 YEARS AGO. (I've never used a spare tire (proxy) so lets get rid of it, duh.)</EndRant>

So, it would appear that I'm looking for another torrent client and re-scripting A LOT, or moving to deluge, or something.

Thanks you guys for help.

---

