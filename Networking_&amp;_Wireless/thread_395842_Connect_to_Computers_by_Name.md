---
title: "Connect to Computers by Name"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Gammell on 2007-03-28
Hi.
I've recently switched my laptop to Xubuntu from XP. I also have a server that's running a certain source based linux distribution for about a year. In XP, I could always connect to it through putty by it's computer name, ie in 'psuedo code'
```
ssh server
```However, now that I'm in Ubuntu, it no longer works and I need to connect with an ip address, ie
```
ssh 192.168.2.103
```Since the server is always on, its IP address is quasi-static *however* for configuring some programs on the laptop, that's not good enough. This isn't a Samba issue, I can browse with the smbclient fine. It's just some sort of setting issue in Ubuntu (DNS?). The network settings list my router (192.168.2.1) as a DNS server and all my roommates windows machines can still connect to it by name.
Thanks.

---

### Post by Mr. C. on 2007-03-28
You have your choice:

1) add entries to /etc/hosts
2) configure the server to be a DNS server as well
3) add wins to the /etc/nsswitch.conf file and configure your samba server to be a wins server

I don't know what "quasi-static" means.  Its either a static address or it is not.  If the address of the server changes, it is dynamic.  Which is it?  As a server, is should be static.

How do the XP stations know the name, but Ubuntu does not, you ask?  Because your samba server, or one of your XP stations on the net is acting as a master browser for the other SMB clients.  Ubuntu does not do name lookups based upon SMB.  It searches for hosts based upon the lookup methods specified in /etc/nsswitch.conf.

MrC

---

### Post by Gammell on 2007-03-29
> **Mr. C. said:**
> I don't know what "quasi-static" means.  Its either a static address or it is not.  If the address of the server changes, it is dynamic.  Which is it?  As a server, is should be static.
It's always on, with a dynamic address. Therefore, except for power failures and other large scale events, the address is mostly constant. That's what I meant by 'quasi-static'. It's static in day to day use, but one day I'm going to wake up and it's going to have changed. It's unfortunately not an option to let this server have a static address, it physically moves too frequently (couple times a year). It doesn't even have a static subnet! ;)

> **Mr. C. said:**
> How do the XP stations know the name, but Ubuntu does not, you ask?  Because your samba server, or one of your XP stations on the net is acting as a master browser for the other SMB clients.  Ubuntu does not do name lookups based upon SMB.  It searches for hosts based upon the lookup methods specified in /etc/nsswitch.conf.
Yes, that's exactly what I wanted to know. I've now set up the server's Samba to be a WINS server and everything seems to work properly. I don't really understand why ubuntu couldn't use the dynamically negotiated one that all the windows machines were using (I assume that's how it was working for windows?), but that's fine. Things work now and should be nicely dynamic. Thanks.

---

### Post by Mr. C. on 2007-03-29
You're welcome.  Glad its working.

---

