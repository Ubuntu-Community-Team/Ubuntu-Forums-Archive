---
title: "Trying to change DNS Server"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Thelasko on 2009-09-21
I'm trying to change my DNS server across my whole network.  I've changed it in my router, but I'm pretty sure it's controlled by my cable modem.  I know I've accessed the settings screen for the cable modem before, but I can't find the address for it.  Does anybody know how to figure that out?  All of my network settings point me to the router.  I can't find anything in the router settings that points me to the modem.

---

### Post by LewRockwell on 2009-09-21
your ISP will serve up default DNS servers

Comcast Chicago sometimes serves up these:

68.87.72.134

68.87.77.134

your router/gateway will be the place to check on these and possibly change them

cable modems and DSL modems may or may not provide router/gateway service to your LAN

we prefer to have a separate modem and router as opposed to a single device

these devices should always be utilizing the latest firmware releases as the manufacturers update/upgrade firmware as security vulnerabilities arise

.

---

### Post by Thelasko on 2009-09-21
> **LewRockwell said:**
> your router/gateway will be the place to check on these and possibly change them.
Yeah, I already tried that and it didn't work.  I think the DNS settings are in the cable modem.  How can I find it's IP address?

---

### Post by scrooge_74 on 2009-09-21
But can't you config your router to use which ever DNS you want? I do that with mine. 

TO get to your cable modem you could hook a PC directly to the ethernet port of it instead of your router, if it gives the PC and address like 192.168.1.100, then most likely the cable modem address is 192.168.1.1

---

### Post by Thelasko on 2009-09-21
> **scrooge_74 said:**
> But can't you config your router to use which ever DNS you want? I do that with mine. 

TO get to your cable modem you could hook a PC directly to the ethernet port of it instead of your router, if it gives the PC and address like 192.168.1.100, then most likely the cable modem address is 192.168.1.1

I've tried configuring the router, but it doesn't seem to work.  I'm switching to OpenDNS and when I go to the OpenDNS homepage it says "oops you aren't using OpenDNS yet"

I've thought about connecting directly to the cable modem's ethernet port. but haven't tried that yet.

---

### Post by LewRockwell on 2009-09-21
> **scrooge_74 said:**
> But can't you config your router to use which ever DNS you want? I do that with mine. 

TO get to your cable modem you could hook a PC directly to the ethernet port of it instead of your router, if it gives the PC and address like 192.168.1.100, then most likely the cable modem address is 192.168.1.1

yes, modems will probably require a direct hardwire connection from your pc to get to the device's interface

we do not recommend doing this while the modem is connected to the internet unless the modem is also a gateway/router complete with a hardware firewall

if you don't have the documentation that may have shipped with your unit then a brief search across the interwebs is probably in order
(same goes for your router/gateway as well)

.

---

### Post by LewRockwell on 2009-09-21
it might be helpful to us to know which devices you are working with

it might save time and effort if we could just post a link like this:

[http://en.wikipedia.org/wiki/Linksys_WRT54G_series](http://en.wikipedia.org/wiki/Linksys_WRT54G_series)

or maybe this:

[http://en.wikipedia.org/wiki/Dd-wrt](http://en.wikipedia.org/wiki/Dd-wrt)

or even this:

[http://blog.mattventura.net/2009/08/17/a-mostly-complete-openwrt-tutorial/](http://blog.mattventura.net/2009/08/17/a-mostly-complete-openwrt-tutorial/)

Matt's tutorial will reflect similarily on other devices as well

.

---

### Post by Thelasko on 2009-09-21
I've got a WRT54G with v8.00.6 firmware and an Arris [TM502G]("http://www.arrisi.com/support/guides/_docs/TM502_User_Guide.pdf") modem.

---

### Post by Thelasko on 2009-09-21
I should also mention that the DNS settings on my router were previously set to 0.0.0.0 by default.

---

### Post by kevdog on 2009-09-21
Can't you change it in the router such as what is shown in the screen cap below?

---

### Post by Thelasko on 2009-09-21
> **kevdog said:**
> Can't you change it in the router such as what is shown in the screen cap below?

I can, but it doesn't do anything.

---

### Post by Thelasko on 2009-09-21
Could it be because my router is set to "Automatic Configuration -DHCP"?

---

### Post by Thelasko on 2009-09-21
I'm an idiot and didn't restart the computers on my network.  That fixed it!

---

### Post by LewRockwell on 2009-09-21
[http://forums.opendns.com/comments.php?DiscussionID=2216](http://forums.opendns.com/comments.php?DiscussionID=2216)

[http://blogs.sun.com/ldcubed/entry/opendns_very_kewl](http://blogs.sun.com/ldcubed/entry/opendns_very_kewl)

[http://www.youtube.com/watch?v=PbZxSNu8wdk](http://www.youtube.com/watch?v=PbZxSNu8wdk)

[http://forums.linksysbycisco.com/linksys/board/message?board.id=Wireless_Routers&thread.id=138794](http://forums.linksysbycisco.com/linksys/board/message?board.id=Wireless_Routers&thread.id=138794)

[http://www.dslreports.com/forum/r22894224-OpenDNS](http://www.dslreports.com/forum/r22894224-OpenDNS)

[http://www.ehow.com/how_4894384_block-websites-wrtg-v.html](http://www.ehow.com/how_4894384_block-websites-wrtg-v.html)

[http://www.dd-wrt.com/phpBB2/viewtopic.php?p=337653&sid=d0b6e78ad348ab2a453224a2b852907f](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=337653&sid=d0b6e78ad348ab2a453224a2b852907f)

[http://www.dd-wrt.com/phpBB2/viewtopic.php?p=84121&sid=b87749219f249e6b6a83121b41047065](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=84121&sid=b87749219f249e6b6a83121b41047065)

[https://www.opendns.com/start/device/linksys](https://www.opendns.com/start/device/linksys)

.

---

### Post by LewRockwell on 2009-09-21
> **Thelasko said:**
> I'm an idiot and didn't restart the computers on my network.  That fixed it!

thanks for letting us know what fixed your trouble-call

.

---

