---
title: "Ubuntu server with CUPS"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by shanep-server on 2010-11-03
Ok I have a server running Ubuntu Server 10.04.1 LTS and a Desktop running Ubuntu 10.04.1 Desktop... I'm looking to setup a printer on the server. I would like this printer to serve all print requests on the network automatically.

I'm not sure what needs to be done to the server for this to work... or what needs to be done to my desktop for this too be done.

I'm not looking for the answer or a tutorial... I'm looking for useful information to help me accomplish this. Links to good sources would be great. Also any information you think might save me time figuring this out. IE the usual problems people have when attempting this.

I understand linux and networking pretty good... so something like.. don't do this... or remember to do this... an look at this thread / link. Thats what i'm really hoping to gain from this thread.

Thank you in advance for any help.

---

### Post by Dark_Stang on 2010-11-03
It's actually quite easy to share printers with via an Ubuntu box.
[https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)

---

### Post by papibe on 2010-11-03
> **Dark_Stang said:**
> It's actually quite easy to share printers with via an Ubuntu box.
[https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)

That is more suitable to share a Ubuntu attached printer to Windows clients.

If your network is just what you said (just Linux boxes), take a look at this:

[INDENT][Network Printing With Ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")
[Linux/UNIX: Sharing A CUPS Printer Queue]("http://www.cyberciti.biz/tips/linuxunix-sharing-a-cups-printer-queue.html")[/INDENT]

Good Luck!

---

### Post by HermanAB on 2010-11-04
Howdy,

The most important thing is to give the printer a simple name.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

---

### Post by drdos2006 on 2010-11-04
The server printer would be accessed from the desktop with the browser :
http://<server-IP-address>:631
The CUPS uses port 631

regards

---

### Post by shanep-server on 2010-11-04
My question is... I have the printer connected to a ubuntu server that does not have gnome or any other desktop running... So how to I access the System>Administration>Printing to change these settings? Or how would I go about opening up [http://localhost:631](http://localhost:631) from the server to change these settings to share my printer?

I usually change everything / access my server via ssh from my ubuntu desktop.

---

### Post by shanep-server on 2010-11-05
Ok I figured it out... found a tutorial though extremely out of date eventually gets up to speed pages deep in the thread.

We seriously need to get up to date How to's on ubuntu server editions. It seems that with the explosion of the linux desktop references to working with current server installs are fallin the the wayside.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=310450](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=310450)

Sharing printers after setting up CUPS is done via web browser from a machine on the network or over internet if setup correctly.

[http://ipaddress-of-server/631](http://ipaddress-of-server/631)

---

