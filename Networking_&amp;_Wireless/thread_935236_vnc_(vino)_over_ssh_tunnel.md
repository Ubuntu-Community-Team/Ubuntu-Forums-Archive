---
title: "vnc (vino) over ssh tunnel"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by wonko on 2008-10-01
I've been searhing through these threads now till my face is blue :confused:
I've been trying to follow [this]("https://help.ubuntu.com/community/VNC") ubuntu community article to set up an as secure as possible vnc server, by tunneling over over ssh and setting vino to "Only allow local connections". But I keep getting an error. My vnc client (krdc) says "the server is not accepting any new connections", while the server (via the ssh sesstion) says "channel 3: open failed: connect failed: Connection refused".

And when I finally gave up and tried tightvnc (because when I had to install a new server anyway, I wanted to try one that's supposed to be faster, not the "boring" x11vnc :p ), this gives me only an orange window with an x terminal. And all guides about tightvnc says "uncomment the $fontpath lines in /etc/vnc.conf" but there is no file called /etc/vnc.conf !

Please help!

---

### Post by billybennett on 2008-10-03
I would also like to know.... I've been using Vino to connect to my desktop at home from work but I've learned that VNC by itself is not secure.  I've tried to install X11VNC but have not had any luck.  I don't mean to hijack your thread but I'd like to know the best way to ssh then VNC.

---

### Post by Steve1961 on 2008-10-03
I regularly use vnc to access ubuntu and windows boxes from my ubuntu laptop.  There's a few ways that this can be done, but first of all you need to make sure that the openssh-server is installed on all the machines you need to access, and that you can ssh to them.  It's best to set up access using secure key authentication rather than passwords, and to change the default port 22 to something higher.  See this how to:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Also setup any port-forwarding in routers, and make sure the firewall on the host allows connections on whatever port you've allocated to ssh.  Most importantly, then make sure that you can connect to these boxes with ssh.

Then set up the vino-server on the Ubuntu hosts you want to access:

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

or vnc/tighvnc on any windows boxes.

After that you can either use the vinagre vnc client that comes as default in Ubuntu, or install xtightvncviewer from the repos.  If you install the xtightvncviewer you can securely connect to your host through an ssh tunnel by just issuing the following command in a terminal:

vncviewer -via "user@host -p port" localhost:0

Just adapt the user@host part to match the host you want to connect to, and "port" should be the port you set up for ssh.  This should prompt you for the vnc password, and once entered the vnc window should open.

AFAIK vinagre doesn't have this option to automatically create an shh tunnel, so if you want to use that you'll have to set up your ssh tunnel manually.  You do this with a command similar to this:

ssh -L 5900:localhost:5900 user@host -p port

Then just go to vinagre and connect to "localhost"

As an aside, I also use a utility called GSTM (gnome shh tunnel manager) which allows me to set up tunnels with one click after initial configuration.

Finally, if you need to create an shh tunnel from a windows box I believe that this can be done with putty:

[http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html](http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html)

You will of course need to install openssh on a windows box.  There seems to be a number of packages available, but I've used [copssh]("http://www.itefix.no/i2/node/27") successfully.

Hope this helps :)

---

### Post by wonko on 2008-10-03
@billybennet: Do you have the same problem as me, getting the "channel 3: open failed: connect failed: Connection refused" - error? If not, you can read the ubuntu community article I mentioned for some tips on how to make vnc more secure.

@Steve1961: Thanks for the little lecture, but I'm not sure you've understood exactly what I meant. I want to set up my vnc server to **only allow** sessions over an ssh tunnel. This is described on the ubuntu community, but when i follow that article, I only get the error message described in my previous post.

Anybody had similar experiences and found a way to fix it?

btw: as long as I don't tick the "Only allow local connections" option in vino, vnc works fine (even through an ssh tunnel).

---

### Post by Steve1961 on 2008-10-03
> @Steve1961: Thanks for the little lecture, but I'm not sure you've understood exactly what I meant. I want to set up my vnc server to only allow sessions over an ssh tunnel. This is described on the ubuntu community, but when i follow that article, I only get the error message described in my previous post.

Wasnt meant to be a lecture, but I clearly did misunderstand your meaning.  However, it seems you're not the only one having this problem, and I haven't found a solution after doing a quick search.

---

### Post by billybennett on 2008-10-03
Your way ahead of me Wonko.  I'm still trying to get VNC over SSH to work.   


Steve I thank you for the instructions I hope to give them a try today.

---

### Post by Steve1961 on 2008-10-03
One possible solution to the connection refused issue has been posted [here]("http://manas.tungare.name/blog/2008/05/30/ssh-port-forwarding-on-mac-os-x/").  The quoted solution is:

> Change localhost to 127.0.0.1 in the ssh -L parameter. 

Worth a try anyway.  Also, though you shouldn't need it, make sure you explictly allow connections on 127.0.0.1 in your firewall

---

### Post by zka on 2008-10-07
> **Steve1961 said:**
> I regularly use vnc to access ubuntu and windows boxes from my ubuntu laptop.  There's a few ways that this can be done, but first of all you need to make sure that the openssh-server is installed on all the machines you need to access, and that you can ssh to them.  It's best to set up access using secure key authentication rather than passwords, and to change the default port 22 to something higher.  See this how to:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Also setup any port-forwarding in routers, and make sure the firewall on the host allows connections on whatever port you've allocated to ssh.  Most importantly, then make sure that you can connect to these boxes with ssh.

Then set up the vino-server on the Ubuntu hosts you want to access:

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

