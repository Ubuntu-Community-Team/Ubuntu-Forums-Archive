---
title: "New DSL modem not being recognized"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Bladeforger on 2009-02-06
After two weeks almost, and having Verizon techs out twice, it was finally determined that my old modem at the home computer was failing intermittently.  Verizon shipped me a new DSL modem, which arrived yesterday.

When I plugged it in and booted up, the connection applet recognized a connection.  Firefox didn't.  Synaptic Package Manager didn't either.

I ran the hardware test, which said I had a connection to the internet--jives with the applet.

I went to the Network Configuration: (System->Administration->) and played around a little.  Nothing worked.  I left it back as I found it.

Somehow, I need, apparently, to mount or configure something; and I can't figure out what.  Any help is appreciated.

Keith

---

### Post by adam_kimber on 2009-02-06
Are you using a USB DSL modem? Or one that is connected via ethernet (network)? 

Sounds to me like the modem and ubuntu are talking fine if the connection applet popped up. It also sounds like you are not being assigned an IP address for the remote connection by your ISP. This could be due to a number of things. Usually its down to a typo in the username or password fields or a wrong number in one of connection type fields in the modem.

---

### Post by Bladeforger on 2009-02-06
> **adam_kimber said:**
> Are you using a USB DSL modem? Or one that is connected via ethernet (network)? 

Sounds to me like the modem and ubuntu are talking fine if the connection applet popped up. It also sounds like you are not being assigned an IP address for the remote connection by your ISP. This could be due to a number of things. Usually its down to a typo in the username or password fields or a wrong number in one of connection type fields in the modem.

It'll connect with either USB or ethernet.  The old modem had both ports.  The new one came with a cable with an ethernet plug for the modem at one end and a split USB / ethernet at the other end.  I only plugged in the ethernet.

Username / password:  In the past I've never used one.  I don't use their email or their other fancy software--even when I had Winders.

---

### Post by handydan918 on 2009-02-06
just for fun, maybe you could post the output of ```
sudo dhclient
```

---

### Post by perlluver on 2009-02-06
All new Verizon modems, have to be set up with the Software that is available at [http://activatemydsl.verizon.com](http://activatemydsl.verizon.com).  Although anytime I have used it, it requires Windows to run.  You can also gain access to the modem via [http://192.168.1.1](http://192.168.1.1), and see if you can set up in there.

---

### Post by Bladeforger on 2009-02-07
> **adam_kimber said:**
> Usually its down to a typo in the username or password fields or a wrong number in one of connection type fields in the modem.

> **perlluver said:**
> All new Verizon modems, have to be set up with the Software that is available at [http://activatemydsl.verizon.com](http://activatemydsl.verizon.com).  Although anytime I have used it, it requires Windows to run.  You can also gain access to the modem via [http://192.168.1.1](http://192.168.1.1), and see if you can set up in there.
Aha!  the 192.168.1.1 address popped up a neat little configuration screen.  Since I couldn't remember my username and password, I called Verizon to ask.  They went ahead and stepped me through everything until it was working.  

For anyone looking at this after encountering the same problem:
Username defaults to "admin"; password defaults to "password".  That's apparently stored inside the modem somewhere.

There's a menu at the top for My Network.  Then you go to Network Connections.  Click on the Action icon by the broadband DSL description.  Then under VCs, you click the edit box.  You change protocol to "bridge"; change bridge mode to "routed bridge" and tell the DHCP client to obtain addresses automatically.  That's about the gist of the tough part.  Under the part where you see "My connection" you might have to click "renew".  At one point, the Verizon person had me get a paperclip and reset the modem.  It's hold the button inside the red circle in for a minute.  

The best news in all this is that the Verizon folks will help you, and they don't seem to be all fazed that someone isn't using Windows.  So, if the above doesn't help ya, give the DSL folks a phone call.

Thanks, bunches, to everyone that responded.  

OH!  Even with internet working, dhclient gives me this:

```
:~$ dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

```Don't know what that means, but this post is coming from the now-working internet connection.

Thanks, again!

---

### Post by halitech on 2009-02-07
it means that as a normal user you don't have permission to try and get an IP address. Next time run```
sudo dhclient
``` and it should work

---

### Post by freak42 on 2009-02-07
> **Bladeforger said:**
> 
For anyone looking at this after encountering the same problem:
Username defaults to "admin"; password defaults to "password".  That's apparently stored inside the modem somewhere.


By the way, for security reasons you (and everyone else that encounters this) should change to another password from this default "password".

---

### Post by Ellaine on 2009-02-07
This is interesting since with ATT DSL & a Cisco Router I must enable PPPoE in the router instead of obtain IP automatically.This requires my putting in my real name at att & the real password, then any probe on the internet can't find my computer, only the router.

---

### Post by kansasnoob on 2009-02-07
Speaking of At&T DSL, I've set up over 20 Ubuntu/Xubuntu machines on AT&T's $10.00 @ month DSL and they provide ZERO support for Linux so I always cart my "midtower" (I don't own a laptop) with XP still loaded in a multi-boot to complete the initial installation.

IMHO it's time for DSL and cable providers to wake up to the fact that Linux is continually gaining ground!

Now, I'm in rural Kansas, but I have a friend in Cleveland, Ohio that's having trouble with the cable to DSL transition! Not good!

After using Ubuntu for nearly a year I can guarantee that we're going to grow in numbers! I'm using Windows now to do taxes for free as a service to the elderly, disabled, and others living on low incomes and it's totally painful to revert to Windows!

---

### Post by handydan918 on 2009-02-07
I would suggest that all the dsl set up disk does is to use windows t configure the modem. If you know what settings you need to use, you should be able to do it without their silly disk.

---

### Post by Bladeforger on 2009-02-08
> **kansasnoob said:**
> 

After using Ubuntu for nearly a year I can guarantee that we're going to grow in numbers! I'm using Windows now to do taxes for free as a service to the elderly, disabled, and others living on low incomes and it's totally painful to revert to Windows!

I do taxes for a living, and I can tell you that it's now the ONLY reason that I still use Windows at all--via Win4Lin on the Ubuntu box (okay, Kubuntu with Gnome) at the office.  Almost everything else has been switched over to Linux, and with a little effort, everything else could be... and will be by the end of this year.  The tax software vendors will jump in line as soon as one or two of them make the effort and take the plunge...;)

---