### Post by Gammell on 2007-03-29
I'm sure this has been documented elsewhere, but it's a strange problem to search for (at least *I* didn't know what to call it). So to help of anyone who stumbles upon this thread here's the solution. I'm hoping the smb.conf location is correct for Ubuntu, the computer I had to change it on (my server) is currently running Gentoo.

Enable samba server as a WINS server:

```
**nano /etc/samba/smb.conf**

[global]

...

wins support = yes
name resolve order = wins lmhosts hosts bcast
dns proxy = no

```



Tell computers to look to WINS server before DNS (resolves left to right) by adding the wins to your hosts line before DNS. An **example**:

```
**nano /etc/nsswitch.conf**

hosts:       files wins dns

```

---

### Post by Mr. C. on 2007-03-29
> I don't really understand why ubuntu couldn't use the dynamically negotiated one that all the windows machines were using (I assume that's how it was working for windows?)

Your configuration line in /etc/hosts clarifies this:

hosts:       files wins dns

By default, your configuration of /etc/hosts did not use wins for hosts lookup, which is a very old, weak lookup service.  It exists for compatibility with older windows systems, and eventually will fade away.  It has been replaced ubiquitously with DNS and Active Directory.

MrC

---

### Post by Gammell on 2007-03-29
> **Mr. C. said:**
> Your configuration line in /etc/hosts clarifies this:

hosts:       files wins dns

By default, your configuration of /etc/hosts did not use wins for hosts lookup, which is a very old, weak lookup service.  It exists for compatibility with older windows systems, and eventually will fade away.  It has been replaced ubiquitously with DNS and Active Directory.

MrC

Right. I understand that it originally wasn't asking WINS about the address. It's just that when I enabled WINS before enabling Samba to be a WINS server, it wasn't able to find whatever WINS "server" (I assume a dynamically negotiated computer on the network...?) all the windows computers are using. That's what I don't understand. It's academic really I suppose...

---

### Post by Mr. C. on 2007-03-29
Before you enabled a WINS server, there was no WINS server.  What was available is SMB broadcasts; your XP stations received these messages, and cached the names. 

MrC

---

### Post by Gammell on 2007-03-29
> **Mr. C. said:**
> Before you enabled a WINS server, there was no WINS server.  What was available is SMB broadcasts; your XP stations received these messages, and cached the names. 

MrC
I see, interesting. So does linux not support SMB broadcast names on purpose?... Or was that an option that could have went in the hosts variable of nsswitch.conf?

---

### Post by Mr. C. on 2007-03-29
> **Gammell said:**
> I see, interesting. So does linux not support SMB broadcast names on purpose?... Or was that an option that could have went in the hosts variable of nsswitch.conf?

Unix/Linux systems use TCP/IP.  SMB is an old, Microsoft proprietary networking protocol that does not scale well, and is unsuitable for Internet-wide use.  It is disabled by default, as a) it requires configuration, and b) is not necessary in most sites, as the internet runs on DNS.  There is a reason why the rest of the world has rejected SMB, as has Microsoft itself.   SMB broadcasts create broadcast storms, and use a large amount of network traffic. Routers do not forward broadcast traffic.

MrC

---

### Post by Gammell on 2007-03-29
> **Mr. C. said:**
> Unix/Linux systems use TCP/IP.  SMB is an old, Microsoft proprietary networking protocol that does not scale well, and is unsuitable for Internet-wide use.  It is disabled by default, as a) it requires configuration, and b) is not necessary in most sites, as the internet runs on DNS.  There is a reason why the rest of the world has rejected SMB, as has Microsoft itself.   SMB broadcasts create broadcast storms, and use a large amount of network traffic. Routers do not forward broadcast traffic.

MrC
Thanks, that's interesting to know.

Oh! it looks like i spoke too soon. While that set up worked for my gentoo computer, adding wins to the host line on my ubuntu computer still doesn't do the job. Sorry, I was at work and can only SSH into my server, not my laptop. Since it worked there, I figured things would work here. The WINS server knows of my laptop (all other computers can ping it by name) but Ubuntu isn't using WINS properly. Any other thoughts?

---

### Post by Mr. C. on 2007-03-29
Let's clarify WINS.

WINS is a Microsoft protocol.  Linux TCP/IP networking does not speak that protocol.   Samba does.

You need Samba running in order for your Ubuntu laptop to announce itself to the WINS server, or the WINS server will never know that laptop exists by NETBIOS name.

See also:

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id318265](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id318265)

if you have multiple subnets.

MrC

---

### Post by Gammell on 2007-03-29
The ubuntu laptop is announcing to the WINS server fine and all other computers can ping the laptop by name (including the server that runs linux). It's that the laptop still can't do anything by netbios names. My nsswitch.conf on the ubuntu laptop:
```

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins dns
#hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

```
Is there any packages I need installed to *use* the WINS server for name lookups? It seems that the WINS server is fine, just that the ubuntu laptop isn't using it.

---

### Post by dbott67 on 2007-03-29
You would need the **winbind** package (which functions as the WINS server for linux), as well as smbclient & smbfs for full WINS/SMB support:
```
sudo apt-get install smbfs smbclient winbind
```-Dave

---

### Post by Mr. C. on 2007-03-29
> **dbott67 said:**
> You would need the **winbind** package (which functions as the WINS server for linux)

Hmmm.  Winbind is for user and group name lookups, not hostname.

MrC

---

