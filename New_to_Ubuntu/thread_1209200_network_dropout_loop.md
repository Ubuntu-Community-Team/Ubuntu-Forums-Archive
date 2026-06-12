---
title: "network dropout loop"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by clt on 2009-07-10
Hey guys, I tried searching for a solution to this problem but I couldn't find one.

I'm running kubuntu, 8.10 I think, and using knetworkmanager to manage the network. I haven't turned it on in a while (it's used as our file server but has been out of use). I've got a new ISP and a new adsl2 wifi router that I'm using for our network.

The problem is that when I plug a network cable into the server, and add a new connection in knetworkmanager, it tries to connect but is stuck in a loop where it shows the globe and then the 'trying to connect to a network' icon. Every second or less it switches between these 2 icons. So it seems like it's connecting then dropping out. I tried adding a wifi connection and connecting to that, but the same thing happens, but instead of the globe it shows the successfully connected wifi icon. It only does this when trying to connect to a network.

Any ideas how I could resolve this without an internet connection on that pc?

---

### Post by Peter09 on 2009-07-10
Check that your router has DHCP enabled and that your server uses DHCP.

If you have a static IP setup on your server, make sure if reflects the scheme you have on your router.

---

### Post by clt on 2009-07-10
How do I check that my server is using DHCP? Also, I haven't set static IPs or anything.

---

### Post by superprash2003 on 2009-07-10
post output of **ifconfig** from your terminal

---

### Post by Peter09 on 2009-07-10
Right click on the network Icon, select edit connection and the interface. Click the ip4 tab and under there you should see that DHCP is specified.

You need to do the same for your router.

---

### Post by clt on 2009-07-10
Well, just out of nowhere it kinda started working. Well, ethernet still isn't working at all, but the icons aren't stuck in a loop any more, it just goes straight to the globe icon and doesn't try to connect at all. Wireless on the other hand, when I create a new connection, some times it will connect, and it will be on the network. But the internet is EXTREMELY slow on that PC for some reason.

Maybe an update to the latest kubuntu with all the other updates might fix it, but the internet is running at about 1KB per second!

Any ideas?

And I couldn't find anything about DHCP in my network settings. I found 'manual IP settings' options, but nothing with DHCP

---

### Post by clt on 2009-07-11
I have no idea how to get my server on the network with a network cable, does anyone know what's going on?

---

### Post by clt on 2009-07-13
Well it's been resolved now. I think it was the wifi card interfering with the on-board network card.

---

