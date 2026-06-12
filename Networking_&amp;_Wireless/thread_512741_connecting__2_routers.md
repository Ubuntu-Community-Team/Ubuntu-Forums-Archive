---
title: "connecting  2 routers?"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by jba6511 on 2007-07-29
here is the situation. I have an old Pentium 3 that is currently running xubuntu. It has no wireless card and I would really like to avoid buying one. I have a new D-Link DIR-625 that is my current router. I have an old Linksys WRT54G router not being used. I would like to hook the old computer into the linksys router and then have this router serve as an access point so that it will communicate with the new router (the d-link). This way I can share files between all computers and have everyone on the same network. Is this even possible?

The network is currently set up as follows:

                                                                    Cable Modem
                                                                              |
                                                                    D-Link DIR-625   192.168.1.1
                                                                  /             |             \                           \
                                           comp 1 (wired)  comp2 (wired)  xbox(wireless)  laptop(wireless)
                                           192.168.1.101     192.168.1.102      192.168.1.103     192.168.1.104

now I would like to add to this (if possible)  the Linksys router connecting to the D-Link router
so:

                                     D-Link DIR-625
                                               /
                                     Linksys Router 
                                              |
                                      comp 3 (192.168.1.15)

---

### Post by bbzbryce on 2007-07-29
> **jba6511 said:**
> This way I can share files between all computers and have everyone on the same network. Is this even possible?

Of course that'll work. Just turn off the DHCP server on the second router (linksys) and set it's operating mode to router rather than gateway.

---

### Post by jba6511 on 2007-07-29
i have done what you suggested but it still is not connecting. What am I doing wrong?

I have the old comp plugged from the ethernet port into the router ethernet port 1. I have disabled dhcp and set to router from gateway. I assigned the old comp a static IP of 192.168.1.109 and used subnet 255.255.255.0 and gateway 192.168.1.1. It just comes up looking for [www.google.com](www.google.com)... Any ideas?

---

### Post by bbzbryce on 2007-07-29
> **jba6511 said:**
> i have done what you suggested but it still is not connecting. What am I doing wrong?

I have the old comp plugged from the ethernet port into the router ethernet port 1. I have disabled dhcp and set to router from gateway. I assigned the old comp a static IP of 192.168.1.109 and used subnet 255.255.255.0 and gateway 192.168.1.1. It just comes up looking for [www.google.com](www.google.com)... Any ideas?

You aren't connecting through the wan connection are you? If you are you need to use one of the other ports. Also I forgot to mention but you might want to statically set the ip of the linksys router (192.168.1.2) so you can get to the configuration if needed. For testing I'd recommend removing the static IP; if you get an ip address then it'll be connected properly.

---

### Post by jba6511 on 2007-07-29
no I am not connecting through the wan connection. Ethernet from router to ethernet on computer. I will assign the router an IP of 192.168.1.2 if it is not to late. I could not log into 192.168.1.1 after I turned off dhcp and gateway and try a static IP. I was doing this on the live cd so I will give it ago once I get fiesty fawn installed on the old comp (xubuntu was taking forever to launch apps).

---

### Post by bbzbryce on 2007-07-29
> **jba6511 said:**
> no I am not connecting through the wan connection. Ethernet from router to ethernet on computer. I will assign the router an IP of 192.168.1.2 if it is not to late. I could not log into 192.168.1.1 after I turned off dhcp and gateway and try a static IP. I was doing this on the live cd so I will give it ago once I get fiesty fawn installed on the old comp (xubuntu was taking forever to launch apps).

Well just keep giving it a try. I have the same setup, but with two Linksys Wrt54G routers. For completeness here is my setup.

[LIST]
[*]Cable Modem plugged into wan port on Router 1.
[*]Port 1 of Router 2 plugged into Port 1 of Router 1.
[*]My computer plugged into port 2 of router 2.
[/LIST]

There are obviously other things connected however that's it in it's simplicity. Any actually I have a switch between the two routers which makes me think you might need a crossover cable between the two routers since my switch provides auto-uplinking. I think it's required between routers/switches/hubs that a crossover cable be used.

---

### Post by jba6511 on 2007-07-29
oh ok, I am trying to do the same as you except I do not want to plug the ethernet cable from router 1 to router 2, I would like this link to be wireless. Can it be done still?

---

### Post by bbzbryce on 2007-07-29
> **jba6511 said:**
> oh ok, I am trying to do the same as you except I do not want to plug the ethernet cable from router 1 to router 2, I would like this link to be wireless. Can it be done still?

Oh I see. It is possible using 3rd party firmware though I have not done this so I'm not of much help. I know you'll at least need third party firmware. Check out [DD-WRT]("http://www.dd-wrt.com/dd-wrtv2/ddwrt.php"). I use this firmware on one of my routers but not for this purpose, though if I remember correctly it does support this. There are other 3rd party firmwares  which you can find a list here:
[http://en.wikipedia.org/wiki/Wrt54g#Third-party_firmware_projects](http://en.wikipedia.org/wiki/Wrt54g#Third-party_firmware_projects)

Good luck.

Edit: Oh and what I said before should still apply (the router mode and disabling of DHCP).

---

### Post by jba6511 on 2007-07-30
flashed the router with DDT-WRT micro v23. Can someone please walk me through the rest now?

---

### Post by bbzbryce on 2007-07-31
> **jba6511 said:**
> flashed the router with DDT-WRT micro v23. Can someone please walk me through the rest now?

Sorry I can't help much more than this, but the following is the DD-WRT page which describes the process. I don't know if the Micro version supports the wireless bridge.

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by jba6511 on 2007-07-31
everything is up and running now. thanks for the help. Maybe this should be moved to the How-To or it should be written up.

---

### Post by bbzbryce on 2007-07-31
> **jba6511 said:**
> everything is up and running now. thanks for the help. Maybe this should be moved to the How-To or it should be written up.

Just out of curiosity does it work about as well as being connected via a wire or is there a noticeable latency increase. I guess it would be no different than connecting a laptop wired versus wireless, but you never know.

---

### Post by jba6511 on 2007-08-02
i have not noticed any latency, but if it there I am probably attributing it to the machine (old p3 533 MHz). So far it has worked out perfectly, except I have not tried to stream any video yet.

---

### Post by llewyn on 2008-06-27
Could you possibly post the procedure you used to accomplish connecting the two routers? I need to do the same thing and I am sure other people would find it useful. Thanks Larry

---