### Post by Gammell on 2007-03-29
> **dbott67 said:**
> You would need the **winbind** package (which functions as the WINS server for linux), as well as smbclient & smbfs for full WINS/SMB support:
```
sudo apt-get install smbfs smbclient winbind
```-Dave
Thank you. I was missing winbind. It works now.
As soon as Feisty is officially released I'm migrating the server to it. Keeping track of two different distros is too much. ;)

---

### Post by Gammell on 2007-03-29
> **Mr. C. said:**
> Hmmm.  Winbind is for user and group name lookups, not hostname.

MrC

I know adding the winbind keyword to *passwd* and *group* in nsswitch.conf gives you user and group network lookups, but the winbind package must have the service for WINS lookup because without changing any configurations, it worked after installing it. Thanks everyone for the speedy responses and the off topic conversations. ;)

---

### Post by Mr. C. on 2007-03-30
Something changed in your configuration; what you are seeing is an artifact of that.  The WINS client and server is provided by smbd, not winbind.

Be sure you now have only 1 and only 1 WINS servers running on the same network.

Your client Samba systems need to have in their smb.conf files:

```
wins support = No
wins server = WINS_SERVER_IP_HERE
```

and your Samba server needs to have

```
wins support = Yes
```

MrC

---

### Post by Gammell on 2007-03-30
> **Mr. C. said:**
> 
```
wins support = No
wins server = WINS_SERVER_IP_HERE
```

Good point, I should have had to point Samba at the WINS server, I'd made a note to do that on the laptop when I was setting up the server and forgot. However, I just checked and with winbind installed, there still isn't a wins server line in smb.conf and it works. Could it be that somehow winbind dynamically finds the WINS server? Some how related to it's job handling network users and passwords? By apt-get'ing winbind, it worked without ever having to configure where my WINS server was...

---

### Post by dbott67 on 2007-03-30
This is very interesting.  Back in October/November I came across this [thread]("http://www.ubuntuforums.org/showthread.php?p=1683473#post1683473") in which feather_king posted about the winbind package, which cured some name resolution issues that the OP was suffering from.

I had (incorrectly, I suppose) jumped to the conclusion that winbind was the WINS server component of Samba (I guess because bind=DNS in linux, I assumed that  winbind must equal WINS name server).  Strange that it seems to make everything work.  I have posted feather_kings suggestion in other threads and many times it seems to fix the problem.

Of course, after reading up on winbind I realize that this is not the case.  I came across this very comprehensive [guide]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html") on Network Browsing and it seems to cover most issues with regards to name resolution (none of which include winbind).

I wonder if removing winbind will cause any problems now that WINS is working properly.

-Dave

---

### Post by Mr. C. on 2007-03-30
None of this stuff is easy or obvious - there are so many layers and complexities.

While I love the idea of just adding packages to get things to work, this approach leaves us often relying more on magic spells, than on understanding.

Granted, most don't want to know, care to know, or need to know the underlying details of how all this software works.  Unfortunately, when things don't work as expected, there is confusion, and often an inability to resolve the problem.  At that point, users resort to the magic spells and prayers to get things to work again.  Reinstall, reboot, delete, hack, slash!

In the end, with everyone's help, we'll get there.
MrC

---

### Post by dbott67 on 2007-03-30
When I get a chance, I'm going to fiddle about with smb & winbind and see if there is some sort of magic voodoo that's going on.

I'm like Mr.C in that I like to know what's going on & address the problem rather than reinstall, reboot, delete, hack, slash! (although, every once-in-a-while I'm guilty of muttering a few curse words and trying one of the above methods) :)

I got to thinking this morning about how or why winbind would make things work and might try to track the key conf files from a fresh install to see if any of the packages are making changes.  It may be a while before I do this, but I will be upgrading my desktop to Feisty soon and will see if I can spot anything during my travels.

-Dave

---

### Post by Gammell on 2007-04-02
> **dbott67 said:**
> I wonder if removing winbind will cause any problems now that WINS is working properly.

If you disable the winbind daemon from the services, netbios names continue to work. If you remove winbind from the system, you can no longer ping netbios names.  Putting it right back makes everything work again. 

I agree, I'd love to know what's going on instead of just installing magical packages. Let me know if there's anything I can do to help.



```

$ ping server
ping: unknown host server

```

---

