---
title: "How to open ports on Ubuntu"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by 7raTEYdCql on 2008-09-05
How do i open ports that are closed on ubuntu. I mean suppose if i want to download a torrent from a port that i want to define then can I.

---

### Post by Vivaldi Gloria on 2008-09-05
> **i.mehrzad said:**
> How do i open ports that are closed on ubuntu. I mean suppose if i want to download a torrent from a port that i want to define then can I.

In the default desktop ubuntu install all ports are open. 

All you need to do is the forward ports in your router and change your firewall settings in your router.

---

### Post by 7raTEYdCql on 2008-09-05
However when i nmap scan a computer that is running ubuntu it seems that all the ports are closed, and http is redirected to some other port.

So what do you mean by all ports are open.

I heard something about the ubuntu philosophy in this respect. Whenever a system call wants to hear from a port it will open the port so that it can hear. Am i correct?

---

### Post by Vivaldi Gloria on 2008-09-05
All ports are open but there is no application listening to any port. So if a packet comes to your ubuntu box then it is just ignored because there's no app (server) listening to the port that the packet arrives to. That's why ports appear closed to outside world. When you install any app which listens to a port (like P2P apps) then they'll receive the packets without a problem because the ports are not blocked.

Actually ubuntu comes with a firewall called iptables. "When you install Ubuntu, iptables is there, but it allows all traffic by default." See

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I use ssh and amule and I didn't need to make any changes in ubuntu. I only changed my router's settings and they work fine. I get a high id in amule.

---

### Post by Twitch6000 on 2008-09-05
@Vivaldi Gloria you are incorrect on the default ubuntu install all ports are CLOSED.

This is part of the good security of Ubuntu.

To open these ports download Firestarter and open whichever port you and.You can also mess with other firewall settings.

---

### Post by Vivaldi Gloria on 2008-09-05
1) From [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

> Discussions about firewalls often are passionate (just search the Ubuntu forums). By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.

So ports are closed because there is no server app listening, not because they are firewalled. When you install a server app it'll just work, no need to change anything in ubuntu. Just change your router settings.

2) Let me prove to you that ports are not firewalled. I have two computers in my lan behind my home router. Both run Hardy. In the first computer I give the command

```
netcat -nvlp <port_number>
```

and in the second give the command

```
netcat -nv 192.168.1.35 <port_number>
```

and start chatting between computers. (192.168.1.35 is my first computer's ip). I can do this with any port I want (other than the ports already used). This shows that no port is firewalled.

3) Using firestarter (or ufw etc) will of course close ports with the firewall. Firestarter is NOT a firewall btw but it's a frontend to iptables which is the firewall that ubuntu comes with. When you firewall then of course you'll have to open ports. But in the default ubuntu installed no port is firewalled.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

4) Actually, I suggest not to use firestarter. It's dead. The last update was in 2005. The developers are not working on it anymore. It hasn't been updated to reflect the latest libraries for Gnome and other fundamental iptables changes in newer kernels. It crashes and screws up some systems.

ubuntu comes with ufw. See

```
man ufw 
```

for more info. See especially the examples section. Also see

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

5) To sum up, in the default desktop ubuntu install no port is firewalled and you can use any P2P program without changing anything in ubuntu. Just change your router settings.

---

### Post by Twitch6000 on 2008-09-05
This does not cause all ports to open...
When you install server software it will only open the ports needed.
Normally the http/s and pop3 ports are opened.Unless you do otherwise.

Also he has not said if he has server software or not.

---

### Post by Vivaldi Gloria on 2008-09-05
> **Twitch6000 said:**
> This does not cause all ports to open...

I used "open" to mean "not firewalled". Yes it is not a very good terminology and I'll use "not firewalled" explicitly the next time. Though I don't know what you mean by open.

> When you install server software it will only open the ports needed.

Not sure what do you mean by "opening ports". When you install a server software and it's running then it will listen only the ports it needs and these are already not firewalled in a default ubuntu desktop install. 

> Normally the http/s and pop3 ports are opened.Unless you do otherwise.

Those ports are not "opened" as if a webserver or a mailserver does. For example firefox doesn't accept packets on port 80 unless the packages are from a server that ff sent a request message previously. See [[COLOR="DarkOliveGreen"]wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol") for more info on HTTP protocol.

To check what processes are listening for connections use the command

```
sudo netstat -plntu
```

Note that most of these are on the local loopback (e.g. cups) so no need to get alarmed.

> Also he has not said if he has server software or not.

He said he wants to use a server software (a torrent app in this case).

The bottom line is:

[COLOR="Sienna"]In the default desktop ubuntu install no port is firewalled and you can use any P2P program without changing anything in ubuntu. Just change your router settings. [/COLOR]

---

