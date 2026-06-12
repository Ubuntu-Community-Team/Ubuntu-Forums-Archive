---
title: "asus p5b deluxe wifi on ubuntu"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by mind on 2007-05-27
hey guys,

i've got a asus p5b deluxe wifi-ap motherbord.
i've installed kubuntu feisty recently and i cant get my wireless to work.
i've been searching the forums for some kind of driver, but nothing seems to work out...

anyone else with this problem?
it's my first time with linux and i'm kindda lost with this... :(

thanks in advance :)

---

### Post by ryanVickers on 2007-05-27
In 7.04 they supposively fixed all the wireless problems, but I've noticed it to be no easier, or maybe worse in some cases, but here's what I did:

Go in to System > Administration > Network

check ON your wireless network (ra0)
go into it - properties

and uncheck the roaming mode.  Enter the name of the router (not the make/model, the name you gave it) and the key and type, and then probably pick Automatic Configuration (DHCP)

then in the ubuntu help files, look up the iwconfig command.  Using it in the command line, specify your mac address, channel/frequency, and key again.

now wait a while and it should randomly work after about 10 - 20 minutes.  From then on it should never be a problem again.

See if that works!

---

