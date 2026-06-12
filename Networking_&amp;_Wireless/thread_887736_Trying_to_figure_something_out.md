---
title: "Trying to figure something out"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by LowSky on 2008-08-12
OK so I am at work, and when I use Windows, I need to have the correct proxy to get onto the internet, but on Ubuntu (while at work) I don't need my connection pointed to a proxy it just works  and I can view some website that can be blocked by the proxy, nothing bad just web mail and gaming websites.

So my question is how is Ubuntu getting an internet connection when Windows fails to? Why isn't Ubuntu effected by our Proxy settings, is it using a different port to get to the outside world or something? I know the Network Administrator uses Ubuntu as well, did he make some exception on web server for machines running the OS? I would ask him but he doesn't know I run Ubuntu at work and I don't really want him to. The desktop support guy does but he doesn't care.

Sorry, I'm horrible at networking stuff, I'm just trying to understand how this works. I am assuming it has something to do with ports because I can't use Thunderbird to look at my email while at work (using Ubuntu). At home it's fine.

---

### Post by LowSky on 2008-08-14
bump?

---

### Post by bgerlich on 2008-08-14
Check the TCP/IP settings in Windows. It may be preconfigured to use static settings. Additionally there is a DHCP server running on the network providing DHCP config for machines that weren't preconfigured. That is the first thing that comes to my mind. You also may have some software running on Windows that manages your connection or/and monitors the network/your activity. Try reinstalling Windows using a vanilla installation media.

---

### Post by TwiceOver on 2008-08-14
THis is a function of Group Policy.  The server at your work is saying "Windows Computers... I am your god.  Force the user to use this proxy and don't let them change it".  Ubuntu looks at that and says "Umm no, I don't think so".

In reality your Ubuntu machine does not even see the request for group policy enforcement.  All sorts of things happen on your windows machine when you press ctrl+alt+del and logon.  Scripts are processed to map network drives and printers and also group policy tells your system what the administrator will/won't allow you to do.  Proxy settings are assigned in group policy and not during DHCP request.

---

### Post by Proot on 2008-08-14
Can you get to the lan settings in internet explorers options?
**ie7:** tools>internet options>connections tab>lan settings

If you can and the proxy option is ticked try unticking it and see how you get on.

---

### Post by LowSky on 2008-08-14
> **Proot said:**
> Can you get to the lan settings in internet explorers options?
**ie7:** tools>internet options>connections tab>lan settings

If you can and the proxy option is ticked try unticking it and see how you get on.
While using Windows if you untick it the world wide web is completely unavailable.

---

### Post by LowSky on 2008-08-14
> **bgerlich said:**
>  Try reinstalling Windows using a vanilla installation media.

I would love to do this but its a work PC.. They don't even know Ubuntu is on it. At least no one has said anything. If I have to turn it in, im just going to delete Ubuntu and resize the partition back to 100% Windows.

Thanks for the info guys. :guitar:

---

