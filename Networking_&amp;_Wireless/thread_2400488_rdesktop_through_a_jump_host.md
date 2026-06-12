---
title: "rdesktop through a jump host?"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by 1clue on 2018-09-06
Hi,

I have a situation. I have a Mac which has a VPN client on my desktop. I have an Ubuntu 18.04 box sitting right next to it. Ubuntu is my primary workstation, and the mac is circa 2011 so it's old. I can and do regularly ssh from Ubuntu to Mac, and then ssh to a host on the remote system through the Mac's VPN client. It works great.

What I want to do is initiate rdesktop from the Ubuntu box and then use the Mac as an intermediate gateway, not using a remote desktop client from the mac. The reasons are as follows:
[LIST=1]
[*]The mac remote desktop client sucks.
[*]My main workstation is the Ubuntu box.
[*]I use Dvorak keyboard layout locally, which is not allowed at the remote site. Linux's rdesktop does the translation locally, but the Mac forces the keys to match what the remote Windows system has.
[/LIST]

So what I'm asking is, does somebody know a way to use netcat or some other intermediate command with rdesktop to do this?

Thanks.

---

### Post by TheFu on 2018-09-06
ssh can do that.  [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)
Look at the jumping through servers example.

---

### Post by 1clue on 2018-09-06
Yes, as I said I'm doing ssh that way already. What I want to do is rdesktop through the proxy, using the rdesktop from the user workstation rather than one on the intermediate proxy.

---

### Post by 1clue on 2018-09-06
OK I got it though.

```

linux% ssh -L 13389:<remote windows ip address>:3389 mac-proxy
linux% rdesktop localhost:13389

```

Your link actually helped, just had to work it through. Thanks.

---

### Post by TheFu on 2018-09-06
> **1clue said:**
> Yes, as I said I'm doing ssh that way already. What I want to do is rdesktop through the proxy, using the rdesktop from the user workstation rather than one on the intermediate proxy.

Perhaps I misunderstand.  You want to ssh through 1 server to another, then ssh into another.  Through both those ssh tunnels, you want rdp through both, right?  That's what the example ssh link shows.... just without the rdp port forward pre-configured the client-side ~/.ssh/config file.

The VPN is incidental, but required (I assume) for the 2nd ssh to work at all.

Or did I misunderstand?

I don't have the same config here to test until Sunday and then I'd use 
```
laptop --NX--> desktop (x2go) --rdp--> Win7
```
This works all the time. My Win7 doesn't support ssh.

I'm also positive that 
```
laptop --rdp via ssh tunnel--> desktop (ssh) --rdp--> Win7
```
works, but NX is 2-3x faster than RDP so even when running a remote desktop within a remote desktop, it is faster than using RDP from the client I'm on into an ssh LAN host.

Clear as mud?

If you post specific IPs and OSes (versions too), I can probably make the ssh commands you need.

---

### Post by TheFu on 2018-09-06
Didn't see the other post.  

People under estimate ssh all the time, including me. ;)
I've had to use reverse ssh connections a few times to get things working when I couldn't open any ports on the router where I was. 

The ~/.ssh/config file and automatically make the tunnel you want with a simple alias - something like "ssh rdp" command.  You probably know this and just want to get everything working in a shell before making it easy.

---

### Post by 1clue on 2018-09-06
There are only 3 hosts. Linux(workstation), Mac(gateway) and Windows(remote host).

I knew about the netcat mode of ssh, but I didn't know it would drop standard packets off at the other end without an ssh running on the remote host.

As far as getting it into a config file, I have literally dozens of VPNs I need to connect to, each with several hosts. Most of the remote administrators will not even talk to you if you mention Linux. So I need to use a Mac or a Windows client for the vpn. Generally speaking only one VPN can be connected at a time or we get bizarre networking issues. IMO that's a sign of their VPN not being configured correctly, but in any case it's a one-at-a-time deal.

So there are lots of hoops to jump through to connect, and sometimes it involves booting an antique box with Mac OS or Windows on it, logging into the VPN on that system and then connecting to the appropriate system. If it's a mac I can now use my nice dual monitor setup and an rdesktop client that works the way I like, which is a step in the right direction.

