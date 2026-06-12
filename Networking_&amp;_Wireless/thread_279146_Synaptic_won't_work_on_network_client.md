---
title: "Synaptic won't work on network client"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by Coburn on 2006-10-17
I'm setting up a home network w/ 2 computers that use Dapper, thru a 3com switch box (for expandability BTW).

So far I have the network up, but when I try to download packages with Synaptic on the client computer, it won't.

I had to configure the following programs to get the network to open:
System -> Administration -> Networking
System -> Preferences -> Network Proxy
System -> Administration -> Shared Folders --Never mind that it doesn't work until you:
<sudo> Nautilus -> <right-click> -> Share Folder
Firestarter

I also have Samba installed.  I haven't really configured it to any appreciable degree yet--there is a dual boot on the client, WinXPPro, and I want to learn how to config Samba to get that link going.  But that's another post.

The folders are shared w/ Samba.  I have a NFS share enabled in -> Shared Folders, but as we know, that doesn't turn on until you actually enable the folder...

I had to explicitly enable the connection in almost every available tab or window, using IP's 192.168.0.1/2, before it would work.  The only thing I don't have enabled, offhand, is System -> Preferences -> Network Proxy -> Socks host: --but I am using Automatic.  I know Network Proxy looks for the explicit settings anyway, but I haven't had time to google the default port for Socks host...

I also enabled all services in Firestarter -> Policy -> Services on the server computer--to the best of my recollection.

So, what do I need to enable so I can apt-get update and install via Synaptic on the client?

Thanks

---

### Post by handy on 2006-10-17
When I haven't been able to use the repo's it's been a DNS issue.

If you think it's worth a look, [go here]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2"), **Option 3**, **Post 13**.

All the best...

---

### Post by Coburn on 2006-10-18
Thanks, I'll take a look at that.

One thing at first impression--My ISP is Netscape and gives me different IP addresses every time I connect.  Local, Remote, and Primary.  You suggest prepending known IP's in resolv.conf...

I will look into disabling DNS itself, as some of the posts mentioned...

Thanks

---

### Post by handy on 2006-10-18
My ISP also changes the **DNS** addresses, but usually every couple of weeks.

What you could do is find out the range that they use & prepend them in **/etc/dhcp3/dhclient.conf**.

The **resolv.conf** is a temp file anyway, it is overwritten when you boot up.

The way I handle it, is when I notice that updates or the like are not working, I have a look at the current **DNS** addresses in my router & prepend them in **/etc/dhcp3/dhclient.conf** which only takes a couple of minutes.

So, don't prepend in the **resolv.conf**, go to the **dhclient.conf** would be my suggestion.

All this is due to cheap windoze centric routers or router/modems it would seem.

I have been having this problem for the last 11 months of using Ubuntu. **dhclient.conf** is the solution for me.  I hope it gets you out of trouble too...

---

### Post by Coburn on 2006-10-20
So is resolv.conf the reason that my DNS list reverts to one entry every time I reboot or reopen Sys > Admin > Networking?  FYI the entry is the primary IP I entered the first time I configured Networking...

---

### Post by handy on 2006-10-23
> **Coburn said:**
> So is resolv.conf the reason that my DNS list reverts to one entry every time I reboot or reopen Sys > Admin > Networking?  FYI the entry is the primary IP I entered the first time I configured Networking...

**No**, **resolve.conf** is rewritten everytime you reboot or bring the network down & up again.

**/etc/dhcp3/dhclient.conf**

Tells **/etc/resolv.conf** what to do, though I think the story is not quite that simple... ;)

---

