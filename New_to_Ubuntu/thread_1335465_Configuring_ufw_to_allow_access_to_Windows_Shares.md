---
title: "Configuring ufw to allow access to Windows Shares"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Geraba on 2009-11-23
Hello!
I used to access my windows shares on another computer on my home network thru Ubuntu with no problem. But I installed recently the firewall ufw, and I noticed that if it is enabled, I can't acess the shares. I open the Network folder, open Windows Network... It loads a while, then shows nothing.
When I turn ufw off, the other computer appears.
I tried to add access from the other PC ip to mine using port 139, 445... nothing.
I tried to allow access to ports 139 and 445 from ANY source. Nothing again.
Any ideas?
Thanks in advance!

---

### Post by dca on 2009-11-23
[I]sudo ufw allow proto tcp to any port 135
sudo ufw allow proto udp to any port 137
sudo ufw allow proto udp to any port 138
sudo ufw allow proto tcp to any port 139
sudo ufw allow proto tcp to any port 445[/I]
 
...those should be the relevant Samba ports for file sharing, don't forget to restart ufw after making changes...

---

### Post by bodhi.zazen on 2009-11-23
You can be a bit more restrictive, server side.

Assuming your LAN is 192.168.0.0/24 and your server is 192.168.1.10 :

```
ufw allow proto tcp from 192.168.0.0/24 to 192.168.1.10 port 135
ufw allow proto tcp from 192.168.0.0/24 to 192.168.1.10 port 139
ufw allow proto tcp from 192.168.0.0/24 to 192.168.1.10 port 445

ufw allow proto udp from 192.168.0.0/24 to 192.168.1.10 port 137
ufw allow proto udp from 192.168.0.0/24 to 192.168.1.10 port 138
```

This allows samba traffic from all clients on your LAN, but restricts from outside your LAN.

You do not need to re-start UFW after making those changes.

---

### Post by motorcity909 on 2009-11-23
I've had the same issue as the OP, in that I have to disable the firewall to access the Windows shares (no probs accessing Ubuntu shares on the WinXP machines)

In order to limit sharing to just the computers on my network, I added this to my settings:

sudo ufw allow proto udp from 192.168.0.2/26 to any port 135
sudo ufw allow proto udp from 192.168.0.2/26 to any port 137
sudo ufw allow proto udp from 192.168.0.2/26 to any port 138
sudo ufw allow proto tcp from 192.168.0.2/26 to any port 139
sudo ufw allow proto tcp from 192.168.0.2/26 to any port 445

I got that from [another thread]("http://ubuntuforums.org/showthread.php?t=1169149") about Window shares and added port 135 this evening.

Still the same issue I'm afraid.

From my router settings, I've noticed my IP range is up to 51, so do I need to change the above from 26 to 51?

If so, how do I remove those settings and re-add them with the wider IP range?

Thanks!

---

### Post by motorcity909 on 2009-11-23
I think bodhi.zazen has part answered my question (that reply got posted as I was typing my question).

What's the best way to clear my original settings and add the new ones as per bodhi.zazen's reply.

Cheers!

---

### Post by Geraba on 2009-11-23
I tried dca's and bhodi.zazen's suggestions, but it didn't work...
By server you mean the computer I'm tryind to access, right?
The server is running on Windows XP, so there's no ufw running on it.
I tried changing the server IP on zazen's post (192.168.1.10) to my WinXP ip and then to my Ubuntu ip, same thing.

---

### Post by dca on 2009-11-23
I think I got what you're saying...
 
Instead of browsing network, on blank Ubuntu desktop, pres [CTRL] + [L] (lower-case L)...  When run box pops up put in *smb://serverip/sharename*
 
then see if login prompt follows...

---

### Post by dca on 2009-11-23
I think this bug with ufw may be relative to why you can't browse network but you should still be able to access the way I showed you above...
 
[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975)

---

### Post by Geraba on 2009-11-23
> **dca said:**
> I think I got what you're saying...
 
Instead of browsing network, on blank Ubuntu desktop, pres [CTRL] + [L] (lower-case L)...  When run box pops up put in *smb://serverip/sharename*
 
then see if login prompt follows...

Tried that, I can't connect to my windows shared files, with or without ufw. I get:

```
Error: Failed to mount Windows share
Please select another viewer and try again.
```

---

### Post by dca on 2009-11-23
Did you use the actual correct IP address of the windows box plus the share name (probably C$ or something like that or whatever you have it named?)
 
smb://192.xxx.xxx.xxx/c$

---

### Post by dca on 2009-11-23
I do see bugs referencing nautilus as culprit but that dates back, are you using Ubuntu 9.10?  I know for a fact something was changed during the 8.04 to 8.10 release that caused these issues but you were still able to access using machine's physical IP address...

---

### Post by Geraba on 2009-11-23
I added the " nf_conntrack_pptp and nf_conntrack_netbios_ns" to IPT_MODULES as in [https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975), and it worked!! I don't even need to add the ports 139, 445,.....
Thanks dca!

Now... I would like to learn and understand what I'm doing, hoping to be a power user some day...
The thing I just did, what does it mean? What kind of configuration I modified?
And how would I know that I needed to do that without asking?

Thanks!!!

---

### Post by Geraba on 2009-11-23
> **dca said:**
> Did you use the actual correct IP address of the windows box plus the share name (probably C$ or something like that or whatever you have it named?)
 
smb://192.xxx.xxx.xxx/c$

Strangely, now I can open it without even specifying the share... i.e., just need to type the ip. Before I couldn't even with ufw disabled... Rather odd. :/

---

