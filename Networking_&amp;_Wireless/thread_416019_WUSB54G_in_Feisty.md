---
title: "WUSB54G in Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by fob9546 on 2007-04-20
Hi there,

Awhile ago I installed ubuntu on my computer and for the life of me I couldnt get the wireless to work. I even tried Ndiswrapper and it didnt work out for me. Now I hear that they allow restricted drivers on Feisty, so I was wondering if the Linksys WUSB54G (ver. 4) would work out of the box without anything to install. If I still have to use ndiswrapper, I might skip using ubuntu for awhile.

Thanks for any answers

---

### Post by vronp on 2007-05-08
I have a WUSB54G v4 that works on Feisty "right out of the box"

Having said that, not all of my wireless gnome tools work as I expect.  For instance, Network Monitor shows ZERO signal strength for the networks in my area, even though I am close to them.

But,  considering the state of wi-fi support in Feisty, I consider myself luck.

> **fob9546 said:**
> Hi there,

Awhile ago I installed ubuntu on my computer and for the life of me I couldnt get the wireless to work. I even tried Ndiswrapper and it didnt work out for me. Now I hear that they allow restricted drivers on Feisty, so I was wondering if the Linksys WUSB54G (ver. 4) would work out of the box without anything to install. If I still have to use ndiswrapper, I might skip using ubuntu for awhile.

Thanks for any answers

---

### Post by gkinal on 2007-05-16
Odd!  Are you sure that you really have a connection if the signal strength shows as zero ?

When I had that set of circumstances, I was unable to connect, and ifconfig confirmed that I did not have a valid IP address from DHCP.

So I had to use NDISWRAPPER. I am still chasing down the problem that I do not get a valid connection if the Linksys is already plugged in during boot - I have to plug it in after booting. I think that may be a problem of conflicting drivers (default and NDISWRAPPER).

But when it works (plug in after boot), the NDISWRAPPER method seems to work pretty well, and reports decent signal quality (92% for a nearby AP, at 54 Mbps).

GK

---

### Post by vronp on 2007-07-04
Yes, I have a connection.  But, things are such that it's not quite as rosy a picture as I initially indicated.  I have to manually assign the IP address to get it to work.

It seems that dhclient is never able to get an IP address on it's own.

> **gkinal said:**
> Odd!  Are you sure that you really have a connection if the signal strength shows as zero ?

When I had that set of circumstances, I was unable to connect, and ifconfig confirmed that I did not have a valid IP address from DHCP.

So I had to use NDISWRAPPER. I am still chasing down the problem that I do not get a valid connection if the Linksys is already plugged in during boot - I have to plug it in after booting. I think that may be a problem of conflicting drivers (default and NDISWRAPPER).

But when it works (plug in after boot), the NDISWRAPPER method seems to work pretty well, and reports decent signal quality (92% for a nearby AP, at 54 Mbps).

GK

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

### Post by vronp on 2007-07-11
> **be4truth said:**
> I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

Is DHCP working ok for you or do you have to manually set the IP address?

thanks,
Dave

---

### Post by be4truth on 2007-07-16
DHCP is working fine.

---

