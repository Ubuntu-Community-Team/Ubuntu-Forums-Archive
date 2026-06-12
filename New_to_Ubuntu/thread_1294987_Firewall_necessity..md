---
title: "Firewall necessity."
date: 2009-10-18
forum: New to Ubuntu
---

### Post by melrokz on 2009-10-18
Is there a need for a firewall in Ubuntu? 
Which is the simplest firewall? 
i've tried Ipcop and Kmyfirewall. Both are nt tht usr friendly.
I need a firewall similar to zonealarm, since i use tht on WinXp.

---

### Post by coldReactive on 2009-10-18
ufw is installed in ubuntu by default, you can't see it though, you have to install the GUI if you want to see it with your eyes, rather than your brain.

But nothing is as complicated as zonealarm that is available for linux.

---

### Post by melrokz on 2009-10-18
what's the GUI called?

---

### Post by coldReactive on 2009-10-18
It should be gufw in synaptic.

---

### Post by cor2y on 2009-10-18
gufw [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Dont forget to enable ufw while it ships with ubuntu it must be enabled first before use.
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by 3rdalbum on 2009-10-19
> **melrokz said:**
> Is there a need for a firewall in Ubuntu?

By default, Ubuntu doesn't listen to any incoming ports. So you don't need a firewall unless you install anything that listens to incoming ports.

> Which is the simplest firewall?

On Linux, there is exactly one firewall: IPTables (netfilter). Ipcop, Kmyfirewall, Firestarter and UFW will just configure this firewall.

> i've tried Ipcop and Kmyfirewall. Both are nt tht usr friendly.
I need a firewall similar to zonealarm, since i use tht on WinXp.

You don't need anything like Zonealarm. gUFW is a good choice to configure a firewall, it's very easy to use. Just block all ports except the ones you want to pass through.

---

### Post by melrokz on 2009-10-20
how do i know what ports are being used by which program?

---

### Post by Peter09 on 2009-10-20
You need to find out more about the concept of ports and firewalls. Basically when you (say) start your web browser it opens a port and begins talking to the outside world. This is fine because any conversations started are between your web browser and the site that you initiated the conversation with.

Occasionally people want to be able to initiate a conversation from the outside world to the computer. This is normally not possible because all the ports are closed. To enable this you must open a port to allow the conversation to be started - this is where the risk is.

So - do you actually want to be able to start a conversation from the internet to your machine?

Also if you are going through a router, these normally have a firewall already configured, which does the same job as the one on your machine, so you will need to open ports on that if you want to have an Internet initiated conversation.  

Finally, some applications are designed to open ports and listen, you do not need to do that for them, such as openssh-server.

---

### Post by melrokz on 2009-10-20
if i want to allow google talk gadget through my firewall, that deny incoming connection, what should i do?

---

### Post by Peter09 on 2009-10-20
If your Gadget initiates the connection you do not need to do anything - normally the instructions will tell you what ports need to be open. Also on the local machine the Gadget will most probably open the port itself, you will need to open (and port forward) any router ports. Try the gadget first and see if it works without doing anything else.

---

### Post by melrokz on 2009-10-20
So, how to practically use gufw on ubuntu for allowing or blocking programs/sites?

---

### Post by carnagex420x on 2009-10-20
> **Peter09 said:**
> If your Gadget initiates the connection you do not need to do anything - normally the instructions will tell you what ports need to be open. Also on the local machine the Gadget will most probably open the port itself, you will need to open (and port forward) any router ports. Try the gadget first and see if it works without doing anything else.

The point of the firewall is to keep the junk out, the only ports you need to open are ports listening for a connection, like samba or if you were hosting a server or remoting in. You would be hosting a service, like a server, and that would be your reason to open a port. As long as your firewall is on you are not an easy target. If you find that a program or app isn't working, turn off the firewall and try again, if it now works then you will have to find the ports and open them. Like I said you shouldn't have to open a port unless you are hosting a service or listening for a connection on a server.

---

### Post by mcduck on 2009-10-20
> **melrokz said:**
> So, how to practically use gufw on ubuntu for allowing or blocking programs/sites?

You really can't, unless you can find out what ports those apps use to connect. But application-based filtering isn't really usually even necessity in Linux, since you don't have to worry about apps calling home etc, all applications come from trusted sources and therefore you can trust the apps themselves as well.

So, actually even needing a firewall is more of a special case than a standard, and having to limit a certain apps access (while not doing it based n ports/IP-addresses) would be even less common situation.

---

### Post by ibuclaw on 2009-10-20
> **melrokz said:**
> how do i know what ports are being used by which program?

```
sudo netstat -pan | grep ESTABLISHED
```

If you want to restrict applications, try configuring something like apparmor, which also comes with ubuntu (disabled by default).

Regards
Iain

---

