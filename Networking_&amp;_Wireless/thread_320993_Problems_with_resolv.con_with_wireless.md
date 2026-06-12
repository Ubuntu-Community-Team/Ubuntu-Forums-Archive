---
title: "Problems with resolv.con with wireless"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by tafsen on 2006-12-18
I get the ip address from dhcp, but the resolve.conf isn't correct.

resolv.conf looks like this after I connected with the wireless:
search NetScreen-5GT
nameserver 192.168.2.1

after I've connected with the wired network, resolv.conf looks like this:
search NetScreen-5GT
nameserver 84.20.96.10
nameserver 213.142.0.242
nameserver 81.191.32.23

If I copy the resolv.conf I get from the wired network, and replace it with the one I get from the wireless, the wireless works.  But this is not an acceptable method since the computer is for a friend that don't know how to use the terminal.

What's wrong, and how can I fix this?

---

### Post by pnael on 2006-12-18
The resolv.conf settings are provided by the dhcp protocol. So if the settings
are not correct it is more likely a dhcp server configuration error.
In your case, your wireless AP does not provide the right dhcp configuration.
The problem is not on the computer.

---

### Post by dbott67 on 2006-12-18
You'll need to do the following:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]84.20.96.10[/COLOR]**;
```

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR="Blue"]prepend domain-name-servers 84.20.96.10;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```

-Dave

---

### Post by tafsen on 2006-12-18
Well, it works fine on my other computer.  And I can't bind it to one dns address, need it to work with difrent networks.

---

### Post by dbott67 on 2006-12-18
What make & model wireless router do you have?

Under normal circumstances, the resolv.conf file should look like this if you are connecting to the wireless AP:
```
search NetScreen-5GT
nameserver 192.168.2.1
```

If the router is configured correctly, it should either have a static IP and the appropriate "real" DNS servers whould be listed in the router or it should obtain the correct network settings via DHCP (see attached screenshot #1 - WAN DNS Settings). 

Next, the router should be configured to provide DNS Relay (see attached screenshot #2 at the bottom).  When your computer requests a lookup, the computer checks with the wireless router which then forwards the request to the real DNS server on the network.

So, make sure that the router has the correct network settings and that DNS forwarding is enabled.

-Dave

---

### Post by pnael on 2006-12-19
You can't suggest to setup directly the DNS servers in the dhcp client configuration :

>3. Look for the following line:
>```
#prepend domain-name-servers 127.0.0.1;
```
>Remove the comment (#) and change it to:
>```
prepend domain-name-servers **[COLOR="Red"]84.20.96.10[/COLOR]**;
```

In some locations (my company for example)  this setup will not work since you have to use the local DNS servers to have name resolution working. In this problem the dhcp server does not provide the correct settings. Don't break the dhcp client if the dhcp server does not work !

---

### Post by dbott67 on 2006-12-19
> **pnael said:**
> You can't suggest to setup directly the DNS servers in the dhcp client configuration :

>3. Look for the following line:
>```
#prepend domain-name-servers 127.0.0.1;
```
>Remove the comment (#) and change it to:
>```
prepend domain-name-servers **[COLOR="Red"]84.20.96.10[/COLOR]**;
```



I agree that one shouldn't go messing with the dhclient.conf file (especially if they don't know what they're doing), but your comment about not setting up the DNS directly in the file is wrong.  The file itself contains the instructions and commented line to prepend DNS servers:
```
#prepend domain-name-servers 127.0.0.1;
```
What I've suggested in my previous post is the reason the above line exists in the file.

> **pnael said:**
> In some locations (my company for example)  this setup will not work since you have to use the local DNS servers to have name resolution working. In this problem the dhcp server does not provide the correct settings. 

True.  As you mention, changing this line has serious repercussions on a corporate LAN.  My post was about how to change the DNS servers to something other than the default and make the settings be persistent between sessions.  Hopefully, the sys admin of the corporate LAN has taken the appropriate precautions to prevent the end-user from fiddling with the network settings.  In this case, it appears that the OP is just helping a friend.

> **pnael said:**
> Don't break the dhcp client if the dhcp server does not work !
This hack wouldn't "break" the DHCP client; it may mess up name resolution, but seeing as it doesn't work with the current DNS settings, it's worth a try.  **Step #4** (removing the DHCP assigned DNS server) is a little more drastic, but it may be a workable solution for a home user with name resolution problems and wanting to use something like the OpenDNS servers.

As always, document your steps and backup your config files so that you can always undo anything.

-Dave

---

