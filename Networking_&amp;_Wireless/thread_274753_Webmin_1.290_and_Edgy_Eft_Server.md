---
title: "Webmin 1.290 and Edgy Eft Server"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2006-10-10
Hi all,

Not sure if this is the right place to open this thread but here goes...

I am setting up a test Edgy Eft server and I have configured OpenSSH-Server and this works well from both linux and windows clients. I have installed Webmin_1.290 on the server and the install went smoothly with no errors. Once it had finished it told me that to access the server just redirect a browser to [http://ipaddress:10000](http://ipaddress:10000). This is where the problem lies.

As the default install of Ubuntu has no open ports, I need to open port 10000. So my question is how do I do this with iptables? I have done an extensive search on the net and to be honest I am confused. There is no gui installed so everything is done via the command line, so telling me to install lokki or guarddog isn't going to work.

Cheers in advance for any help

EmyrB

---

### Post by mips on 2006-10-10
Firewall Builder might be helpfull. [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

It's in the repos as far as i'm aware. Provides a nice gui to create just about any firewall config file like iptables for example.

---

### Post by EmyrB on 2006-10-10
Thanks for that Mips, but there is no gui installed on the server, just pure command line. Would it be better to install gnome-core on the server so I can then install the firewall gui's or is there an easy way to configure iptables through the command line and then get it working?

---

### Post by mips on 2006-10-10
> **EmyrB said:**
> Thanks for that Mips, but there is no gui installed on the server, just pure command line. Would it be better to install gnome-core on the server so I can then install the firewall gui's or is there an easy way to configure iptables through the command line and then get it working?

Let me try and explain a bit better.

You don't have to install fwbuilder on the server. Install it on any Linux/Mac/Windows PC. On that PC you then use the software to create the config file for your intended system (iptables, ipfilter, OpenBSD pf, Cisco PIX, checkpoint, netnice etc)

If you read the documentation on the site you will see it is a great gui tool that suites many firewalls.

---

### Post by EmyrB on 2006-10-10
Ahh, right. Ok, I shall give that a shot and see what comes of it, cheers Mpis :)

As a side question, I have no experience of a *nix server what so ever, I have only ever been exposed to Windows Server enviroments, tell me is it worth putting a gui on the server, say Xfce as it is light and not so resource hungry or am I forever in the clutches of MS?

---

### Post by mips on 2006-10-10
I don't have any server experience either but I would not install X on a server. I would just use something like webmin.

---

### Post by EmyrB on 2006-10-10
My thoughts exactly. We did have a Novell server and that had no gui either. Well, I shall download Firewall builder and I shall post my results here.

Thanks Mpis :)

---

### Post by mips on 2006-10-10
Geez, I did novell traing years ago. cannot remember anything. then they brought out that remote management console to add users etc. Just shows you how long ago it was.

---

### Post by EmyrB on 2006-10-11
Ok. I downloaded Firewall Builder and I managed to kill the server as I somehow closed all ports to the point that even port 80 wouldn't talk to the outside world :\

I think for now I shall install a gui on it and download a gui based firewall front end and configure it that way to get webmin to work. Firewalls were never my strongest point as we use Sonicwalls at work which are child's play compared to this :(

Any help with Firewall Builder would be really greatfull :)

---

### Post by EmyrB on 2006-10-11
Ok, an update on my situation. I gave up with Firewall Builder as it seems to be very complicated in the way you build the policies for the firewall and I found a simple little script called ubuntu-firewall from Robert Pectol's web site.

I have set port 22, 80 and 10000 to be opened and still I cannot connect to the server through a browser (at least I didn't kill the ports like I did the last time :))

Man this is getting to be a drag now, why is something so simple so hard to achieve ](*,)

---

### Post by EmyrB on 2006-10-12
Sorted XD

I did a manual download of webmin-1.300 and ran it's own setup script and it worked a treat.

Cheers Mpis for all your help

---