At some point I may make an attempt to get this working with a Windows gateway.

---

### Post by TheFu on 2018-09-06
I understand completely. 

Where I've worked we didn't allow split tunnels, so your Mac wouldn't allow connections from any local clients with our VPN.  You wouldn't be able to network print locally, except with a directly connected printer. 

There are ways around most setups, but not all.  We even had CAs on each client and MiTM'd all https traffic going outbound.  The company was clear - anything on our network is our business. If you want privacy, don't do it on our network, our phones, or our computers. It was a regulated industry, so all this monitoring wasn't just for fun.  Before they put the CA and MiTM infrastructure in place which would dynamically create HTTPS certs as needed per client, it was possible to do ssh over the HTTPS proxy.  Desktops couldn't get to the internet, not even public DNS, without using a corporate proxy server. But the new systems can recognize the difference between HTTPS and all other SSL traffic.  If  the traffic can't be MiTM'd, then it is invalid and blocked.

---

### Post by 1clue on 2018-09-06
That actually makes a lot of sense security-wise. What's odd to me is that most of the admins I've talked to at the remote sites don't seem to mind local networking or even this netcat bit I'm doing. Years back it was actually one of those admins who suggested it to me first.

Back when I worked at IBM they were much more like the scenario you describe, although that was 20+ years ago and the world was different then. I'm sure the details are much more specific now. The line was no personal hardware on-site, and almost always no company hardware off-site. There were exceptions to that. But again it was all completely monitored and people were actually watching. I got called out for it. They had a top 10 bandwidth abusers list every day, and it wasn't just for through the firewall. I was working on a website on an internal (in my lab) server, and since I had a pretty much antique desktop running Linux and the website was on AIX, I had the browser running on the server and X running on my client. There was a sequence of videos that would play, somewhat like on modern news sites. When one finished the next one started, and when you got to the end of the list it looped back around.

I left the browser open all night, and when I got back in the morning my boss was sitting on my desk, and there were two network admins with him. They wanted me to explain the traffic between the server and my desktop. Since the browser was actually running on the server and X was running full-bandwidth all night with video streams, it wasn't the raw stream going through the wire but the post-rendering frames. Which is (or was at the time) much much bigger than a video stream. I had the number one slot on the network abusers list by almost an order of magnitude. And this was between my desk and the server in the lab right next to me. We were on the same subnet.

---

### Post by TheFu on 2018-09-07
Not everyone understands the risks and even if they do, convenience can override security in many places.  

netcat freaks me out. There's a reason we don't use rsh, rlogin or telnet anymore.  Netcat is 10x worse, IMHO.  Sure, it is useful, but not without limits.

---

### Post by 1clue on 2018-09-07
I would have thought that at least some of the risks of netcat proxies would be immediately obvious to everyone the moment they heard about the process. I found out about it after I was already managing site security, so alarm bells were going off in my head before the explanation was over. That said, I use it all the time even on my own equipment. But it's my equipment and it's secured to the best of my ability, and I'm careful about what I'm doing. Yes it multiplies the exposure of the secured system, but most of the time I'm doing everything inside the same network or through a frequently-connected VPN from secured site to secured site. Not from a coffee shop, for example. Not from a system which can be accessed through wifi either.

netcat is evil, to be sure. Not just because it's a security risk, but also because it's so incredibly convenient and useful.

---

### Post by TheFu on 2018-09-07
> **1clue said:**
> 
netcat is evil, to be sure. Not just because it's a security risk, but also because it's so incredibly convenient and useful.

But to a programmer creating a client/server connection, if they don't bother with encryption, netcat really isn't any different than using java serialization and sending/receiving data between a client and server.  C/S json, xml, corba ... are also the same level of security, so what does netcat really matter?

They will play it down. And they are correct, except that there is a slightly higher level of effort needed to make those other connections, whereas a netcat connection takes next to zero special skills.

BTW, modern bash can do something like netcat easily.  The idea works for pretty much any scripting language.  I've seen implementations in perl, python, ruby, bash, and even php.  Usually the implementation is 1 line.  The bash version is the cleanest. ;) "bash reverse shell" is the search, if anyone is interested.

Guess we've beaten this topic into submission.

---

