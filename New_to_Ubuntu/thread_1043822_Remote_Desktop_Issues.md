---
title: "Remote Desktop Issues"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by paikchris on 2009-01-18
I'm thoroughly confused after hours of tweaking and reading.

I am trying to remotely access my Triple Boot(XP, Hardy, OSX Leopard) from my Ubuntu Laptop. THEREFORE I will need 3 solutions:

1. Ubuntu to XP
2. Ubuntu to Ubuntu
3. Ubuntu to OSX Leopard

Daunting? Yes... i've found that out.

I've read all the documentation on VNC and SSH tunneling. I can get VNC working just fine on my Local Area Network. I havn't tested vnc from outside my network. 

But trying to enable SSH Tunneling is where i get stuck.

Can someone point me in the right direction? (I've done my port forwarding already, port 22)

---

### Post by pytheas22 on 2009-01-18
What's not working?  What happens when you open a terminal in OS X and try to ssh into your Ubuntu machine?  Or vice versa?  Which command are you using to try to connect?

---

### Post by d-mac on 2009-01-19
I've been experiencing a similar issue.

I am trying to securely access my Ubuntu desktop from my Mac running OS X Tiger with SSH port forwarding.

I am able to access the Ubuntu desktop through VNC using the Remote Desktop under preferences when the option to "Only allow local users" on the advanced tab is **not** checked.  

When I check this box, and use SSH port forwarding, I receive the following error from the host terminal:

```
channel 3: open failed: connect failed: Connection refused
```

I also experienced the same issue when trying to connect from a remote Ubuntu system using Vinagre.

The command I am using to create the SSH connection is:
```

ssh -L 5900:localhost:5900 myusername@[IP address of host]
```

Any help would be greatly appreciated.

---

### Post by superprash2003 on 2009-01-19
havbe you configured ssh to listen to the correct interface?? is iptables blocking anythign?? do you run firestarter or anything similar?

---

### Post by d-mac on 2009-01-19
How can I check to see if iptables is blocking anything?

I am not running firestarter or a firewall.

I am able to SSH into the remote server and run port forwarding, it just seems like the connection is being blocked by something on the host system.

Thanks for the help.  I've got little experience dealing with networking.

---

### Post by pytheas22 on 2009-01-20
d-mac: do you have better luck using this command:
```

ssh -D 5900 myusername@[IP address of host]
```

Also, is there a reason that you're trying to ssh on port 5900 instead of just using normal 22?  If you just want to access a normal command-line, it should be sufficient to type from your Mac:
```

ssh myusername@[IP address of Ubuntu machine]
```

or vice-versa for Ubuntu-to-Mac.

---

### Post by d-mac on 2009-01-20
Thanks Pytheus.

I'm doing the port forwarding so I can use the Remote Desktop on my Ubuntu server more securely by only allowing local hosts and access the VNC as if I am on the local computer with port forwarding.

I am not planning on accessing it from outside of the network, however, so I can probably just leave the box unchecked.  I was just trying to make it as secure as possible.

---

### Post by pytheas22 on 2009-01-20
Instead of using ssh on port 5900--which will not make the presence of your ssh server invisible to someone who really wants to find it--you could just edit your /etc/ssh/sshd_config file to allow access only by certain users or from certain IP addresses.

---

### Post by d-mac on 2009-01-20
I just found this thread which appears to be the same as my issue.  Thanks for all the help.

[http://ubuntuforums.org/showthread.php?t=935236](http://ubuntuforums.org/showthread.php?t=935236)

---

### Post by pytheas22 on 2009-01-20
> I just found this thread which appears to be the same as my issue.

If that doesn't solve it for you, let me know.  I do admit that I'm sort of out of ideas, though...I don't know too much about this kind of stuff to begin with.

---

### Post by d-mac on 2009-01-21
Unfortunately, that post did not help me, as it was unresolved.  I think it might have something to do with the fact that I'm already on the local network, and not tunneling in from outside the router.  

I read a post where someone had the same experience, where port forwarding 5900 did not work behind the lan.

I just turned off the VNC server, I do not think I will have much need for it.  I'll just use SSH.

---

### Post by superprash2003 on 2009-01-22
you could try via this online port scanner to see if port 5900 is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) also post output of sudo iptables -L to get iptable rules

---

### Post by genti on 2009-03-13
I had a similar issue with my parents laptop and I was going crazy.
I had checked the port with

netstat -a -t TCP

and saw that 5900 was listening. While hunting the forums somebody suggested nmap.

nmap localhost

and it did not show 5900. Hmmmm. I started paying more attention and i saw that vino was actually listening on port 5900 but using the **IPV6**

After disabling IPV6 remote desktop was working as expected.
Worth to give it a try.
You can either add the following to /etc/modprobe.d/blacklist:
blacklist ipv6

or do it properly via /etc/modpprobe.d/aliases.
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Good luck

---

