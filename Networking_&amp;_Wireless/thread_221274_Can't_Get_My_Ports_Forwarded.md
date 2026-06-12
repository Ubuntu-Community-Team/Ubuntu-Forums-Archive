---
title: "Can't Get My Ports Forwarded"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by Epperly on 2006-07-22
I've tried a lot of things to get em working and Idk but they just won't (I tried on Windows mainly, if it makes a difference).

Can anyone help me? Suggestions please

Thanks!

[edit (taken from bottom post)]Ok, well I have made a static IP (192.168.2.100), router's local IP is 192.168.2.1, I have a linksys router model # BEFW11S4 version 4 with up-to-date firmware.

In the router setup the internet connection type is obtain IP automatically, in the port range forwarding I have AZU(azureus) port 53497 to 53497 on both protocols with the IP 192.168.2.100 on enable and VNC on 5900 to 5900 with same settings, none of them work.

When I go here [https://www.grc.com/x/portprobe=53497](https://www.grc.com/x/portprobe=53497) and same with 5900, it says they are closed, and when I go to azureus and hit NAT test it says NAT error (meaning 53497 isn't open), and I have followed portforward.com as best as I could.

I've had my ports forwarded before, but the DSL went down in my area and before I found out and noticed it wasn't working I tried to fix it, then when I found out it went down locally I had to reset everything with Embarq(ISP) and Linksys.

If anyone can help that'd be great(I'm also up for remote desktop if anyone thinks they know how they can fix my problem)

Thanks!
[/edit]

---

### Post by tturrisi on 2006-07-22
and this has what exactly to do w/ wifi?

---

### Post by Epperly on 2006-07-22
forwarding is done through a wireless router..

---

### Post by tturrisi on 2006-07-23
understood...but port forwarding really has nothing to do w/ wifi, it has to do with the router settings.  With that in mind, what router do you have and have you looked at the router manual?  Most router prot forwarding is cut+dry and easy to do.  Just remember to use a static ip address for your computer & not dhcp, else at some point in the future the port forwarding will break (when the computer's dhcp address changes).

---

### Post by Epperly on 2006-07-23
Ok, then where would I put this thread? Cause I wasn't really sure anyway, sorry.

I have a linksys and have tried just about everything to get it to work, static IP, no antivirus/firewall(linux), portforward.com... I'm thinking I might just try and start over get on the phone with linksys/sprint(embarq), and reset everything. Idk.

---

### Post by matthew on 2006-07-23
I moved the thread to a better location (networking). I think you will have a better response if you are more descriptive in what you are attempting, what you have done so far, how things have failed (what error messages you have received, etc.) and so on. The more detail you give the quicker and more likely you are to get help. :) Good luck!

---

### Post by Epperly on 2006-07-23
Ok, well I have made a static IP (192.168.2.100), router's local IP is 192.168.2.1, I have a linksys router model # BEFW11S4 version 4 with up-to-date firmware.

In the router setup the internet connection type is obtain IP automatically, in the port range forwarding I have AZU(azureus) port 53497 to 53497 on both protocols with the IP 192.168.2.100 on enable and VNC on 5900 to 5900 with same settings, none of them work.

When I go here [https://www.grc.com/x/portprobe=53497](https://www.grc.com/x/portprobe=53497) and same with 5900, it says they are closed, and when I go to azureus and hit NAT test it says NAT error (meaning 53497 isn't open), and I have followed portforward.com as best as I could.

I've had my ports forwarded before, but the DSL went down in my area and before I found out and noticed it wasn't working I tried to fix it, then when I found out it went down locally I had to reset everything with Embarq(ISP) and Linksys.

If anyone can help that'd be great(I'm also up for remote desktop if anyone thinks they know how they can fix my problem)

Thanks!

---

### Post by cmfarley19 on 2006-07-23
I am having a similar problem.

I wrote a script to forward ports via ssh
```
#!/bin/bash

sudo ssh -p 443 -L 5906:192.168.0.101:5900 -L 26:pop.mailserver.com:25 -L 112:smpt.mailserver.com:110 uname@192.168.0.163
```

When I try to send mail from thunderbird on port 26 I get the following message:
```
channel 7: open failed: administratively prohibited: open failed
```

This worked fine in breezy.

Any thoughs?

---

