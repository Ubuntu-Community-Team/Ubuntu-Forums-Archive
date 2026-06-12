---
title: "Static IP OpenDNS - Lose My Local Network"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by jpatt on 2006-09-24
To speed up webpages, I have switched to opendns. In the process, I have lost access to my local puters on mshome network. Can I have my cake and eat it to?

---

### Post by wieman01 on 2006-09-25
I don't seem to understand your question...

---

### Post by jpatt on 2006-09-25
Sorry for the poor explanation. When I installed 6.0.6, auto assign IP address, I was able to acces shares on another pc. I wanted the benefits involved with using opendns.com, now I am running a static ip, cached dns. Got what I am wanted, although I lost my access to the local network.

As I read into my own problem, it looks like I need to create samba sharing. Or possibly, add network server share address information to dnsclient.conf or host.conf or ??? I did like when I did nothing and the server shares were accessable.

---

### Post by wieman01 on 2006-09-25
Alright, you need to enable Samba sharing, that's it. Samba is good for sharing files between Linux & Windows machines. I think even the "Share folder" applet asks you if you want to install Samba. At least that happens when I fire it up.

So share folders with Windows clients you need to specify a workgroup. Take a look at the screenshot (Gnome applet).

---

### Post by jpatt on 2006-09-25
After much pain and anxiety, I got it to work. OpenDNS.com changed my IP. No longer had share access. When I stopped Samba, I notice I could access my network shares. Wrong settings the issue. Messed with Smb.conf. Since I am not worried about security, I changed the line security=user to security=share. I double checked the proper hash marks to remove, naturally I forgot some. Presto.

---

### Post by jpatt on 2006-09-26
Also, I forget to mention I removed my OpenDNS numbers out and saved networking profile. Below is the response from OpenDNS.

[I][COLOR="DarkSlateBlue"]The short answer is that I don't know why that would be happening. We've heard from a few other Ubuntu users about a similiar issue.

We're looking into it and I will get back to you if/when we figure something out. Please let me know if you are able to do the same.[/COLOR][/I]

---

### Post by berserker on 2006-11-11
> **jpatt said:**
> Messed with Smb.conf. Since I am not worried about security, I changed the line security=user to security=share. I double checked the proper hash marks to remove, naturally I forgot some. Presto.

I have the same problem (my Ubuntu box can't see my other networked computers but they can see it).  However, I already have security=share in my smb.conf so I'm not sure what the solution is for me.

---

### Post by Derspankster on 2006-11-19
I have the same issue. Looking for a cure. I recently enabled OpenDNS and enjoy it but I have a problem now with my Ubuntu computer. I can no longer browse my Windows network.  I was always able to browse shared folders on any of my 3 Windows computers on my network. I have a Linksys router and entered the nameservers in the router config.  I also made the nameserver changes in network settings on my Linux computer.

Below is the output of the smbtree command after enabling OpenDNS.

larry47@larry47-linux:~$ smbtree
Password:
MSHOME
        \\LAIRDLA                       NETWORK SERVER
timeout connecting to 208.67.219.40:445
timeout connecting to 208.67.219.40:139
Error connecting to 208.67.219.40 (Operation already in progress)
cli_start_connection: failed to connect to LAIRDLA<20> (208.67.219.40)
larry47@larry47-linux:~$

---

### Post by Derspankster on 2006-11-20
I guess no one knows the answer to this issue. No reply from OpenDNS as yet either.

---

### Post by Derspankster on 2006-11-22
I posted the same question at Broadband Reports and got some useful information. Please follow [this link]("http://www.dslreports.com/forum/remark,17303938").

---

### Post by berserker on 2006-11-22
> **Derspankster said:**
> I posted the same question at Broadband Reports and got some useful information. Please follow [this link]("http://www.dslreports.com/forum/remark,17303938").

Thank you!  That did the trick for me.  I can now use OpenDNS AND browse my networked computers with Samba.  This is an example of what my /etc/hosts file looks like now:

```
127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
192.168.1.0 gateway #modem/router
192.168.1.1 george #my computer
192.168.1.2 pete #windows computer
192.168.1.3 dave #windows computer
192.168.1.4 stan #windows computer
192.168.1.5 gary #vmware

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

EDIT:  Disregard.  I could not access my networked computers after restarting SAMBA.

---

