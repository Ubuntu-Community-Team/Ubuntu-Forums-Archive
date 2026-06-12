---
title: "systemd-networkd overriding networkmanager settings"
date: 2023-01-08
forum: Networking &amp; Wireless
---

### Post by jfaberna on 2023-01-08
I installed Ubuntu server 22.10 on a Raspberry Pi 4 and it seems to come with systemd-networkd. I then installed ubuntu-mate-desktop. I did this because for my setup Ubuntu Desktop comes with Gnome which is too heavy for this application and it's the only choice except Server. 

So once Mate was running on server the WiFi was fine, but I could not use the Network gui to set eth0 to static or local-link. It basically did what netplan had built sometime during the Server 22.10 setup.

How can I get this to a point where NetworkManager can be used to setup both WiFi and ethernet (eth0)? If I have to reinstall Server and do something before installing ubuntu-mate-desktop that would be great.

---

### Post by TheFu on 2023-01-08
> **jfaberna said:**
>  How can I get this to a point where NetworkManager can be used to setup both WiFi and ethernet (eth0)? If I have to reinstall Server and do something before installing ubuntu-mate-desktop that would be great.

You installed Server and seem surprised when it wants to use server methods to manage the networking?
If you want a desktop, install a desktop.  That will solve this.

It might be possible to tell the system, via netplan, to use network-manager as the renderer.  I've never done that, since I purge network-manager* from all my systems.  The netplan config files are in /etc/netplan/.  Make a backup of the files there before screwing around with them.  At a minimum, you'll need to change the "renderer" line.
[https://ubuntu.com/core/docs/networkmanager/networkmanager-and-netplan](https://ubuntu.com/core/docs/networkmanager/networkmanager-and-netplan) might help.  It just feels so very wrong to suggest someone install any snap program.  I feel bad even pointing to documentation with that suggestion.  I don't think it is strictly required.

---

### Post by jfaberna on 2023-01-08
> **TheFu said:**
> You installed Server and seem surprised when it wants to use server methods to manage the networking?
If you want a desktop, install a desktop.  That will solve this.


I think I mentioned for the RPI4 Ubuntu (Canonical) only provided Desktop and Server at this time.  To get any other Desktop you have to work at it. Sorry to not conform to your standards.

I figured it out.

---

### Post by TheFu on 2023-01-08
> **jfaberna said:**
> I think I mentioned for the RPI4 Ubuntu (Canonical) only provided Desktop and Server at this time.  To get any other Desktop you have to work at it. Sorry to not conform to your standards.

I figured it out.

Not my standards.  22.10 isn't an LTS, so support will end in June 2023. Images for it aren't created for many downstream releases. However, 
[https://ubuntu-mate.org/download/arm64/](https://ubuntu-mate.org/download/arm64/) has the 22.04.1 release, which I bet could be upgraded to 22.10, if you wanted to live dangerously. Release upgrades always leave a big of cruft behind.  Beware that non-LTS releases are were Canonical tries things that aren't always as stable as we'd like. Nobody recommends them for production use.

BTW, it would be helpful if you posted an explanation for what worked for your needs, since there are probably 100+ other people with a similar desire. Also, it would help them and others to find this thread if you would please use the "Thread Tools" button and mark it as "SOLVED".  That simple action helps the community greatly.

---

### Post by jfaberna on 2023-01-08
1. Not my standard either. Just helping a friend who wants Ubuntu on a RPI 4 project. My standard is Archlinux via EndeavourOS.

2. Maybe not a Solution, but this seemed to work for me:

Create the file: /etc/netplan/01-network-manager-all.yaml 
And put this in it:
```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```
It"s what Ubuntu Desktop has in the same directory.

---

### Post by TheFu on 2023-01-08
So, SOLVED?  
Seems to be similar to what I suggested in post #2.  You'd probably already been searching for answers and found it independently.

---