or vnc/tighvnc on any windows boxes.

After that you can either use the vinagre vnc client that comes as default in Ubuntu, or install xtightvncviewer from the repos.  If you install the xtightvncviewer you can securely connect to your host through an ssh tunnel by just issuing the following command in a terminal:

vncviewer -via "user@host -p port" localhost:0

Just adapt the user@host part to match the host you want to connect to, and "port" should be the port you set up for ssh.  This should prompt you for the vnc password, and once entered the vnc window should open.

AFAIK vinagre doesn't have this option to automatically create an shh tunnel, so if you want to use that you'll have to set up your ssh tunnel manually.  You do this with a command similar to this:

ssh -L 5900:localhost:5900 user@host -p port

Then just go to vinagre and connect to "localhost"

As an aside, I also use a utility called GSTM (gnome shh tunnel manager) which allows me to set up tunnels with one click after initial configuration.

Finally, if you need to create an shh tunnel from a windows box I believe that this can be done with putty:

[http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html](http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html)

You will of course need to install openssh on a windows box.  There seems to be a number of packages available, but I've used [copssh]("http://www.itefix.no/i2/node/27") successfully.

Hope this helps :)


Just the thing I was googling for. Thank you very much Steve!

---

### Post by Steve1961 on 2008-10-07
> **zka said:**
> Just the thing I was googling for. Thank you very much Steve!

You're welcome :)

---

### Post by wonko on 2008-10-07
> **Steve1961 said:**
> One possible solution to the connection refused issue has been posted [here]("http://manas.tungare.name/blog/2008/05/30/ssh-port-forwarding-on-mac-os-x/").  The quoted solution is:
...
Worth a try anyway.  Also, though you shouldn't need it, make sure you explictly allow connections on 127.0.0.1 in your firewall

Actually, I've already tried this, without any luck, but thanks for the tip anyway. And afaik I don't use any firewall (unless it's activated by default in ubuntu 8.10?).

btw: I wasn't sarcastic or anything thanking you for the lecture earlier, if that's what you thought... It's just my English isn't very good :( In retrospect, "guide" probably would've been a better word to use than "lecture"...?

---

### Post by Steve1961 on 2008-10-07
> **wonko said:**
> Actually, I've already tried this, without any luck, but thanks for the tip anyway. And afaik I don't use any firewall (unless it's activated by default in ubuntu 8.10?).

btw: I wasn't sarcastic or anything thanking you for the lecture earlier, if that's what you thought... It's just my English isn't very good :( In retrospect, "guide" probably would've been a better word to use than "lecture"...?

No offence taken :)  Sorry it didn't work though.  Have you tried alternatives such as freenx or nomachine's nx?  They may not suit you as the server part only works on Linux but I believe there is a windows client.  Anyway, hope you find a solution.

---

### Post by wonko on 2008-10-07
Hmm.. NX seems a very interesting alternative :) I've heard about it; don't remember why I didn't try it, but I certainly will now. Thanks!

---

### Post by Steve1961 on 2008-10-07
> **wonko said:**
> Hmm.. NX seems a very interesting alternative :) I've heard about it; don't remember why I didn't try it, but I certainly will now. Thanks!


You're welcome.  I've been playing with the nomachine version of nx for the last couple of days and its much much much faster than vnc.  Only problem I've found so far is that you have to enable password based authentication in your /etc/ssh/sshd_config.  But not a huge problem if you generate custom keys, use a non-standard port, limit the number of users who can ssh, and block unwanted hosts in your firewall.

---

### Post by dilaudid on 2008-12-06
I've had the same problem of "connection refused" when I tick "Only allow local connections" and try to connect via an ssh tunnel in 4.1, and it still seems to be a problem in 8.4. The only fix I found for it is turn off the "Only allow local connections" tickbox, and use iptables to drop any packets from anyone but localhost, for safety. The iptables command I used was:
```
sudo iptables -I INPUT -p tcp --dport 5900 -s ! 127.0.0.1 -j DROP
```
This means drop any TCP packet destined for port 5900 that does not come from localhost. Seems to work really well.

By the way, I'm using 8.4 with tightvnc
using ssh -via me@server localhost:0
client is another ubuntu box, both are IBM thinkpads (T41 and T43).

---

### Post by heliosphan10 on 2009-04-21
Sorry for resurrecting an old thread but I feel that some closure is necessary here, especially since this is still an issue.  It seems that the default vnc server on Ubuntu, vino, only accepts ipv6 connections when "Only allow local connections" is checked. This can be remedied by using an ipv6 connection through the ssh tunnel.
```
ssh -L 5900:[::1]:5900 server
```

The bug report can be found [here]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/228370").

---

### Post by thingswelostinthefire on 2009-07-18
> **heliosphan10 said:**
> Sorry for resurrecting an old thread but I feel that some closure is necessary here, especially since this is still an issue.  It seems that the default vnc server on Ubuntu, vino, only accepts ipv6 connections when "Only allow local connections" is checked. This can be remedied by using an ipv6 connection through the ssh tunnel.
```
ssh -L 5900:[::1]:5900 server
```

The bug report can be found [here]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/228370").

this solution was no good for me... vncviewer was still not working...

I found a way through [http://forum.ubuntu-it.org/index.php?topic=193988.msg1287216]("http://forum.ubuntu-it.org/index.php?topic=193988.msg1287216")

```
sudo nano /etc/modprobe.d/blacklist
```

writing at the bottom:

```
blacklist ipv6
```

if you don't need ipv6... Maybe there will be a fix for Hardy in the future...

---

