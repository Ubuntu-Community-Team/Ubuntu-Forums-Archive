---
title: "NoIP ddns with ssh?"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by CantankRus on 2016-07-14
Firstly, I haven't used ssh before and have little experience networking.
I have managed to set up ssh so as I can connect over the local network from my android phone to my Xenial PC.
I have set ssh to use key authorization only and I can ssh into my PC succressfully.

I want to also be able to connect over Wan as well but my IP address is dynamic.
I set up a dynamic dns address with [**_[COLOR="#B22222"]NoIP[/COLOR]_**]("http://www.noip.com/") and installed their client in Ubuntu.
> Our Dynamic DNS Update Client continually checks for IP address changes in the background 
and automatically updates the DNS at No-IP whenever it changes.

Checking my IP with what is shown at NoIP, the updating of my IP appears to work.
In the router I have forwarded port 22 to my PC but I can't connect when using the NoIP dns address with ssh.

I believe my ISP blocks port 80 among [**_[COLOR="#B22222"]other ports[/COLOR]_**]("https://myhelp.westnet.com.au/node/986#toc_1").
I can turn off port blocking in my ISP account.
Do I need to turn off port blocking and is there anything I need to know if I do this?

---

### Post by TheFu on 2016-07-14
Your router needs to forward the port open for ssh.  Using 22/tcp will lead to hassles that just aren't worth it, IMHO. Use a high port, something above 60K to make life easier.  HAve the router do the port translation from  60022 --> 22 on the LAN.

You didn't say whether your "server" has a static IP on the LAN. It should.  Routers aren't good at forwarding ports to dynamic LAN IPs.

Also, you'll want to secure this connection and block brute force attempts.  Fail2ban does that, but there are more settings to secure ssh in a general way that do not impact usability.  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) - grab a copy of this page, since my ISP has been up/down the last few days a bunch.

ssh is the way that unix system communicate. By setting up ssh, you get sftp and scp and sshfs access too.

---

### Post by CantankRus on 2016-07-15
Thanks,
The IP address of my PC never seems to change...maybe because it's always on and is wired to the router.
I haven't worried about setting up static IP's on the Lan.
Everything else connects over wireless...chromecast, rapberrypi and phone.

I have opened a high port and redirected it to 22.
I installed fail2ban and will do some reading.

PS:Couldn't connect to your link....had to get a "[**_[COLOR="#B22222"]Text-only version[/COLOR]_**]("http://webcache.googleusercontent.com/search?q=cache:0nRpD2RoHfkJ:blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures&num=1&hl=en&gl=au&strip=1&vwsrc=0")" from googles cache.

---

